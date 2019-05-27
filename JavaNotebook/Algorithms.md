## Java Algorithms

```java
public class ArrayStructures {
	
	private int[] theArray = new int[50]; // Creates an array with 50 indexes
	
	private int arraySize = 10; // Elements in theArray
	
	
	// Fills the Array with random values
	
	public void generateRandomArray(){
		
		for(int i = 0; i < arraySize; i++){
			
			// Random number 10 through 19
			
			theArray[i] = (int)(Math.random()*10)+10;
			
		}
		
	}
	
	public int[] getTheArray(){
		
		return theArray;
		
	}
	
	public int getArraySize(){
		
		return arraySize;
		
	}
	
	// Prints the Array on the screen in a grid
	
	public void printArray(){
		
		System.out.println("----------");
		
		for(int i = 0; i < arraySize; i++){
			
			System.out.print("| " + i + " | ");
			
			System.out.println(theArray[i] + " |");
			
			System.out.println("----------");
			
		}
		
	}
	
	// Gets value at provided index
	
	public int getValueAtIndex(int index){
		
		if(index < arraySize) return theArray[index];
		
		return 0;
		
	}
	
	// Returns true or false if a value is in the Array
	
	public boolean doesArrayContainThisValue(int searchValue){
		
		boolean valueInArray = false;
		
		for(int i = 0; i < arraySize; i++){
			
			if(theArray[i] == searchValue){
				
				valueInArray = true;
				
			}
			
		}
		
		return valueInArray;
		
	}
	
	
	// Delete Array row for the index and move elements up
	
	public void deleteIndex(int index){
		
		if(index < arraySize){
			
			// Overwrite the value for the supplied index
			// and then keep overwriting every index that follows
			// until you get to the last index in the array
			
			for(int i = index; i < (arraySize - 1); i++){
				
				theArray[i] = theArray[i+1];
		
			}
			
			arraySize--;
			
		}
		
	}
	
	public void insertValue(int value){
		
		if(arraySize < 50){
			
			theArray[arraySize] = value;
			
			arraySize++;
			
		}
		
	}
	
	// Linear Search : Every index must be looked at
	
	public String linearSearchForValue(int value){
		
		boolean valueInArray = false;
		
		String indexsWithValue = "";
			
		System.out.print("The Value was Found in the Following Indexes: ");
		
		for(int i = 0; i < arraySize; i++){
			
			if(theArray[i] == value) {
				valueInArray = true;
				
				System.out.print(i + " ");
				
				indexsWithValue+= i + " ";
			}
			
		}
		
		if(!valueInArray){
			indexsWithValue = "None";
			
			System.out.print(indexsWithValue);
		}
			
		System.out.println();
		
		return indexsWithValue;
			
	}
	
	// This bubble sort will sort everything from 
	// smallest to largest
	
	public void bubbleSort(){
		
		// i starts at the end of the Array
		// As it is decremented all indexes greater
		// then it are sorted
		
		for(int i = arraySize - 1; i > 1; i--){
			
			// The inner loop starts at the beginning of 
			// the array and compares each value next to each 
			// other. If the value is greater then they are 
			// swapped
			
			for(int j = 0; j < i; j++){
				
				if(theArray[j] > theArray[j + 1]){
					
					swapValues(j, j+1);
					
				}
				
			}
			
		}
		
	}
	
	public static void main(String[] args){
		
		ArrayStructures newArray = new ArrayStructures();
		
		newArray.generateRandomArray();
		
		newArray.printArray();
		
		System.out.println(newArray.getValueAtIndex(3));
		
		System.out.println(newArray.doesArrayContainThisValue(18));
		
		newArray.deleteIndex(4);
		
		newArray.printArray();
		
		newArray.insertValue(55);
		
		newArray.printArray();
		
		newArray.linearSearchForValue(17);
	}

}
```

 The MVC Version of the Above Program

```java
public class ArrayStructure {
	
	private int[] theArray = new int[50]; // Creates an array with 50 indexes
	
	private int arraySize = 10; // Elements in theArray
	
	
	// Fills the Array with random values
	
	public void generateRandomArray(){
		
		for(int i = 0; i < arraySize; i++){
			
			theArray[i] = (int)(Math.random()*9)+10;
			
		}
		
	}
	
	public int[] getTheArray(){
		
		return theArray;
		
	}
	
	public int getArraySize(){
		
		return arraySize;
		
	}
	
	
	
	// Used to slow down calculations
	
	public void pauseAndUpdate(){
		
		try {
			Thread.sleep(700);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
	}
	
	// Prints the Array on the screen in a grid
	
	public void printArray(){
		
		System.out.println("----------");
		
		for(int i = 0; i < arraySize; i++){
			
			System.out.print("| " + i + " | ");
			
			System.out.println(theArray[i] + " |");
			
			System.out.println("----------");
			
		}
		
	}
	
	// Gets value at provided index
	
	public int getValueAtIndex(int index){
		
		if(index < arraySize) return theArray[index];
		
		return 0;
		
	}
	
	// Returns true or false if a value is in the Array
	
	public boolean doesArrayContainThisValue(int searchValue){
		
		boolean valueInArray = false;
		
		for(int i = 0; i < arraySize; i++){
			
			if(theArray[i] == searchValue){
				
				valueInArray = true;
				
			}
			
		}
		
		return valueInArray;
		
	}
	
	
	// Delete Array row for the index and move elements up
	
	public void deleteIndex(int index){
		
		if(index < arraySize){
			
			// Overwrite the value for the supplied index
			// and then keep overwriting every index that follows
			// until you get to the last index in the array
			
			for(int i = index; i < (arraySize - 1); i++){
				
				pauseAndUpdate();
				
				theArray[i] = theArray[i+1];
		
			}
			
			arraySize--;
			
		}
		
	}
	
	public void insertValue(int value){
		
		if(arraySize < 50){
			
			pauseAndUpdate();
			
			theArray[arraySize] = value;
			
			arraySize++;
			
		}
		
	}
	
	// Linear Search : Every index must be looked at
	
	public String linearSearchForValue(int value){
		
		boolean valueInArray = false;
		
		String indexsWithValue = "";
			
		System.out.print("The Value was Found in the Following Indexes: ");
		
		for(int i = 0; i < arraySize; i++){
			
			if(theArray[i] == value) {
				valueInArray = true;
				
				System.out.print(i + " ");
				
				indexsWithValue+= i + " ";
			}
			
		}
		
		if(!valueInArray){
			indexsWithValue = "None";
			
			System.out.print(indexsWithValue);
		}
			
		System.out.println();
		
		return indexsWithValue;
			
	}
	
	// This bubble sort will sort everything from 
	// smallest to largest
	
	public void bubbleSort(){
		
		// i starts at the end of the Array
		// As it is decremented all indexes greater
		// then it are sorted
		
		for(int i = arraySize - 1; i > 1; i--){
			
			// The inner loop starts at the beginning of 
			// the array and compares each value next to each 
			// other. If the value is greater then they are 
			// swapped
			
			for(int j = 0; j < i; j++){
				
				if(theArray[j] > theArray[j + 1]){
					
					swapValues(j, j+1);
					
				}
				
			}
			
		}
		
	}
	
	// This bubble sort will sort everything from 
	// largest to smallest
	
	public void bubbleSortDescending(){
		
		// i starts at the beginning of the array
		
		for(int i = 0; i < arraySize; i++){
			
			// The inner loop starts at the beginning of 
			// the array 1 index in more than i. 
			
			for(int j = 1; j < (arraySize - i); j++){
				
				// Here we check if the 1st index is less
				// than the next during the first run through
				// Then we just increase the indexes until
				// they have all been checked
				
				if(theArray[j-1] < theArray[j]){
					
					swapValues(j-1, j);
					
				}
				
			}
			
		}
		
	}
	
	public void swapValues(int indexOne, int indexTwo){
		
		int temp = theArray[indexOne];
		theArray[indexOne] = theArray[indexTwo];
		theArray[indexTwo] = temp;
		
	}
	
	// The Binary Search is quicker than the linear search
	// because all the values are sorted. Because everything
	// is sorted once you get to a number larger than what
	// you are looking for you can stop the search. Also
	// you be able to start searching from the middle 
	// which speeds the search. It also works best when 
	// there are no duplicates
	
	public void binarySearchForValue(int value){
		
		int lowIndex = 0;
		int highIndex = arraySize - 1;
		
		while(lowIndex <= highIndex){
			
			int middleIndex = (highIndex + lowIndex) / 2;
			
			if(theArray[middleIndex] < value) lowIndex = middleIndex + 1;
			
			else if(theArray[middleIndex] > value) highIndex = middleIndex - 1;
			
			else {
				
				System.out.println("Found a Match for " + value + " at Index " + middleIndex);
				
				lowIndex = highIndex + 1;
				
			}
			
		}
		
	}
	
	public static void main(String[] args){
		
		/*
		
		ArrayStructure newArray = new ArrayStructure();
		
		newArray.generateRandomArray();
		
		newArray.printArray();
		
		System.out.println(newArray.getValueAtIndex(9));
		
		System.out.println(newArray.doesArrayContainThisValue(11));
		
		newArray.deleteIndex(3);
		
		newArray.insertValue(100);
		
		newArray.bubbleSort();
		
		newArray.printArray();
		
		newArray.linearSearchForValue(11);
		
		newArray.binarySearchForValue(12);
		
		newArray.bubbleSortDescending();
		
		newArray.printArray();
		
		*/
		
	}

}
```



## Java Sort Algorithm

```java
public class ArrayStructures {
		
	private int[] theArray = new int[50];
	
	private int arraySize = 10;
	
	public void generateRandomArray(){
		
		for(int i = 0; i < arraySize; i++){
			
			theArray[i] = (int)(Math.random()*10)+10;
			
		}
		
	}
	
	public void printArray(){
		
		System.out.println("----------");
		for(int i = 0; i < arraySize; i++){
			
			System.out.print("| " + i + " | ");
			System.out.println(theArray[i] + " |");
			
			System.out.println("----------");
			
		}
		
	}
	
	public int getValueAtIndex(int index){
		
		if(index < arraySize) return theArray[index];
		
		return 0;
		
	}
	
	public boolean doesArrayContainThisValue(int searchValue){
		
		boolean valueInArray = false;
		
		for(int i = 0; i < arraySize; i++){
			
			if(theArray[i] == searchValue){
				
				valueInArray = true;
				
			}
			
		}
		
		return valueInArray;
		
	}
	
	public void deleteIndex(int index){
		
		if(index < arraySize){
			
			for(int i = index; i < (arraySize - 1); i++){
				
				theArray[i] = theArray[i+1];
				
			}
			
			arraySize--;
			
		}
		
	}
	
	public void insertValue(int value){
		
		if(arraySize < 50){
			
			theArray[arraySize] = value;
			
			arraySize++;
			
		}
		
	}
	
	public String linearSearchForValue(int value){
		
		boolean valueInArray = false;
		
		String indexsWithValue = "";
		
		for(int i = 0; i < arraySize; i++){
			
			if(theArray[i] == value){
				
				valueInArray = true;
				
				indexsWithValue+= i + " ";
				
			}
			
			printHorzArray(i, -1);
			
		}
		
		if(!valueInArray){
			
			indexsWithValue = "None";
			
		}
		
		System.out.print("The Value was Found in the Following: " + indexsWithValue);
		
		System.out.println();
		
		return indexsWithValue;
		
	}
	
public void printHorzArray(int i, int j){
		
		for(int n = 0; n < 51; n++)System.out.print("-");
		
		System.out.println();
		
		for(int n = 0; n < arraySize; n++){
			
			System.out.print("| " + n + "  ");
			
		}
		
		System.out.println("|");
		
		for(int n = 0; n < 51; n++)System.out.print("-");
		
		System.out.println();
		
		for(int n = 0; n < arraySize; n++){
			
			System.out.print("| " + theArray[n] + " ");
			
		}
		
		System.out.println("|");
		
		for(int n = 0; n < 51; n++)System.out.print("-");
		
		System.out.println();
		
		// END OF FIRST PART
		
		
		// ADDED FOR BUBBLE SORT
		
		if(j != -1){
		
			// ADD THE +2 TO FIX SPACING
			
			for(int k = 0; k < ((j*5)+2); k++)System.out.print(" ");
			
			System.out.print(j);
			
		}
		
		
		// THEN ADD THIS CODE
		
		if(i != -1){
			
			// ADD THE -1 TO FIX SPACING
			
			for(int l = 0; l < (5*(i - j)-1); l++)System.out.print(" ");
			
			System.out.print(i);
			
		}
		
		System.out.println();
		
	}
	
	// This bubble sort will sort everything from 
		// smallest to largest
		
		public void bubbleSort(){
			
			// i starts at the end of the Array
			// As it is decremented all indexes greater
			// then it are sorted
			
			for(int i = arraySize - 1; i > 1; i--){
				
				// The inner loop starts at the beginning of 
				// the array and compares each value next to each 
				// other. If the value is greater then they are 
				// swapped
				
				for(int j = 0; j < i; j++){
					
					// To change sort to Descending change to <
					
					if(theArray[j] > theArray[j + 1]){
						
						swapValues(j, j+1);
						
						printHorzArray(i, j);
						
					}
					
				}
				
			}
			
		}
		
		public void swapValues(int indexOne, int indexTwo){
			
			int temp = theArray[indexOne];
			theArray[indexOne] = theArray[indexTwo];
			theArray[indexTwo] = temp;
			
		}
		
		
		// The Binary Search is quicker than the linear search
		// because all the values are sorted. Because everything
		// is sorted once you get to a number larger than what
		// you are looking for you can stop the search. Also
		// you be able to start searching from the middle 
		// which speeds the search. It also works best when 
		// there are no duplicates
		
		public void binarySearchForValue(int value){
			
			int lowIndex = 0;
			int highIndex = arraySize - 1;
			
			while(lowIndex <= highIndex){
				
				int middleIndex = (highIndex + lowIndex) / 2;
				
				if(theArray[middleIndex] < value) lowIndex = middleIndex + 1;
				
				else if(theArray[middleIndex] > value) highIndex = middleIndex - 1;
				
				else {
					
					System.out.println("\nFound a Match for " + value + " at Index " + middleIndex);
					
					lowIndex = highIndex + 1;
					
				}
				
				printHorzArray(middleIndex, -1);
				
			}
			
		}
		
		// Selection sort search for the smallest number in the array
		// saves it in the minimum spot and then repeats searching
		// through the entire array each time
		
		public void selectionSort(){
			
			for(int x=0; x < arraySize; x++){
				  int minimum = x;
				  
				  for(int y=x; y < arraySize; y++){
				  
					  // To change direction of sort just change 
					  // this from > to <
					  
					  if(theArray[minimum]>theArray[y]){
						  minimum = y;
					  }
				  }
				  
				  swapValues(x, minimum);
				  
				  printHorzArray(x, -1);
			}
			
		}
		
		// The Insertion Sort is normally the best of 
		// the elementary sorts. Unlike the other sorts that
		// had a group sorted at any given time, groups are
		// only partially sorted here.
		
		public void insertionSort(){
			
			for (int i = 1; i < arraySize; i++){
				  int j = i;
				  int toInsert = theArray[i];
				  while ((j > 0) && (theArray[j-1] > toInsert)){
					  theArray[j] = theArray[j-1];
					  j--;
					  
					  printHorzArray(i, j);
					  
				  }
				  theArray[j] = toInsert;
				  
				  printHorzArray(i, j);
				  
				  System.out.println("\nArray[i] = " + theArray[i] + " Array[j] = " + theArray[j] + " toInsert = " + toInsert + "\n");
				  
			}
			
		}
	
	public static void main(String[] args){
		
		ArrayStructures newArray = new ArrayStructures();
		
		newArray.generateRandomArray();
		
		newArray.printHorzArray(-1,-1);
		
		// newArray.linearSearchForValue(10);
		
		// newArray.bubbleSort();
		
		// We must Sort first
		
		// newArray.binarySearchForValue(17);
		
		// newArray.selectionSort();
		
		newArray.insertionSort();
		
	}

}
```

