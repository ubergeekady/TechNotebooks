## Lesson 1

```java
// Here I'm defining a new class (Blueprint) named HelloWorld
// public tells Java that this should be available to all other classes
// classes are blue prints used to design objects that contain attributes (variables) and methods (functions)
// HelloWorld is just what you named your program. That allows you to reference it later
// { is the opening brace that surrounds the code used by HelloWorld
public class HelloWorld
{
		// public allows other classes to use this function
		// static means that only a class can call for this function to execute
		// void states that this function doesn't return any values after it is done executing
		// main is required in every Java program. This function is always executed first
		// Every main function must accept an array of string objects
	
		// Class variables must start with static if you want to access them with any other 				// methods in the class
		static String randomString = "String to print";
		
		// Constant variables are defined with the word final
		static final double PINUM = 3.1415929;
	
		public static void main(String[] args)
		{
			// System.out is an object that outputs information
			// println is a function that prints to the screen what ever you provide between 						// braces
			// "Hello World" is a string of characters. Strings must be surrounded with quotes
			// Every statement ends with a semicolon ;
			System.out.println("Hello World");
			
			// Variable names are case sensitive. Age is not the same as age.
			// Variables must begin with a letter and contain numbers, _, or $
			// You must declare all variables before you can use them with a data type
						
			/* You can use any variable name except for 
			 * abstract		continue	for		new		switch	assert	default	goto	package			* 						 * synchronized
			 * boolean	do	if	private	this	break	double	implements	protected	throw
			 * byte	else	import	public	throws	case	enum	instanceof	return	transient
			 * catch	extends	int	short	try	char	final	interface	static	void
			 * class	finally	long	strictfp	volatile	const	float	native	super	while
			 */
			
			// This is a declaration statement
			// integerOne is a local variable to the main function. It can only be accessed in 					// main
			int integerOne = 22; 
			
			int integerTwo = integerOne + 1; // This is an expression statement
			
			// White space has no meaning in Java, aside from variables and keywords
			integerTwo =
					integerOne
					+ 3;
			
			System.out.println(integerTwo);
			
			// Javas Primitive Types
			
			byte bigByte = 127; // Minimum value -128 Maximum value 127
			short bigShort = 32767; // Minimum value -32768 Maximum value 32767
			int bigInt = 2147483647; // Minimum value -2147483648 Maximum value 2147483647
			long bigLong = 9223372036854775807L; // Minimum value -9223372036854775808L
			
			float bigFloat = 3.14F; // You must end a float with an F
			double bigDouble = 3.1234567890D; // The D is not required with doubles
			System.out.println(Float.MAX_VALUE); // Float is precise to 6 decimal places
			System.out.println(Double.MAX_VALUE); // Double is precise to 15 decimal places
			
			boolean trueOrFalse = true; // Booleans are True or False, not 1 or 0
			
			// A char will accept a number or a character surrounded by apostrophes
			char randomChar = 65; // Character Code for A is 65 Minimum value 0 Maximum value 					// 65535
			char anotherChar = 'A';
			System.out.println(randomChar);
			
			// chars can also contain escaped characters
			char backSpace = '\b';
			char formFeed = '\f';
			char lineFeed = '\n';
			char carriageReturn = '\r';
			char horizontalTab = '\t';
			char doubleQuote = '\"';
			char singleQuote = '\'';
			char backSlash = '\\';
			
			// A string contains a series of characters
			String randomString = "I'm just a random";
			String anotherString = "string";
			
			// You combine strings with a +
			String combinedString = randomString + ' ' + anotherString;
			System.out.println(combinedString);
			
			// How to convert any other type to a string
			String byteString = Byte.toString(bigByte);
			String shortString = Short.toString(bigShort);
			String intString = Integer.toString(bigInt);
			String longString = Long.toString(bigLong);
			String floatString = Float.toString(bigFloat);
			String doubleString = Double.toString(bigDouble);
			String booleanString = Boolean.toString(trueOrFalse);
			String charString = Character.toString(randomChar); // You don't need to do this
			
			System.out.println(charString);
			
			// Can't do this because char is a primitive data type
			// System.out.println(randomChar.getClass());
			
			// You can do this because String is an object
			System.out.println(charString.getClass());
			
			// You use casting to convert from one primitive type to another
			// If you convert from a number that is to big the largest possible value will be 
			// used instead
			double aDoubleValue = 3.1456789;
			int doubleToInt = (int) aDoubleValue;
			System.out.println(doubleToInt);
			
			/* To cast to other primitive types just proceed with the conversion to type
			 * ie (byte) (short) (long) (double) 
			 * (float) & (boolean) & (char) don't work. 
			 * (char) stays as a number instead of a character
			 */
			
			// Use parseInt to convert a string into an integer
			int stringToInt = Integer.parseInt(intString);
			
			/* Other parse functions
			 * parseShort, parseLong, parseByte, parseFloat, parseDouble, parseBoolean
			 * There is no reason to parse a Character
			 */
			
		}
		// You must provide a closing brace } so Java knows when the function has ended
}
```

## Lesson 2

```java
// To import an external class you use import
// You can import whole libraries of classes like this import java.util.*;
import java.util.Scanner; 

public class LessonTwo
{
	/* static means that only a class can call for this function to execute
	* Creates a new scanner object named userInput
	* You create the Scanner object by calling new and passing the Scanner constructor
	* the input stream to look at (System.in = keyboard input)
	*/ 
	static Scanner userInput = new Scanner(System.in);
	
	public static void main(String[] args)
	{
		System.out.print("Your favorite number: "); // Same as println without a newline
		
		/* The if statement will only execute the code that lies between {} if the value inside () is true
		 * userInput.hasNextDouble() returns true if the next value entered is a Double
		 * There are similar methods for the other data types
		 * hasNextInt() : Integer input
		 * hasNextFloat() : Float input
		 * There are others for Boolean, Byte, Long, and Short
		 */
		
		if (userInput.hasNextInt())
		{
		
			int numberEntered = userInput.nextInt();
			/* userInput.nextDouble() receives user input and stores it in the variable numberEntered
			 * You have to use a different method based on the type of input
			 * nextInt() : Works for Integers
			 * nextDouble() : Works for Doubles
			 * nextFloat() : Works for Floats
			 * nextLine() : Works for Strings
			 * There are others for Boolean, Byte, Long, and Short
			 * If the user enters a value of the wrong type the program crashes
			 */
		
			System.out.println("You entered " + numberEntered);
			
			// Here I perform basic mathematics calculations
			int numEnteredTimes2 = numberEntered + numberEntered;
			System.out.println(numberEntered + " + " + numberEntered + " = " + numEnteredTimes2);
			
			int numEnteredMinus2 = numberEntered - 2;
			System.out.println(numberEntered + " - 2 " + " = " + numEnteredMinus2);
			
			int numEnteredTimesSelf = numberEntered * numberEntered;
			System.out.println(numberEntered + " * " + numberEntered + " = " + numEnteredTimesSelf);
			
			// Without the cast the value wouldn't consider fractions
			double numEnteredDivide2 = (double)numberEntered / 2; 
			System.out.println(numberEntered + " / 2 " + " = " + numEnteredDivide2);
			
			// % Modulus returns the remainder of a division
			int numEnteredRemainder = numberEntered % 2;
			System.out.println(numberEntered + " % 2 " + " = " + numEnteredRemainder);
			
			// Shorthand way to add to 2 to a variable and assign the result to self
			numberEntered += 2; // *= 	/=	%=  Also work
			numberEntered -= 2;
			
			// Shorthand way to add 1 to a variable
			numberEntered++;
			
			// Shorthand way to subtract 1 from a variable
			numberEntered--;
			
			int numEnteredABS = Math.abs(numberEntered); // Returns the absolute value
			
			// Returns the larger of the two arguments (They must be of the same type)
			int whichIsBigger = Math.max(5, 7); 
			
			// Returns the smaller of the two arguments (They must be of the same type)
			int whichIsSmaller = Math.min(5, 7);
			
			// Returns the square root argument 
			double numSqrt = Math.sqrt(5.23);
			
			// Rounds the number provided up
			int numCeiling = (int) Math.ceil(5.23);
			System.out.println("Ceiling: " + numCeiling);
			
			// Rounds the number provided down
			int numFloor = (int) Math.floor(5.23);
			System.out.println("Floor: " + numFloor);
			
			// Rounds the number based on the fraction
			int numRound = (int) Math.round(5.23);
			System.out.println("Rounded: " + numRound);
			
			// Generates random numbers between 0 to 9
			int randomNumber = (int) (Math.random() * 10); 
			System.out.println("A random number " + randomNumber);
			
		// If the above condition is false, the code following else is executed	
		} else {
			System.out.println("Sorry you must enter an integer");
		}
	}
	
}
```

## Lesson 3

