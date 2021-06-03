# Competitve coding problems

[https://www.journaldev.com/370/java-programming-interview-questions](Website link)

## 1. How to Reverse a String in Java ?

Solution:
1. Approach 1: Just print the string in the reverse order
2. Approach 2: Store the character from the last character to a string and then keep adding the character from the string
                in reverse order , this will form a string and then print this string.
                
3. Approach 3: Use String builder method reverse
                new StringBuilder(h1).reverse().toString();
                
                ** use this when there is no thread safety required **
                ** in case of thread safefy required use string buffer **
  
  
  #### Approach 1 : code
  
  ```java
  public class MyClass {
    public static void main(String args[]) {
      
      String nameOfWebsite="hashcodehub";
      int lengthOfString=nameOfWebsite.length();
      
      for(int i=lengthOfString-1;i>=0;i--) {
          
          System.out.print(nameOfWebsite.charAt(i));
      }
      
      
    }
}
  
  
  ```
  
  
  #### Approach 2: code 
  
  ```java
  public class MyClass {
    public static void main(String args[]) {
      
      String nameOfWebsite="hashcodehub";
      int lengthOfString=nameOfWebsite.length();
      
      String reversedString="";
      for(int i=lengthOfString-1;i>=0;i--) {
          
          reversedString=reversedString+nameOfWebsite.charAt(i);
          
             }
      
      System.out.println(reversedString);
      
    }
}
```

#### Approach 3: code

```java
public class MyClass {
    public static void main(String args[]) {
      
      String nameOfWebsite="hashcodehub";
      int lengthOfString=nameOfWebsite.length();
      
      
      StringBuilder str= new StringBuilder(nameOfWebsite);
      
      String reversed=str.reverse().toString();
      
      System.out.println(reversed);
      
    }
     
}

```


## 2. How to swap two numbers without using a third variable ?

- Approach 1 : multiplication
```code
a=a*b;
b=a/b;
a=a/b;

```
- Approach 2: Addition
```code
a=a+b;
b=a-b;
a=a-b;

```

## 3. How to check vowel is present in the string ?

- Approach 1 : Most Useful, We will use regex to find wether vowels present in the stirng or not.
```java
    public static Boolean isVowelPresent(String sample) {

        return sample.toLowerCase().matches(".*[aeiou].*");
    }
```

- Approach 2 : Traversing one by one and finding whether vowel is present or not using ```indexOf``` method


```java

    public static Boolean isVowelPresent(String sample) {
        char vowelArr[] = { 'a', 'e', 'i', 'o', 'u' };

        for (int i = 0; i < vowelArr.length; i++) {
            char currentVowel = vowelArr[i];

           if(sample.indexOf(currentVowel)!=-1){
               return true;
           }
        }
        return false;
    }
}


```

- Approach 3 : Traversing one by one and finding the vowel ``` old fashion ```
```java
    public static Boolean isVowelPresent(String sample) {
        char vowelArr[] = { 'a', 'e', 'i', 'o', 'u' };

        for (int i = 0; i < vowelArr.length; i++) {
            char currentVowel = vowelArr[i];

            for (int j = 0; j < sample.length(); j++) {
                if (currentVowel == sample.charAt(j)) {
                    return true;
                }
            }
        }
        return false;
    }
}
```

## 3. How to print nth Fibonacci number using recursion and iteration ?

- Approach 1 : Recursion , this one is comparetively easy 
``` java
public static  int  printFibonacciNthRecursion(int n) {
      
     
        if(n==1)
            return 0;

        if(n==2)
            return 1;

        return printFibonacciNthRecursion(n-1)+printFibonacciNthRecursion(n-2);

    }
```

- Approach 2: Iteration : here we have used two variable first and second after each iteration , first will store value of second and second will store result value.
- 

```java
 public static int printNthFibonacci(int n) {

        if(n==1) 
            return 0;

        if(n==2) 
            return 1;

        int first=0;
        int second =1;
        int result=0;

        for(int i=3;i<=n;i++) {
            result=first+second;
            first=second;
            second=result;

        }
        return result;
    }
```


                   
