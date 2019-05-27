## Lesson 31

```java
import java.io.*;

import javax.swing.*;


public class Lesson31 extends JFrame{
	
	static String filePath,parentDirectory;
	
	static File randomDir, randomFile, randomFile2;
	
	public static void main(String[] args){
		
		// Creates a File object in memory
		
		randomDir = new File("/Users/AdityaSingh/Documents/workspace3/Java Code/Random");
		
		// Make a directory
		
		randomDir.mkdir();
		
		// Make a file named random.txt
		
		randomFile = new File("random.txt");
		
		// Make a file and define where to save it in the file system
		
		randomFile2 = new File("/Users/AdityaSingh/Documents/workspace3/Java Code/Random/random2.txt");
		
		// createNewFile and getCanonicalPath have to be called in 
		// a try block to catch IOException
		
		try {
			
			// createNewFile creates the file in the file system
			
			randomFile.createNewFile();
			
			randomFile2.createNewFile();
			
			// Returns the path for the file
			
			filePath = randomFile.getCanonicalPath();
			
		} catch (IOException e) {
			
			// You have to catch the IOException
			e.printStackTrace();
			
		}
		
		// Check to see if the file exists in the current directory
		
		if (randomFile.exists()){
			
			System.out.println("File Exists");
			System.out.println("File is readable: " + randomFile.canRead());
			System.out.println("File is writable: " + randomFile.canWrite());
			System.out.println("File location: " + filePath);
			System.out.println("File name: " + randomFile.getName());
			
			// Since you created the file without defining a path this returns null
			
			System.out.println("Parent directory: " + randomFile.getParent());
			
			// This returns the parent because it was defined
			
			parentDirectory = randomFile2.getParent();
			
			System.out.println("File Two Parent Directory: " + parentDirectory);
			
			System.out.println("Is this a directory: " + randomDir.isDirectory());
			
			// list provides a string array containing all the files
			
			String[] filesInDir = randomDir.list();
			
			System.out.println("Files in Random Directory\n");
			
			// Use the enhanced for loop to cycle through the files
			
			for(String fileName : filesInDir){
				System.out.println(fileName + "\n");
			}
			
			
			System.out.println("Is this a file: " + randomFile.isFile());
			
			System.out.println("Is this hidden: " + randomFile.isHidden());
			
			// Milliseconds since Jan 1, 1970 when modified
			
			System.out.println("Last modified: " + randomFile.lastModified());
			
			// Return size of file
			
			System.out.println("Size of file: " + randomFile.length());
			
			// Changes the name of the file
			
			randomFile2.renameTo(new File("/UsersAdityakSingh/Documents/workspace3/Java Code/Random/random3.txt"));
			
			// Output the full path for the file unless the path wasn't
			// defined when the File was created
			
			System.out.println("New Name: " + randomFile2.toString());
			
			new Lesson31();
			
		} else {
			
			System.out.println("File Doesn't Exist");
			
		}
		
		// You call delete to delete a file
		
		if(randomFile.delete()){
			System.out.println("File Deleted");
		}
		
		// I could get an array of File objects from the directory
					
		File[] filesInDir = randomDir.listFiles();
		
		for(File fileName : filesInDir){
			fileName.delete();
		}
		
		// You can only delete a directory if it is empty
		
		if(randomDir.delete()){
			System.out.println("Directory Deleted");
		}
		
		
	}
	
	public Lesson31(){
		
		// Creates a file chooser at the location specified
		
		JFileChooser fileChooser = new JFileChooser(randomDir);
		
		// Opens the file chooser
		
		fileChooser.showOpenDialog(this);
		
		
		
	}
	
}
```

## Lesson 32

