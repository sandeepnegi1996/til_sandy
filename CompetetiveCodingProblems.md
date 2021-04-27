# Competitve coding problems


1. How to Reverse a String in Java ?

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

