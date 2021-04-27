# Competitve coding problems


1. How to Reverse a String in Java ?

Solution: 
  
  Approach 1: Just print the string in the reverse order
  
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