```java
import java.io.*;

// A character stream is just a series of characters
// Important information is normally separated by a comma,
// space, or tab.

public class Lesson32{
	
	public static void main(String[] args){
		
		// Create an array of type Customer
		
		Customer[] customers = getCustomers();
		
		// PrintWriter is used to write characters to a file in this situation
		
		PrintWriter custOutput = createFile("/Users/AdityaSingh/Documents/workspace3/Java Code/src/customers.txt");
		
		// Enhanced for loop for arrays
		// Cycles through all of the people in the customers array
		
		for(Customer person : customers){
			
			createCustomers(person, custOutput);
			
		}
		
		// Closes the connection to the PrintWriter
		
		custOutput.close();
		
		getFileInfo();
		
	}
	
	// class that defines all the fields for my customers
	
	private static class Customer{
		
		public String firstName, lastName;
		public int custAge;
		
		// constructor that's called when a customer is made
		
		public Customer(String firstName, String lastName, int custAge){
			
			this.firstName = firstName;
			this.lastName = lastName;
			this.custAge = custAge;
			
		}
		
	}
	
	// Creates an array of Customer Objects
	
	private static Customer[] getCustomers(){
		
		Customer[] customers = new Customer[5];
		
		customers[0] = new Customer("John", "Smith", 21);
		customers[1] = new Customer("Sally", "Smith", 30);
		customers[2] = new Customer("Paul", "Ryan", 21);
		customers[3] = new Customer("Mark", "Jacobs", 21);
		customers[4] = new Customer("Steve", "Nash", 21);
		
		return customers;
		
	}
	
	// Create the file and the PrintWriter that will write to the file
	
	private static PrintWriter createFile(String fileName){
		
		try{
			
			// Creates a File object that allows you to work with files on the hardrive
			
			File listOfNames = new File(fileName);
			
			// FileWriter is used to write streams of characters to a file
			// BufferedWriter gathers a bunch of characters and then writes
			// them all at one time (Speeds up the Program)
			// PrintWriter is used to write characters to the console, file
	
			PrintWriter infoToWrite = new PrintWriter(
			new BufferedWriter(
					new FileWriter(listOfNames)));
			return infoToWrite;
		}
	
		// You have to catch this when you call FileWriter
		
		catch(IOException e){
		
			System.out.println("An I/O Error Occurred");
			
			// Closes the program
			
			System.exit(0);
		
		}
		return null;
		
	}
	
	// Create a string with the customer info and write it to the file
	
	private static void createCustomers(Customer customer, PrintWriter custOutput){
		
		// Create the String that contains the customer info
		
		String custInfo = customer.firstName + " " + customer.lastName + " ";
		custInfo += Integer.toString(customer.custAge);
		
		// Writes the string to the file
		
		custOutput.println(custInfo);
		
	}
	
	// Read info from the file and write it to the screen
	
	private static void getFileInfo(){
		
		System.out.println("Info Written to File\n");
		
		// Open a new connection to the file
		
		File listOfNames = new File("/UsersAdityakSingh/Documents/workspace3/Java Code/src/customers.txt");
		
		try {
			
			// FileReader reads character files
			// BufferedReader reads as many characters as possible
			
			BufferedReader getInfo = new BufferedReader(
					new FileReader(listOfNames));
			
			// Reads a whole line from the file and saves it in a String
			
			String custInfo = getInfo.readLine();
			
			// readLine returns null when the end of the file is reached
			
			while(custInfo != null){
				
				// System.out.println(custInfo);
				
				// Break lines into pieces
				
				String[] indivCustData = custInfo.split(" ");
				
				// Convert the String into an integer with parseInt
				
				int custAge = Integer.parseInt(indivCustData[2]);
				
				System.out.print("Customer " + indivCustData[0] + " is " + custAge +"\n");
				
				custInfo = getInfo.readLine();
				
			}
			
			
			
		} 
		
		// Can be thrown by FileReader
		
		catch (FileNotFoundException e) {
			
			System.out.println("Couldn't Find the File");
			System.exit(0);
		}
		
		catch(IOException e){
			
			System.out.println("An I/O Error Occurred");
			System.exit(0);
		
		}
		
	}
	
	
}
```

## Lesson 33