## Stacks And Queues

```java
// Arrays, linked lists, trees, etc. are best for
// data that represents real objects.

// Stacks & Queues are instead used to complete a 
// task and are soon after discarded.

// Stacks & Queues
// 1. Allow only a single item to be added or removed at a time
// 2. Stacks allow access to the last item inserted (LIFO)
// 3. Queues allow access to the first item inserted (FIFO)

import java.util.Arrays;

public class TheStack {
	
	private String[] stackArray;
	private int stackSize;
	
	// Sets stack as empty
	
	private int topOfStack = -1;
	
	TheStack(int size){
		
		stackSize = size;
		
		stackArray = new String[size];
		
		// Assigns the value of -1 to every value in the array
		// so I control what gets printed to screen
		
		Arrays.fill(stackArray, "-1");
		
	}

	public void push(String input){
		
		if(topOfStack+1 < stackSize){
			
			topOfStack++;
			
			stackArray[topOfStack] = input;
			
		} else System.out.println("Sorry But the Stack is Full");
		
		displayTheStack();
		
		System.out.println("PUSH " + input + " Was Added to the Stack\n");
		
	}
	
	public String pop(){
		
		if(topOfStack >= 0){
			
			displayTheStack();
			
			System.out.println("POP " + stackArray[topOfStack] + " Was Removed From the Stack\n");
			
			// Just like in memory an item isn't deleted, but instead is just not available
			
			stackArray[topOfStack] = "-1"; // Assigns -1 so the value won't appear
			
			return stackArray[topOfStack--];
	
			
		} else {
			
			displayTheStack();
			
			System.out.println("Sorry But the Stack is Empty");
			
			return "-1";
		}
		
		
	}
	
	public String peek(){
		
		displayTheStack();
		
		System.out.println("PEEK " + stackArray[topOfStack] + " Is at the Top of the Stack\n");
		
		return stackArray[topOfStack];
		
	}
	
	public void pushMany(String multipleValues){
		
		String[] tempString = multipleValues.split(" ");
		
		for(int i = 0; i < tempString.length; i++){
			
			push(tempString[i]);
			
		}
		
	}
	
	public void popAll(){
		
		for(int i = topOfStack; i >= 0; i--){
			
			pop();
			
		}
		
	}
	
	public void popDisplayAll(){
		
		String theReverse = "";
		
		for(int i = topOfStack; i >= 0; i--){
			
			theReverse += stackArray[i];
			
		}
		
		System.out.println("The Reverse: " + theReverse);
		
		popAll();
		
	}
	
	public void displayTheStack(){
		
			for(int n = 0; n < 61; n++)System.out.print("-");
			
			System.out.println();
			
			for(int n = 0; n < stackSize; n++){
				
				System.out.format("| %2s "+ " ", n);
				
			}
			
			System.out.println("|");
			
			for(int n = 0; n < 61; n++)System.out.print("-");
			
			System.out.println();
			
			for(int n = 0; n < stackSize; n++){
				
				
				
				if(stackArray[n].equals("-1")) System.out.print("|     ");
				
				else System.out.print(String.format("| %2s "+ " ", stackArray[n]));
				
			}
			
			System.out.println("|");
			
			for(int n = 0; n < 61; n++)System.out.print("-");
			
			System.out.println();
		
	}
	
	public static void main(String[] args){
		
		TheStack theStack = new TheStack(10);
		
		theStack.push("10");
		theStack.push("17");
		theStack.push("13");
		
		// Look at the top value on the stack
		
		theStack.peek();
		
		// Remove values from the stack (LIFO)
		
		theStack.pop();
		theStack.pop();
		theStack.pop();
		
		// Add many to the stack
		
		theStack.pushMany("R E D R U M");
		
		// Remove all from the stack
		
		// theStack.popAll();
		
		// Remove all from the stack and print them
		
		theStack.popDisplayAll();
		
		theStack.displayTheStack();
		
		
	}
	
}
```

```java
import java.util.Arrays;


public class TheQueue {
	
	private String[] queueArray;
	private int queueSize;
	
	// Sets stack as empty
	
	private int front, numberOfItems, rear = 0;
	
	TheQueue(int size){
		
		queueSize = size;
		
		queueArray = new String[size];
		
		// Assigns the value of -1 to every value in the array
		// so I control what gets printed to screen
				
		Arrays.fill(queueArray, "-1");
		
	}
	
	public void insert(String input){
		
		if(numberOfItems + 1 <= queueSize){
		
			queueArray[rear] = input;
			
			rear++;
		
			numberOfItems++;
			
			System.out.println("INSERT " + input + " Was Added to the Stack\n");
		
		} else {
			
			System.out.println("Sorry But the Queue is Full");
			
		}
		
	}
	
	// This priority insert will add items in order from high to low
	
	public void priorityInsert(String input){
		
		int i;
		
		if(numberOfItems == 0){
			
			insert(input);
			
		} else {
			
			for(i = numberOfItems-1; i >= 0; i--){
				
				if(Integer.parseInt(input) > Integer.parseInt(queueArray[i])){
					
					queueArray[i+1] = queueArray[i];
					
				} else break; // Done shifting items in queue
				
			}
			
			queueArray[i+1] = input;
			
			rear++;
			
			numberOfItems++;
			
		}
		
	}
	
	public void remove(){
		
		if(numberOfItems > 0){
			
			System.out.println("REMOVE " + queueArray[front] + " Was Removed From the Queue\n");
			
			// Just like in memory an item isn't deleted, but instead is just not available
			
			queueArray[front] = "-1";
			
			front++;
		
			numberOfItems--;
		
		} else {
			
			System.out.println("Sorry But the Queue is Empty");
			
			
		}
		
	}
	
	public void peek(){
		
		System.out.println("The First Element is " + queueArray[front]);
		
	}
	
	public void displayTheQueue(){
		
		for(int n = 0; n < 61; n++)System.out.print("-");
		
		System.out.println();
		
		for(int n = 0; n < queueSize; n++){
			
			System.out.format("| %2s "+ " ", n);
			
		}
		
		System.out.println("|");
		
		for(int n = 0; n < 61; n++)System.out.print("-");
		
		System.out.println();
		
		for(int n = 0; n < queueSize; n++){
			
			
			if(queueArray[n].equals("-1")) System.out.print("|     ");
			
			else System.out.print(String.format("| %2s "+ " ", queueArray[n]));
			
		}
		
		System.out.println("|");
		
		for(int n = 0; n < 61; n++)System.out.print("-");
		
		System.out.println();
		
		// Number of spaces to put before the F
		
		int spacesBeforeFront = 3*(2*(front+1)-1);
		
		for(int k = 1; k < spacesBeforeFront; k++)System.out.print(" ");
		
		System.out.print("F");
		
		// Number of spaces to put before the R
		
		int spacesBeforeRear = (2*(3*rear)-1) - (spacesBeforeFront);
		
		for(int l = 0; l < spacesBeforeRear; l++)System.out.print(" ");
		
		System.out.print("R");
		
		System.out.println("\n");
	
}
	
	public static void main(String[] args){
		
		TheQueue theQueue = new TheQueue(10);
		
		theQueue.priorityInsert("16");
		
		theQueue.priorityInsert("25");
		
		theQueue.priorityInsert("10");
		
		/*
		theQueue.insert("10");
		
		theQueue.displayTheQueue();
		
		theQueue.insert("15");
		
		theQueue.displayTheQueue();
		
		theQueue.insert("25");
		
		theQueue.displayTheQueue();
		
		theQueue.insert("25");
		
		theQueue.displayTheQueue();
		
		theQueue.insert("25");
		*/
		
		theQueue.displayTheQueue();
		
		theQueue.remove();
		
		theQueue.displayTheQueue();
		
		theQueue.remove();
		
		theQueue.displayTheQueue();
		
		theQueue.peek();
		
	}

}
```



## Linked List In Java

```java
public class Link {

	// Set to public so getters & setters aren't needed
	
	public String bookName;
	public int millionsSold;
	
	// Reference to next link made in the LinkList
	// Holds the reference to the Link that was created before it
	// Set to null until it is connected to other links
	
	public Link next; 
	
	public Link(String bookName, int millionsSold){
		
		this.bookName = bookName;
		this.millionsSold = millionsSold;
		
	}
	
	public void display(){
		
		System.out.println(bookName + ": " + millionsSold + ",000,000 Sold");
		
	}
	
	public String toString(){
		
		return bookName;
		
	}
	
	public static void main(String[] args) {
		
		LinkList theLinkedList = new LinkList();
		
		// Insert Link and add a reference to the book Link added just prior
		// to the field next
		
		theLinkedList.insertFirstLink("Don Quixote", 500);
		theLinkedList.insertFirstLink("A Tale of Two Cities", 200);
		theLinkedList.insertFirstLink("The Lord of the Rings", 150);
		theLinkedList.insertFirstLink("Harry Potter and the Sorcerer's Stone", 107);
		
		theLinkedList.display();
		
		System.out.println("Value of first in LinkedList " + theLinkedList.firstLink + "\n");
		
		// Removes the last Link entered
		
		theLinkedList.removeFirst();
		
		theLinkedList.display();
		
		System.out.println(theLinkedList.find("The Lord of the Rings").bookName + " Was Found");
		
		theLinkedList.removeLink("A Tale of Two Cities");
		
		System.out.println("\nA Tale of Two Cities Removed\n");
		
		theLinkedList.display();
		
	}
	
}
```

