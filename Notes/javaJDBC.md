## Java JDBC

JDBC stands for Java Database Connectivity. JDBC is a Java API to connect and execute the query with the database. JDBC API uses JDBC drivers to connect with the database. There are four types of JDBC drivers:

* **JDBC ODBC(Open Database Connection)**
* **JDBC Native API**
* **JDBC Net Pure**
* **JDBC Pure Java**

The JDBC API is used to access tabular data stored in any relational database. By the help of JDBC API, we can save, update, delete and fetch data from the database. The `java.sql` package contains classes and interfaces for JDBC API. Main Classes of JDBC API are :
 
* DriverManager 
* Connection
* Statement
* ResultSet
* SQLException
* Types

## Implementing JDBC Drivers :

The Steps for implementing JDBC Drivers are as follows :

### Register the Driver class

The `forName()` method of Class class is used to register the driver class. This method is used to dynamically load the driver class. Syntas :
```java
public static void forName(String className);
```
It throws `ClassNotFoundExecption`.  

**Example :** 

* For oracle database driver 
```java
class.forName("oracle.jdbc.driver.OracleDriver");  
```
* For mysql database driver
```java
class.forName("com.mysql.jdbc.Driver");
```
* for MSSQL Server
```java
class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
```
It throws `ClassNotFoundException` exception.

### Create the connection object

The `getConnection()` method of `DriverManager` class is used to establish connection with the database. Syntax :
```java
public static Connection getConnection(String url,String name,String password);
```
Where : name and password are the credentials to access the databasem, and **url** is the usr of database server which are :   

* For Oracle Database : 
```java
url = "jdbc:oracle:thin:@localhost:1521:xe";
```
* For MySQL database : 
```java
url = "jdbc:mysql://localhost:3306/database_name";
```
* For MSSQL database :
```java
url = "jdbc.sqlserver://localhost:1433;databaseName=XYZ;integratedSecurity=true";
```
It throws `SQLException`.   

Example :
```java
Connection con = DriverManager.getConnection(url, user, password);
```
### Create a statement Object :

The createStatement() method of Connection interface is used to create statement. The object of statement is responsible to execute queries with the database. Syntax :
```java
public Statement createStatement();
```
Example :
```java
Statement stmt = con.createStatement();
```
It throws `SQLException`.

### Execute the Query :

The `executeQuery()` method of Statement interface is used to execute queries to the database. This method returns the object of `ResultSet` that can be used to get all the records of a table. Syntax :
```java
public ResultSet executeQuery(String sql); 
```
Example :
```java
Connection con = DriverManager.getConnection(url, user, password);
Statement stmt = con.createStatement();
ResultSet rs = stmt.executeQuery("select * from table_name"); 
while(re.next()) {
	System.out.println(rs.getInt(1)+" "+rs.getString(2));
} 
```
It throws `SQLException`.

### Closing the Connection :

By closing connection object statement and ResultSet will be closed automatically. The close() method of Connection interface is used to close the connection.
```java
public void close();
```
Exmaple :
```java
con.close();
```
It throws SQLException.

# Example of Java JDBC

## Example of Oracle Database :
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;
import java.sql.ResultSet;
import java.sql.SQLException;

class dbConnect {  
    public static void main(String args[]){  
        Connection con = null;
		Statement stmt = null;
		ResultSet rs = null;
		try{  
            Class.forName("oracle.jdbc.driver.OracleDriver");  
            con=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","AJAY1","12345");  
            stmt=con.createStatement();  
            rs=stmt.executeQuery("select * from emp");  
            System.out.println("\nEmployeeID\tEmployeeName\tJobTitle");
            while(rs.next()) {  
                System.out.println("-------------------------------------   -----");
                System.out.println(rs.getInt(1)+"\t|\t"+rs.getString(2)+"\t|\t"+rs.getString(3));  
            }
		}catch(SQLException e) {
			e.printStackTrace();
		}catch(Exception e){ 	
			e.printStackTrace();
		}finally{
			try{
				if(rs!=null)rs.close();
				if(stmt!=null)stmt.close();
				if(con!=null)con.close();
			} catch(Exception es) {
				es.printStackTrace();
			}
		}
    }
}
```

## Example of MySQL Database :
```java
mport java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;
import java.sql.ResultSet;
import java.sql.SQLException;

class dbConnect {  
    public static void main(String args[]){  
        Connection con = null;
		Statement stmt = null;
		ResultSet rs = null;
		try{  
            Class.forName("com.mysql.jdbc.Driver");  
            con=DriverManager.getConnection("jdbc:mysql://localhost:3306/database_name","AJAY1","12345");  
            stmt=con.createStatement();  
            rs=stmt.executeQuery("select * from emp");  
            System.out.println("\nEmployeeID\tEmployeeName\tJobTitle");
            while(rs.next()) {  
                System.out.println("-------------------------------------   -----");
                System.out.println(rs.getInt(1)+"\t|\t"+rs.getString(2)+"\t|\t"+rs.getString(3));  
            }
		}catch(SQLException e) {
			e.printStackTrace();
		}catch(Exception e){ 	
			e.printStackTrace();
		}finally{
			try{
				if(rs!=null)rs.close();
				if(stmt!=null)stmt.close();
				if(con!=null)con.close();
			} catch(Exception es) {
				es.printStackTrace();
			}
		}
    }
}
```

## Example of MSSQL Database :
```
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;
import java.sql.ResultSet;
import java.sql.SQLException;

class dbConnect {  
    public static void main(String args[]){  
        Connection con = null;
		Statement stmt = null;
		ResultSet rs = null;
		try{  
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
            con=DriverManager.getConnection("jdbc.sqlserver://localhost:1433;databaseName=XYZ;integratedSecurity=true","AJAY1","12345");  
            stmt=con.createStatement();  
            rs=stmt.executeQuery("select * from emp");  
            System.out.println("\nEmployeeID\tEmployeeName\tJobTitle");
            while(rs.next()) {  
                System.out.println("-------------------------------------   -----");
                System.out.println(rs.getInt(1)+"\t|\t"+rs.getString(2)+"\t|\t"+rs.getString(3));  
            }
		}catch(SQLException e) {
			e.printStackTrace();
		}catch(Exception e){ 	
			e.printStackTrace();
		}finally{
			try{
				if(rs!=null)rs.close();
				if(stmt!=null)stmt.close();
				if(con!=null)con.close();
			} catch(Exception es) {
				es.printStackTrace();
			}
		}
    }
}
```
