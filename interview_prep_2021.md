# Prepare for the interview 


1. Datastructures
2. Algorithms
3. Coding problems
4. Architectural design questions
5. Behavioral Questions



#### Material
1. [](https://github.com/sandeepnegi1996/coding-interview-university)

## Lam Research Interview Questions :
- There are 2 coding problems and one puzzle 

Q1. Write any of the sorting algorithm ? 
Ans. I have written bubble sort , but i think it is better if i can code other sorting algorithms too.
Q2. Write the code to generate the pyramid (triangle one). ?
Ans. This one was working fine .
Q3. Two candle of same length but different thickness
	- thick candle take 6 hours to burn completely 
	- Thin candle take 4 hours to burn completely
- So i lit both the candle and went out of the room , after some time when i return i can see that thick is twice as much as thin.

Ans. So to solve the candle problem, after 1 hour what will happen
 1 hour --> thick candle --> remaining --> 5/6 remaining 
        --> thin candle  --> remiaing  --> 3/4 remaining 
	

2nd hour  --> thick candle  --> remaining  --> 4/6 
         ---> thin candle   --> reamining  --> 2/4 
	
3rd hour  --> thick candle  --> remaining  --> 3/6 --> 1/2
          --> thin candle   --> remaining  --> 1/4  --> 1/4
	  
	  at this time thick candle is twice as thin candle , so it took basically 3 hours.
	 



## Java Interview Questions 

Q1. jdk vs jre vs jvm
- jd k is a development kit , it contains jre and inside jre there is jvm , jdk also contains other bunch of tools such as , javac
- javadoc, jar,

2. JRE :- java runtime environment : this is the minimum requirement to run the code , if we have a java code we can run using jre , we don't need 
  jdk to run the code
  
3. JVM :- actual Java virtual machine which will basically run the code , it will take the bytecode and run it .

Q2. Explain public static void main(String args[]) in Java.

- public : access modifier means who can access this , since it is public it can be accessed by any of the classes in any of the packages there are other access modifier also like private,protected ,default

- static  👍 means it is associated with class , we can directly call this without even creating object of the class.
- void : it is a return type means the method will not return anything.
- main : it is method , which will be searched by the JVM this is where the execution of the code will start.
- String args[] -> basically an array of string which is passed as method argument.

Q3. Why Java is platform independent?
- Since the bytecode that is generated it can be ran on any system, i have tested this in windows and linux not in mac.


Q5. What are wrapper classes in Java?
- Wrapper claases are used to wrap the primitive data type into Refrence type, we have wrapper classes for each of the primitive data type.
- 
Q6. What are constructors in Java?
- basically its a method , and its name is same as the class name with no return type and it is used to initialize the object of the class
- whenever we create an object of the class this contructor will be invoked
- **Default Constructor** - this constructor does not have any parameters.
- **Prameterized Constructor** -has parameters

Q7. What is singleton class in Java and how can we make a class singleton?
- A class in which we can have only one instance of the class at any given point.
- We require - private constructor and a method with return type as the class reference to return the object
- So whenever we call the getInstance method same object will be returned if the install is null, then it will create an instance.


```java
// Java program implementing Singleton class
// with getInstance() method
class Singleton
{
	// static variable single_instance of type Singleton
	private static Singleton single_instance = null;

	// variable of type String
	public String s;

	// private constructor restricted to this class itself
	private Singleton()
	{
		s = "Hello I am a string part of Singleton class";
	}

	// static method to create instance of Singleton class
	public static Singleton getInstance()
	{
		if (single_instance == null)
			single_instance = new Singleton();

		return single_instance;
	}
}

// Driver Class
class Main
{
	public static void main(String args[])
	{
		// instantiating Singleton class with variable x
		Singleton x = Singleton.getInstance();

		// instantiating Singleton class with variable y
		Singleton y = Singleton.getInstance();

		// instantiating Singleton class with variable z
		Singleton z = Singleton.getInstance();

		// changing variable of instance x
		x.s = (x.s).toUpperCase();

		System.out.println("String from x is " + x.s);
		System.out.println("String from y is " + y.s);
		System.out.println("String from z is " + z.s);
		System.out.println("\n");

		// changing variable of instance z
		z.s = (z.s).toLowerCase();

		System.out.println("String from x is " + x.s);
		System.out.println("String from y is " + y.s);
		System.out.println("String from z is " + z.s);
	}
}


```
Q9. What is the difference between equals() and == in Java?

```java
// Java program to understand 
// the concept of == operator
public class Test {
    public static void main(String[] args)
    {
        String s1 = new String("HELLO");
        String s2 = new String("HELLO");
        System.out.println(s1 == s2);
        System.out.println(s1.equals(s2));
    }
}
```