```java
class LinkList{
	
	// Reference to first Link in list
	// The last Link added to the LinkedList
	
	public Link firstLink; 
	
	LinkList(){
		
		// Here to show the first Link always starts as null
		
		firstLink = null;
		
	}
	
	// Returns true if LinkList is empty
	
	public boolean isEmpty(){
		
		return(firstLink == null);
		
	}
	
	public void insertFirstLink(String bookName, int millionsSold){
		
		Link newLink = new Link(bookName, millionsSold);
		
		// Connects the firstLink field to the new Link 
		
		newLink.next = firstLink;
		
		firstLink = newLink;
		
	}
	
	public Link removeFirst(){
		
		Link linkReference = firstLink;
		
		if(!isEmpty()){
		
			// Removes the Link from the List
		
			firstLink = firstLink.next;
		
		} else {
			
			System.out.println("Empty LinkedList");
			
		}
		
		return linkReference;
		
	}
	
	public void display(){
		
		Link theLink = firstLink;
		
		// Start at the reference stored in firstLink and
		// keep getting the references stored in next for
		// every Link until next returns null
		
		while(theLink != null){
			
			theLink.display();
			
			System.out.println("Next Link: " + theLink.next);
			
			theLink = theLink.next;
			
			System.out.println();
			
		}
		
	}
	
	public Link find(String bookName){
		
		Link theLink = firstLink;
		
		if(!isEmpty()){
		
			while(theLink.bookName != bookName){
			
				// Checks if at the end of the LinkedList
			
				if(theLink.next == null){
				
					// Got to the end of the Links in LinkedList
					// without finding a match
				
					return null;
				
				} else {
				
					// Found a matching Link in the LinkedList
				
					theLink = theLink.next;
				
				}
			
			}
			
		} else {
			
			System.out.println("Empty LinkedList");
			
		}
		
		return theLink;
		
	}
	
	public Link removeLink(String bookName){
		
		Link currentLink = firstLink;
		Link previousLink = firstLink;
		
		// Keep searching as long as a match isn't made
		
		while(currentLink.bookName != bookName){
			
			// Check if at the last Link in the LinkedList
			
			if(currentLink.next == null){
				
				// bookName not found so leave the method
				
				return null; 
				
			} else {
				
				// We checked here so let's look in the
				// next Link on the list
				
				previousLink = currentLink; 
				
				currentLink = currentLink.next;
				
			}
			
		}
		
		if(currentLink == firstLink){
			
			// If you are here that means there was a match
			// in the reference stored in firstLink in the
			// LinkedList so just assign next to firstLink
			
			firstLink = firstLink.next;
			
		} else {
			
			// If you are here there was a match in a Link other 
			// than the firstLink. Assign the value of next for
			// the Link you want to delete to the Link that's 
			// next previously pointed to the reference to remove
			
			System.out.println("FOUND A MATCH");
			System.out.println("currentLink: " + currentLink);
			System.out.println("firstLink: " + firstLink);
			
			previousLink.next = currentLink.next;
			
		}
		
		return currentLink;
		
	}
	
}
```

## Linked List In java 2

```java
// A Double Ended LinkedList has a reference to 
// the first and last Link in the List

public class DoubleEndedLinkedList {
	
	Neighbor firstLink;
	Neighbor lastLink;
	
	public void insertInFirstPosition(String homeOwnerName, int houseNumber){
		
		Neighbor theNewLink = new Neighbor(homeOwnerName, houseNumber);
		
		// If no items in the list add the new Link
		// to lastLink in the LinkedList
		
		if(isEmpty()){
			
			lastLink = theNewLink;
			
		} /* FOR DOUBLY LINKED LIST */ else {
			
			firstLink.previous = theNewLink;
			
		} // END OF DOUBLY LINKED LIST ADDITION
		
		// DOUBLY LINKED LIST
		// Just like you can go forward in the list with next
		// with a doubly linked list you can go backwards
		// because it also has a previous as well as a next
			
		// Assign the reference to the previous 
		// firstLink and assign the new Link
		// to firstLink in LinkedList
			 
		theNewLink.next = firstLink;
			
		firstLink = theNewLink;
		
	}
	
	public void insertInLastPosition(String homeOwnerName, int houseNumber){
		
		Neighbor theNewLink = new Neighbor(homeOwnerName, houseNumber);
		
		// If empty put the new Neighbor in first position
		
		if(isEmpty()){
			
			firstLink = theNewLink;
			
		} else {
			
			// Assign the last Neighbors next to the new Neighbor
			
			lastLink.next = theNewLink;
			
			theNewLink.previous = lastLink; // FOR DOUBLY LINKED LIST
			
		}
			
		lastLink = theNewLink;
		
	}
	
	// DOUBLY LINKED LIST ADDITION
	// Insert after the provided key
	
	public boolean insertAfterKey(String homeOwnerName, int houseNumber, int key){
		
		Neighbor theNewLink = new Neighbor(homeOwnerName, houseNumber);
		
		Neighbor currentNeighbor = firstLink; // Starts search at first link
		
		// while the current houseNumber isn't the key keep looking
		
		while(currentNeighbor.houseNumber != key){
			
			currentNeighbor = currentNeighbor.next; // Switch to the next Neighbor
			
			// If we get to the last Neighbor without a match leave the method
			
			if(currentNeighbor == null){
				
				return false;
				
			}
			
		}
		
		// If we make it here we have a match for the key
		
		// If the match was for the last Neighbor in the list
		
		if(currentNeighbor == lastLink){
			
			// Assign the new Neighbor as the last link
			
			theNewLink.next = null;
			lastLink = theNewLink;
			
		} else {
			
			// It didn't match for the last link
			// So take next from the Neighbor that was 
			// here previously and assign theNewLink to
			// the previous Neighbor
			
			theNewLink.next = currentNeighbor.next;
			currentNeighbor.next.previous = theNewLink;
			
		}
		
		theNewLink.previous = currentNeighbor;
		currentNeighbor.next = theNewLink;
		return true;
		
		
	}
	
	public static void main(String[] args) {
		
		DoubleEndedLinkedList theLinkedList = new DoubleEndedLinkedList();
		
		
		theLinkedList.insertInFirstPosition("Mark Evans", 7);
		theLinkedList.insertInFirstPosition("Piers Polkiss", 9);
		theLinkedList.insertInFirstPosition("Doreen Figg", 6);
		theLinkedList.insertInLastPosition("Petunia Dursley", 4);
		
		
		/*
		theLinkedList.insertInOrder("Mark Evans", 7);
		theLinkedList.insertInOrder("Piers Polkiss", 9);
		theLinkedList.insertInOrder("Doreen Figg", 6);
		theLinkedList.insertInOrder("Petunia Dursley", 4);
		*/
		
		theLinkedList.display();
		
		theLinkedList.insertAfterKey("Aditya Singh", 2, 6);
		
		theLinkedList.display();
		
		System.out.println("\n");
		
		// Send the LinkedList to the iterator
		
		NeighborIterator neighbors = new NeighborIterator(theLinkedList);
		
		// Get the first neighbor and display
		
		neighbors.currentNeighbor.display();
		
		// Is there another?
		
		System.out.println(neighbors.hasNext());
		
		// Switch to the next Neighbor
		
		neighbors.next();
		
		neighbors.currentNeighbor.display();
		
		neighbors.remove();
		
		neighbors.currentNeighbor.display();
		
	}
	
	// Returns true if LinkList is empty
	
	public boolean isEmpty(){
				
		return(firstLink == null);
				
	}
	
	// Inserts Neighbors in order based on house number
	
	public void insertInOrder(String homeOwnerName, int houseNumber){
		
		Neighbor theNewLink = new Neighbor(homeOwnerName, houseNumber);
		
		// Holds he last Neighbor searched so we can change 
		// its value for next if we input a new Neighbor
		
		Neighbor previousNeighbor = null;
		
		Neighbor currentNeighbor = firstLink;
		
		// While there are still Neighbors and the new houseNumber
		// is greater than the current focused houseNumber
		// Change the > to < for opposite sort
		
		while((currentNeighbor != null) && (houseNumber > currentNeighbor.houseNumber)){
			
			previousNeighbor = currentNeighbor;
			currentNeighbor = currentNeighbor.next; // Get the next Neighbor
			
		}
		
		// We are still at the beginning of the list
		
		if(previousNeighbor == null){
			
			// Save new Neighbor in the first position
			
			firstLink = theNewLink; 
			
		} else {
			
			// Assign the new Neighbor as the value for next
			
			previousNeighbor.next = theNewLink;
			
		}
		
		// Assign the value of next to the next Neighbor
		
		theNewLink.next = currentNeighbor;
		
	}
			
			
			
		
	public void display(){
			
		Neighbor theLink = firstLink;
			
		while(theLink != null){
				
			theLink.display();
				
			System.out.println("Next Link: " + theLink.next);
				
			theLink = theLink.next;
				
			System.out.println();
				
		}
			
	}	

}

class Neighbor {
	
	public String homeOwnerName;
	public int houseNumber;
	
	public Neighbor next; 
	
	public Neighbor previous; // Used with Doubly Linked List
	
	public Neighbor(String homeOwnerName, int houseNumber){
		
		this.homeOwnerName = homeOwnerName;
		this.houseNumber = houseNumber;
		
	}
	
	public void display(){
		
		System.out.println(homeOwnerName + ": " + houseNumber + " Privet Drive");
		
	}
	
	public String toString(){
		
		return homeOwnerName;
		
	}
	
}

// An iterator provides an easy way to cycle through all
// the objects in a LinkedList

class NeighborIterator{
	
	Neighbor currentNeighbor; // The current focus Neighbor
	Neighbor previousNeighbor; // The previous Neighbor
	
	DoubleEndedLinkedList theNeighbors;
	
	// hasNext, next, remove are common iterator methods
	
	NeighborIterator(DoubleEndedLinkedList theNeighbors){
		
		this.theNeighbors = theNeighbors;
		
		currentNeighbor = theNeighbors.firstLink;
		previousNeighbor = theNeighbors.lastLink;
		
	}
	
	public boolean hasNext(){
		
		if(currentNeighbor.next != null){
			
			return true;
			
		}
		
		return false;
		
	}
	
	public Neighbor next(){
		
		if(hasNext()){
			
			previousNeighbor = currentNeighbor;
			currentNeighbor = currentNeighbor.next;
			
			return currentNeighbor;
			
		}
		
		return null;
		
	}
	
	public void remove(){
		
		// If at the beginning of the list
		
		if(previousNeighbor == null){
			
			theNeighbors.firstLink = currentNeighbor.next;
			
		} else {
			
			previousNeighbor.next = currentNeighbor.next;
			
			// If at end of list
			
			if(currentNeighbor.next == null){
				
				// Assign first link as the current link
				
				currentNeighbor = theNeighbors.firstLink;
				previousNeighbor = null;
				
			} else {
				
				currentNeighbor = currentNeighbor.next;
				
			}
			
		}
		
	}
	
}
```

## Java Recursion

```java
public class Recursion {
	
	public static void main(String[] args) {
		
		Recursion recursionTool = new Recursion();
			
		// Demonstrate what a triangular number is
		// Triangular numbers can be visualized as triangles
		// Equals itself plus every number before it to 1
		// TN of 5 = 5+4+3+2+1
		
		recursionTool.calculateSquaresToPrint(10);
		
		System.out.println("\nTriangular Number: " + recursionTool.getTriangularNum(3) + "\n");
		
		System.out.println("GET TRIANGULAR NUMBER");
		
		System.out.println("Recursion Triangular Number: " + recursionTool.getTriangularNumR(6));
		
		System.out.println("\nGET FACTORIAL");
		
		System.out.println("Factorial: " + recursionTool.getFactorial(3));
		
	}
	
	// Calculate triangular number not using recursion
	
	public int getTriangularNum(int number){
		
		int triangularNumber = 0;

		while(number > 0){
			
			triangularNumber = triangularNumber + number;
			number--;
			
		}
		
		// If number equals 3, you find TN by adding 3+2+1 = 6
		
		return triangularNumber;
		
	}
	
	// Calculate triangular number using recursion
	
	public int getTriangularNumR(int number){
		
		// Every recursive method must have a condition that
		// leads to the method no longer making another method
		// call on itself. This is known as the base case
		
		System.out.println("Method " + number);
		
		if(number == 1){
			
			System.out.println("Returned 1");
			
			return 1;
			
		} else {
			
			int result = number + getTriangularNumR(number - 1);
			
			System.out.print("Return " + result);
			
			System.out.println(" : " + number + " + getFactorial(" + number + " - 1)");
			
			return result;
			
		}
		
	}
	
	// Returns the factorial of a number
	// factorial(3) = 3 * 2 * 1
	
	public int getFactorial(int number){
		
		System.out.println("Method " + number);
		
		if(number == 1){
			
			System.out.println("Returned 1");
			
			return 1;
			
		} else {
			
			int result = number * getFactorial(number - 1);
			
			System.out.print("Return " + result);
			
			System.out.println(" : " + number + " * getFactorial(" + number + " - 1)");
			
			return result;
			
		}
		
	}
	
	
	// USED TO DEMONSTRATE TRIANGULAR NUMBERS --------------------
	
	// Draws the number of squares that are passed in horizontally 
	
		public void drawSquares(int howManySquares){
			
			for(int i = 0; i < howManySquares; i++) System.out.print(" --  ");
			
			System.out.println();
				
			for(int i = 0; i < howManySquares; i++) System.out.print("|" + howManySquares + " | ");
			
			System.out.println();
				
			for(int i = 0; i < howManySquares; i++) System.out.print(" --  ");
				
			System.out.println("\n");
			
		}
		
		// Outputs the number of squares to print to represent a triangle
		
		public void calculateSquaresToPrint(int number){
			
			for(int i = 1; i <= number; i++){
				
				for(int j = 1; j < i; j++){
				
					drawSquares(j);
				
				
				}
				
				System.out.println("Triangular Number: " + calcTriangularNum(i));
				
			}
			
		}
		
		public double calcTriangularNum(int number){
			
			return .5 * number * (1 + number);
			
		}

}
```