```java
public class LessonThree {
	
	public static void main(String[] args)
	{
		// Creates a random number between 0 and 50
		int randomNumber = (int) (Math.random() * 50);
		
		/* Relational Operators: 
		 * Java has 6 relational operators
		 * > : Greater Than
		 * < : Less Than
		 * == : Equal To
		 * != : Not Equal To
		 * >= : Greater Than Or Equal To
		 * <= : Less Than Or Equal To
		 */
		
		// If randomNumber is less than 25, execute the code between {} and then stop checking
		if (randomNumber < 25)
		{
			System.out.println("The random number is less than 25");
		}
		
		// If randomNumber wasn't less than 25, then check if it's greater than it. If so, execute the code between {} and then stop checking
		else if (randomNumber > 25)
		{
			System.out.println("The random number is greater than 25");
		}
		
		// Checks if randomNumber equals 25
		else if (randomNumber == 25)
		{
			System.out.println("The random number is equal to 25");
		}
		
		// Checks if randomNumber is not equal to 25
		else if (randomNumber != 15)
		{
			System.out.println("The random number is not equal to 15");
		}
		
		// Checks if randomNumber is less than or equal to 25
		else if (randomNumber <= 25)
		{
			System.out.println("The random number is less than or equal to 25");
		}
		
		// Checks if randomNumber is greater than or equal to 25
		else if (randomNumber >= 25)
		{
			System.out.println("The random number is greater than or equal to 25");
		}
		
		// If none of the above were correct print out the random number
		else 
		{
			System.out.println("The random number is " + randomNumber);
		}
		
		// Prints out the random number
		System.out.println("The random number is " + randomNumber);
		
		/* Logical Operators:
		 * Java has 6 logical operators
		 * ! : Converts the boolean value to its right to its opposite form ie. true to false
		 * & : Returns true if boolean value on the right and left are both true (Always evaluates both boolean values)
		 * && : Returns true if boolean value on the right and left are both true (Stops evaluating after first false)
		 * | : Returns true if either boolean value on the right or left are true (Always evaluates both boolean values)
		 * || : Returns true if either boolean value on the right or left are true (Stops evaluating after first true)
		 * ^ : Returns true if there is 1 true and 1 false boolean value on the right or left
		 */
		
		if (!(false))
		{
			System.out.println("I turned false into true");
		}
		
		
		if ((false) && (true))
		{
			System.out.println("\nBoth are true");
		}
		
		// There is also a & logical operator it checks the second boolean result even if the first comes back false
		
		if ((true) || (true))
		{
			System.out.println("\nAt least 1 are true");
		}
		
		// There is also a | logical operator it checks the second boolean result even if the first comes back true
		
		if ((true) ^ (false))
		{
			System.out.println("\n1 is true and the other false");
		}
		
		int valueOne = 1;
		int valueTwo = 2;
		
		// The Conditional or Ternary Operator assigns one or another value based on a condition
		// If true valueOne is assigned to biggestValue. If not valueTwo is assigned
		int biggestValue = (valueOne > valueTwo) ? valueOne : valueTwo;
		
		System.out.println(biggestValue + " is the biggest\n");
		
		char theGrade = 'B';
		
		/* When you have a limited number of possible values a switch statement makes sense 
		 * The switch statement checks the value of theGrade to the values that follow case
		 * If it matches it executes the code between {} and then break ends the switch statement
		 * default code is executed if there are no matches
		 * You are not required to use the break or default statements
		 * The expression must be an int, short, byte, or char
		 */
		switch (theGrade)
		{
		case 'A':
			System.out.println("Great Job");
			break; // Ends the switch statement
		case 'b': // You can use multiple case statements in a row
		case 'B':
			System.out.println("Good Job, get an A next time");
			break;
		case 'C':
			System.out.println("OK, but you can do better");
			break;
		case 'D':
			System.out.println("You must work harder");
			break;
		default:
			System.out.println("You failed");
			break;
		}
		
	}
	
}
```

## Lesson 4

```java
import java.util.Scanner; // Library that allows us to capture user input

public class LessonFour {
	
	// Creates a Scanner object that monitors keyboard input
	static Scanner userInput = new Scanner(System.in);
	
	public static void main(String[] args)
	{
		/*
		 * The while loop : A while loop executes the code between {} until the 
		 * condition is no longer true
		 */
		// while loops create a loop iterator before the loop begins
		int i = 1;
		
		while(i < 20)
		{
			// Use continue to skip over printing 3
			if(i == 3)
			{
				i+=2; // When using continue, don't forget to change the iterator
				continue; // continue skips a loop iteration, but not the loop
			}
			
			System.out.println(i);
			i++;
			
			// Just print odd numbers
			if((i%2) == 0)
			{
				i++;
			}
			
			// i is greater than 10 jump out of the loop
			if(i > 10)
			{
				break; // Forces the program to leave the loop prematurely
			}
		}
		
		/* 
		 * Code that calculates the value for PI
		 */
		double myPi = 4.0; // My starting value for pi
		
		// Starting value for my loop iterator in the loop
		double j = 3.0; 
		
		// The while loop
		while(j<11)
		{
			// I calculate pi with this formula
			// PI = 4 - 4/3 + 4/5 - 4/7...
			myPi = myPi - (4/j) + (4/(j+2));
			j += 4;
			System.out.println(myPi);
		}
		
		System.out.println("Value of PI: " + Math.PI);
		
		/*
		 * Execute while loop until the user quits it
		 */
		String contYorN = "Y";
		int h = 1;
		
		// equalsIgnoreCase checks if the input string is equal to y or Y
		while (contYorN.equalsIgnoreCase("y"))
		{
			System.out.println(h);
			System.out.print("Continue y or n?");
			contYorN = userInput.nextLine(); // Accepts a string input from the user
			h++;
			
		}
		
		/* 
		 * The do while loop : Used when you want to guarantee the code 
		 * between {} will execute at least once. The code is executed and
		 * then java checks if it should execute again
		 */
		// loop iterator for the do while loop
		// It must be created before the expression is evaluated below
		int k = 1;
		
		do 
		{
			System.out.println(k);
			k++;
		} while (k <= 10); // Counts from 1 to 10
		
		/*
		 * The for loop : Another looping tool in Java
		 * for( declare iterator; conditional statement; change iterator value)
		 */
		
		for (int l=10; l >= 1; l--)
		{
			System.out.println(l);
		}
		
		// System.out.println(l); The variable l is not callable outside of for

		int m, n; // You don't have to declare variables in the for loop
		// You can use multiple variables in the for loop
		for (m=1, n=2; m <= 9; m+=2, n+=2)
		{
			System.out.println(m + "\n" + n);
		}
		
		// You can have for loops inside of for loops, but I'll save 
		// that topic until I talk about arrays
		
	}
	
}
```

## Lesson 5

```java
import java.util.Scanner; // Scanner is a class that contains a bunch of methods

public class LessonFive {
	// main is a method that contains all of the code to be executed when a program runs
	
	// This is a class variable that is available to every method
	// If you declare a variable in a method it is only accessible in that method (local variable)
	
	static double myPI = 3.14159265; 
	
	// Any changes made to randomNumber in any functions will effect its global value
	
	static int randomNumber;
	
	// Creates a Scanner object that monitors keyboard input
	
	static Scanner userInput = new Scanner(System.in);
	
	public static void main(String[] args)
	{
		
		/* Basic Method
		 * accessModifier static returnDataType methodName (parameters)
		 * { Statements }
		 * Access Modifier: Determines who can execute a method
		 * static: Used when you want to be able to execute a method that isn't part of a class definition
		 * Return Data Type: The data type of value returned after a method executes (void if no values are returned)
		 * Method Name: Must start with a letter, but can include letters, numbers, $, or _
		 * Parameters / Arguments: Values passed to a method
		 */
		
		System.out.println(addThem(1,2)); // addThem(1,2) will be replaced with the value that method returns
		
		// Demonstrating passing by value
		int d = 5;
		
		// Changes to the variable d in tryToChange don't effect its value globally
		// We are passing the value of d to tryToChange and not the variable
		
		tryToChange(d);
		System.out.println("Static Variable d = "+ d);
		
		// Guessing a random number
		System.out.println("\n");
		
		System.out.println(getRandomNum()); // Both prints and generates the value for randomNumber
		
		int guessResult = 1;
		int randomGuess = 0;
		
		while(guessResult != -1)
		{
		System.out.print("Guess a number between 0 and 50: ");
		
		// Accepts an integer input from the user
		// You can't declare this variable inside the while loop if you want to access it outside the while loop
		
		randomGuess = userInput.nextInt(); 
		
		guessResult = checkGuess(randomGuess);
		}
		
		System.out.println("Yes the random number is " + randomGuess);
		
		System.out.println(randomNumber); // Random value was changed globally by getRandomNum
		
	}
	
	// Adds the two numbers sent and returns the solution
	// public is the access modifier and means anyone can execute this method
	// Java Methods can return any primitive data type, or reference to an object (More on that later)
	
	public static int addThem(int a, int b)
	{
		double smallPI = 3.140; // This variable is local to the addThem function
		
		// compare returns 0 if equal | -1 if smallPI is less than myPI | 1 if smallPI is greater than myPI
		
		System.out.println(Double.compare(smallPI, myPI));
		
		int c = a + b;
		
		// return returns a value that replaces the call to this method
		// It must be an int since you defined this method returns ints above
		
		return c; 
	}
	
	// When you define an attribute / parameter you must define its type
	// That's why you can't type tryToChange(d)
	// Because this function doesn't return a value return type is void
	
	public static void tryToChange(int d)
	{
		d = d + 1;
		System.out.println("tryToChange d = " + d);
	}
	
	public static int getRandomNum()
	{
		// Creates a random number between 0 and 50
		// Since randomNumber is a class variable you don't have to declare, or define its type
		// If int randomNumber was declared in this method it wouldn't effect the global variable named randomNumber
		
		randomNumber = (int) (Math.random() * 51);
		return randomNumber;
	}
	
	public static int checkGuess(int guess)
	{
		if(guess == randomNumber)
		{
			return -1;
		} else {
			return guess; // Must return a value of type int
		}
	}
	
}
```

## Lesson 6