```java
import java.io.*;

// A binary stream is a series of data type values
// To read and write to them you use different methods
// based on the type of data that you are using

public class Lesson33{
	
	public static void main(String[] args){
		
		// Create an array of type Customer
		
		Customer[] customers = getCustomers();
		
		// A DataOutputStream allows you to print 
		// primitive data types to a file
		
		DataOutputStream custOutput = createFile("/Users/AdityaSingh/Documents/workspace3/Java Code/src/customers.dat");
		
		// Enhanced for loop for arrays
		// Cycles through all of the people in the customers array
		
		for(Customer person : customers){
			
			createCustomers(person, custOutput);
			
		}
		
		// Closes the connection to the DataOutputStream
		
		try {
			custOutput.close();
		} catch (IOException e) {
			
			System.out.println("An I/O Error Occurred");
			
			// Closes the program
			
			System.exit(0);
		}
		
		getFileInfo();
		
	}
	
	// class that defines all the fields for my customers
	
	private static class Customer{
		
		public String custName;
		public int custAge; 
		public double custDebt;
		public boolean oweMoney;
		public char custSex;
		
		// constructor that's called when a customer is made
		
		public Customer(String custName, int custAge, double custDebt, boolean oweMoney, char custSex){
			
			this.custName = custName; // String
			this.custAge = custAge; // Integer
			this.custDebt = custDebt; // Double
			this.oweMoney = oweMoney; // Boolean
			this.custSex = custSex; // Character
			
		}
		
	}
	
	// Creates an array of Customer Objects
	
	private static Customer[] getCustomers(){
		
		Customer[] customers = new Customer[5];
		
		customers[0] = new Customer("John Smith", 21, 12.25, true, 'M');
		customers[1] = new Customer("Sally Smith", 30, 2.25, true, 'F');
		customers[2] = new Customer("Paul Ryan", 21, 0, false, 'M');
		customers[3] = new Customer("Mark Jacobs", 21, 3.25, true, 'M');
		customers[4] = new Customer("Steve Nash", 21, 5.25, true, 'M');
		
		return customers;
		
	}
	
	// Create the file and the DataOutputStream that will write to the file
	
	private static DataOutputStream createFile(String fileName){
		
		try{
			
			// Creates a File object that allows you to work with files 
			// on the hard drive. There is no difference between File
			// for character or binary stream writing, or reading
			
			File listOfNames = new File(fileName);
			
			// FileOutputStream is used to write streams of data to a file
			// You define whether a new file is created versus appended
			// to based on if you add a boolean to the FileOutputStream
			// FileOutputStream(file, true) : Appends to the file
			// FileOutputStream(file, false) : Creates a new file
			
			// BufferedOutputStream gathers all the data and then writes
			// it all at one time (Speeds up the Program)
			// DataOutputStream is used to write primitive data to the file
	
			DataOutputStream infoToWrite = new DataOutputStream(
			new BufferedOutputStream(
					new FileOutputStream(listOfNames)));
			return infoToWrite;
		}
	
		// You have to catch this when you call FileWriter
		
		catch(IOException e){
		
			System.out.println("An I/O Error Occurred");
			
			// Closes the program
			
			System.exit(0);
		
		}
		return null;
		
	}
	
	// Create a string with the customer info and write it to the file
	
	private static void createCustomers(Customer customer, DataOutputStream custOutput){
		
		try{
		// Write primitive data to the file
		
		// Writes a String in UTF format
		custOutput.writeUTF(customer.custName); 
		
		// Writes an Integer 
		custOutput.writeInt(customer.custAge); 
		
		// Writes a Double
		custOutput.writeDouble(customer.custDebt); 
		
		// Writes a Boolean 
		custOutput.writeBoolean(customer.oweMoney); 
				
		// Writes a Character
		custOutput.writeChar(customer.custSex);
		
		// You also have writeByte, writeFloat, writeLong
		// and writeShort
		}
		
		catch(IOException e){
			
			System.out.println("An I/O Error Occurred");
			System.exit(0);
		
		}
		
	}
	
	// Read info from the file and write it to the screen
	
	private static void getFileInfo(){
		
		System.out.println("Info Written to File\n");
		
		// Open a new connection to the file
		
		File listOfNames = new File("/UsersAdityakSingh/Documents/workspace3/Java Code/src/customers.dat");
		
		boolean eof = false;
		
		try {
			
			// A DataInputStream object has the methods for reading the data
			// The BufferedInputStream gathers the data in blocks
			// FileInputStream gets data from the file
			
			DataInputStream getInfo = new DataInputStream(
					new BufferedInputStream(
					new FileInputStream(listOfNames)));
			
			// Using a while loop that pulls data until EOFException is thrown
			
			while (!eof){
				
				// You have to read data in the exact order it was put in the file
				
				String custName = getInfo.readUTF();
				int custAge = getInfo.readInt(); 
				double custDebt = getInfo.readDouble();
				boolean oweMoney = getInfo.readBoolean();
				char custSex = getInfo.readChar();
				
				System.out.println(custName);
				System.out.println(custAge);
				System.out.println(custDebt);
				System.out.println(oweMoney);
				System.out.println(custSex + "\n");
				
			}	
			
		} // END OF TRY
		
		catch (EOFException e) {
			
			eof = true;
		}
		
		// Can be thrown by FileInputStream
		
		catch (FileNotFoundException e) {
			
			System.out.println("Couldn't Find the File");
			System.exit(0);
		}
		
		catch(IOException e){
			
			System.out.println("An I/O Error Occurred");
			System.exit(0);
		
		}
		
	}
	
	
}
```