```java
import java.util.Arrays;

public class MergeSort {
	public static void main(String a[]) {

		int array[] = { 10, 8, 4, 80, 13, 1, 3, 11 };

		System.out.println("STARTING ARRAY\n");

		printHorzArray(-1, -1, array, 49);

		System.out.println();

		// Send the array, 0 and the array size

		mergeSort_srt(array, 0, array.length - 1);

		System.out.print("FINAL SORTED ARRAY\n");

		printHorzArray(-1, -1, array, 49);

	}

	// Receives the array, 0 and the array size

	public static void mergeSort_srt(int array[], int lo, int n) {
		int low = lo;
		int high = n;

		if (low >= high) {
			return;
		}

		// Find the middle index of the array

		int middle = (low + high) / 2;

		// CREATE 2 ARRAYS FROM THE ONE

		// Send the array, 0 and the middle index of the array

		mergeSort_srt(array, low, middle);

		// Send the array, the middle index + 1 and the highest
		// index of the array

		mergeSort_srt(array, middle + 1, high);

		// Store the last index of the first array

		int end_low = middle;

		// Store the first index of the second array

		int start_high = middle + 1;

		// If the lowest index is less than or equal to the bottom arrays
		// highest index & the lowest index of the 2nd array is less than
		// or equal to its highest index

		while ((lo <= end_low) && (start_high <= high)) {

			System.out.println("\nBOTTOM ARRAY");

			printSmallArray(array, lo, middle);

			System.out.println("\nTOP ARRAY");

			printSmallArray(array, start_high, high);

			printHorzArray(-1, -1, array, 49);

			// If the value in the 1st index of the 1st array is less
			// than the value in the 1st index of the 2nd array

			System.out.println("Is " + array[low] + " < " + array[start_high]
					+ "? " + (array[low] < array[start_high]));

			if (array[low] < array[start_high]) {

				// Increment to the next index in the 1st array

				low++;
			} else {

				// Store the value in the 1st index of the 2nd array

				int Temp = array[start_high];

				System.out.println("Temp: " + Temp);

				// Decrement backwards through the first array starting
				// at the last index in the first array

				for (int k = start_high - 1; k >= low; k--) {

					System.out.println("array[" + k + "] = " + array[k]
							+ " Stored in array index " + (k + 1));

					array[k + 1] = array[k];
				}

				System.out.println(Temp + " is stored in index " + low);

				printHorzArray(-1, -1, array, 49);

				array[low] = Temp;
				low++;
				end_low++;
				start_high++;
			}
		}

		printHorzArray(-1, -1, array, 49);

	}

	// Used to print out the smaller arrays

	static void printSmallArray(int theArray[], int lo, int high) {

		int[] tempArray = Arrays.copyOfRange(theArray, lo, high);

		int tempArrayDashes = tempArray.length * 6;

		System.out.println("Array Index Start " + lo + " and End " + high);

		printHorzArray(-1, -1, tempArray, tempArrayDashes);

	}

	static void printHorzArray(int i, int j, int theArray[], int numDashes) {

		for (int n = 0; n < numDashes; n++)
			System.out.print("-");

		System.out.println();

		for (int n = 0; n < theArray.length; n++) {

			System.out.format("| %2s " + " ", n);

		}

		System.out.println("|");

		for (int n = 0; n < numDashes; n++)
			System.out.print("-");

		System.out.println();

		for (int n = 0; n < theArray.length; n++) {

			System.out.print(String.format("| %2s " + " ", theArray[n]));

		}

		System.out.println("|");

		for (int n = 0; n < numDashes; n++)
			System.out.print("-");

		System.out.println();

	}
}
```

## Shell Sort

```java
import java.util.Arrays;

public class ShellSort {

	public void sort() {

		int inner, outer, temp;

		int interval = 1;
		while (interval <= arraySize / 3){

			// Define an interval sequence

			interval = interval * 3 + 1;

		// Keep looping until the interval is 1
		// Then this becomes an insertion sort

		while (interval > 0) {

			// Continue incrementing outer until the end of the array is reached

			for (outer = interval; outer < arraySize; outer++) {

				// Store the value of the array in temp unless it has to be
				// copied to a space occupied by a bigger number closer to the
				// beginning of the array

				temp = theArray[outer];

				System.out.println("Copy " + theArray[outer] + " into temp");

				// inner is assigned the value of the highest index to check
				// against all values the proceed it. Along the way if a
				// number is greater than temp it will be moved up in the array

				inner = outer;

				System.out.println("Checking if " + theArray[inner - interval]
						+ " in index " + (inner - interval)
						+ " is bigger than " + temp);

				// While there is a number bigger than temp move it further
				// up in the array

				while (inner > interval - 1
						&& theArray[inner - interval] >= temp) {

					System.out.println("In While Checking if "
							+ theArray[inner - interval] + " in index "
							+ (inner - interval) + " is bigger than " + temp);

					printHorzArray(inner, outer, interval);

					// Make room for the smaller temp by moving values in the
					// array
					// up one space if they are greater than temp

					theArray[inner] = theArray[inner - interval];

					System.out.println(theArray[inner - interval]
							+ " moved to index " + inner);

					inner -= interval;

					System.out.println("inner= " + inner);

					printHorzArray(inner, outer, interval);

					System.out.println("outer= " + outer);
					System.out.println("temp= " + temp);
					System.out.println("interval= " + interval);

				}

				// Now that everything has been moved into place put the value
				// stored in temp into the index above the first value smaller
				// than it is

				theArray[inner] = temp;

				System.out.println(temp + " moved to index " + inner);

				printHorzArray(inner, outer, interval);

			}

			// Once we get here we have interval sorted our array
			// so we decrement interval and go again

			interval = (interval - 1) / 3;
		}

	}

	public static void main(String[] args) {

		ShellSort theSort = new ShellSort(10);

		System.out.println(Arrays.toString(theSort.theArray));

		theSort.sort();

		System.out.println(Arrays.toString(theSort.theArray));

	}

	private int[] theArray;

	private int arraySize;

	ShellSort(int arraySize) {

		this.arraySize = arraySize;

		theArray = new int[arraySize];

		generateRandomArray();

	}

	public void generateRandomArray() {

		for (int i = 0; i < arraySize; i++) {

			// Generate a random array with values between
			// 10 and 59

			theArray[i] = (int) (Math.random() * 50) + 10;

		}

	}

	public void printHorzArray(int i, int j, int h) {

		if (i == j)
			i = i - h;

		for (int n = 0; n < 51; n++)
			System.out.print("-");

		System.out.println();

		for (int n = 0; n < arraySize; n++) {

			System.out.print("| " + n + "  ");

		}

		System.out.println("|");

		for (int n = 0; n < 51; n++)
			System.out.print("-");

		System.out.println();

		for (int n = 0; n < arraySize; n++) {

			System.out.print("| " + theArray[n] + " ");

		}

		System.out.println("|");

		for (int n = 0; n < 51; n++)
			System.out.print("-");

		System.out.println();

		if (i != -1) {

			// Number of spaces to put before the F

			int spacesBeforeFront = 5 * i + 1;

			for (int k = 0; k < spacesBeforeFront; k++)
				System.out.print(" ");

			System.out.print("I");

			// Number of spaces to put before the R

			int spacesBeforeRear = (5 * j + 1 - 1) - spacesBeforeFront;

			for (int l = 0; l < spacesBeforeRear; l++)
				System.out.print(" ");

			System.out.print("O");

			System.out.println("\n");

		}

	}

}
```

## QuickSort

```java
import java.util.Arrays;

// When we partition data we are dividing it into
// two parts. All items with data above a defined value
// will go in one part and the rest will go in the other

// The value that defines in which group data will go
// is known as the pivot value

public class Partitioning {

	private static int[] theArray;

	private static int arraySize;

	public static void main(String[] args) {

		Partitioning partitionArray = new Partitioning(10);

		partitionArray.generateRandomArray();

		System.out.println(Arrays.toString(Partitioning.theArray));

		// Every item smaller than 35 will be on the left and
		// everything bigger will be on the right

		partitionArray.partitionArray(35);

		System.out.println(Arrays.toString(Partitioning.theArray));

	}

	public void partitionArray(int pivot) {

		// If leftPointer finds an item that is greater
		// than pivot it stops and waits for the rightPointer
		// to find a value less than pivot. Then the items
		// are switched

		// Starts at the left side of array before index 0

		int leftPointer = -1;

		// Starts at the right side of the array after the last index

		int rightPointer = arraySize;

		while (true) {

			// Cycle through array until the end is reached
			// or an item bigger than pivot is found. Then
			// wait for rightPointer to finish cycling

			while (leftPointer < (arraySize - 1)
					&& theArray[++leftPointer] < pivot)
				;

			printHorzArray(leftPointer, rightPointer);

			System.out.println(theArray[leftPointer] + " in index "
					+ leftPointer + " is bigger than the pivot value " + pivot);

			// Cycle through array until the beginning is reached
			// or an item smaller than pivot is found.

			while (rightPointer > 0 && theArray[--rightPointer] > pivot)
				;

			printHorzArray(leftPointer, rightPointer);

			System.out.println(theArray[rightPointer] + " in index "
					+ rightPointer + " is smaller than the pivot value "
					+ pivot);

			printHorzArray(leftPointer, rightPointer);

			// When the 2 pointers meet at the middle break
			// out of the while loop

			if (leftPointer >= rightPointer)
				break;

			else {

				// Swap the values in the pointers

				swapValues(leftPointer, rightPointer);

				System.out.println(theArray[leftPointer] + " was swapped for "
						+ theArray[rightPointer]);

			}

		}

	}

	public void swapValues(int indexOne, int indexTwo) {

		int temp = theArray[indexOne];
		theArray[indexOne] = theArray[indexTwo];
		theArray[indexTwo] = temp;

	}

	Partitioning(int newArraySize) {

		arraySize = newArraySize;

		theArray = new int[arraySize];

		generateRandomArray();

	}

	public void generateRandomArray() {

		for (int i = 0; i < arraySize; i++) {

			// Generate a random array with values between
			// 10 and 59

			theArray[i] = (int) (Math.random() * 50) + 10;

		}

	}

	static void printHorzArray(int i, int j) {

		for (int n = 0; n < 61; n++)
			System.out.print("-");

		System.out.println();

		for (int n = 0; n < arraySize; n++) {

			System.out.format("| %2s " + " ", n);

		}

		System.out.println("|");

		for (int n = 0; n < 61; n++)
			System.out.print("-");

		System.out.println();

		for (int n = 0; n < arraySize; n++) {

			System.out.print(String.format("| %2s " + " ", theArray[n]));

		}

		System.out.println("|");

		for (int n = 0; n < 61; n++)
			System.out.print("-");

		System.out.println();

		if (i != -1) {

			// Number of spaces to put before the F

			int spacesBeforeFront = 5 * i + 1;

			for (int k = 0; k < spacesBeforeFront; k++)
				System.out.print(" ");

			System.out.print("L");

			// Number of spaces to put before the R

			int spacesBeforeRear = (5 * j + 1 - 1) - spacesBeforeFront;

			for (int l = 0; l < spacesBeforeRear; l++)
				System.out.print(" ");

			System.out.print("H");

			System.out.println("\n");

		}

	}

}
```