```java
		/* An exception object is created when an error occurs
		 * It tells you what error occurred
		 * Here are many of the java exceptions
		 * 
		 * java.lang.RuntimeException : exceptions that can be thrown during the normal 
		 * operation of the Java Virtual Machine. These exceptions are your responsibility 
		 * as a programmer
		 * 
		 * ArithmeticException, ArrayStoreException, BufferOverflowException, 
		 * BufferUnderflowException, CannotRedoException, CannotUndoException, 
		 * ClassCastException, CMMException, ConcurrentModificationException, 
		 * DOMException, EmptyStackException, IllegalArgumentException, 
		 * IllegalMonitorStateException, IllegalPathStateException, 
		 * IllegalStateException, ImagingOpException, IndexOutOfBoundsException, 
		 * MissingResourceException, NegativeArraySizeException, NoSuchElementException, 
		 * NullPointerException, ProfileDataException, ProviderException, 
		 * RasterFormatException, SecurityException, SystemException, 
		 * UndeclaredThrowableException, UnmodifiableSetException, 
		 * UnsupportedOperationException
		 * 
		 * java.lang.Exception : exceptions that are checked for by the java compiler
		 * 
		 * AclNotFoundException, ActivationException, AlreadyBoundException, 
		 * ApplicationException, AWTException, BackingStoreException, 
		 * BadAttributeValueExpException, BadBinaryOpValueExpException, 
		 * BadLocationException, BadStringOperationException, 
		 * BrokenBarrierException, CertificateException, ClassNotFoundException, 
		 * CloneNotSupportedException, DataFormatException, 
		 * DatatypeConfigurationException, DestroyFailedException, 
		 * ExecutionException, ExpandVetoException, FontFormatException, 
		 * GeneralSecurityException, GSSException, IllegalAccessException, 
		 * IllegalClassFormatException, InstantiationException, 
		 * InterruptedException, IntrospectionException, 
		 * InvalidApplicationException, InvalidMidiDataException, 
		 * InvalidPreferencesFormatException, InvalidTargetObjectTypeException, 
		 * InvocationTargetException, IOException, JAXBException, JMException, 
		 * KeySelectorException, LastOwnerException, LineUnavailableException, 
		 * MarshalException, MidiUnavailableException, MimeTypeParseException, 
		 * MimeTypeParseException, NamingException, NoninvertibleTransformException, 
		 * NoSuchFieldException, NoSuchMethodException, NotBoundException, 
		 * NotOwnerException, ParseException, ParserConfigurationException, 
		 * PrinterException, PrintException, PrivilegedActionException, 
		 * PropertyVetoException, RefreshFailedException, RemarshalException, 
		 * RuntimeException, SAXException, ScriptException, ServerNotActiveException, 
		 * SOAPException, SQLException, TimeoutException, TooManyListenersException, 
		 * TransformerException, TransformException, UnmodifiableClassException, 
		 * UnsupportedAudioFileException, UnsupportedCallbackException, 
		 * UnsupportedFlavorException, UnsupportedLookAndFeelException, 
		 * URIReferenceException, URISyntaxException, UserException, XAException, 
		 * XMLParseException, XMLSignatureException, XMLStreamException, XPathException
		 */

		/* Common Exceptions
		 * ArithmeticException: An arithmetic operation occurs with no answer 
		 * (Division by Zero)
		 * 
		 * ClassNotFoundException: A class is called for that doesn't exist
		 * 
		 * IllegalArgumentException: A method has been passed an illegal argument
		 * 
		 * IndexOutOfBoundsException: Thrown when an index for an array, string is
		 * called for, but doesn't exist
		 * 
		 * InputMismatchException: (Part of NoSuchElementException) User enters the 
		 * wrong data type into a Scanner method
		 * 
		 * IOException: An I/O operation failed
		 */
import java.util.Scanner; // Library that allows us to capture user input
import java.util.*; // Allows me to check for InputMismatchException
import java.io.*; // Allows for system input and output through data streams, serialization and the file system

public class LessonSix {
	
	// Creates a Scanner object that monitors keyboard input
	static Scanner userInput = new Scanner(System.in);
	
	public static void main(String[] args){
		
		divideByZero(2);
		
		System.out.print("How old are you? ");
		int age = checkValidAge();
		
		if (age != 0){
		System.out.println("You are " + age + " years old");
		}
		
		getAFile("./somestuff.txt");
		
	}
	
	public static void divideByZero(int a)
	{
		
		try
		{
			// The following throws an error because you can't divide by zero
			// Exception in thread "main" java.lang.ArithmeticException
			System.out.println(a/0);
		}
		
		// If the exception ArithmeticException is thrown the following execute
		catch (ArithmeticException e)
		{
			// Your custom error message
			System.out.println("You can't divide by zero");
			
			// Java's error message for this exception
			System.out.println(e.getMessage());
			
			// Prints the exception name and error message
			System.out.println(e.toString());
			
			// Prints the standard error stack trace
			e.printStackTrace();
		}
		
	}
	
	public static int checkValidAge()
	{
		
		try
		{
			return userInput.nextInt(); // nextInt() receives the user input
		}
		
		catch (InputMismatchException e)
		{
			userInput.next(); // Skips the last user input and waits for the next
			System.out.print("That isn't a whole number");
			return 0;
		}
		
	}
	
	/* If you prefer to throw an exception to the calling method you use throw
	 * public static void getAFile(String fileName) throws IOException, FileNotFoundException
	 * {
	 * 		FileInputStream file = new FileInputStream(fileName);
	 * }
	 * 
	 * If main called this method, main would have to handle the exception
	 * 
	 * public static void main(String[] args) {
	 * 		try {
	 * 			getAFile("./somestuff.txt");
	 * 		}
	 * 		catch(IOException e) {
	 * 			System.out.println("An unknown IO Error Occured");
	 * 		}
	 */
	
	public static void getAFile(String fileName)
	{
		try 
		{
		/* If I tried to do this without providing for an exception
		* I'd get the error Unhandled Exception Type FileNotFoundException
		* A checked exception is an exception the compiler forces you to protect against
		*/ 
		FileInputStream file = new FileInputStream(fileName); 
		}
		
		catch (FileNotFoundException e)
		{
			System.out.println("Sorry I couldn't find that file");
		}
		
		// You can catch numerous exceptions (List most specific first
		catch (IOException e) // Catches any IO Exception
		{
			System.out.println("An unknown IO Error Occured");
		}
		
		/* To ignore an exception do this
		 * catch (ClassNotFoundException e)
		 * {}
		 */
		
		/* Java 7 allows you to catch multiple exceptions at once
		 * catch (FileNotFoundException | IOException e)
		 * {}
		 */
		
		// This will catch any exception (This should always be last)
		catch (Exception e)
		{
			System.out.println("I catch every exception");
		}
		
		// If used finally is always executed whether there was an exception or not
		// It is used for clean up work like closing files and database connections
		finally
		{
			System.out.println("");
		}
		
	}
	
}
```

## Lesson 7

```java
// Basic class definition
// public means this class can be used by other classes
// Class names should begin with a capital letter
// A file can't contain two public classes. It can contain classes that are not public
// If you place class files in the same folder the java compiler will be able to find them

public class Monster{
	
	// Class Variables or Fields
	// You declare constants with final
	
	public final String TOMBSTONE = "Here Lies a Dead monster";
	
	// private fields are not visible outside of the class
	private int health = 500;
	private int attack = 20;
	private int movement = 2;
	private int xPosition = 0;
	private int yPosition = 0;
	private boolean alive = true;
	
	// public variables are visible outside of the class
	// You should have as few as possible public fields
	public String name = "Big Monster";
	
	// Class Methods
	// Accessor Methods are used to get and set the values of private fields
	
	public int getAttack()
	{
		return attack;
	}
	
	public int getMovement()
	{
		return movement;
	}
	
	public int getHealth()
	{
		return health;
	}
	
	// You can create multiple versions using the same method name
	// Now setHealth can except an attack that contains decimals
	// When overloading a method you can't just change the return type
	// Focus on creating methods that except different parameters
	
	public void setHealth(int decreaseHealth)
	{
		health = health - decreaseHealth;
		if (health < 0)
		{
			alive = false;
		}
	}
	
	public void setHealth(double decreaseHealth)
	{
		int intDecreaseHealth = (int) decreaseHealth;
		health = health - intDecreaseHealth;
		if (health < 0)
		{
			alive = false;
		}
	}
	
	/* The Constructor
	 * Code that is executed when an object is created from this class definition
	 * The method name is the same as the class
	 * The constructor is only executed once per object
	 * The constructor can't return a value
	 */
	
	public Monster(int health, int attack, int movement)
	{
		this.health = health;
		this.attack = attack;
		this.movement = movement;
		/* If the attributes had the same names as the class health, attack, movement
		 * You could refer to the objects fields by proceeding them with this
		 * this.health = health;
		 * this.attack = attack;
		 * objectFieldName = attributeFieldName;
		 */
		
	}
	
	// You can overload constructors like any other method
	// The following constructor is the one provided by default if you don't create any other constructors
	// Default Constructor
	
	public Monster()
	{
		
	}
	
	/* You can use the this keyword to call other constructors
	 * public LessonSeven(int newHealth)
	 * {
	 * 		health = newHealth;
	 * }
	 * 
	 * public LessonSeven(int newHealth, int newAttack)
	 * {
	 * 		this(newHealth); // Any calls to another constructor must occur on the first line
	 * 		attack = newAttack;
	 * }
	 */
	
}
```

```java
public class JavaLessonSeven {
	
	public static void main(String[] args){
		
		// You create an object using the blueprint of this class as follows
		// className objectName = new className();
		
		Monster Frank = new Monster();
		
		// Since the objects name is public you can change it directly
		
		Frank.name = "Frank";
		
		// You retrieve class field values by listing the objectName.fieldName
		// You execute class methods by listing objectName.methodName()
		
		System.out.println(Frank.name + " has an attack value of " + Frank.getAttack());
	
	}
}
```



## Lesson 8

```java
import java.util.Arrays;
import org.apache.commons.lang3.ArrayUtils;

// Basic class definition
// public means this class can be used by other classes
// Class names should begin with a capital letter
// A file can't contain two public classes. It can contain classes that are not public
// If you place class files in the same folder the java compiler will be able to find them

/* The Goal of this tutorial is to make a game like this
------------------------------
|*||*||*||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|*||M||F||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|P||*||*||*||*||*||*||*||*||*|
|*||*||*||*||D||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
------------------------------
[9,9]

 */

public class LessonEight {
	
	public static void main(String[] args)
	{
		
		MonsterTwo.buildBattleBoard();
		
		char[][] tempBattleBoard = new char[10][10];
		
		// ObjectName[] ArrayName = new ObjectName[4];
		
		MonsterTwo[] Monsters = new MonsterTwo[4];
		
		// MonsterTwo(int health, int attack, int movement, String name)
		
		Monsters[0] = new MonsterTwo(1000, 20, 1, "Frank");
		Monsters[1] = new MonsterTwo(500, 40, 2, "Drac");
		Monsters[2] = new MonsterTwo(1000, 20, 1, "Paul");
		Monsters[3] = new MonsterTwo(1000, 20, 1, "George");
		
		MonsterTwo.redrawBoard();
		
	}
	
	
}
```

