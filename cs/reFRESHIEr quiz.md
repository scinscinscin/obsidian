**Choose the best fitting answer**
1. Statements that affect the order in which code is being run are called
	1. If statements
	2. While statements
	3. **Control Structures**
	4. Loops
2. Insert the missing line of code so that the loop iterates until a newline is entered.
	1. **``(input = scanner.nextLine()).length() > 0``**
	2. ``(scanner.nextLine() = input).length() > 0``
	3. ``(scanner.nextLine() = input).length() == 0``
	4. ``(input = scanner.nextLine()).length() == 0``

```java
import java.util.Scanner;  
  
public class Testing {  
	public static void main(String[] args) {  
		System.out.println("Keep inputting a string");  
		Scanner scanner  = new Scanner(System.in);  
		String input;  
  
		while(/* insert code here*/){  
			System.out.println("The user inputted a string: " + input);  
		}  
  
		System.out.println("Goodbye");  
	}  
}
```
3. Conditional expressions are called
	1. While expressions
	2. If expressions
	3. Switch expressions
	4. **Ternary expressions**
4. This statement must be inserted after a switch case to prevent fallthrough
	1. `continue;`
	2. `break;`
	3. `return;`
	4. `goto;`
5. These are values that are passed into a method by the method caller
	1. Return value
	2. Variables
	3. **Arguments**
	4. Constants
6. **Complete the for loop such that the output prints the numbers from 1-10**
	1. `int i = 1; i < 10; i++`
	2. `int i = 1; i <= 10; i++`
	3. `int i = 0; i < 10; i++`
	4. `int i = 0; i <= 10; i++`
	   ```java
		for(/* insert your code here */){  
			System.out.printf("Current number: %d\n", i);  
		}
		```
7. How many of the following lines of code can be inserted such that the full code compiles and runs **without any error**
		``int i = 1; i <= numbersArray.length; i++``
		``int i = 0; i < numbersArray.length; i++``
		``int i : numbersArray``
		``int i : numbersArray[]``
	1. 1
	2. 2
	3. 3
	4. 4
	```java
	int []numbersArray = { 0, 1, 2, 3, 4 };  
	for(/* insert code here */){  
		System.out.println(numbersArray[i]);  
	}
	```
8. This refers to the name of the method and the names + types of its parameters.
	1. Method declaration
	2. Method signature
	3. Method implementation
	4. Parameter list
9. What's the difference between the while loop and the do-while loop?
	1. The while loop consumes less resources than the do-while loop, at the cost of taking longer to execute.
	2. The do-while loop evaluates the condition after every iteration, the while loop evaluates the condition before every iteration.
	3. The while loop is counter controller loop while the do-while loop is not.
	4. There are no differences, it is purely aesthetic.
10. How many of the following integer array declarations are valid?
	1. 1
	2. 2
	3. 3
	4. 4
	   ```java
		int []myArray = { 0, 1, 2, 3, 4 };  
		int myArray2[] = { 0, 1, 2, 3, 4 };  
		int myArray3[] = new int[]{ 0, 1, 2, 3, 4 };  
		int []myArray4 = new int[]{ 0, 1, 2, 3, 4 };
```