## Lesson 34

```java
// The API for accessing and processing data stored in a database

import java.sql.*;

public class Lesson34 {
    public static void main(String[] args) {
    	
    	// A connection object is used to provide access to a database
    	
    	Connection conn = null;
    	
        try {
            // The driver allows you to query the database with Java
        	// forName dynamically loads the class for you
           
            Class.forName("com.mysql.jdbc.Driver");
            
            // DriverManager is used to handle a set of JDBC drivers
            // getConnection establishes a connection to the database
            // You must also pass the userid and password for the database
            
            conn = DriverManager.getConnection("jdbc:mysql://localhost/customer","mysqladm","turtledove");
            
            // Statement objects executes a SQL query
            // createStatement returns a Statement object
            
            Statement sqlState = conn.createStatement();
            
            // This is the query I'm sending to the database
            
            String selectStuff = "Select first_name from customer";
            
            // A ResultSet contains a table of data representing the
            // results of the query. It can not be changed and can 
            // only be read in one direction
            
            ResultSet rows = sqlState.executeQuery(selectStuff);
            
            // next is used to iterate through the results of a query
            
            while(rows.next()){
            	System.out.println(rows.getString("first_name"));
            }
        } 
        
        catch (SQLException ex) {
            
        	// String describing the error
        	
            System.out.println("SQLException: " + ex.getMessage());
            
            // Vendor specific error code
            
            System.out.println("VendorError: " + ex.getErrorCode());
        } 
        
        catch (ClassNotFoundException e) {
			// Executes if the driver can't be found
			e.printStackTrace();
		} 
        
    }
}
```