```java
import java.util.Arrays;

// Basic class definition
// public means this class can be used by other classes
// Class names should begin with a capital letter
// A file can't contain two public classes. It can contain classes that are not public
// If you place class files in the same folder the java compiler will be able to find them

public class MonsterTwo{
	
	static char[][] battleBoard = new char[10][10];
	
	public static void buildBattleBoard(){
		
		for(char[] row : battleBoard)
		{
			
			Arrays.fill(row, '*');
			
		}
		
	}
	
	public static void redrawBoard()
	{
		
		int k = 1;
		while(k <= 30){ System.out.print('-'); k++; }
		System.out.println();
		
		for (int i = 0; i < battleBoard.length; i++)
		{
			
			for(int j = 0; j < battleBoard[i].length; j++)
			{
				
				System.out.print("|" + battleBoard[i][j] + "|");
				
			}
			System.out.println();
			
		}
		k = 1;
		while(k <= 30){ System.out.print('-'); k++; }
		System.out.println();
		
		
	}
	
	// Class Variables or Fields
	// You declare constants with final
	
	public final String TOMBSTONE = "Here Lies a Dead monster";
	
	// private fields are not visible outside of the class
	private int health = 500;
	private int attack = 20;
	private int movement = 2;
	
	private boolean alive = true;
	
	// public variables are visible outside of the class
	// You should have as few as possible public fields
	public String name = "Big Monster";
	public char nameChar1 = 'B';
	public int xPosition = 0;
	public int yPosition = 0;
	public static int numOfMonsters = 0;
	
	// Class Methods
	// Accessor Methods are used to get and set the values of private fields
	
	public int getAttack()
	{
		return attack;
	}
	
	public int getMovement()
	{
		return movement;
	}
	
	public int getHealth()
	{
		return health;
	}
	
	public boolean getAlive()
	{
		return alive;
	}
	
	// You can create multiple versions using the same method name
	// Now setHealth can except an attack that contains decimals
	// When overloading a method you can't just change the return type
	// Focus on creating methods that except different parameters
	
	public void setHealth(int decreaseHealth)
	{
		health = health - decreaseHealth;
		if (health < 0)
		{
			alive = false;
		}
	}
	
	public void setHealth(double decreaseHealth)
	{
		int intDecreaseHealth = (int) decreaseHealth;
		health = health - intDecreaseHealth;
		if (health < 0)
		{
			alive = false;
		}
	}
	
	/* The Constructor
	 * Code that is executed when an object is created from this class definition
	 * The method name is the same as the class
	 * The constructor is only executed once per object
	 * The constructor can't return a value
	 */
	
	public MonsterTwo(int health, int attack, int movement, String name)
	{
		this.health = health;
		this.attack = attack;
		this.movement = movement;
		this.name = name;
		/* If the attributes had the same names as the class health, attack, movement
		 * You could refer to the objects fields by proceeding them with this
		 * this.health = health;
		 * this.attack = attack;
		 * objectFieldName = attributeFieldName;
		 */
		
		int maxXBoardSpace = battleBoard.length - 1;
		int maxYBoardSpace = battleBoard[0].length - 1;
		
		int randNumX, randNumY;
		
		do {
			
			randNumX = (int) (Math.random() * maxXBoardSpace);
			randNumY = (int) (Math.random() * maxYBoardSpace);
			
		} while(battleBoard[randNumX][randNumY] != '*');
		
		this.xPosition = randNumX;
		this.yPosition = randNumY;
		
		this.nameChar1 = name.charAt(0);
		
		battleBoard[this.yPosition][this.xPosition] = this.nameChar1;
		
		numOfMonsters++;
		
	}
	
	// You can overload constructors like any other method
	// The following constructor is the one provided by default if you don't create any other constructors
	// Default Constructor
	
	public MonsterTwo()
	{
		numOfMonsters++;
	}
	
public static void main(String[] args)
{
	
	
}
	
}
```



## Lesson 9

```java
import java.util.Arrays;

public class LessonNine {
	
	public static void main(String[] args){
		
		// An array is a variable that can hold a bunch of values
		// Think of an array as a big box filled with other boxes
		// Each box has a number on it called an index that you use 
		// to access its specific value
		
		/* Array Rules
		 * An array can contain only values of the same type
		 * An arrays size can't be changed once it is set
		 * An array is an object
		 */
		
		// You declare an array with the dataType[] arrayName
		int[] randomArray; 
		
		// You create an array with 
		// dataType[] arrayName = new dataType[sizeOfArray];
		
		int[] numberArray = new int[10];
		
		// You can add values to the array in many ways
		// Individually
		
		// Most create array and define size first
		randomArray = new int[20]; 
		randomArray[1] = 2;
		
		// You can also create the array and its values from the start
		String[] stringArray = {"Just", "Random", "Words"};
		
		// You can add values with a loop
		// arrayName.length returns the number of elements in the array
		for(int i = 0; i < numberArray.length; i++)
		{
			
			numberArray[i] = i;
			
		}
		
		// Draws 41 lines on the screen
		int k = 1;
		while(k <= 41){ System.out.print('-'); k++; }
		System.out.println();
		
		// Cycles through all of the boxes in the array and prints them
		for(int j = 0; j < numberArray.length; j++)
		{
			System.out.print("| " + j + " ");
		}
		System.out.println("|");
		
		// Draws 41 lines on the screen
		k = 1;
		while(k <= 41){ System.out.print('-'); k++; }
		System.out.println();
		
		// Multidimensional Array
		// To but arrays in an array just add another []
		
		String[][] multiDArray = new String[10][10];
		
		// Adding values to a multidimensional array
		
		for(int i = 0; i < multiDArray.length; i++)
		{
			
			// To get the length for the array in the array you must follow it 
			// with brackets with the index between them like [i]
			
			for(int j = 0; j < multiDArray[i].length; j++)
			{
				
				multiDArray[i][j] = i + " " + j;
				
			}
			
		}
		
		// Draws 61 lines on the screen
		k = 1;
		while(k <= 61){ System.out.print('-'); k++; }
		System.out.println();
		
		// Prints out a multidimensional array with the values being the indexes
		
		for(int i = 0; i < multiDArray.length; i++)
		{
			
			for(int j = 0; j < multiDArray[i].length; j++)
			{
				
				System.out.print("| " + multiDArray[i][j] + " ");
				
			}
			System.out.println("|");
			
		}
		
		// Draws 61 lines on the screen
		k = 1;
		while(k <= 61){ System.out.print('-'); k++; }
		System.out.println();
		
		// You can use the enhanced for loop to print out array values
		// for(itemDataType tempVariable : arrayName)
		
		for(int row : numberArray)
		{
			System.out.print(row);
		}
		System.out.println("\n");
		
		// To use enhanced for for a multidimensional array you follow this formula
		// for(dataType[] varForRow : arrayName)
		
		for(String[] rows : multiDArray) 
		{
			// for(elementDataType varForColumn : varForRow)
			for(String column : rows) 
			{
				System.out.print("| " + column + " ");
		    }
		        System.out.println("|");
		}
		
		// You can copy an array in a couple of ways
		// Arrays.copyOf(arrayToCopy, numberToCopyFromBeginning);
		
		int[] numberCopy = Arrays.copyOf(numberArray, 5);
		for(int num : numberCopy)
		{
			System.out.print(num);
		}
		System.out.println("\n");
		
		// You can copy an array from one index to another with copyOfRange
		// int[] numberCopy = Arrays.copyOf(numberArray, 1, 5);
		
		// You can print out the whole array with toString
		System.out.println(Arrays.toString(numberCopy));
		
		
		// Do define a default value for an array use fill
		// Arrays.fill(arrayName, valueToFill);
		// valueToFill must be the same for each element in the array
		
		int[] moreNumbers = new int[100];
		Arrays.fill(moreNumbers, 2);
		
		// Filling a multidimensional array
		char[][] boardGame = new char[10][10];
		for(char[] row : boardGame)
		{
			Arrays.fill(row, '*');
		}
		
		// You can sort an array using sort()
		int[] numsToSort = new int[10];
		
		// Generate array full of random numbers
		for(int i = 0; i < 10; i++)
		{
			numsToSort[i] = (int) (Math.random() * 100);
		}
		
		// Sort the array in ascending order
		Arrays.sort(numsToSort);
		
		System.out.println(Arrays.toString(numsToSort));
		
		// binarySearch returns the index for the searched for value
		// If it doesn't find it it returns a negative number
		
		int whereIs50 = Arrays.binarySearch(numsToSort, 50);
		
		System.out.println(whereIs50);
	}
	
}
```

## Lesson 10