```java
import java.util.Arrays;

// The Quick Sort is normally the fastest sorting algorithm

public class QuickSort {

	private static int[] theArray;

	private static int arraySize;

	public static void main(String[] args) {

		QuickSort theSort = new QuickSort(10);

		theSort.generateRandomArray();

		System.out.println(Arrays.toString(QuickSort.theArray));

		theSort.quickSort(0, 9);

		System.out.println(Arrays.toString(QuickSort.theArray));

	}

	QuickSort(int newArraySize) {

		arraySize = newArraySize;

		theArray = new int[arraySize];

		generateRandomArray();

	}

	public void quickSort(int left, int right) {

		if (right - left <= 0)
			return; // Everything is sorted

		else {

			// It doesn't matter what the pivot is, but it must
			// be a value in the array

			int pivot = theArray[right];

			System.out.println("Value in right " + theArray[right]
					+ " is made the pivot");

			System.out.println("left = " + left + " right= " + right
					+ " pivot= " + pivot + " sent to be partitioned");

			int pivotLocation = partitionArray(left, right, pivot);

			System.out.println("Value in left " + theArray[left]
					+ " is made the pivot");

			quickSort(left, pivotLocation - 1); // Sorts the left side

			quickSort(pivotLocation + 1, right);

		}

	}

	public int partitionArray(int left, int right, int pivot) {

		int leftPointer = left - 1;

		int rightPointer = right;

		while (true) {

			while (theArray[++leftPointer] < pivot)
				;

			printHorzArray(leftPointer, rightPointer);

			System.out.println(theArray[leftPointer] + " in index "
					+ leftPointer + " is bigger than the pivot value " + pivot);

			while (rightPointer > 0 && theArray[--rightPointer] > pivot)
				;

			printHorzArray(leftPointer, rightPointer);

			System.out.println(theArray[rightPointer] + " in index "
					+ rightPointer + " is smaller than the pivot value "
					+ pivot);

			printHorzArray(leftPointer, rightPointer);

			if (leftPointer >= rightPointer) {

				System.out.println("left is >= right so start again");

				break;

			}

			else {

				swapValues(leftPointer, rightPointer);

				System.out.println(theArray[leftPointer] + " was swapped for "
						+ theArray[rightPointer]);

			}

		}

		swapValues(leftPointer, right);

		return leftPointer;

	}

	public void swapValues(int indexOne, int indexTwo) {

		int temp = theArray[indexOne];
		theArray[indexOne] = theArray[indexTwo];
		theArray[indexTwo] = temp;

	}

	public void generateRandomArray() {

		for (int i = 0; i < arraySize; i++) {

			// Generate a random array with values between
			// 10 and 59

			theArray[i] = (int) (Math.random() * 50) + 10;

		}

	}

	static void printHorzArray(int i, int j) {

		for (int n = 0; n < 61; n++)
			System.out.print("-");

		System.out.println();

		for (int n = 0; n < arraySize; n++) {

			System.out.format("| %2s " + " ", n);

		}

		System.out.println("|");

		for (int n = 0; n < 61; n++)
			System.out.print("-");

		System.out.println();

		for (int n = 0; n < arraySize; n++) {

			System.out.print(String.format("| %2s " + " ", theArray[n]));

		}

		System.out.println("|");

		for (int n = 0; n < 61; n++)
			System.out.print("-");

		System.out.println();

		if (i != -1) {

			// Number of spaces to put before the F

			int spacesBeforeFront = 6 * (i + 1) - 5;

			for (int k = 0; k < spacesBeforeFront; k++)
				System.out.print(" ");

			System.out.print("L" + i);

			// Number of spaces to put before the R

			int spacesBeforeRear = 5 * (j + 1) - spacesBeforeFront;

			for (int l = 0; l < spacesBeforeRear; l++)
				System.out.print(" ");

			System.out.print("R" + j);

			System.out.println("\n");

		}

	}

}
```

## Big O Notations

```java
// Big O notation is a way to measure how well a
// computer algorithm scales as the amount of data
// involved increases. It is not always a measure
// of speed as you'll see below

// This is a rough overview of Big O and doesn't 
// cover topics such as asymptotic analysis, which
// covers comparing algorithms as data approaches
// infinity

// What we are defining is the part of the algorithm 
// that has the greatest effect. For example
// 45n^3 + 20n^2 + 19 = 84 (n=1)
// 45n^3 + 20n^2 + 19 = 459 (n=2) Does 19 matter?
// 45n^3 + 20n^2 + 19 = 47019 (n=10) 
// Does the 20n^2 matter if 45n^3 = 45,000?
// Has an O(n^3) Order of n-cubed

public class BigONotation {

	private int[] theArray;

	private int arraySize;

	private int itemsInArray = 0;

	static long startTime;

	static long endTime;

	public static void main(String[] args) {

		/*
		 * 0(1) Test BigONotation testAlgo = new BigONotation(10);
		 * 
		 * testAlgo.addItemToArray(10);
		 * 
		 * System.out.println(Arrays.toString(testAlgo.theArray));
		 */

		BigONotation testAlgo2 = new BigONotation(100000);
		testAlgo2.generateRandomArray();

		BigONotation testAlgo3 = new BigONotation(200000);
		testAlgo3.generateRandomArray();

		BigONotation testAlgo4 = new BigONotation(30000);
		testAlgo4.generateRandomArray();

		BigONotation testAlgo5 = new BigONotation(400000);
		testAlgo5.generateRandomArray();

		/*
		 * O(N) Test
		 * 
		 * testAlgo2.linearSearchForValue(20);
		 * 
		 * testAlgo3.linearSearchForValue(20);
		 * 
		 * testAlgo4.linearSearchForValue(20);
		 * 
		 * testAlgo5.linearSearchForValue(20);
		 */

		// O(N^2) Test
		/*
		 * testAlgo2.bubbleSort();
		 * 
		 * testAlgo3.bubbleSort();
		 * 
		 * testAlgo4.bubbleSort();
		 * 
		 * // 0 (log N) Test
		 * 
		 * testAlgo2.binarySearchForValue(20);
		 * testAlgo3.binarySearchForValue(20);
		 */

		// O (n log n) Test

		startTime = System.currentTimeMillis();

		testAlgo2.quickSort(0, testAlgo2.itemsInArray);

		endTime = System.currentTimeMillis();

		System.out.println("Quick Sort Took " + (endTime - startTime));

	}

	// O(1) An algorithm that executes in the same
	// time regardless of the amount of data
	// This code executes in the same amount of
	// time no matter how big the array is

	public void addItemToArray(int newItem) {

		theArray[itemsInArray++] = newItem;

	}

	// 0(N) An algorithm thats time to complete will
	// grow in direct proportion to the amount of data
	// The linear search is an example of this

	// To find all values that match what we
	// are searching for we will have to look in
	// exactly each item in the array

	// If we just wanted to find one match the Big O
	// is the same because it describes the worst
	// case scenario in which the whole array must
	// be searched

	public void linearSearchForValue(int value) {

		boolean valueInArray = false;
		String indexsWithValue = "";

		startTime = System.currentTimeMillis();

		for (int i = 0; i < arraySize; i++) {

			if (theArray[i] == value) {
				valueInArray = true;
				indexsWithValue += i + " ";
			}

		}

		System.out.println("Value Found: " + valueInArray);

		endTime = System.currentTimeMillis();

		System.out.println("Linear Search Took " + (endTime - startTime));

	}

	// O(N^2) Time to complete will be proportional to
	// the square of the amount of data (Bubble Sort)
	// Algorithms with more nested iterations will result
	// in O(N^3), O(N^4), etc. performance

	// Each pass through the outer loop (0)N requires us
	// to go through the entire list again so N multiplies
	// against itself or it is squared

	public void bubbleSort() {

		startTime = System.currentTimeMillis();

		for (int i = arraySize - 1; i > 1; i--) {

			for (int j = 0; j < i; j++) {

				if (theArray[j] > theArray[j + 1]) {

					swapValues(j, j + 1);

				}
			}
		}

		endTime = System.currentTimeMillis();

		System.out.println("Bubble Sort Took " + (endTime - startTime));
	}

	// O (log N) Occurs when the data being used is decreased
	// by roughly 50% each time through the algorithm. The
	// Binary search is a perfect example of this.

	// Pretty fast because the log N increases at a dramatically
	// slower rate as N increases

	// O (log N) algorithms are very efficient because increasing
	// the amount of data has little effect at some point early
	// on because the amount of data is halved on each run through

	public void binarySearchForValue(int value) {

		startTime = System.currentTimeMillis();

		int lowIndex = 0;
		int highIndex = arraySize - 1;

		int timesThrough = 0;

		while (lowIndex <= highIndex) {

			int middleIndex = (highIndex + lowIndex) / 2;

			if (theArray[middleIndex] < value)
				lowIndex = middleIndex + 1;

			else if (theArray[middleIndex] > value)
				highIndex = middleIndex - 1;

			else {

				System.out.println("\nFound a Match for " + value
						+ " at Index " + middleIndex);

				lowIndex = highIndex + 1;

			}

			timesThrough++;

		}

		// This doesn't really show anything because
		// the algorithm is so fast

		endTime = System.currentTimeMillis();

		System.out.println("Binary Search Took " + (endTime - startTime));

		System.out.println("Times Through: " + timesThrough);

	}

	// O (n log n) Most sorts are at least O(N) because
	// every element must be looked at, at least once.
	// The bubble sort is O(N^2)
	// To figure out the number of comparisons we need
	// to make with the Quick Sort we first know that
	// it is comparing and moving values very
	// efficiently without shifting. That means values
	// are compared only once. So each comparison will
	// reduce the possible final sorted lists in half.
	// Comparisons = log n! (Factorial of n)
	// Comparisons = log n + log(n-1) + .... + log(1)
	// This evaluates to n log n

	public void quickSort(int left, int right) {

		if (right - left <= 0)
			return;

		else {

			int pivot = theArray[right];

			int pivotLocation = partitionArray(left, right, pivot);

			quickSort(left, pivotLocation - 1);
			quickSort(pivotLocation + 1, right);

		}

	}

	public int partitionArray(int left, int right, int pivot) {

		int leftPointer = left - 1;
		int rightPointer = right;

		while (true) {

			while (theArray[++leftPointer] < pivot)
				;

			while (rightPointer > 0 && theArray[--rightPointer] > pivot)
				;

			if (leftPointer >= rightPointer) {

				break;

			} else {

				swapValues(leftPointer, rightPointer);

			}

		}

		swapValues(leftPointer, right);

		return leftPointer;

	}

	BigONotation(int size) {

		arraySize = size;

		theArray = new int[size];

	}

	public void generateRandomArray() {

		for (int i = 0; i < arraySize; i++) {

			theArray[i] = (int) (Math.random() * 1000) + 10;

		}

		itemsInArray = arraySize - 1;

	}

	public void swapValues(int indexOne, int indexTwo) {

		int temp = theArray[indexOne];
		theArray[indexOne] = theArray[indexTwo];
		theArray[indexTwo] = temp;

	}

}
```

## Java Hash Table