```java
import java.lang.Math.*;

public class Lesson35{
	
	// ERROR 1: Cannot make a static reference to the non-static method
	// SOLVED: You can't call a non static method from a static method
	// private void printSomething(){
	
	private static void printSomething(){
	
	// ERROR 2: Unresolved compilation problem
	// SOLVED: Pay attention to Eclipse Errors
	// Int BigNumber = 100000;
		
		
		// ERROR 3: A string literal isn't properly closed
		// SOLVED: Pay attention to Eclipse
		//String something = "A string error
				//is occurring";
		
		System.out.println("Something");
		
	} // If this is missing you get ERROR 2
	
	// ERROR 4: Exception in thread "main" java.lang.NoSuchMethodError: main
	// SOLVED: Make sure you type the main function correctly
	// public static void main(String args){ // This is Wrong
	
	public static void main(String[] args){
		
		// ERROR 5: Can't be resolved to a variable
		// SOLVED: Pay attention to Eclipse
		// printsomething; // This is Wrong
		
		printSomething();
		
		// ERROR 6: Type mismatch Can't convert from int to String
		// SOLVED: Convert the integer
		
		int number = 12;
		// String anotherNum = number; // This is Wrong
		String anotherNum = Integer.toString(number);
		
		// int number = Integer.parseInt(anotherNum); // Convert from string to int
		
		
		// ERROR 7: Can't be resolved to a type
		// SOLVED: import the dimension library
		// Dimension dim = new Dimension();
		
		// ERROR 8: Method is undefined
		// SOLVED: Make sure methods are in the class
		
		double pi = 3.14;
		// long randLong = Lesson34.round(pi); // The wrong way
		
		// ERROR 9: Can't invoke method
		// SOLVED: Understand how methods work
		
		long randLong = Math.round(pi); // The right way
		// randLong = pi.round(); // Wrong way
		
		// ERROR 11: The method is not applicable for the arguments
		// SOLVED: Provide the right arguments in the right order
		
		// getStuff(1.234, 5); // Wrong Way
		
		getStuff(1,5.0); // Right Way
		
		// ERROR 12: Syntax error on token ",; expected
		// SOLVED: Understand how methods are called in Java vs. other languages
		
		// double sumNum = addThem(LessonFive,1,2); // Wrong Way
		double sumNum = LessonFive.addThem(1,2);
		
		// ERROR 13: Syntax error on token '=='
		// SOLVED: = is different from ==
		// int value == 1;
		
		
	}
	
	// ERROR 10: Can't be resolved to a type
	// SOLVED: Always provide the type in methods
	
	/* public static void getStuff(number1, number2){
		
	} */
	
	// ERROR 14: Return type for method is missing
	// SOLVED: Provide a return type or void
	
	public static void getStuff(int number1, double number2){
		
		// ERROR 15: Syntax error on token ",[ expected
		// SOLVED: Understand how arrays are defined in Java
				
		// int[] intArray = new [10,10]int; // Wrong Way
				
		int[][] intArray = new int[10][10];
		
		// ERROR 16: The method is not visible
		// SOLVED: You can't private methods which are declared in 
		// another class. private static void getFileInfo()
		
		// Lesson33.getFileInfo(); // Wrong Way
		
		// ERROR 17: Local variable may not have been initialized
		// SOLVED: Always give variables default values
		
		String howMany = "10";
		// String howMany; // Wrong Way
		System.out.println(howMany);
		
		// ERROR 18: Cannot be Resolved
		// SOLVED: Understand that arrays and strings use a 
		// different version of length
		
		System.out.println(howMany.length());
		// System.out.println(howMany.length); // Wrong Way
		
		// System.out.println(intArray.length()); // Wrong Way
		System.out.println(intArray.length); 
		
		// ERROR 19: Prefix Operator vs. Postfix Operator
		
		int xInt = 1, yInt = 1;
		
		xInt = yInt++; // Passes the original value of yInt before incrementing
		
		System.out.println("xInt: " + xInt); 
		
		// ERROR 20: Not calling break at end of case
		
		int day = 1;
		
		switch (day){
			case 1: System.out.println("Monday");
			case 2: System.out.println("Tuesday");
			case 3: System.out.println("Wednesday");
			case 4: System.out.println("Thursday");
			default: System.out.println("Friday");
		}
		
		
	}
	
	
}
```

## Lesson 35