```java
import java.util.Arrays;

import org.apache.commons.lang3.ArrayUtils;

// Basic class definition
// public means this class can be used by other classes
// Class names should begin with a capital letter
// A file can't contain two public classes. It can contain classes that are not public
// If you place class files in the same folder the java compiler will be able to find them

public class MonsterTwo{
	// Creates a multidimensional array of chars
	static char[][] battleBoard = new char[10][10];
	
	// This static method builds an empty battle board
	public static void buildBattleBoard(){
		
		// Cycles through the array and gives a default value of * to everything
		
		for(char[] row : battleBoard)
			Arrays.fill(row, '*');
	}
	
	// Redraws the board
	public static void redrawBoard()
	{
		
		int k = 1;
		while(k <= 30){ System.out.print('-'); k++; }
		System.out.println();
		
		for(int i = 0; i < battleBoard.length; i++)
		{
			for(int j = 0; j < battleBoard[i].length; j++)
			{
				System.out.print("|" + battleBoard[i][j] + "|");
			}
			System.out.println();
			
		}
		k = 1;
		while(k <= 30){ System.out.print('-'); k++; }
		System.out.println();
	}
	
	// Class Variables or Fields
	// You declare constants with final
	
	public final String TOMBSTONE = "Here Lies a Dead monster";
	
	// private fields are not visible outside of the class
	private int health = 500;
	private int attack = 20;
	private int movement = 2;
	
	// Monitors whether the monster is alive or dead
	private boolean alive = true;
	
	// public variables are visible outside of the class
	// You should have as few as possible public fields
	public String name = "Big Monster";
	public int xPosition = 0;
	public int yPosition = 0;
	public char nameChar1 = 'B';
	public static int numOfMonsters = 0;
	
	
	// Class Methods
	// Accessor Methods are used to get and set the values of private fields
	
	public int getAttack()
	{
		return attack;
	}
	
	public int getMovement()
	{
		return movement;
	}
	
	public int getHealth()
	{
		return health;
	}
	
	public boolean getAlive()
	{
		return alive;
	}
	
	// You can create multiple versions using the same method name
	// Now setHealth can except an attack that contains decimals
	// When overloading a method you can't just change the return type
	// Focus on creating methods that except different parameters
	
	public void setHealth(int decreaseHealth)
	{
		health = health - decreaseHealth;
		if (health < 0)
		{
			alive = false;
		}
	}
	
	public void setHealth(double decreaseHealth)
	{
		int intDecreaseHealth = (int) decreaseHealth;
		health = health - intDecreaseHealth;
		if (health < 0)
		{
			alive = false;
		}
	}
	
	public void moveMonster(MonsterTwo[] monster, int arrayItemIndex)
	{
		// isSpaceOpen will be used to track whether the space the
		// monster plans to move into is occupied
		boolean isSpaceOpen = true;
		
		// Define the maximum x and y for the battle board
		// It's 1 less because the array index starts at 0
		int maxXBoardSpace = battleBoard.length - 1;
		int maxYBoardSpace = battleBoard[0].length - 1;
		
		
		// while loop used to make sure I don't move a monster
		// into an occupied space
		while(isSpaceOpen)
		{
		
		// Randomly generate move direction N, S, E, or W
		int randMoveDirection = (int) (Math.random() * 4);
		
		// Randomly generate move distance based on max move distance
		int randMoveDistance = (int) (Math.random() * (this.getMovement() + 1));
		
		// Prints move distance and move direction
		System.out.println(randMoveDistance + " " + randMoveDirection);
		
		// Erase monsters character on the board by replacing it with a *
		
		battleBoard[this.yPosition][this.xPosition] = '*';
		

			
		if(randMoveDirection == 0)
		{
			// Find new xPosition & yPosition based on the current position on the board
			// If statements won't allow monster to move off the board
			
			if((this.yPosition - randMoveDistance) < 0)
			{
				this.yPosition = 0;
			} else {
				this.yPosition = this.yPosition - randMoveDistance;
			}
		} else if (randMoveDirection == 1) {
			if((this.xPosition + randMoveDistance) > maxXBoardSpace)
			{
				this.xPosition = maxXBoardSpace;
			} else {
				this.xPosition = this.xPosition + randMoveDistance;
			}
		} else if (randMoveDirection == 2) {
			if((this.yPosition + randMoveDistance) > maxYBoardSpace)
			{
				this.yPosition = maxYBoardSpace;
			} else {
				this.yPosition = this.yPosition + randMoveDistance;
			}
		} else {
			if((this.xPosition - randMoveDistance) < 0)
			{
				this.xPosition = 0;
			} else {
				this.xPosition = this.xPosition - randMoveDistance;
			}
		}
		
		// monster.length returns the number of items in the array monster
		for (int i = 0; i < monster.length; i++)
		{
			// if statement skips checking the same monster position against itself
			
			if (i == arrayItemIndex)
			{
				continue;
			} 
			
			// onMySpace receives the monster array, index for the object I'm 
			// checking currently, and the index for the monster sent to 
			// this function
			
			if(onMySpace(monster, i, arrayItemIndex))
			{
				// If a monster tries to move to an occupied space the
				// while loop repeats after I break out of the for loop
				
				isSpaceOpen = true;
				break;
			} else {
				// There was no monster in the space so end the while loop
				isSpaceOpen = false;
				
			}
			
		}
		
		} // End of while loop
		
		// Set the value in the array to the first letter of the monster
		battleBoard[this.yPosition][this.xPosition] = this.nameChar1;	
	}
	
	// Checks if one monster is trying to move into the same x/y position as 
	// another monster
	public boolean onMySpace(MonsterTwo[] monster, int indexToChk1, int indexToChk2)
	{
		// Checks if the 2 monsters have the same x/y position
		if((monster[indexToChk1].xPosition)==(monster[indexToChk2].xPosition)&&(monster[indexToChk1].yPosition)==(monster[indexToChk2].yPosition))
		{
			// If they are equal return true so a new x/y position is calculated
			
			return true;
			
		} else {
			
			// If false I know the x/y position isn't occupied
			return false;
		}
	}
	
	
	/* The Constructor
	 * Code that is executed when an object is created from this class definition
	 * The method name is the same as the class
	 * The constructor is only executed once per object
	 * The constructor can't return a value
	 */
	
	public MonsterTwo(int health, int attack, int movement, String name)
	{
		this.health = health;
		this.attack = attack;
		this.movement = movement;
		this.name = name;
		/* If the attributes had the same names as the class health, attack, movement
		 * You could refer to the objects fields by proceeding them with this
		 * this.health = health;
		 * this.attack = attack;
		 * objectFieldName = attributeFieldName;
		 */
		
		// Define the maximum x and y for the battle board
		// It's 1 less because the array index starts at 0
		int maxXBoardSpace = battleBoard.length - 1;
		int maxYBoardSpace = battleBoard[0].length - 1;
		
		// The random starting position for a monster
		int randNumX, randNumY;
		
		// We use a do loop because we always want to define a start 
		// position for each monster
		
		do {
		// Calculate start position based on max board space
		randNumX = (int) (Math.random() * maxXBoardSpace);
		randNumY = (int) (Math.random() * maxYBoardSpace);
		} while(battleBoard[randNumY][randNumX] != '*');
		// Only allow monster to start on a space with a * on it
		
		// Assign x and y position to the object that called this method
		this.xPosition = randNumX;
		this.yPosition = randNumY;
		
		// Assign character in the array based on the first initial
		// of the monsters name charAt(0) returns first letter of name
		this.nameChar1 = this.name.charAt(0);
		
		// Put first character of monster in the array
		battleBoard[this.yPosition][this.xPosition] = this.nameChar1;
		
		numOfMonsters++; // Adds 1 to the number of monsters on the board
	}
	
	// You can overload constructors like any other method
	// The following constructor is the one provided by default if you don't create any other constructors
	// Default Constructor
	
	public MonsterTwo()
	{
		numOfMonsters++; // Adds 1 to the number of monsters on the board
	}
	
public static void main(String[] args)
{
	
	
	
}
	
}
```

```java
import java.util.Arrays;
import org.apache.commons.lang3.ArrayUtils;

// Basic class definition
// public means this class can be used by other classes
// Class names should begin with a capital letter
// A file can't contain two public classes. It can contain classes that are not public
// If you place class files in the same folder the java compiler will be able to find them

/* The Goal of this tutorial is to make a game like this
------------------------------
|*||*||*||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|*||M||F||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
|P||*||*||*||*||*||*||*||*||*|
|*||*||*||*||D||*||*||*||*||*|
|*||*||*||*||*||*||*||*||*||*|
------------------------------
[9,9]

 */

public class LessonTen {
	
	public static void main(String[] args)
	{
		
		MonsterTwo.buildBattleBoard();
		
		// char[][] tempBattleBoard = new char[10][10];
		
		// ObjectName[] ArrayName = new ObjectName[4];
		
		MonsterTwo[] Monsters = new MonsterTwo[4];
		
		// MonsterTwo(int health, int attack, int movement, String name)
		
		Monsters[0] = new MonsterTwo(1000, 20, 1, "Frank");
		Monsters[1] = new MonsterTwo(500, 40, 2, "Drac");
		Monsters[2] = new MonsterTwo(1000, 20, 1, "Paul");
		Monsters[3] = new MonsterTwo(1000, 20, 1, "George");
		
		MonsterTwo.redrawBoard();
		
	
	for (MonsterTwo m : Monsters)
	{
		
		if(m.getAlive())
		{
			int arrayItemIndex = ArrayUtils.indexOf(Monsters, m);
			m.moveMonster(Monsters, arrayItemIndex);
		}
		
	}
	
	MonsterTwo.redrawBoard();
	
	
}
}
```



## Lesson 11

```java
// Collection classes were created to make it easy to keep track 
// of groups of objects. An ArrayList differs from an array in
// that it automatically resizes itself automatically. ArrayLists
// are easy to add to and delete from.

import java.util.ArrayList; // The ArrayList library
import java.util.Iterator; // The Iterator Library
import java.util.Arrays; // The Arrays Library

public class LessonEleven {
	
	public static void main(String[] args)
	{
		
		// You can create an ArrayList variable
		ArrayList arrayListOne;
		
		// Then create an ArrayList object
		// You don't have to declare the ArrayList size like you
		// do with arrays (Default Size of 10)
		arrayListOne = new ArrayList();
		
		// You can create the ArrayList on one line
		
		ArrayList arrayListTwo = new ArrayList();
		
		// You can also define the type of elements the ArrayList
		// will hold
		ArrayList<String> names = new ArrayList<String>();
		
		// This is how you add elements to an ArrayList
		names.add("John Smith");
		names.add("Mohamed Alami");
		names.add("Oliver Miller");
		
		// You can also add an element in a specific position
		names.add(2, "Jack Ryan");
		
		// You retrieve values in an ArrayList with get
		// arrayListName.size() returns the size of the ArrayList
		for( int i = 0; i < names.size(); i++)
		{
			System.out.println(names.get(i));
		}
		
		// You can replace a value using the set method
		names.set(0, "John Adams");
		
		// You can remove an item with remove
		names.remove(3);
		
		// You can also remove the first and second item with
		// the removeRange method
		// names.removeRange(0, 1);
		
		// When you print out the ArrayList itself the toString
		// method is called
		System.out.println(names);
		
		// You can also use the enhanced for with an ArrayList
		for(String i : names)
		{
			System.out.println(i);
		}
		System.out.println(); // Creates a newline
		
		// Before the enhanced for you had to use an iterator
		// to print out values in an ArrayList
		
		// Creates an iterator object with methods that allow
		// you to iterate through the values in the ArrayList
		Iterator indivItems = names.iterator();
		
		// When hasNext is called it returns true or false
		// depending on whether there are more items in the list
		
		while(indivItems.hasNext())
		{
			// next retrieves the next item in the ArrayList
			System.out.println(indivItems.next());
			
		}
		
		// I create an ArrayList without stating the type of values
		// it contains (Default is Object)
		ArrayList nameCopy = new ArrayList();
		ArrayList nameBackup = new ArrayList();
		
		// addAll adds everything in one ArrayList to another
		nameCopy.addAll(names);
		System.out.println(nameCopy);
		
		String paulYoung = "Paul Young";
		
		// You can add variable values to an ArrayList
		names.add(paulYoung);
		
		// contains returns a boolean value based off of whether
		// the ArrayList contains the specified object
		
		if(names.contains(paulYoung))
		{
			System.out.println("Paul is here");
		}
		
		// containsAll checks if everything in one ArrayList is in
		// another ArrayList
		if(names.containsAll(nameCopy))
		{
			System.out.println("Everything in nameCopy is in names");
		}
		
		// Clear deletes everything in the ArrayList
		names.clear();
		
		// isEmpty returns a boolean value based on if the ArrayList 
		// is empty
		if (names.isEmpty())
		{
			
			System.out.println("The ArrayList is empty");
			
		}
		
		Object[] moreNames = new Object[4];
		
		// toArray converts the ArrayList into an array of objects
		moreNames = nameCopy.toArray();
		
		// toString converts items in the array into a String
		System.out.println(Arrays.toString(moreNames));
		
		
	}
	
}
```

