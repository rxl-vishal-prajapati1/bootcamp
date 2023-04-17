# Java Assignment - 3
---
### Question1.  
Take 20 integer inputs from user and print the following:

* number of positive numbers
* number of negative numbers
* number of odd numbers
* number of even numbers
* number of 0s.

> **Answer:** 
> ```java
>   public static void main(String[] args) {
>     int pos = 0;
>     int neg = 0;
>     int odd = 0;
>     int even = 0;
>     int zeroes = 0;
>     Scanner sc = new Scanner(System.in);
>     for (int i = 0; i < 10; i++) {
>       int x = sc.nextInt();
>       if (x > 0) ++pos;
>       else if (x == 0) ++zeroes;
>       else ++neg;
> 
>       if (x % 2 == 0) ++even;
>       else ++odd;
>     }
>     sc.close();
> 
>     System.out.println("Positive " + pos);
>     System.out.println("Negative " + neg);
>     System.out.println("Odd " + odd);
>     System.out.println("Even " + even);
>     System.out.println("Zeroes " + zeroes);
>   }  
> ```



---
### Question2.  
Take an array of 10 elements. Split it into middle and store the elements in two dfferent arrays. 
E.g.-  
INITIAL array :
58 24 13 15 63 9 8 81 1 78  
After spliting :
58 24 13 15 63  
9 8 81 1 78

> **Answer:**  
> ```java
>    public static void main(String[] args) {
>      int[] arr = new int[10];
> 
>      Scanner sc = new Scanner(System.in);
>      for (int i = 0; i < 10; i++) {
>        arr[i] = sc.nextInt();
>      }
>      sc.close();
> 
>      int[] left = new int[5];
>      int[] right = new int[5];
> 
>      for (int i = 0; i < 5; i++) {
>        left[i] = arr[i];
>        right[i] = arr[i + 5];
>      }
> 
>      for (int i = 0; i < left.length; i++) System.out.print(left[i] + " ");
>      System.out.print("\n");
>      for (int i = 0; i < right.length; i++) System.out.print(right[i] + " ");
>    }
> ```


---
### Question3.  
Create a class with a method that prints `"This is parent class"` and its subclass with another method that prints `"This is child class"`.  
Now, create an object for each of the class and call  
1 - method of parent class by object of parent class  
2 - method of child class  by object of child class
3 - method of parent class by object of child class

> **Answer:** 
>   
> ```java
> class Parent {
>   public void print() {
>     System.out.println("This is parent class");
>   }
> }
> 
> class Child extends Parent {
>   public void printChild() {
>     System.out.println("This is child class");
>   }
> }
> 
> class example{
>   public static void main(String args[])  {
>     Parent p = new Parent();
>     Child c = new Child();
>     p.print(); // method of parent class by object of parent class
>     c.printChild(); // method of child class by object of child class
>     c.print(); // method of parent class by object of child class
>   }
> }
> ```
> 
> **Output:**  
> ```
> This is parent class
> This is child class
> This is parent class
> ```
---
### Question4.  
Write a program to print the name, salary and date of joining of 10 employees in a company.
Use array of objects.

> **Answer:** 
> ```java
>   class Employee {
>   String name;
>   int salary;
>   String date_of_joining;
> 
>   Employee( String name, int salary, String date_of_joining) {
>     this.name = name;
>     this.salary = salary;
>     this.date_of_joining = date_of_joining;
>   }
> 
>   @Override
>   public String toString() {
>     return "Name " + name +
>           "\nSalary " + salary + 
>           "\nDate of joining: " + date_of_joining;
>   }
> };
> 
> public class example {
> 	public static void main(String[] args) {
>     Employee[] arr = new Employee[10];
>     
>     Scanner sc = new Scanner(System.in);
>     for (int i = 0; i < arr.length; i++) {
>       System.out.println("Enter name");
>       String name = sc.nextLine();
>       
>       System.out.println("Enter salary");
>       int salary = sc.nextInt(); sc.nextLine();
>       
>       System.out.println("Enter date of joining");
>       String doj = sc.nextLine();
> 
>       arr[i] = new Employee(name, salary, doj);
>     }
>     
>     sc.close();
> 
>     for (int i = 0; i < arr.length; i++) {
>       System.out.println(arr[i]);
>     }
>   }
> }
> ```
---
### Question5.  
Write a program that takes your full name as input and displays the abbreviations of the first and middle names except the last name which is displayed as it is.  

