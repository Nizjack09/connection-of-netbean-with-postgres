# connection-of-netbean-with-postgres

package databasedemo;

import java.sql.Connection; import java.sql.DriverManager; import java.sql.PreparedStatement; import java.sql.ResultSet; import java.sql.SQLException; import java.sql.Statement; import java.util.Scanner; import java.util.logging.Level; import java.util.logging.Logger;

public class DatabaseDemo {

public static void main(String[] args) {
    try {
        Connection conn = DriverManager.getConnection("jdbc:postgresql://localhost:5432/DBname","postgres","password");
// Statement st = conn.createStatement(); // ResultSet rs = st.executeQuery("SELECT * FROM EVENINGSTUDENTS"); // while(rs.next()){ // System.out.println("ID: "+rs.getInt(1)); // System.out.println("NAME: "+rs.getString(2)); // } Scanner sc = new Scanner(System.in); System.out.println("Enter your ID"); int id = sc.nextInt(); System.out.println("Enter your name:"); String name = sc.next(); // st.execute("INSERT INTO EVENINGSTUDENTS VALUES ("+id+",'"+name+"')"); PreparedStatement pst = conn.prepareStatement("INSERT INTO EVENINGSTUDENTS VALUES(?,?)"); pst.setInt(1, id); pst.setString(2, name); pst.execute(); conn.close(); } catch (SQLException ex) { ex.printStackTrace(); } }

}