```java
import java.util.Arrays;

// If we think of a Hash Table as an array
// then a hash function is used to generate
// a unique key for every item in the array.
// The position the item goes in is known
// as the slot. Hashing doesn't work very well
// in situations in which duplicate data
// is stored. Also it isn't good for searching
// for anything except a specific key. 
// However a Hash Table is a data structure that 
// offers fast insertion and searching capabilities.

public class HashFunction {

	String[] theArray;
	int arraySize;
	int itemsInArray = 0;

	public static void main(String[] args) {

		HashFunction theFunc = new HashFunction(30);

		// Simplest Hash Function

		// String[] elementsToAdd = { "1", "5", "17", "21", "26" };

		// theFunc.hashFunction1(elementsToAdd, theFunc.theArray);

		// Mod Hash Function
		// This contains exactly 30 items to show how collisions
		// will work

		String[] elementsToAdd2 = { "100", "510", "170", "214", "268", "398",
				"235", "802", "900", "723", "699", "1", "16", "999", "890",
				"725", "998", "978", "988", "990", "989", "984", "320", "321",
				"400", "415", "450", "50", "660", "624" };

		theFunc.hashFunction2(elementsToAdd2, theFunc.theArray);

		// Locate the value 660 in the Hash Table

		theFunc.findKey("660");

		theFunc.displayTheStack();

	}

	// Simple Hash Function that puts values in the same
	// index that matches their value

	public void hashFunction1(String[] stringsForArray, String[] theArray) {

		for (int n = 0; n < stringsForArray.length; n++) {

			String newElementVal = stringsForArray[n];

			theArray[Integer.parseInt(newElementVal)] = newElementVal;

		}

	}

	// Now let's say we have to hold values between 0 & 999
	// but we never plan to have more than 15 values in all.
	// It wouldn't make sense to make a 1000 item array, so
	// what can we do?

	// One way to fit these numbers into a 30 item array is
	// to use the mod function. All you do is take the modulus
	// of the value versus the array size

	// The goal is to make the array big enough to avoid
	// collisions, but not so big that we waste memory

	public void hashFunction2(String[] stringsForArray, String[] theArray) {

		for (int n = 0; n < stringsForArray.length; n++) {

			String newElementVal = stringsForArray[n];

			// Create an index to store the value in by taking
			// the modulus

			int arrayIndex = Integer.parseInt(newElementVal) % 29;

			System.out.println("Modulus Index= " + arrayIndex + " for value "
					+ newElementVal);

			// Cycle through the array until we find an empty space

			while (theArray[arrayIndex] != "-1") {

				++arrayIndex;

				System.out.println("Collision Try " + arrayIndex + " Instead");

				// If we get to the end of the array go back to index 0

				arrayIndex %= arraySize;

			}

			theArray[arrayIndex] = newElementVal;

		}

	}

	// Returns the value stored in the Hash Table

	public String findKey(String key) {

		// Find the keys original hash key
		int arrayIndexHash = Integer.parseInt(key) % 29;

		while (theArray[arrayIndexHash] != "-1") {

			if (theArray[arrayIndexHash] == key) {

				// Found the key so return it
				System.out.println(key + " was found in index "
						+ arrayIndexHash);

				return theArray[arrayIndexHash];

			}

			// Look in the next index

			++arrayIndexHash;

			// If we get to the end of the array go back to index 0

			arrayIndexHash %= arraySize;

		}

		// Couldn't locate the key

		return null;

	}

	HashFunction(int size) {

		arraySize = size;

		theArray = new String[size];

		Arrays.fill(theArray, "-1");

	}

	public void displayTheStack() {

		int increment = 0;

		for (int m = 0; m < 3; m++) {

			increment += 10;

			for (int n = 0; n < 71; n++)
				System.out.print("-");

			System.out.println();

			for (int n = increment - 10; n < increment; n++) {

				System.out.format("| %3s " + " ", n);

			}

			System.out.println("|");

			for (int n = 0; n < 71; n++)
				System.out.print("-");

			System.out.println();

			for (int n = increment - 10; n < increment; n++) {

				if (theArray[n].equals("-1"))
					System.out.print("|      ");

				else
					System.out
							.print(String.format("| %3s " + " ", theArray[n]));

			}

			System.out.println("|");

			for (int n = 0; n < 71; n++)
				System.out.print("-");

			System.out.println();

		}

	}

}
```

## Java Hash Tables #2

```java
import java.util.ArrayList;
import java.util.Arrays;

public class HashFunction2 {

	String[] theArray;
	int arraySize;
	int itemsInArray = 0;

	public static void main(String[] args) {

		HashFunction2 theFunc = new HashFunction2(31);

		String[] elementsToAdd2 = { "100", "510", "170", "214", "268", "398",
				"235", "802", "900", "723", "699", "1", "16", "999", "890",
				"725", "998", "978", "988", "990", "989", "984", "320", "321",
				"400", "415", "450", "50", "660", "624" };

		// Demonstrate how data normally follows patterns and how
		// a non-prime sized array can cause havoc

		String[] elementsToAdd3 = { "30", "60", "90", "120", "150", "180",
				"210", "240", "270", "300", "330", "360", "390", "420", "450",
				"480", "510", "540", "570", "600", "989", "984", "320", "321",
				"400", "415", "450", "50", "660", "624" };

		theFunc.hashFunction2(elementsToAdd2, theFunc.theArray);

		// theFunc.modThirty();

		theFunc.increaseArraySize(60);

		theFunc.displayTheStack();

		theFunc.fillArrayWithNeg1();

		theFunc.doubleHashFunc(elementsToAdd2, theFunc.theArray);

		theFunc.displayTheStack();

		theFunc.findKeyDblHashed("990");

	}

	// Outputs the matches that would put an item in
	// index 0 if arraySize was 31

	public void modThirty() {

		for (int i = 1; i < 999; i++) {

			if (i % 30 == 0) {

				System.out.println(i);

			}

		}

	}

	public boolean isPrime(int number) {

		// Eliminate the need to check versus even numbers

		if (number % 2 == 0)
			return false;

		// Check against all odd numbers

		for (int i = 3; i * i <= number; i += 2) {

			if (number % i == 0)
				return false;

		}

		// If we make it here we know it is odd

		return true;

	}

	// Receives a number and returns the next prime
	// number that follows

	public int getNextPrime(int minNumberToCheck) {

		for (int i = minNumberToCheck; true; i++) {

			if (isPrime(i))
				return i;

		}

	}

	// Increase array size to a prime number

	public void increaseArraySize(int minArraySize) {

		// Get a prime number bigger than the array
		// requested

		int newArraySize = getNextPrime(minArraySize);

		// Move the array into a bigger array with the
		// larger prime size

		moveOldArray(newArraySize);

	}

	public void moveOldArray(int newArraySize) {

		// Create an array that has all of the values of
		// theArray, but no empty spaces

		String[] cleanArray = removeEmptySpacesInArray(theArray);

		// Increase the size for theArray

		theArray = new String[newArraySize];

		arraySize = newArraySize;

		// Fill theArray with -1 in every space

		fillArrayWithNeg1();

		// Send the values previously in theArray into
		// the new larger array

		hashFunction2(cleanArray, theArray);

	}

	// Will remove all empty spaces in an array

	public String[] removeEmptySpacesInArray(String[] arrayToClean) {

		ArrayList<String> stringList = new ArrayList<String>();

		// Cycle through the array and if a space doesn't
		// contain -1, or isn't empty add it to the ArrayList

		for (String theString : arrayToClean)
			if (!theString.equals("-1") && !theString.equals(""))
				stringList.add(theString);

		return stringList.toArray(new String[stringList.size()]);

	}

	public void doubleHashFunc(String[] stringsForArray, String[] theArray) {

		for (int n = 0; n < stringsForArray.length; n++) {

			// Store value in array index

			String newElementVal = stringsForArray[n];

			// Create an index to store the value in by taking
			// the modulus

			int arrayIndex = Integer.parseInt(newElementVal) % arraySize;

			// Get the distance to skip down in the array
			// after a collision occurs. We are doing this
			// rather than just going to the next index to
			// avoid creating clusters

			int stepDistance = 7 - (Integer.parseInt(newElementVal) % 7);

			System.out.println("step distance: " + stepDistance);

			/*
			 * System.out.println("Modulus Index= " + arrayIndex + " for value "
			 * + newElementVal);
			 */

			// Cycle through the array until we find an empty space

			while (theArray[arrayIndex] != "-1") {

				arrayIndex += stepDistance;

				// System.out.println("Collision Try " + arrayIndex +
				// " Instead");

				// If we get to the end of the array go back to index 0

				arrayIndex %= arraySize;

			}

			theArray[arrayIndex] = newElementVal;

		}

	}

	// Returns the value stored in the Double Hashed Hash Table

	public String findKeyDblHashed(String key) {

		// Find the keys original hash key
		int arrayIndexHash = Integer.parseInt(key) % arraySize;

		// Find the keys original step distance

		int stepDistance = 5 - (Integer.parseInt(key) % 5);

		while (theArray[arrayIndexHash] != "-1") {

			if (theArray[arrayIndexHash] == key) {

				// Found the key so return it
				System.out.println(key + " was found in index "
						+ arrayIndexHash);

				return theArray[arrayIndexHash];

			}

			// Look in the next index

			arrayIndexHash += stepDistance;

			// If we get to the end of the array go back to index 0

			arrayIndexHash %= arraySize;

		}

		// Couldn't locate the key

		return null;

	}

	public void hashFunction2(String[] stringsForArray, String[] theArray) {

		for (int n = 0; n < stringsForArray.length; n++) {

			String newElementVal = stringsForArray[n];

			// Create an index to store the value in by taking
			// the modulus

			int arrayIndex = Integer.parseInt(newElementVal) % arraySize;

			/*
			 * 
			 * System.out.println("Modulus Index= " + arrayIndex + " for value "
			 * + newElementVal);
			 */

			// Cycle through the array until we find an empty space

			while (theArray[arrayIndex] != "-1") {

				++arrayIndex;

				// System.out.println("Collision Try " + arrayIndex +
				// " Instead");

				// If we get to the end of the array go back to index 0

				arrayIndex %= arraySize;

			}

			theArray[arrayIndex] = newElementVal;

		}

	}

	// Returns the value stored in the Hash Table

	public String findKey(String key) {

		// Find the keys original hash key
		int arrayIndexHash = Integer.parseInt(key) % arraySize;

		while (theArray[arrayIndexHash] != "-1") {

			if (theArray[arrayIndexHash] == key) {

				// Found the key so return it
				System.out.println(key + " was found in index "
						+ arrayIndexHash);

				return theArray[arrayIndexHash];

			}

			// Look in the next index

			++arrayIndexHash;

			// If we get to the end of the array go back to index 0

			arrayIndexHash %= arraySize;

		}

		// Couldn't locate the key

		return null;

	}

	HashFunction2(int size) {

		arraySize = size;

		theArray = new String[size];

		// Fill Array with -1 for each empty space

		fillArrayWithNeg1();

	}

	public void fillArrayWithNeg1() {

		Arrays.fill(theArray, "-1");

	}

	public void displayTheStack() {

		int increment = 0;

		int numberOfRows = (arraySize / 10) + 1;

		for (int m = 0; m < numberOfRows; m++) {

			increment += 10;

			for (int n = 0; n < 71; n++)
				System.out.print("-");

			System.out.println();

			for (int n = increment - 10; n < increment; n++) {

				System.out.format("| %3s " + " ", n);

			}

			System.out.println("|");

			for (int n = 0; n < 71; n++)
				System.out.print("-");

			System.out.println();

			for (int n = increment - 10; n < increment; n++) {

				if (n >= arraySize)
					System.out.print("|      ");

				else if (theArray[n].equals("-1"))
					System.out.print("|      ");

				else
					System.out
							.print(String.format("| %3s " + " ", theArray[n]));

			}

			System.out.println("|");

			for (int n = 0; n < 71; n++)
				System.out.print("-");

			System.out.println();

		}

	}

}
```

## Java Hash Tables #3

```java
import java.util.Scanner;

public class HashFunction3 {

	WordList[] theArray;
	int arraySize;
	int itemsInArray = 0;

	public String[][] elementsToAdd = {
			{ "ace", "Very good" },
			{ "act", "Take action" },
			{ "add", "Join (something) to something else" },
			{ "age", "Grow old" },
			{ "ago", "Before the present" },
			{ "aid", "Help, assist, or support" },
			{ "aim", "Point or direct" },
			{ "air", "Invisible gaseous substance" },
			{ "all", "Used to refer to the whole quantity" },
			{ "amp",
					"Unit of measure for the strength of an electrical current" },
			{ "and", "Used to connect words" }, { "ant", "A small insect" },
			{ "any", "Used to refer to one or some of a thing" },
			{ "ape", "A large primate" },
			{ "apt", "Appropriate or suitable in the circumstances" },
			{ "arc", "A part of the circumference of a curve" },
			{ "are", "Unit of measure, equal to 100 square meters" },
			{ "ark", "The ship built by Noah" },
			{ "arm", "Two upper limbs of the human body" },
			{ "art", "Expression or application of human creative skill" },
			{ "ash", "Powdery residue left after the burning" },
			{ "ask", "Say something in order to obtain information" },
			{ "asp", "Small southern European viper" },
			{ "ass", "Hoofed mammal" },
			{ "ate", "To put (food) into the mouth and swallow it" },
			{ "atm", "Unit of pressure" },
			{ "awe", "A feeling of reverential respect" },
			{ "axe", "Edge tool with a heavy bladed head" },
			{ "aye", "An affirmative answer" } };

	public int stringHashFunction(String wordToHash) {

		int hashKeyValue = 0;

		for (int i = 0; i < wordToHash.length(); i++) {

			// 'a' has the character code of 97 so subtract
			// to make our letters start at 1

			int charCode = wordToHash.charAt(i) - 96;

			int hKVTemp = hashKeyValue;

			// Calculate the hash key using the 26 letters
			// plus blank

			hashKeyValue = (hashKeyValue * 27 + charCode) % arraySize;

			System.out.println("Hash Key Value " + hKVTemp
					+ " * 27 + Character Code " + charCode + " % arraySize "
					+ arraySize + " = " + hashKeyValue);

		}
		System.out.println();

		return hashKeyValue;

	}

	HashFunction3(int size) {

		arraySize = size;

		theArray = new WordList[size];

		// Fill the array with WordLists

		for (int i = 0; i < arraySize; i++) {

			theArray[i] = new WordList();

		}

		addTheArray(elementsToAdd);

	}

	public void insert(Word newWord) {

		String wordToHash = newWord.theWord;

		// Calculate the hashkey for the Word

		int hashKey = stringHashFunction(wordToHash);

		// Add the new word to the array and set
		// the key for the word

		theArray[hashKey].insert(newWord, hashKey);

	}

	public Word find(String wordToFind) {

		// Calculate the hash key for the word

		int hashKey = stringHashFunction(wordToFind);

		// NEW

		Word theWord = theArray[hashKey].find(hashKey, wordToFind);

		return theWord;

	}

	public void addTheArray(String[][] elementsToAdd) {

		for (int i = 0; i < elementsToAdd.length; i++) {

			String word = elementsToAdd[i][0];
			String definition = elementsToAdd[i][1];

			// Create the Word with the word name and
			// definition

			Word newWord = new Word(word, definition);

			// Add the Word to theArray

			insert(newWord);

		}

	}

	public void displayTheArray() {

		for (int i = 0; i < arraySize; i++) {

			System.out.println("theArray Index " + i);

			theArray[i].displayWordList();

		}

	}

}

class Word {

	public String theWord;
	public String definition;

	public int key;

	// Reference to next Word made in the WordList

	public Word next;

	public Word(String theWord, String definition) {

		this.theWord = theWord;
		this.definition = definition;

	}

	public String toString() {

		return theWord + " : " + definition;

	}

}

class WordList {

	// Reference to first Link in list
	// The last Link added to the LinkedList

	public Word firstWord = null;

	public void insert(Word newWord, int hashKey) {

		Word previous = null;
		Word current = firstWord;

		newWord.key = hashKey;

		while (current != null && newWord.key > current.key) {

			previous = current;
			current = current.next;

		}

		if (previous == null)
			firstWord = newWord;

		else
			previous.next = newWord;

		newWord.next = current;

	}

	public void displayWordList() {

		Word current = firstWord;

		while (current != null) {

			System.out.println(current);
			current = current.next;

		}

	}

	public Word find(int hashKey, String wordToFind) {

		Word current = firstWord;

		// Search for key, but stop searching if
		// the hashKey < what we are searching for
		// Because the list is sorted this allows
		// us to avoid searching the whole list

		while (current != null && current.key <= hashKey) {

			// NEW

			if (current.theWord.equals(wordToFind))
				return current;

			current = current.next;

		}

		return null;

	}

	public static void main(String[] args) {

		Scanner input = new Scanner(System.in);

		// Make a 11 item array that will hold words
		// and definitions

		HashFunction3 wordHashTable = new HashFunction3(11);

		String wordLookUp = "a";

		// Keep retrieve requests until x is entered

		while (!wordLookUp.equalsIgnoreCase("x")) {

			System.out.println(": ");

			wordLookUp = input.nextLine();

			// Look for the word requested and print
			// it out to screen

			System.out.println(wordHashTable.find(wordLookUp));

		}

		// Display every item in the array with
		// the index they are associated with

		wordHashTable.displayTheArray();

	}
}
```