## Lesson 12

```java
// The LinkedList class is a collection based on a Linked List
// instead of an array. They are particularly good when you
// expect to perform many additions and deletions with a 
// collection. When using a linked list you don't have to 
// move items around when you add or delete an item. They 
// aren't particularly suited to providing access based off
// of index searches like an array though. Each object in a
// linked list contains a pointer to the objects that proceed
// and follow it.
// When you change an ArrayList a new array is created by it.

import java.util.Arrays;
import java.util.LinkedList; // LinkedList Library methods

public class LessonTwelve {
	
	public static void main(String[] args){
		
		// Creates a LinkedList object
		LinkedList linkedListOne = new LinkedList();
		
		// Creates a LinkedList that contains Strings
		LinkedList<String> names = new LinkedList<String>();
		
		// You use add to add items to the Linked List
		names.add("Ahmed Bennani");
		names.add("Ali Syed");
		
		// addLast places the object last in the list
		names.addLast("Nathan Martin");
		
		// addLast places the object first in the list
		names.addFirst("Joshua Smith");
		
		// You can define what position to place the object in
		names.add(0, "Noah Peeters");
		
		// You replace a value in an index with set()
		names.set(2, "Paul Newman");
		
		// You remove items either by providing the index, or 
		// the value
		names.remove(4);
		names.remove("Joshua Smith");
		
		// removeFirst() removes the first element
		// removeLast() removes the last element
		// removeFirstOccurrence(Object) removes the  
		// first Object that matches what you passed
		
		// You can use the enhanced for to print them out
		for(String name : names)
		{
			System.out.println(name);
		}
		
		/* OUTPUT
		 * Noah Peeters
		 * Paul Newman
		 * Ali Syed
		 */
		
		// You can retrieve values with get()
		System.out.println("\nFirst Index: " + names.get(0));
		
		/* OUTPUT
		 * First Index: Noah Peeters
		 */
		
		// Retrieve the first value with getFirst()
		System.out.println("\nFirst Index: " + names.getFirst());
		
		/* OUTPUT
		 * First Index: Noah Peeters
		 */
		
		// Retrieve the first value with getFirst()
		System.out.println("\nLast Index: " + names.getLast());
		
		/* OUTPUT
		 * Last Index: Ali Syed
		 */
		
		LinkedList<String> nameCopy = new LinkedList<String>(names);
		
		// When you print out the LinkedList itself the toString
		// method is called
		System.out.println("\nnameCopy: " + nameCopy);
		
		/* OUTPUT
		 * nameCopy: [Noah Peeters, Paul Newman, Ali Syed]
		 */
		
		// You can check if an object is in the list with contains()
		if(names.contains("Noah Peeters"))
		{
			System.out.println("\nNoahs Here");
		}
		
		/* OUTPUT
		 * Noahs Here
		 */
		
		// You can check if everything in one list is in another
		if(names.containsAll(nameCopy))
		{
			System.out.println("\nCollections are the same");
		}
		
		/* OUTPUT
		 * Collections are the same
		 */
		
		// Return the index for an object with indexOf
		System.out.println("\nIndex of Ali is: " + names.indexOf("Ali Syed"));
		
		/* OUTPUT
		 * Index of Ali is: 2
		 */
		
		// Check if a list is empty with isEmpty()
		System.out.println("List Empty: " + names.isEmpty());
		
		/* OUTPUT
		 * List Empty: false
		 */
		
		// Get the number of items in the list with size
		System.out.println("How many values: " + names.size());
		
		/* OUTPUT
		 * How many values: 3
		 */
		
		// peek() retrieves the first element, but doesn't throw an error 
		// if there is no element to retrieve
		System.out.println("Look without error: " + names.peek());
		
		/* OUTPUT
		 * Look without error: Noah Peeters
		 */
		
		// poll() returns the first value and deletes it from the list
		System.out.println("Remove first element: " + nameCopy.poll());
		
		/* OUTPUT
		 * Remove first element: Noah Peeters
		 */
		
		// poll() returns the last value and deletes it from the list
		System.out.println("Remove last element: " + nameCopy.pollLast());
		
		/* OUTPUT
		 * Remove last element: Ali Syed
		 */
		
		// push puts a new element on the front of the list
		nameCopy.push("Noah Peeters");
		
		// pop removes an element on the front of the list
		nameCopy.pop();
		
		System.out.println("\nnameCopy: " + nameCopy);
		
		/* OUTPUT
		 * nameCopy: [Paul Newman]
		 */
		
		// Create a new array to hold values from the Linked List
		Object[] nameArray = new Object[4];
		
		// toArray converts the LinkedList into an array of objects
		nameArray = names.toArray();
		
		// toString converts items in the array into a String
		System.out.println(Arrays.toString(nameArray));
		
		/* OUTPUT
		 * [Noah Peeters, Paul Newman, Ali Syed]
		 */
		
		// clear() deletes everything in the Linked List
		names.clear();
		
		
	}
	
}
```

## Lesson 13

```java
// Here I introduce the String class
// A String is an object unlike the other primitive data types

import java.util.Arrays;

public class LessonThirteen {
	
	public static void main(String[] args){
		
		// You create a String like this
		String randomString = "I'm just a random string";
		
		// If you want to use quotes in a string escape it with \
		// Always surround Strings with quotes " " and not Apostrophes ' '
		String gotToQuote ="He said, \"I'm here\"";
		
		/* Other common Escape Codes
		 * \n : Newline
		 * \b : Backspace
		 * \' : Apostrophe
		 * \" : Quote
		 * \\ : Backslash
		 */
		
		// You combine Strings with a +
		System.out.println(randomString + " " + gotToQuote);
		
		// You can add other data type to the string with a +
		int numTwo = 2;
		System.out.println(randomString + " " + numTwo);
		
		/* You convert primitive types to a string with toString
		 * String byteString = Byte.toString(bigByte);
		 * String shortString = Short.toString(bigByte);
		 * String intString = Integer.toString(bigInt);
		 * String longString = Long.toString(bigByte);
		 * String floatString = Float.toString(bigByte);
		 * String doubleString = Double.toString(bigByte);
		 * String booleanString = Boolean.toString(bigByte);
		 * 
		 * You convert from String to primitives with parse
		 * int stringToInt = Integer.parseInt(intString);
		 * parseSort, parseLong, parseByte, parseDouble, 
		 * parseBoolean, parseFloat
		 */
		
		// You compare strings with equals or equalsIgnoreCase
		String uppercaseStr = "BIG";
		String lowercaseStr = "big";
		
		if(uppercaseStr.equals(lowercaseStr))
		{
			System.out.println("They're equal");
		}
		
		if(uppercaseStr.equalsIgnoreCase(lowercaseStr))
		{
			System.out.println("Same letters");
		}
		
		String letters = "abcde";
		String moreLetters = "fghijk";
		
		// charAt returns the character in a string
		System.out.println("2nd Character: " + letters.charAt(1));
		
		// compareTo returns 0 if strings are equal
		// Returns a negative number if letters comes before moreLetters
		// Returns a positive number if letters comes after moreLetters
		// There is also a compareToIgnoreCase()
		System.out.println(letters.compareTo(moreLetters));
		
		// contains() returns a boolean depending on whether the 
		// String contains the String you pass it
		System.out.println(letters.contains("abc"));
		
		// endsWith() checks if the String ends with the String you pass
		System.out.println(letters.endsWith("de"));
		
		// startsWith() works similar to endsWith()
		
		// indexOf() returns the 1st index that matches the String passed
		System.out.println(letters.indexOf("cd"));
		
		// You can also specify the index to start searching from
		// indexOf(StringToLookFor, IndexStartPosition)
		
		// lastIndexOf() works like indexOf except it starts from the 
		// end of the String you are searching
		
		// length() returns the number of characters in a String
		System.out.println("Length of string: " + letters.length());
		
		// replace() replaces every occurrence of the first String with
		// the second String you provide
		System.out.println(letters.replace("abc", "xy"));
		
		// You can create an array of Strings with split()
		// You define how to break up the String using a delimiter
		// If you had 123,456 and used the delimiter "," you would
		// create the array [123,456]
		String[] letterArray = letters.split("");
		
		// toString() converts the array into a String to print it 
		System.out.println(Arrays.toString(letterArray));
		
		// toCharArray() inserts every character in the string into
		// separate indexes in an array 
		char[] charArray = letters.toCharArray();
		
		System.out.println(Arrays.toString(charArray));
		
		// substring() returns a String starting at the first index
		// through the last index provided
		System.out.println(letters.substring(1,4));
		
		// toUpperCase() converts all letters into uppercase
		// toLowerCase() does the opposite
		System.out.println(letters.toUpperCase());
		
		String randString = "   abc   ";
		
		// trim() gets rid of leading and trailing white space
		System.out.println(randString.trim());
		
		// A String is immutable, which means every time you change 
		// a String a new version is created in memory.
		// If you manipulate Strings allot use a StringBuilder
		
		// How to create a StringBuilder
		// It has a fixed space in memory
		StringBuilder randSB = new StringBuilder("A random string");
		
		// append() adds anything to the end of a SB
		System.out.println(randSB.append(" again"));
		
		// append() permanently effected the StringBuilder
		System.out.println(randSB);
		
		// delete() removes part of the SB from first index to the last
		System.out.println(randSB.delete(15, 21));
		
		// deleteCharAt(index) is used to delete individual chars
		
		// capacity() returns the number of indexs for the SB
		System.out.println(randSB.capacity());
		
		// ensureCapacity() increases the capacity for the SB
		randSB.ensureCapacity(60);
		System.out.println(randSB.capacity());
		
		// length() returns the number of characters in the SB
		System.out.println(randSB.length());
		
		// trimToSize() forces capacity to equal length
		randSB.trimToSize();
		
		// insert() inserts at the index you provide anything
		System.out.println(randSB.insert(1, "nother"));
		
		// toString converts a SB into a String
		String oldSB = randSB.toString();
		
		/* StringBuilders also have the same methods as Strings
		 * charAt(), indexOf(), lastIndexOf(), subString()
		 */
	}
	
}
```

## Lesson 14