```java
import java.lang.Math.*;

public class Lesson35{
	
	// ERROR 1: Cannot make a static reference to the non-static method
	// SOLVED: You can't call a non static method from a static method
	// private void printSomething(){
	
	private static void printSomething(){
	
	// ERROR 2: Unresolved compilation problem
	// SOLVED: Pay attention to Eclipse Errors
	// Int BigNumber = 100000;
		
		
		// ERROR 3: A string literal isn't properly closed
		// SOLVED: Pay attention to Eclipse
		//String something = "A string error
				//is occurring";
		
		System.out.println("Something");
		
	} // If this is missing you get ERROR 2
	
	// ERROR 4: Exception in thread "main" java.lang.NoSuchMethodError: main
	// SOLVED: Make sure you type the main function correctly
	// public static void main(String args){ // This is Wrong
	
	public static void main(String[] args){
		
		// ERROR 5: Can't be resolved to a variable
		// SOLVED: Pay attention to Eclipse
		// printsomething; // This is Wrong
		
		printSomething();
		
		// ERROR 6: Type mismatch Can't convert from int to String
		// SOLVED: Convert the integer
		
		int number = 12;
		// String anotherNum = number; // This is Wrong
		String anotherNum = Integer.toString(number);
		
		// int number = Integer.parseInt(anotherNum); // Convert from string to int
		
		
		// ERROR 7: Can't be resolved to a type
		// SOLVED: import the dimension library
		// Dimension dim = new Dimension();
		
		// ERROR 8: Method is undefined
		// SOLVED: Make sure methods are in the class
		
		double pi = 3.14;
		// long randLong = Lesson34.round(pi); // The wrong way
		
		// ERROR 9: Can't invoke method
		// SOLVED: Understand how methods work
		
		long randLong = Math.round(pi); // The right way
		// randLong = pi.round(); // Wrong way
		
		// ERROR 11: The method is not applicable for the arguments
		// SOLVED: Provide the right arguments in the right order
		
		// getStuff(1.234, 5); // Wrong Way
		
		getStuff(1,5.0); // Right Way
		
		// ERROR 12: Syntax error on token ",; expected
		// SOLVED: Understand how methods are called in Java vs. other languages
		
		// double sumNum = addThem(LessonFive,1,2); // Wrong Way
		double sumNum = LessonFive.addThem(1,2);
		
		// ERROR 13: Syntax error on token '=='
		// SOLVED: = is different from ==
		// int value == 1;
		
		
	}
	
	// ERROR 10: Can't be resolved to a type
	// SOLVED: Always provide the type in methods
	
	/* public static void getStuff(number1, number2){
		
	} */
	
	// ERROR 14: Return type for method is missing
	// SOLVED: Provide a return type or void
	
	public static void getStuff(int number1, double number2){
		
		// ERROR 15: Syntax error on token ",[ expected
		// SOLVED: Understand how arrays are defined in Java
				
		// int[] intArray = new [10,10]int; // Wrong Way
				
		int[][] intArray = new int[10][10];
		
		// ERROR 16: The method is not visible
		// SOLVED: You can't private methods which are declared in 
		// another class. private static void getFileInfo()
		
		// Lesson33.getFileInfo(); // Wrong Way
		
		// ERROR 17: Local variable may not have been initialized
		// SOLVED: Always give variables default values
		
		String howMany = "10";
		// String howMany; // Wrong Way
		System.out.println(howMany);
		
		// ERROR 18: Cannot be Resolved
		// SOLVED: Understand that arrays and strings use a 
		// different version of length
		
		System.out.println(howMany.length());
		// System.out.println(howMany.length); // Wrong Way
		
		// System.out.println(intArray.length()); // Wrong Way
		System.out.println(intArray.length); 
		
		// ERROR 19: Prefix Operator vs. Postfix Operator
		
		int xInt = 1, yInt = 1;
		
		xInt = yInt++; // Passes the original value of yInt before incrementing
		
		System.out.println("xInt: " + xInt); 
		
		// ERROR 20: Not calling break at end of case
		
		int day = 1;
		
		switch (day){
			case 1: System.out.println("Monday");
			case 2: System.out.println("Tuesday");
			case 3: System.out.println("Wednesday");
			case 4: System.out.println("Thursday");
			default: System.out.println("Friday");
		}
		
		
	}
	
	
}
```