## Java Binary Search Tree

```java
public class BinaryTree {

	Node root;

	public void addNode(int key, String name) {

		// Create a new Node and initialize it

		Node newNode = new Node(key, name);

		// If there is no root this becomes root

		if (root == null) {

			root = newNode;

		} else {

			// Set root as the Node we will start
			// with as we traverse the tree

			Node focusNode = root;

			// Future parent for our new Node

			Node parent;

			while (true) {

				// root is the top parent so we start
				// there

				parent = focusNode;

				// Check if the new node should go on
				// the left side of the parent node

				if (key < focusNode.key) {

					// Switch focus to the left child

					focusNode = focusNode.leftChild;

					// If the left child has no children

					if (focusNode == null) {

						// then place the new node on the left of it

						parent.leftChild = newNode;
						return; // All Done

					}

				} else { // If we get here put the node on the right

					focusNode = focusNode.rightChild;

					// If the right child has no children

					if (focusNode == null) {

						// then place the new node on the right of it

						parent.rightChild = newNode;
						return; // All Done

					}

				}

			}
		}

	}

	// All nodes are visited in ascending order
	// Recursion is used to go to one node and
	// then go to its child nodes and so forth

	public void inOrderTraverseTree(Node focusNode) {

		if (focusNode != null) {

			// Traverse the left node

			inOrderTraverseTree(focusNode.leftChild);

			// Visit the currently focused on node

			System.out.println(focusNode);

			// Traverse the right node

			inOrderTraverseTree(focusNode.rightChild);

		}

	}

	public void preorderTraverseTree(Node focusNode) {

		if (focusNode != null) {

			System.out.println(focusNode);

			preorderTraverseTree(focusNode.leftChild);
			preorderTraverseTree(focusNode.rightChild);

		}

	}

	public void postOrderTraverseTree(Node focusNode) {

		if (focusNode != null) {

			postOrderTraverseTree(focusNode.leftChild);
			postOrderTraverseTree(focusNode.rightChild);

			System.out.println(focusNode);

		}

	}

	public Node findNode(int key) {

		// Start at the top of the tree

		Node focusNode = root;

		// While we haven't found the Node
		// keep looking

		while (focusNode.key != key) {

			// If we should search to the left

			if (key < focusNode.key) {

				// Shift the focus Node to the left child

				focusNode = focusNode.leftChild;

			} else {

				// Shift the focus Node to the right child

				focusNode = focusNode.rightChild;

			}

			// The node wasn't found

			if (focusNode == null)
				return null;

		}

		return focusNode;

	}

public static void main(String[] args) {

		BinaryTree theTree = new BinaryTree();

		theTree.addNode(50, "Boss");

		theTree.addNode(25, "Vice President");

		theTree.addNode(15, "Office Manager");

		theTree.addNode(30, "Secretary");

		theTree.addNode(75, "Sales Manager");

		theTree.addNode(85, "Salesman 1");

		// Different ways to traverse binary trees

		// theTree.inOrderTraverseTree(theTree.root);

		// theTree.preorderTraverseTree(theTree.root);

		// theTree.postOrderTraverseTree(theTree.root);

		// Find the node with key 75

		System.out.println("\nNode with the key 75");

		System.out.println(theTree.findNode(75));

}
}

class Node {

	int key;
	String name;

	Node leftChild;
	Node rightChild;

	Node(int key, String name) {

		this.key = key;
		this.name = name;

	}

	public String toString() {

		return name + " has the key " + key;

		/*
		 * return name + " has the key " + key + "\nLeft Child: " + leftChild +
		 * "\nRight Child: " + rightChild + "\n";
		 */

	}

}
```

## Java Binary Search Tree #2

```java
public class BinaryTree {

	Node root;

	public void addNode(int key, String name) {

		// Create a new Node and initialize it

		Node newNode = new Node(key, name);

		// If there is no root this becomes root

		if (root == null) {

			root = newNode;

		} else {

			// Set root as the Node we will start
			// with as we traverse the tree

			Node focusNode = root;

			// Future parent for our new Node

			Node parent;

			while (true) {

				// root is the top parent so we start
				// there

				parent = focusNode;

				// Check if the new node should go on
				// the left side of the parent node

				if (key < focusNode.key) {

					// Switch focus to the left child

					focusNode = focusNode.leftChild;

					// If the left child has no children

					if (focusNode == null) {

						// then place the new node on the left of it

						parent.leftChild = newNode;
						return; // All Done

					}

				} else { // If we get here put the node on the right

					focusNode = focusNode.rightChild;

					// If the right child has no children

					if (focusNode == null) {

						// then place the new node on the right of it

						parent.rightChild = newNode;
						return; // All Done

					}

				}

			}
		}

	}

	// All nodes are visited in ascending order
	// Recursion is used to go to one node and
	// then go to its child nodes and so forth

	public void inOrderTraverseTree(Node focusNode) {

		if (focusNode != null) {

			// Traverse the left node

			preorderTraverseTree(focusNode.leftChild);

			// Visit the currently focused on node

			System.out.println(focusNode);

			// Traverse the right node

			preorderTraverseTree(focusNode.rightChild);

		}

	}

	public void preorderTraverseTree(Node focusNode) {

		if (focusNode != null) {

			System.out.println(focusNode);

			preorderTraverseTree(focusNode.leftChild);
			preorderTraverseTree(focusNode.rightChild);

		}

	}

	public void postOrderTraverseTree(Node focusNode) {

		if (focusNode != null) {

			preorderTraverseTree(focusNode.leftChild);
			preorderTraverseTree(focusNode.rightChild);

			System.out.println(focusNode);

		}

	}

	public Node findNode(int key) {

		// Start at the top of the tree

		Node focusNode = root;

		// While we haven't found the Node
		// keep looking

		while (focusNode.key != key) {

			// If we should search to the left

			if (key < focusNode.key) {

				// Shift the focus Node to the left child

				focusNode = focusNode.leftChild;

			} else {

				// Shift the focus Node to the right child

				focusNode = focusNode.rightChild;

			}

			// The node wasn't found

			if (focusNode == null)
				return null;

		}

		return focusNode;

	}

	public boolean remove(int key) {

		// Start at the top of the tree

		Node focusNode = root;
		Node parent = root;

		// When searching for a Node this will
		// tell us whether to search to the
		// right or left

		boolean isItALeftChild = true;

		// While we haven't found the Node
		// keep looking

		while (focusNode.key != key) {

			parent = focusNode;

			// If we should search to the left

			if (key < focusNode.key) {

				isItALeftChild = true;

				// Shift the focus Node to the left child

				focusNode = focusNode.leftChild;

			} else {

				// Greater than focus node so go to the right

				isItALeftChild = false;

				// Shift the focus Node to the right child

				focusNode = focusNode.rightChild;

			}

			// The node wasn't found

			if (focusNode == null)
				return false;

		}

		// If Node doesn't have children delete it

		if (focusNode.leftChild == null && focusNode.rightChild == null) {

			// If root delete it

			if (focusNode == root)
				root = null;

			// If it was marked as a left child
			// of the parent delete it in its parent

			else if (isItALeftChild)
				parent.leftChild = null;

			// Vice versa for the right child

			else
				parent.rightChild = null;

		}

		// If no right child

		else if (focusNode.rightChild == null) {

			if (focusNode == root)
				root = focusNode.leftChild;

			// If focus Node was on the left of parent
			// move the focus Nodes left child up to the
			// parent node

			else if (isItALeftChild)
				parent.leftChild = focusNode.leftChild;

			// Vice versa for the right child

			else
				parent.rightChild = focusNode.leftChild;

		}

		// If no left child

		else if (focusNode.leftChild == null) {

			if (focusNode == root)
				root = focusNode.rightChild;

			// If focus Node was on the left of parent
			// move the focus Nodes right child up to the
			// parent node

			else if (isItALeftChild)
				parent.leftChild = focusNode.rightChild;

			// Vice versa for the left child

			else
				parent.rightChild = focusNode.rightChild;

		}

		// Two children so I need to find the deleted nodes
		// replacement

		else {

			Node replacement = getReplacementNode(focusNode);

			// If the focusNode is root replace root
			// with the replacement

			if (focusNode == root)
				root = replacement;

			// If the deleted node was a left child
			// make the replacement the left child

			else if (isItALeftChild)
				parent.leftChild = replacement;

			// Vice versa if it was a right child

			else
				parent.rightChild = replacement;

			replacement.leftChild = focusNode.leftChild;

		}

		return true;

	}

	public Node getReplacementNode(Node replacedNode) {

		Node replacementParent = replacedNode;
		Node replacement = replacedNode;

		Node focusNode = replacedNode.rightChild;

		// While there are no more left children

		while (focusNode != null) {

			replacementParent = replacement;

			replacement = focusNode;

			focusNode = focusNode.leftChild;

		}

		// If the replacement isn't the right child
		// move the replacement into the parents
		// leftChild slot and move the replaced nodes
		// right child into the replacements rightChild

		if (replacement != replacedNode.rightChild) {

			replacementParent.leftChild = replacement.rightChild;
			replacement.rightChild = replacedNode.rightChild;

		}

		return replacement;

	}

	public static void main(String[] args) {

		BinaryTree theTree = new BinaryTree();

		theTree.addNode(50, "Boss");

		theTree.addNode(25, "Vice President");

		theTree.addNode(15, "Office Manager");

		theTree.addNode(30, "Secretary");

		theTree.addNode(75, "Sales Manager");

		theTree.addNode(85, "Salesman 1");

		// Different ways to traverse binary trees

		// theTree.inOrderTraverseTree(theTree.root);

		// theTree.preorderTraverseTree(theTree.root);

		// theTree.postOrderTraverseTree(theTree.root);

		// Find the node with key 75

		System.out.println("\nNode with the key 75");

		System.out.println(theTree.findNode(75));

		System.out.println("Remove Key 25");

		theTree.remove(25);

		System.out.println(theTree.findNode(25));

		theTree.inOrderTraverseTree(theTree.root);

	}
}

class Node {

	int key;
	String name;

	Node leftChild;
	Node rightChild;

	Node(int key, String name) {

		this.key = key;
		this.name = name;

	}

	public String toString() {

		return name + " has the key " + key;

		/*
		 * return name + " has the key " + key + "\nLeft Child: " + leftChild +
		 * "\nRight Child: " + rightChild + "\n";
		 */

	}

}
```