```java
// Animal will act as a Super class for other Animals
public class Animal {
	
	private String name = "Animal";
	public String favFood = "Food";
	
	// You use protected when you want to allow subclasses
	// To be able to access methods or fields
	// If you would have used private their would be no
	// way for subclasses to call this method
	// This is a final method which means it can't be overwritten
	
	protected final void changeName(String newName){
		
		// this is a reference to the object you're creating
		
		this.name = newName;
		
	}
	
	protected final String getName(){
		
		return this.name;
		
	}
	
	public void eatStuff(){
		
		System.out.println("Yum " + favFood);
		
	}
	
	public void walkAround(){
		
		System.out.println(this.name + " walks around");
		
	}
	
	public Animal(){
		
	}
	
	public Animal(String name, String favFood){
		
		this.changeName(name);
		this.favFood = favFood;
		
	}
	
}
```

```java
// Cat is a Subclass of Animal
// You create subclasses with the extends keyword
// Now Cat has all the Methods and Fields that Animal defined
// This is known as inheritance because Cat inherits all
// the methods and fields defined in Animal

public class Cat extends Animal{
	
	// You can add new fields to the subclass
	public String favToy = "Yarn";
	
	// You can add new methods
	public void playWith(){
		
		System.out.println("Yeah " + favToy);
		
	}
	
	// Here I overrode the Animal walkAround method
	public void walkAround(){
		
		// this refers to a specific object created of type Cat
		
		System.out.println(this.getName() + " stalks around and then sleeps");
		
	}
	
	public String getToy(){
		
		return this.favToy;
		
	}
	
	public Cat(){
		
	}
	
	public Cat(String name, String favFood, String favToy){
		
		// super calls the constructor for the super class Animal
		
		super(name, favFood);
		
		// We set the favToy value in Cat because it doesn't 
		// exist in the Animal class
		
		this.favToy = favToy;
		
	}
	
}
```

```java
public class LessonFourteen{
	
public static void main(String[] args){
		
		// I create a Animal object named genericAnimal
	
		Animal genericAnimal = new Animal();
		System.out.println(genericAnimal.getName());
		System.out.println(genericAnimal.favFood);
		
	
		// I create a Cat class like any other
		Cat morris = new Cat("Morris", "Tuna", "Rubber Mouse");
		
		// Print out the name, favFood and favToy
		System.out.println(morris.getName());
		System.out.println(morris.favFood);
		System.out.println(morris.favToy);
		
		// You can also create classes based on the super class
		
		Animal tabby = new Cat("Tabby", "Salmon", "Ball");
		
		// You pass objects like any other field
		acceptAnimal(tabby);
		
	}
	
	public static void acceptAnimal(Animal randAnimal){
		
		// Gets the name and favFood for the Animal passed
		System.out.println(randAnimal.getName());
		System.out.println(randAnimal.favFood);
		
		// This is Polymorphism
		// The interpreter automatically figures out what type
		// of Animal it's dealing with and checks to make sure
		// if methods were overwritten that they are called 
		// instead
		randAnimal.walkAround();
		
		// The interpreter won't find anything that doesn't 
		// originally exist in the Animal class however
		// System.out.println(randAnimal.favToy); Throws an ERROR
		
		// If you want access to fields or methods only found
		// in the Cat class you have to cast the object to
		// that specific class first
		Cat tempCat = (Cat) randAnimal;
		
		System.out.println(tempCat.favToy);
		
		// You could also cast the object directly like this
		System.out.println(((Cat) randAnimal).favToy);
		
		// You can use instanceof to check what type of object
		// you have. This results in a positive for Animal 
		// and for Cat
		if (randAnimal instanceof Cat)
		{
			System.out.println(randAnimal.getName() + " is a Cat");
		}
		
	}
	
}
```



## Lesson 15

```java
/* Java doesn't allow you to inherit from more than one 
 * class. So, what do you do when you want do you do
 * when you want to add additional functionality?
 * You create an interface. Interfaces are empty 
 * classes. They provide all of the methods you must
 * use, but none of the code.
 */

// This is how you define an interface. They normally
// have a name that is an adjective. Adjectives modify
// nouns. Most objects have noun names
public interface Drivable {
	
	// You can put fields in an interface, but understand 
	// that their values are final and can't be changed
	double PI = 3.14159265;
	
	// All methods in an interface must be implemented
	// They are public and abstract by default
	// An abstract method must be defined by any class 
	// that uses the interface
	int getWheels();
	
	// You can't define a method as final and abstract
	// final means the method can't be changed and 
	// abstract means it must be changed
	void setWheels(int numWheels);
	
	double getSpeed();
	
	void setSpeed(double speed);
	
	
	
}
```

```java
/* If you want to create a class in which every method
 * doesn't have to be implemented use abstract classes.
 */

// Create an abstract class with the abstract keyword
public abstract class Crashable{
	
	boolean carDrivable = true;
	
	public void youCrashed(){
		this.carDrivable = false;
	}
	
	public abstract void setCarStrength(int carStrength);
	
	public abstract int getCarStrength();
	
}
```

```java
/* You define that you want a class to use an interface
 * with the implements keyword. This class must create
 * a method for each method defined in Drivable
 * You can implement more than 1 interface like this
 * public class Vehicle implements Drivable, Crashable
 */
// You make a class part of an abstract class by using 
//the extends keyword
public class Vehicle extends Crashable implements Drivable {
	
	int numOfWheels = 2;
	double theSpeed = 0;
	
	int carStrength = 0;
	
	// All methods must be as visible as those in the 
	// interface. If they are public in the interface
	// they must be public in the subclass
	public int getWheels(){
		return this.numOfWheels;
	}
	
	public void setWheels(int numWheels){
		this.numOfWheels = numWheels;
	}
	
	public double getSpeed(){
		return this.theSpeed;
	}
	
	public void setSpeed(double speed){
		this.theSpeed = speed;
	}
	
	public Vehicle(int wheels, double speed){
		this.numOfWheels = wheels;
		this.theSpeed = speed;
	}
	
	public void setCarStrength(int carStrength){
		this.carStrength = carStrength;
	}
	
	public int getCarStrength(){
		return this.carStrength;
	}
	
}
```

```java
public class LessonFifteen {
	
	public static void main(String[] args){
		
		Vehicle car = new Vehicle(4, 100.0);
		
		// Using methods from the interface Drivable
		System.out.println("Cars Max Speed: "+car.getSpeed());
		System.out.println("Cars Number of Wheels: "+car.getWheels());
		
		// Using methods from abstract method Crashable
		car.setCarStrength(10);
		System.out.println("Car Strength: "+car.getCarStrength());
		
	}
	
}
```

## Lesson 16

```java
public class LessonSixteen{
	
	public static void main(String[] args){
		
		// Every object inherits all the methods in the Object class
		
		Object superCar = new Vehicle();
		
		// superCar inherits all of the Object methods, but an object
		// of class Object can't access the Vehicle methods
		
		// System.out.println(superCar.getSpeed()); * Throws an error
		
		// You can cast from type Object to Vehicle to access those methods
		
		System.out.println(((Vehicle)superCar).getSpeed());
		
		// The methods of the Object class
		
		Vehicle superTruck = new Vehicle();
		
		// equals tells you if two objects are equal
		System.out.println(superCar.equals(superTruck));
		
		// hashCode returns a unique identifier for an object
		System.out.println(superCar.hashCode());
		
		// finalize is called by the java garbage collector when an object
		// is no longer of use. If you call it there is no guarantee it will
		// do anything though
		
		// getClass returns the class of the object
		
		System.out.println(superCar.getClass());
		
		// THE CLASS OBJECT
		// You can use the Class object method getName to get just the class name
		
		System.out.println(superCar.getClass().getName());
		
		// You can check if 2 objects are of the same class with getClass()
		
		if(superCar.getClass() == superTruck.getClass()){
			System.out.println("They are in the same class");
		}
		
		// getSuperclass returns the super class of the class 
		
		System.out.println(superCar.getClass().getSuperclass());
		
		// the toString method is often overwritten for an object
		
		System.out.println(superCar.toString());
		
		// toString is often used to convert primitives to strings
		
		int randNum = 100;
		System.out.println(Integer.toString(randNum));
		
		// THE CLONE METHOD
		// clone copies the current values of the object and assigns
		// them to another. If changes are made after the clone both
		// objects aren't effected though
		
		superTruck.setWheels(6);
		
		Vehicle superTruck2 = (Vehicle)superTruck.clone();
		
		System.out.println(superTruck.getWheels());
		
		System.out.println(superTruck2.getWheels());
		
		// They are separate objects and don't have equal hashcodes
		System.out.println(superTruck.hashCode());
		System.out.println(superTruck2.hashCode());
		
		// There are subobjects defined in an object clone won't
		// also clone them. You'd have to do that manually, but this
		// topic will be covered in the future because of complexity
		
	}
	
}
```

```java
public class Vehicle extends Crashable implements Drivable, Cloneable{
	
	int numOfWheels = 2;
	double theSpeed = 0;
	
	int carStrength = 0;
	
	public int getWheels(){
		return this.numOfWheels;
	}
	
	public void setWheels(int numWheels){
		this.numOfWheels = numWheels;
	}
	
	public double getSpeed(){
		return this.theSpeed;
	}
	
	public void setSpeed(double speed){
		this.theSpeed = speed;
	}
	
	public Vehicle(){
		
	}
	
	public Vehicle(int wheels, double speed){
		this.numOfWheels = wheels;
		this.theSpeed = speed;
	}
	
	public void setCarStrength(int carStrength){
		this.carStrength = carStrength;
	}
	
	public int getCarStrength(){
		return this.carStrength;
	}
	
	public String toString(){
		return "Num of Wheels: " + this.numOfWheels;
	}
	
	public Object clone(){
		Vehicle car;
		
		try{
			car = (Vehicle) super.clone();
		}
		
		catch(CloneNotSupportedException e){
			return null;
		}
		return car;
	}
	
}
```

## Lesson 17

```java
public class LessonSeventeen{
	
	public static void main(String[] args){
		
		// Create a new Thread that executes the code in GetTime20
		
		Thread getTime = new GetTime20();
		
		// Create a new Thread created using the Runnable interface
		// Execute the code in run after 10 seconds
		
		Runnable getMail = new GetTheMail(10);
		
		Runnable getMailAgain = new GetTheMail(20);
		
		// Call for the code in the method run to execute
		
		getTime.start();
		
		new Thread(getMail).start();
		new Thread(getMailAgain).start();
		
	}
	
}
```