For example, if your name is Robert Brett Roser, then the output should be R.B.Roser.

> **Answer:** 
> ```java
>    public static void main(String[] args) {
>     Scanner sc = new Scanner(System.in);
>     System.out.println("Enter first name");
>     String fname = sc.nextLine();
>     
>     System.out.println("Enter mid name");
>     String mname = sc.nextLine();
> 
>     System.out.println("Enter last name");
>     String lname = sc.nextLine();
>     sc.close();
> 
>     String abb_name = fname.charAt(0) + "." + mname.charAt(0) + "." + lname;
>     System.out.println(abb_name);
>   }
> ```

---
### Question6.  
What is the difference between `equals()` method and equality `operator (==)` in Java?

>**Answer:**   
>  `equals()` method check contect of the two strings. It is invoked as -- `s1.equals(s2);`  
>  
>  `== operator` check for memory address not content. 
  

---
### Question7.  
What is the difference between `StringBuilder` and `StringBuffer`?

>**Answer:**   
>  `StringBuffer` is synchronized, but `StringBuilder` isn't.

---
### Question8.  
Explain the use of `final` keyword in variable, method and class.

>**Answer:**   
>  Variable declared as `final` cannot be changed.  
>  Methods declared as `final` can't be overridden.  
>  Class declared as `final` can't be extended. 


---
### Question9.  
Is it possible that the `finally` block will not be executed? If yes then list the case.

>**Answer:**     
>  Yes, if in the try block we call `System.exit()` the program will get terminated and finally won't be called. 

---
### Question10.  
What are shallow copy and deep copy in java?

>**Answer:**     
>    In deep copy, new memory in heap is allocated and reference is not copied for object fields.
>    Changes in duplicate object won't reflect in the original object.
>
>    In shallow copy, reference is copied for object fields. No memory is allocated.
>    Changes in duplicate object will reflect in the original object.

---
### Question11.  
What will be the output of below program?

```java
public class TestClass {
  public static void main(String[] args) {
    int a = 30;
    int b = 40;
    int c = 10;

    int expression = (a * b) / (a - b + c);
    System.out.println("Result: " + expression);
  }
}
```
  >**Output:**
  >  Arithmetic  exception  (divide by zero) will be thrown (a - b + c) is 0.

---
### Question12.  
Why it is always recommended to keep the clean-up activities like closing the I/O resources or DB connections inside a finally block?  

>  **Answer:**  
Finally block will executed no matter if exception is thrown or not.
>      Only case finally won't get executed when we call `System.exit();`


---
### Question13.  
What happens if the below code is executed?
```java
public class Test {
  public static void main(String[] args) {
    int[] list = new int[4];
    System.out.println(list[4]);
  }
}
```

>**Output:**  
>    Out of bound exception will be thrown as we trying to access 5th element of array of size 4.
    
---
### Question14.  
How many objects will be created for the following codes:

A.  
```java
String str1 = "abc"; //Line1
String str2 = new String("abc"); //Line2
```
B.
```java
String str1 = "abc"; //Line1
String str2 = "abc"; //Line2
```
C.
```java
String str1 = new String("abc"); //Line1
String str2 = new String("abc"); //Line2
```

