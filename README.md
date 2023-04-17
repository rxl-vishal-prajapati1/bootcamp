# JAVA Assignment - 1



---

### Question1.  
How java follows "Write Once And Run Anywhere" concept?  

>**Answer:**  
>    Java programs are compiled to byte code which are platform independent. Byte code are converted to machine code by JVM.


---

### Question2.  
Do java support pass by value and pass by reference?
    
> **Answer:**
>     Java supports pass by value.


---

### Question3.  
Write a program to add 3 to the ASCII value of the character 'd'
and print the equivalent character.
```java
    char c = 'd';
    c += 3;
    System.out.println(c);
```

> **Output:**   
> `g`


---

### Question4.  
What is the size in bits for a `byte` data type.

> **Answer:**  
> `byte` is of 8 bits.

---

### Question5.  
Which of the following lines will compile without warning or error?

   * a) `char d="d";`
   * b) `float f=3.1415;`
   * c) `int i=34;`
   * d) `byte b=257;`
   * e) `boolean isPresent=true;`

>**Answer:**    
>Following won't compile:
>* a) `char d = "d";` `"d"` is a String not char
>* b) `float f = 3.1415;` 3.1415 is a double. We've to append 'f' at the end.
>* d) `byte b = 257;` Range of byte is -128 to 127

---

### Question6.  
Which of the following expressions will evaluate to 7?   
* a) `2 + 4 * 3- 7`  
* b) `(2 + 4) * (3 - 7)`  
* c) `2 + (4 * 3) - 7`  
* d) `((2 + 4) * 3) - 7)` 

> **Answer:**    
> Following will evaluates to 7:
> *  a) `2 + 4 * 3 - 7`
> *  c) `2 + (4 * 3) - 7`


---

### Question7.  
Which of the following statement will compile?  
  `int i = 5; int j = 10;`
  * a) `while(i < j) {}`
  * b) `while(i) {}`
  * c) `while(i = 5) {}`
  * d) `while((i = 12)!=5) {}`  

> **Answer:**      
> Following will compile:  
> * a) `while (i < j) {  }`
> * b) `while ((i = 12) != 5) {  }`


---

### Question8.  
What is the result of the following operation?  
    `System.out.println(4 % 3);`

> **Answer:**      
> `1` 


---

### Question9.  
Which of the following if statements will compile without errors?  
  `int i = 3; int j = 3; int k = 3;`
  * 1. `if(i > j) {}`
  * 2. `if(i > j > k) {}`
  * 3. `if(i > j && i > k) {}`
  * 4. `if(i > j && > k) {}`

**Answer:**  
Following will compile:
* 1. `if (i > j) {  }`
* 3. `if (i > j && i > k) {  }`
      `operator >` is a binary operator and it requires 2 operands  

Following won't compile:  

* in 2. `if (i > j > k) {  }` -- `i > j` is not a valid operand
* in 4. `if (i > j && > k) {}`  -- lhs operand is not there for ` > k`


---

### Question10. 
What will be printed out when the following code is executed?
```java
  switch (5) {
    case 0:
      System.out.println("zero");
      break;
    case 1:
      System.out.println("one");
    default:
      System.out.println("default");
    case 2:
      System.out.println("two");
   }
```
    
> **Output:**  
> `default`      
> `two `
>    
>code in default block will get executed as there is no break statement all statements below it until break is executed.
>
>
---

### Question11.  
What's the output of the following code?
```java
  public class Main {
    public static void main(String args[]) {
      boolean myVal = false;
      if (myVal = true)
        for (int i = 0; i < 2; i++)
          System.out.println(i);
      else
        System.out.println("else");
    }
  }
```

> **Output:**  
> `0`  
> `1`  
>
> `myVal = true` is `true` as the value is first assigned then use so if block is executed.


---

### Question12.  
What's the output of the following code?
```java
  public class Main {
    public static void main(String[] args) {
      int i = 10;
        do
          while (i < 15)
            i = i + 20;
        while (i < 2);
      System.out.println(i);
    }
  }
```

> **Output:**  
> `30`   
> `while (i < 15)` is true in first iteration, it'll update value of `i` to 30.

---
*end*