```java
// By using threads you can execute multiple blocks
// of code at the same time. This program will output 
// the current time and then at a specific time execute
// other code without stopping the time output

// Need this for Date and Locale classes
import java.util.*;

// Need this to format the dates
import java.text.DateFormat;

// By extending the Thread class you can run your code
// concurrently with other threads
public class GetTime20 extends Thread{
	
	// All of the code that the thread executes must be 
	// in the run method, or be in a method called for
	// from inside of the run method
	public void run(){
		
		// Creating fields that will contain date info
		Date rightNow;
		Locale currentLocale;
		DateFormat timeFormatter;
		DateFormat dateFormatter;
		String timeOutput;
		String dateOutput;
		
		// Output the current date and time 20 times
		for(int i = 1; i <= 20; i++){
		
			// A Date object contains date and time data
			rightNow = new Date();
			
			// Locale defines time formats depending on location
			currentLocale = new Locale("en", "US");
			
			// DateFormat allows you to define dates / times using predefined
			// styles DEFAULT, SHORT, MEDIUM, LONG, or FULL
			// getTimeInstance only outputs time information
			timeFormatter = DateFormat.getTimeInstance(DateFormat.DEFAULT, currentLocale);
			
			// getDateInstance only outputs time information
			dateFormatter = DateFormat.getDateInstance(DateFormat.DEFAULT, currentLocale);
			
			// Convert the time and date into Strings
			timeOutput = timeFormatter.format(rightNow);
			dateOutput = dateFormatter.format(rightNow);
			
			System.out.println(timeOutput);
			System.out.println(dateOutput);
			System.out.println();
		
			// You must wrap the sleep method in error handling
			// code to catch the InterruptedException exception
			// sleep pauses thread execution for 2 seconds below
			
			try {
				Thread.sleep(2000);
			}
			catch(InterruptedException e)
			{}
		}
		
	}
	
}
```

```java
// You can use the Runnable interface instead of
// wasting your 1 class extension.

public class GetTheMail implements Runnable {
	
	// Stores the number of seconds before the code
	// will be executed
	private int startTime;
	
	// Constructor that sets the wait time for each 
	// new Thread
	public GetTheMail(int startTime){
		this.startTime = startTime;
	}
	
	// All of the code that the thread executes must be 
	// in the run method, or be in a method called for
	// from inside of the run method
	public void run(){
		
		try
		{
			// Don't execute until 10 seconds has passed if 
			// startTime equals 10
			Thread.sleep(startTime * 1000);
		}
		
		catch(InterruptedException e)
		{}
		System.out.println("Checking for Mail");
	}
	
}
```

## Lesson 18

```java
// In the last tutorial I coordinated threads using
// a timing method. Here I show you how to execute code based
// on a predefined time schedule and much more

// Used to schedule when certain events should be triggered
import java.util.concurrent.ScheduledThreadPoolExecutor;

// Used to tell Java what unit of time I want to use
import static java.util.concurrent.TimeUnit.*;

public class LessonEighteen{
	
	public static void main(String[] args){
		
		addThreadsToPool();
		
	}
	
	public static void addThreadsToPool(){
		
		// Allows you to schedule code execution at some time in the future
		// You can also have code execute repetitively based on a time period
		// It must be big enough to hold all potential Threads
				
		ScheduledThreadPoolExecutor eventPool = new ScheduledThreadPoolExecutor(5);
				
		// Adds a Thread to the pool. Tells that thread to start executing
		// after 0 seconds (immediately) and then execute every 2 seconds
				
		eventPool.scheduleAtFixedRate(new CheckSystemTime(), 0, 2, SECONDS);
				
		eventPool.scheduleAtFixedRate(new PerformSystemCheck("Mail"), 5, 5, SECONDS);
				
		eventPool.scheduleAtFixedRate(new PerformSystemCheck("Calendar"), 10,10, SECONDS);
		
		// Thread.activeCount returns the number of threads running
		
		System.out.println("Number of Threads: " +Thread.activeCount());
		
		// Quiz: Why does it say there are 4 threads when we expect 3?
		
		// Create an array of threads with enough spaces for all active threads
		
		Thread[] listOfThreads = new Thread[Thread.activeCount()];
		
		// enumerate fills the Thread array with all active threads
		
		Thread.enumerate(listOfThreads);
		
		// Cycle through all the active threads and print out their names
		
		for(Thread i : listOfThreads){
			System.out.println(i.getName());
		}
		
		// Get priority of all the threads (Priority is equal to the thread 
		// that created the new thread. Top priority is 10, lowest priority is 1
		
		for(Thread i : listOfThreads){
			System.out.println(i.getPriority());
		}
		
		// threadName.setPriority can be used to set the priority 
		
		// This allows the above threads to run for approximately 20 seconds
		
		try{
			Thread.sleep(20000);
		}
		catch(InterruptedException e)
		{}
		
		// Shuts down all threads in the pool
		
		// eventPool.shutdown();
		
	}
	
}
```

```java
import java.text.DateFormat;
import java.util.*;

public class CheckSystemTime implements Runnable{
	
	public void run(){
		
		Date rightNow;
		Locale currentLocale;
		DateFormat timeFormatter;
		String timeOutput;
		
		rightNow = new Date();
		currentLocale = new Locale("en");
		
		timeFormatter = DateFormat.getTimeInstance(DateFormat.DEFAULT, currentLocale);
		timeOutput = timeFormatter.format(rightNow);
		
		System.out.println("Time: " + timeOutput);
		
		
	}
	
}
```

```java
// You could also lock down a method and then unlock it
// when you are finished with it. This library does that

import java.util.concurrent.locks.ReentrantLock;

public class PerformSystemCheck implements Runnable{
	
	private String checkWhat;
	
	// Creates a lock for your method
	
	ReentrantLock lock = new ReentrantLock();
	
	public PerformSystemCheck(String checkWhat){
		
		this.checkWhat = checkWhat;
		
	}
	
	// By putting synchronized before a method, you make
	// sure only one thread at a time can execute it.
	// Synchronizing slows down Java, so it should only
	// be used when necessary.
	
	/* synchronized */ public void run(){
		
		// this locks down the method just like synchronized
		// You can't use synchronized and lock, that's why 
		// synchronized is commented out above
			
		lock.lock();
		
		System.out.println("Checking " + this.checkWhat);
		
		// this unlocks the method just like synchronized
		
		lock.unlock();
		
	}
	
}
```

## Lesson 19

```java
import java.util.regex.*;

public class LessonNineteen{
	
	public static void main(String[] args){
		
		String longString = " Aditya Singh CA 12345 PA (412)555-1212 johnsmith@hotmail.com 412-555-1234 412 555-1234 "; 
		String strangeString = " 1Z aaa **** *** {{{ {{ { ";
		
		/*
		[ ]  Insert characters that are valid
		[^ ]  Insert characters that are not valid
		\\s  Any white space
		\\S  Any non white space
		{n,m}  Whatever proceeds must occur between n and m times
		*/
		
		// Word must contain letters that are 2 to 20 characters in length
		// [A-Za-z]{2,20} 0r \w{2,20}
		
		regexChecker("\\s[A-Za-z]{2,20}\\s", longString);
		
		/*
		\\d  Any digits 0-9
	 	\\D  Anything not a number
	 	{n}  Whatever proceeds must occur n times
	 	*/
		
		// Only 5 digits
		// \\s[0-9]{5}\\s or \\d{5}
		
		regexChecker("\\s\\d{5}\\s", longString);
		
		/*
		|  Is used for OR clause situations
		*/
		
		// Must start with a A or C, followed by 1 letter in brackets
		// Must be a maximum of 2 characters in length
		// A[KLRZ]|C[AOT]
		
		regexChecker("A[KLRZ]|C[AOT]", longString);
		
		/*
		{n,}  Whatever proceeds must occur at least n times
		+  Whatever proceeds must occur one or more times
		. ^ * + ? { } [ ] \ | ( )  Characters that must be escaped or backslashed
		*/
		
		// Grab any string that contains 1 or more !
		
		regexChecker("(\\{{1,})", strangeString);
		regexChecker("(\\{+)", strangeString);
		
		// Get anything that occurs 3 times except newline
		// .  Anything but newline
		
		regexChecker(".{3}", strangeString);
		
		/*
		\\w  Any word type character A-Z, a-z, 0-9, _
		\\W  Any non word character
		*  Occurs zero or more times
		*/
		
		regexChecker("\\w*", strangeString);
		
		regexChecker("[A-Za-z0-9._\\%-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,4}", longString);
		
		
		// ?  0 or 1 of what proceeds it
		
		regexChecker("([0-9]( |-)?)?(\\(?[0-9]{3}\\)?|[0-9]{3})( |-)?([0-9]{3}( |-)?[0-9]{4}|[a-zA-Z0-9]{7})", longString);
		
		regexReplace(longString);
		
	}
	
	public static void regexChecker(String theRegex, String str2Check){
		
		// You define your regular expression (REGEX) using Pattern
		
		Pattern checkRegex = Pattern.compile(theRegex);
		
		// Creates a Matcher object that searches the String for
		// anything that matches the REGEX
		
		Matcher regexMatcher = checkRegex.matcher( str2Check );
		
		// Cycle through the positive matches and print them to screen
		// Make sure string isn't empty and trim off any whitespace
		
		while ( regexMatcher.find() ){
			if (regexMatcher.group().length() != 0){
				System.out.println( regexMatcher.group().trim() );
				
				// You can get the starting and ending indexs
				
				System.out.println( "Start Index: " + regexMatcher.start());
				System.out.println( "Start Index: " + regexMatcher.end());
			}
		}
		
		System.out.println();
	}
	
	public static void regexReplace(String str2Replace){
		
		// REGEX that matches 1 or more white space
		
		Pattern replace = Pattern.compile("\\s+");
		
		// This doesn't really apply, but this is how you ignore case
		// Pattern replace = Pattern.compile("\\s+", Pattern.CASE_INSENSITIVE);
		
		// trim the string t prepare it for a replace
		
		Matcher regexMatcher = replace.matcher(str2Replace.trim());
		
		// replaceAll replaces all white space with commas
		
		System.out.println(regexMatcher.replaceAll(", "));
		
	}
	
}
```