>**Answer:**   
>
>  A: 2 (for `new String("abc")`, abc is already in string pool so it will create one object)  
>
>  B: 1  
>  
>  C: 3 (for `str1` abc is not in string pool so it'll create two objects, and `str2` will create one)

---
### Question15.  
How do you check whether a String is empty in Java?

>**Answer:**   
>  `isEmpty()` method of String class which returns `boolean`
   
---
### Question16.  
Write a program in java to join two arraylists into one arraylist.

> **Answer:** 
> ```java
>   public static void main(String[] args) {
>     ArrayList < Integer > one = new ArrayList < > (Arrays.asList(1, 2, 3, 4, 5));
>     ArrayList < Integer > two = new ArrayList < > (Arrays.asList(6, 7, 8, 9, 10, 11, 12));
> 
>     ArrayList < Integer > res = new ArrayList < > ();
>     for (int i = 0; i < one.size(); i++) {
>       res.add(one.get(i));
>     }
> 
>     for (int i = 0; i < two.size(); i++) {
>       res.add(two.get(i));
>     }
> 
>     System.out.println(res);
>   }
> ```
---
### Question17.  
Which of the following methods can be used to set every element of the List to a specified value?

`set()`  
`add()`  
`complete()`  
`fill()`  

> **Answer:** 
>   `collections.fill(container, initial_value)`

---
### Question18.  
Which of the following guarantees type-safety in a collection?

* Abstract Classes
* Interface
* Collection
* Generics

>**Answer:** 
  Generics
  
---
### Question19.  
Differentiate between Comparable and Comparator in the context of Java.
>  **Answer:**   
>    Comparable effects the class as we've to implement `comparable<Type>` and then override `compareTo(Obj)`
>
>    Comparator don't effect the class. We've to create a new class which implements `Comparator<Type>`, implement `compare(Obj one, Obj two)` and then pass it to the constructor of `collection.sort();` 

---
### Question20.  
Write a Java program to create and throw custom exceptions.

> **Answer:** 
> ```java
> class CustomException extends Exception {
>   CustomException(String s){
>       super(s);
>   }
> }
> 
> public class example {
>   public static void main(String[] args) {
>     try {
>       // do nothing
>       throw new CustomException("custom exception message");
>     } catch (CustomException ce) {
>       System.out.println(ce.getMessage());
>     }
>   }
> }
> ```

---
### Question21.  
What is the output of the below code?

```java
class IABC {
  public static void main(String args[]) {
    String obj = "Hello";
    String obj1 = "ABC";
    String obj2 = "Hello";
    System.out.println(obj.equals(obj1) + " " + obj.equals(obj2));
  }
}
```

> **Output:**  
>   `false true`

---
### Question22.  
Create a class named 'Member' having the following members:  
Data members  
1 - Name  
2 - Age  
3 - Phone number  
4 - Address  
5 - Salary  

It also has a method named `printSalary` which prints the salary of the members.

Two classes `Employee` and `Manager` inherits the `Member` class.  

The `Employee` and `Manager` classes have data members `specialization` and `department` respectively.  

Now, assign name, age, phone number, address and salary to an employee and a manager by making an object of both of these classes and print the same.


> **Answer:**  
> ```java 
> class Member {
>   String name, number, address;
>   int age, salary;
> 
>   public void printSalary() {
>     System.out.println("Salary is" + salary);
>   }
> }
> 
> 
> class Manager extends Member {
>   String department;
> 
>   Manager(String name, String number, String department, 
>           String address, int age, int salary) {
>     this.name = name;
>     this.number = number;
>     this.address = address;
>     this.age = age;
>     this.salary = salary;
>     this.department = department;
>   }
> 
>   @Override
>   public String toString() {
>     return "Name " + name + " \nNumber" + number
>           + "\nAddress " + address + "\nAge " + age + "\nSalary " + salary
>           + "\nDepartment " + department;
>   }
> }
> 
> 
> class Employee extends Member {
>   String specialization;
> 
>   Employee(String name, String number, String specialization, 
>           String address, int age, int salary) {
>     this.name = name;
>     this.number = number;
>     this.address = address;
>     this.age = age;
>     this.salary = salary;
>     this.specialization = specialization;
>   }
> 
>   @Override
>   public String toString() {
>     return "Name " + name + " \nNumber" + number
>           + "\nAddress " + address + "\nAge " + age + "\nSalary " + salary
>           + "\nSpecialization " + specialization;
>   }
> }
> 
> class example{
>   public static void main(String args[])  {
>     Employee e = new Employee("Ram", "1234567990", "AI", "Delhi", 21, 60000);
>     Manager m = new Manager("Arjun", "9876543210", "HR", "Noida", 27, 80000);
> 
>     System.out.println(e);
>     System.out.println(m);
>   }
> }
> ```

---

*end*
