# SpringBoot-H2-Database:



Install h2 console:

   run in local -> 192.168.0.105:8082/login.jsp?jsessionid=57ffec2d5129387e3198173cfe74194a

		CREATE TABLE CUSTOMER (id number, name varchar(20), age number, address varchar(20), 
		salary number);  

		INSERT into CUSTOMER values (1, 'Ramesh', 32, 'Ahmedabad', 2000); 

		INSERT into CUSTOMER values (2, 'Khilan', 25, 'Delhi', 1500); 


H2 in JDBC:

	import java.sql.Connection; 
	import java.sql.DriverManager; 
	import java.sql.SQLException; 
	import java.sql.Statement;  

	public class H2jdbcCreateDemo { 
	   // JDBC driver name and database URL 
	   static final String JDBC_DRIVER = "org.h2.Driver";   
	   static final String DB_URL = "jdbc:h2:~/test";  

	   //  Database credentials 
	   static final String USER = "sa"; 
	   static final String PASS = ""; 

	   public static void main(String[] args) { 
	      Connection conn = null; 
	      Statement stmt = null; 
	      try { 
		 // STEP 1: Register JDBC driver 
		 Class.forName(JDBC_DRIVER); 

		 //STEP 2: Open a connection 
         System.out.println("Connecting to database..."); 
         conn = DriverManager.getConnection(DB_URL,USER,PASS);  
         
         //STEP 3: Execute a query 
         System.out.println("Creating table in given database..."); 
         stmt = conn.createStatement(); 
         String sql =  "CREATE TABLE   REGISTRATION " + 
            "(id INTEGER not NULL, " + 
            " first VARCHAR(255), " +  
            " last VARCHAR(255), " +  
            " age INTEGER, " +  
            " PRIMARY KEY ( id ))";  
         stmt.executeUpdate(sql);
         System.out.println("Created table in given database..."); 
         
         // STEP 4: Clean-up environment 
         stmt.close(); 
         conn.close(); 
      } catch(SQLException se) { 
         //Handle errors for JDBC 
         se.printStackTrace(); 
      } catch(Exception e) { 
         //Handle errors for Class.forName 
         e.printStackTrace(); 
      } finally { 
         //finally block used to close resources 
         try{ 
            if(stmt!=null) stmt.close(); 
         } catch(SQLException se2) { 
         } // nothing we can do 
         try { 
            if(conn!=null) conn.close(); 
         } catch(SQLException se){ 
            se.printStackTrace(); 
         } //end finally try 
      } //end try 
      System.out.println("Goodbye!");
   } 
}



# Change login H2 url to 

jdbc:h2:mem:testdb

# REST request validation annotations:

@AssertFalse	The annotated element must be false.

@AssertTrue	The annotated element must be true.

@DecimalMax	The annotated element must be a number whose value must be lower or equal to the specified maximum.

@DecimalMin	The annotated element must be a number whose value must be higher or equal to the specified minimum.

@Future	The annotated element must be an instant, date or time in the future.

@Max	The annotated element must be a number whose value must be lower or equal to the specified maximum.

@Min	The annotated element must be a number whose value must be higher or equal to the specified minimum.

@Negative	The annotated element must be a strictly negative number.

@NotBlank	The annotated element must not be null and must contain at least one non-whitespace character.

@NotEmpty	The annotated element must not be null nor empty.

@NotNull	The annotated element must not be null.

@Null	The annotated element must be null.

@Pattern	The annotated CharSequence must match the specified regular expression.

@Positive	The annotated element must be a strictly positive number.

@Size	The annotated element size must be between the specified boundaries (included).

Query:


Delete the table if it exists:

	DROP TABLE IF EXISTS TEST;
	
Create a new table with ID and NAME columns:

  	CREATETABLE TEST(ID INT PRIMARY KEY,  NAME VARCHAR(255));
	
Add a new row:

	INSERT INTO TEST VALUES(1, 'Hello');
	
Add another row:

	INSERT INTO TEST VALUES(2, 'World');
	
Query the table:

	SELECT * FROM TEST ORDER BY ID;
	
Change data in a row:
	
	UPDATE TEST SET NAME='Hi' WHERE ID=1;
	
Remove a row:

	DELETE FROM TEST WHERE ID=2;






# logging, log4j, logback


        LOGGER.debug("This is a debug message");
  
	LOGGER.info("This is an info message");
  
	LOGGER.warn("This is a warn message");
  
	LOGGER.error("This is an error message");

<a href="http://192.168.0.105:8082/login.do?jsessionid=57ffec2d5129387e3198173cfe74194a"> test H2 console </a>


<a href="http://starwalt.in/Blogs/index.html">Follow us on Blog</a>
