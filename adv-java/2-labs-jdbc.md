:beginner: **JDBC Labs**  

:lock: Migrate the UTILITY to use a Singleton Design Pattern

```java
package jdbc.crud.util;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DatabaseUtil {
//SET UP ALL THE DETAILS FOR DATABASE ACCESS
	private static final String ORACLE_USER = "hr";
	private static final String ORACLE_PASSSWORD = "hr";
	private static final String ORACLE_CONNECTION_STRING = "jdbc:oracle:thin:@localhost:1521:xe";

	private static final String MYSQL_USER = "root";
	private static final String MYSQL_PASSWORD = "mysql";
	private static final String MYSQL_CONNECTION_STRING = "jdbc:mysql://localhost:3306/sakila";

	public static Connection getConnection(DatabaseType databaseType) {
		switch (databaseType) {
		case ORACLEDB: {
			try {
				// Loaded the driver for Oracle.
				Class.forName("oracle.jdbc.driver.OracleDriver");
//				A connection (session) with a specific database. 
//				SQL statements are executed and results are returned within the context of a connection. 
				Connection connection = DriverManager.getConnection(ORACLE_CONNECTION_STRING, ORACLE_USER,
						ORACLE_PASSSWORD);
				return connection;
			} catch (ClassNotFoundException e) {
				System.out.println("EXCEPTION :>> " + e);
			} catch (SQLException e) {
				System.out.println("EXCEPTION :>> " + e);
			}
		}
		case MYSQLDB: {
			try {
				// Loaded the driver for Oracle.
				// Deprecated Driver
				// Class.forName("com.mysql.jdbc.Driver");
				Class.forName("com.mysql.cj.jdbc.Driver");
				Connection connection = DriverManager.getConnection(MYSQL_CONNECTION_STRING, MYSQL_USER,
						MYSQL_PASSWORD);
				return connection;
			} catch (ClassNotFoundException e) {
				System.out.println("EXCEPTION :>> " + e);
			} catch (SQLException e) {
				System.out.println("EXCEPTION :>> " + e);
			}
		}
		}
		return null;
	}

	public void testOracleConnection() {
		Connection connection = null;
		connection = DatabaseUtil.getConnection(DatabaseType.ORACLEDB);
		System.out.println("Connected to Oracle!");
	}
	public void testMySQLConnection() {
		Connection connection = null;
		connection = DatabaseUtil.getConnection(DatabaseType.MYSQLDB);
		System.out.println("Connected to MySQL!");
	}
}

```

:lock: Migrate the application to store data to mysql

```java
package jdbc.crud;

import java.sql.Connection;
import java.sql.Date;
import java.sql.SQLException;
import java.sql.Statement;

import jdbc.util.DatabaseType;
import jdbc.util.DatabaseUtil;

public class InsertStatement {
public static void main(String[] args) {
	Connection connection = DatabaseUtil.getConnection(DatabaseType.ORACLEDB);
	
	
	int employeeId = 101;
	String employeeName = "Great";
	double salary = 55.5d;	
	//String queryString = "insert into employee1 (EMPLOYEE_ID, EMPLOYEE_NAME, SALARY) values (" + employeeId + ",'" + employeeName + "',"  + salary + ")";
	
	Date hireDate = Date.valueOf("2020-3-21");
	//String queryString = "insert into employee1  values (" + employeeId + ",'" + employeeName + "','" +hireDate + "'," + salary + ")";
	//String queryString = "insert into employee1  values (" + employeeId + ",'" + employeeName + "','11-07-20'," + salary + ")";
	String queryString = "insert into employee1  values (" + employeeId + ",'" + employeeName + "',to_date('" + hireDate + "','YY-MM-DD')," + salary + ")";
	System.out.println(queryString);
	Statement statement;
	try {
		statement = connection.createStatement();
		int noOfRowsInserted = statement.executeUpdate(queryString);
		System.out.println("Rows Inserted :> " + 1);
	} catch (SQLException e) {
		System.out.println("EXCEPTION :>> " + e);
	}

}
}

```

:lock: Migrate all the programs written for oracle to mysql
