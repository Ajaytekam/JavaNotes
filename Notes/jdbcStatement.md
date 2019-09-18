# JDBC Statement:

Types of Statement :-  
* 1. **Statement**
* 2. **PrepareStatement**
* 3. **CallableStatement**


## 1. Statement

The Statement interface provides methods to execute queries with the database. It provides factory method to get the object of ResultSet. Methods of Statement:
* **executeQuery :** It is used to execute SELECT query. It returns the dataset as object of ResultSet.
```java
public ResultSet executeQuery(String sql);
```
* **executeUpdate :** It is used to execute specified query and return integer value which is the number of affected columns. It may be create, drop, insert, update, delete etc.
```java
public int executeUpdate(String sql);
```
* **execute :** Execute query on the server and return only boolean value, and does not return any other data.
```java
pubic boolean execute(String sql);
```
### Example of `executeUpdate()` :
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;
import java.sql.SQLException;

class dbConnect {  
    public static void main(String args[]){  
        Connection con = null;
		Statement stmt = null;
		String name = "Ajay kumar";
		int id = 1001;
		int retVal=0;
		try{  
            Class.forName("oracle.jdbc.driver.OracleDriver");  
            con=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","AJAY1","12345");
			con.setAutoCommit(false);
            stmt=con.createStatement();  
            String updateSQL="update emp set name = " + name + " where id = " + id;
			retVal = stmt.executeUpdate(updateSQL);
		}catch(SQLException e) {
			try{if(con!=null)con.rollback();}catch(Exception e1){e1.printStackTrace();}
			e.printStackTrace();
		}catch(Exception e){ 	
			try{if(con!=null)con.rollback();}catch(Exception e2){e2.printStackTrace();}
			e.printStackTrace();
		}finally{
			try{
				if(con!=null) {
					con.commit();
					System.out.println(retVal+" number of rows updated.");
				}
				if(stmt!=null)stmt.close();
				if(con!=null)con.close();
			}catch(Exception e){e.printStackTrace();}
		}
    }
}
```
## 2. PreparedStatement :

The PreparedStatement interface is a subinterface of Statement. It is used to execute parameterized query. Methods of `PreparedStatement()` interface are :
* `setInt(int paramIndex, int value)` : sets the integer value to the given parameter index.
* `setString(int paramIndex, String value)` : sets the String value to the given parameter index.
* `setFloat(int paramIndex, float value)` : sets the float value to the given parameter index.
* `setDouble(int paramIndex, double value)` : sets the double value to the given parameter index.

Now lets see the implementation of PreparedStatement:
```java
String sqlUpdate ="update emp set name = ? where id = ?";  
```
at above we are passing parameter (?) for the values. Its value will be set by calling the above setter methods. For example the first argument is String type (name) so we use `setString(1, name)` where `1` denotes the parameter index, similarly for second method (id) we use `setInt(2, value)` where `2` is parameter index. Example :
```java
String sqlUpdate ="update emp set name = ? where id = ?";
```
Now lets see the full example code :
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

class dbConnect {  
    public static void main(String args[]){  
        Connection con = null;
		PreparedStatement pstmt = null;
		int retVal=0;
		try{  
            Class.forName("oracle.jdbc.driver.OracleDriver");  
            con=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","AJAY1","12345");
			con.setAutoCommit(false);
            pstmt=con.prepareStatement("update emp set name = ? where id = ?");
			pstmt.setString(1, "Ajay kumar");
			pstmt.setInt(2, 1001);
			retVal = pstmt.executeUpdate();
		}catch(SQLException e) {
			try{if(con!=null)con.rollback();}catch(Exception e1){e1.printStackTrace();}
			e.printStackTrace();
		}catch(Exception e){ 	
			try{if(con!=null)con.rollback();}catch(Exception e2){e2.printStackTrace();}
			e.printStackTrace();
		}finally{
			try{
				if(con!=null) {
					con.commit();
					System.out.println(retVal+" number of rows updated.");
				}
				if(pstmt!=null)pstmt.close();
				if(con!=null)con.close();
			}catch(Exception e){e.printStackTrace();}
		}
    }
}
```

## 3. CallableStatement:

The CallableStatement interface is used to call the stored procedures and functions.


