# -package com.student.util;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DbUtil {
        private String dbUrl="jdbc:mysql://localhost:3306/db_student";
        private String user="root";
        private String password="123456";
        private String jdbcName="com.mysql.jdbc.Driver";
        public Connection getCon() throws Exception{
                Class.forName(jdbcName);
                Connection con=DriverManager.getConnection(dbUrl, user, password);
                return con;
        }
        public void close(Connection con)throws Exception{
                if(con!=null){
                        con.close();
                }
        }
        public static void main(String[] args){
                Connection con=null;
                try {
                        con = new DbUtil().getCon();
                        System.out.println(con);
                } catch (Exception e) {
                        e.printStackTrace();
                }finally{
                        if(con!=null){
                                try {
                                        con.close();
                                } catch (SQLException e) {
                                        e.printStackTrace();
                                }
                        }
                }
        }
}
