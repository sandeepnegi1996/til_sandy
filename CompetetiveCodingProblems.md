# Competitve coding problems


1. How to Reverse a String in Java ?

Solution:
1. Approach 1: Just print the string in the reverse order
2. Approach 2: Store the character from the last character to a string and then keep adding the character from the string
                in reverse order , this will form a string and then print this string.
                
3. Approach 3: Use some method for the reverse , which is present in java.
  
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