## Algorithms #1

```
4 ROW TREE

_______1
___1_______1
_1___1___1___1
1_1_1_1_1_1_1_1

1st Row Indent 7 Spaces 0
2nd Row Indent 3 Spaces 7
3rd Row Indent 1 Spaces 3
4th Row Indent 0 Spaces 1

Indent : -2^-n * (-16+2^n) start with 1
Spaces : 0 and then whatever Indent was

First Index Per Row
0
1 2
3 4 5 6
7 8 9 10 11 12 13 14
.5 * (-2 + (Math.pow(2, iteration)))

Items Per Row
1, 2, 4, 8
Math.pow(2, iteration - 1)

Max Index Per Row
indexToPrint + itemsPerRow

Indent Number
Indent Number Space Number
Indent Number Space Number Space...

I need 1 index followed by multiple numbers & spaces every time
```

```java
public void printTree(int rows) {

		int spaces = 0;

		int iteration = 1;

		while (iteration <= rows) {

			int indent = (int) Math
					.abs(((Math.pow(-2, -iteration)) * (-16 + (Math.pow(2,
							iteration)))));

			int indexToPrint = (int) (.5 * (-2 + (Math.pow(2, iteration))));

			int itemsPerRow = (int) (Math.pow(2, iteration - 1));

			int maxIndexToPrint = indexToPrint + itemsPerRow;

			for (int j = 0; j < indent; j++)
				System.out.print(" ");

			for (int l = indexToPrint; l < maxIndexToPrint; l++) {

				System.out.print(theHeap[l].key);

				for (int k = 0; k < spaces; k++)
					System.out.print(" ");

			}

			spaces = indent;

			iteration++;

			System.out.println();

		}

	}
```

## Algorithms #2

```java
import java.util.Arrays;

public class Heap2 {

	private Data3[] theHeap;

	private int itemsInArray = 0;

	private int maxSize;

	public Heap2(int maxSize) {

		this.maxSize = maxSize;

		theHeap = new Data3[maxSize];

	}

	public void insert(int index, Data3 newData) {

		theHeap[index] = newData;

		itemsInArray++;

	}

	// Old Tree Generation Code

	public void printTree(int rows) {

		int spaces = 0;

		int iteration = 1;

		while (iteration <= rows) {

			int indent = (int) Math
					.abs(((Math.pow(-2, -iteration)) * (-16 + (Math.pow(2,
							iteration)))));

			int indexToPrint = (int) (.5 * (-2 + (Math.pow(2, iteration))));

			int itemsPerRow = (int) (Math.pow(2, iteration - 1));

			int maxIndexToPrint = indexToPrint + itemsPerRow;

			for (int j = 0; j < indent; j++)
				System.out.print(" ");

			for (int l = indexToPrint; l < maxIndexToPrint; l++) {

				System.out.print(theHeap[l].key);

				for (int k = 0; k < spaces; k++)
					System.out.print(" ");

			}

			spaces = indent;

			iteration++;

			System.out.println();

		}

	}

	public void printTree2(int rows) {

		// Number of spaces between items in tree

		int spaces = 0;

		int iteration = 1;

		// Generate all of the indents that are
		// needed depending on the number of rows
		// to print

		int[] indent = getIndentArray(rows);

		while (iteration <= rows) {

			// Find first Index : .5 * (-2 + 2^n)

			int indexToPrint = (int) (.5 * (-2 + (Math.pow(2, iteration))));

			// Number of Items per Row : 2^(n - 1)

			int itemsPerRow = (int) (Math.pow(2, iteration - 1));

			int maxIndexToPrint = indexToPrint + itemsPerRow;

			/*
			 * System.out.println("Indent: " + indent[iteration - 1]);
			 * System.out.println("indexToPrint: " + indexToPrint);
			 * System.out.println("itemsPerRow: " + itemsPerRow);
			 * System.out.println("maxIndexToPrint: " + maxIndexToPrint);
			 */

			// Print the indents needed

			for (int j = 0; j < indent[iteration - 1]; j++)
				System.out.print(" ");

			// Print all of the index values for each row
			// indexToPrint represents the first index in the
			// row, while maxIndexToPrint equals the last

			for (int l = indexToPrint; l < maxIndexToPrint; l++) {

				// If the array isn't full don't try to print
				// indexes that don't exist

				if (l < itemsInArray) {

					System.out.print(String.format("%02d", theHeap[l].key));

					for (int k = 0; k < spaces; k++)
						System.out.print(" ");

				}

			}

			// In a tree the spaces get bigger in the
			// same way that indents get smaller

			spaces = indent[iteration - 1];

			iteration++;

			System.out.println();

		}

	}

	// Calculate each indent per row for the tree
	// then reverse their order to go from biggest
	// to smallest

	public int[] getIndentArray(int rows) {

		int[] indentArray = new int[rows];

		for (int i = 0; i < rows; i++) {

			indentArray[i] = (int) Math.abs((-2 + (Math.pow(2, i + 1))));

		}

		Arrays.sort(indentArray);

		indentArray = reverseArray(indentArray);

		return indentArray;

	}

	// Reverse the indent values in the array
	// so that they go from biggest to smallest

	public int[] reverseArray(int[] theArray) {

		// Index of the first element
		int leftIndex = 0;

		// Index of last element
		int rightIndex = theArray.length - 1;

		while (leftIndex < rightIndex) {
			// Exchange the left and right elements
			int temp = theArray[leftIndex];
			theArray[leftIndex] = theArray[rightIndex];
			theArray[rightIndex] = temp;

			// Move the indexes to check towards the middle
			leftIndex++;
			rightIndex--;
		}

		return theArray;
	}

	// Fill the heap with random numbers based on
	// the number that is passed in

	public void generateFilledArray(int randNum) {

		Data3 randomData1;

		for (int i = 0; i < this.maxSize; i++) {

			randomData1 = new Data3((int) (Math.random() * randNum) + 1);

			this.insert(i, randomData1);

		}

	}

	public static void main(String args[]) {

		System.out.println("OLD TREE");

		Heap2 newHeap = new Heap2(70);

		// If I generate 2 digit numbers nothing lines up

		// newHeap.generateFilledArray(90);

		newHeap.generateFilledArray(9);

		// If I increase to over 4 rows the spaces are lost in the last row

		// newHeap.printTree(5);

		// newHeap.printTree(6);

		System.out.println("\nNEW TREE\n");

		newHeap.printTree2(6);

	}

}

class Data3 {

	public int key;

	public Data3(int key) {

		this.key = key;

	}

}
```

## Heaps

```java
import java.util.Arrays;

public class Heap2 {

	private Data3[] theHeap;

	private int itemsInArray = 0;

	private int maxSize;

	public Heap2(int maxSize) {

		this.maxSize = maxSize;

		theHeap = new Data3[maxSize];

	}

	public void insert(int index, Data3 newData) {

		theHeap[index] = newData;

	}

	public void incrementTheArray() {

		itemsInArray++;

	}

	public Data3 pop() {

		// if (itemsInArray != 0) {

		int tempItemsInArray = itemsInArray - 1;

		// Used to show how data is moved during sorting

		System.out.println("Store " + theHeap[0] + " in root. Store "
				+ theHeap[tempItemsInArray] + " in index 0");

		System.out.println(Arrays.toString(theHeap) + "\n");

		Data3 root = theHeap[0];

		theHeap[0] = theHeap[--itemsInArray];

		// Send to the array heap method starting with index 0

		heapTheArray(0);

		return root;

		// }

		// return null;

	}

	public void printTree2(int rows) {

		// Number of spaces between items in tree

		int spaces = 0;

		int iteration = 1;

		// Generate all of the indents that are
		// needed depending on the number of rows
		// to print

		int[] indent = getIndentArray(rows);

		while (iteration <= rows) {

			// Find first Index : .5 * (-2 + 2^n)

			int indexToPrint = (int) (.5 * (-2 + (Math.pow(2, iteration))));

			// Number of Items per Row : 2^(n - 1)

			int itemsPerRow = (int) (Math.pow(2, iteration - 1));

			int maxIndexToPrint = indexToPrint + itemsPerRow;

			// Print the indents needed

			for (int j = 0; j < indent[iteration - 1]; j++)
				System.out.print(" ");

			// Print all of the index values for each row
			// indexToPrint represents the first index in the
			// row, while maxIndexToPrint equals the last

			for (int l = indexToPrint; l < maxIndexToPrint; l++) {

				// If the array isn't full don't try to print
				// indexes that don't exist

				if (l < itemsInArray) {

					System.out.print(String.format("%02d", theHeap[l].key));

					for (int k = 0; k < spaces; k++)
						System.out.print(" ");

				}

			}

			// In a tree the spaces get bigger in the
			// same way that indents get smaller

			spaces = indent[iteration - 1];

			iteration++;

			System.out.println();

		}

	}

	// Calculate each indent per row for the tree
	// then reverse their order to go from biggest
	// to smallest

	public int[] getIndentArray(int rows) {

		int[] indentArray = new int[rows];

		for (int i = 0; i < rows; i++) {

			indentArray[i] = (int) Math.abs((-2 + (Math.pow(2, i + 1))));

		}

		Arrays.sort(indentArray);

		indentArray = reverseArray(indentArray);

		return indentArray;

	}

	// Reverse the indent values in the array
	// so that they go from biggest to smallest

	public int[] reverseArray(int[] theArray) {

		// Index of the first element
		int leftIndex = 0;

		// Index of last element
		int rightIndex = theArray.length - 1;

		while (leftIndex < rightIndex) {
			// Exchange the left and right elements
			int temp = theArray[leftIndex];
			theArray[leftIndex] = theArray[rightIndex];
			theArray[rightIndex] = temp;

			// Move the indexes to check towards the middle
			leftIndex++;
			rightIndex--;
		}

		return theArray;
	}

	// Fill the heap with random numbers based on
	// the number that is passed in

	public void generateFilledArray(int randNum) {

		Data3 randomData1;

		for (int i = 0; i < this.maxSize; i++) {

			randomData1 = new Data3((int) (Math.random() * randNum) + 1);

			this.insert(i, randomData1);

			// Need to do this in a separate function because
			// later when I sort the array I need to use insert
			// without incrementing the array

			incrementTheArray();

		}

	}

	public void heapTheArray(int index) {

		int largestChild;

		Data3 root = theHeap[index];

		while (index < itemsInArray / 2) {

			// Get the index for the leftChild

			int leftChild = 2 * index + 1;

			// Get the index for the rightChild

			int rightChild = leftChild + 1;

			// If leftChild is less then rightChild
			// save rightChild in largestChild

			if (rightChild < itemsInArray
					&& theHeap[leftChild].key < theHeap[rightChild].key) {

				System.out.println("Put Value " + theHeap[rightChild]
						+ " in largestChild");

				largestChild = rightChild;

			} else {

				System.out.println("Put Value " + theHeap[leftChild]
						+ " in largestChild");

				// Otherwise save leftChild in largestChild

				largestChild = leftChild;

			}

			// If root is greater then the largestChild
			// jump out of while

			if (root.key >= theHeap[largestChild].key)
				break;

			System.out.println("Put Index Value " + theHeap[largestChild]
					+ " in Index " + index);

			// Save the value in largest child into the top
			// index

			theHeap[index] = theHeap[largestChild];

			index = largestChild;

			System.out.println();

			printTree2(4);

			System.out.println();

		}

		theHeap[index] = root;

	}

	// Cycle through the array and pop off each so
	// the array goes from smallest to largest

	public void heapSort() {

		for (int k = maxSize - 1; k >= 0; k--) {

			Data3 largestNode = pop();
			insert(k, largestNode);

			System.out.println(Arrays.toString(theHeap));

		}

	}

	public static void main(String args[]) {

		Heap2 newHeap = new Heap2(7);

		newHeap.generateFilledArray(90);

		// Print out the array before it is sorted
		System.out.println("Original Array");
		System.out.println(Arrays.toString(newHeap.theHeap));

		System.out.println();

		newHeap.printTree2(4);
		System.out.println();

		for (int j = newHeap.maxSize / 2 - 1; j >= 0; j--) {

			newHeap.heapTheArray(j);

		}

		System.out.println("Heaped Array");

		System.out.println(Arrays.toString(newHeap.theHeap) + "\n");

		newHeap.printTree2(4);

		System.out.println("HEAPED SORTED");

		newHeap.heapSort();

		// Print the sorted array
		System.out.println("\nSorted Array");
		System.out.println(Arrays.toString(newHeap.theHeap));

	}
}

class Data3 {

	public int key;

	public Data3(int key) {

		this.key = key;

	}

	public String toString() {

		return Integer.toString(key);

	}

}
```

