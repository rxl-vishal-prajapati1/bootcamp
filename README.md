# Introduction to Groovy - Exercise

---

**Question1.**  Create a class in Java along with follwing fields.  
* Classname is `Person`   
* fields are `name`, `age`, `gender`, `address` 
* Access the fields in all known ways: like through getter, by dot operator

> **Program**    
> 
> ```groovy
> class Person {
>   public String name;
>   public int age;
>   public String gender;
>   private String address;
> 
>   Person(String name, int age, String gender, 
>           String address) {
>     this.name = name;
>     this.age = age;
>     this.gender = gender;
>     this.address = address;
>   }
> 
>   public String getAddress() {
>     return this.address;
>   }
> }
> 
> Person p = new Person("Abc", 20, "Female", "Delhi");
> 
> System.out.println(p.name);
> System.out.println(p.age);
> System.out.println(p.gender);
> System.out.println(p.getAddress());
> ```
> **Output**
>
> ```
> Abc 
> 20  
> Female
> Delhi
> ```

---



**Question2.**   Extend the Person class in Groovy.  

Add following fields to it: 
`empld`, `company`, `salary`

Access the fields in all known ways: like through getter, by dot operator, by @ operator.

> **Program**    
> 
> ```groovy
> class Person {
>   public String name;
>   public int age;
>   public String gender;
>   private String address;
> 
>   String empId;
>   String company;
>   int salary;
> 
>   Person(String name, int age, String gender, 
>           String address) {
>     this.name = name;
>     this.age = age;
>     this.gender = gender;
>     this.address = address;
>   }
> 
>   public String getAddress() {
>     return this.address;
>   }
> 
>   // getter will give invalid salary
>   public String getSalary() { return 'Not avilable'; }
> }
> 
> Person p = new Person("Abc", 20, "Female", "Delhi");
> 
> p.empId = "123";
> p.company = "XYZ corp";
> p.salary = 600000;
> 
> println (p.name)
> println (p.getCompany())
> println (p.salary) // getter is called
> println (p.@salary) // .@ forces to not use getter
> 
>  ```
> **Output**  
> ```
> Abc
> XYZ corp
> Not avilable
> 600000
> ```

---

**Question3.**   Print this pattern:
> \*  
> \**  
> \****  
> \********  

> **Program**    
> 
> ```groovy
> for (int i = 0; i < 4; i++) {
>   for (int j = 0; j < Math.pow(2, i); j++)
>     print('*');
>   println();
> }
> ```

---

**Question4.**   GString... override the `toString()` of the Person class to return something like... "Sachin is a man aged 24 who lives at Delhi. He works for Intelligrape with
eb employee id 12 and draws $$$$$$$ lots of money !!!!."

> **Program**    
> 
> ```groovy
> class Person {
>   String name;
>   int age;
>   String city;
>   String employer;
>   String employer_id;
> 
> 
>   String toString() {
>     return "${name} is a person aged ${age} who lives at ${city}. He/she works for ${employer} with employee id ${employer_id} and draws \$\$\$\$\$\$\$\$ lots of money!!!!.";
>   }
> }
> 
> Person p = new Person(
>   name: "Sachin", 
>   age: 24,
>   city: "Delhi", 
>   employer: "Intelligrape", 
>   employer_id: 12
> )
> 
> println(p)
> ```
>
> **Output**  
> `Sachin is a person aged 24 who lives at Delhi. He/she works for Intelligrape with employee id 12 and draws $$$$$$$$ lots of money!!!!.`


---

**Question5.**   Groovy Truth: 

```groovy
if('test') { 
  println "test evaluated to true inside if"
}
```
try replacing test with various objects and observe its behaviour.

* a) `"Test"`
* b) empty list   
* c) list with all vaues as `null`   
* d) `List list = new ArrayList()`

> **Answer**    
> Only a and c will be true.  
> Empty list and `null` are evaluated as `false` in if condition.  
> List which are populated are evalauted as `true`.
> 

---

**Question6.**  Write a HourMinute where the class Stores hours and minutes as separate fields. `Overload +` and `- operator` operator for this class.

---

> **Program**    
> 
> ```groovy
>class HourMinute {
>    int hour   = 0;
>    int minute = 0;
>
>    def plus(HourMinute other) {
>      long mins = (hour * 60 + minute) + (other.hour * 60 + other.minute);
>      hour = ((long) (mins / 60)) % 24;
>      minute = mins % 60; 
>      return this;
>    }
>
>    def minus(HourMinute other) {
>      long mins = (hour * 60 + minute) - (other.hour * 60 + other.minute);
>      mins = (24 * 60 + mins) % (24 * 60);
>      hour = ((long) (mins / 60)) % 24;
>      minute = mins % 60; 
>      return this;
>    }
>  
>    String toString() {
>      return "${this.hour} : ${this.minute}";
>    }
>}
>
>HourMinute one = new HourMinute(hour: 3, minute: 20);
>HourMinute two = new HourMinute(hour: 8, minute: 20);
>
>println(one + two) // 11 : 40
>// one is now 11:40
>println(one - two) // 3 : 20
>
> ```
 

**Question7.**  Print multiple of 3 upto 10 terms in at least three different ways using groovy special methods.

---

> **Program**    
> 
> ```groovy
>// first
>for (int i = 1; i <= 10; i++) {
>  println(3 * i);
>}
>
>// second
> 10.times { println ((it + 1) * 3) }
> 
>// third
> 3.step 31, 3,  {
>  println(it)
> }
>
> // fourth
> 1.upto 10, {
>  println(it * 3);
> }
> ```

---


**Question8.**  Write a closure which checks if a value is contained within a list where the closure accepts two parameters.

> **Program**    
> 
> ```groovy
> def exists = {
>   element, List li ->
>   for (int i = 0; i < li.size(); i++)
>     if (element == li[i]) return true;
>   return false; 
> }
> ```

---

**Question9.**  Combine content of all the files in a specific directory to another new file.

> **Program**    
> 
> ```groovy
> def dir      = new File('/home/vishalprajapati/Desktop/Bootcamp/groovy_1/test_dir')
> def new_file = new File('/home/vishalprajapati/Desktop/Bootcamp/groovy_1/test_dir/merged/all.txt')
> new_file.createNewFile();
> 
> dir.eachFile {
>   file -> 
>   if (file.isFile()) {
>     file.eachLine {
>       line ->
>       new_file.append(line + "\n");
>     }
>   }  
> }
> ```

---

**Question10.**  Create a file which contains all the Odd numbered lines of a given file. Each line should be numbered at the beginning of line viz - 1. 3. 5 ....

> **Program**    
> 
> ```groovy
> def file      = new File('/home/vishalprajapati/Desktop/Bootcamp/groovy_1/groovy_file_handling/orignal.txt')
> def new_file = new File('/home/vishalprajapati/Desktop/Bootcamp/groovy_1/groovy_file_handling/seperated.txt')
> new_file.createNewFile();
> 
> int line_num = 1;
> 
> file.eachLine {
>   line -> 
>   if (line_num % 2 == 1) {
>     new_file.append("${line_num}. ${line} \n");
>   }
>   ++line_num;
> }
> ```

---

**Question11.**  Write a method which removes all the white spaces in a file and writes the output to another file. Suppose white space characters are Space, Tab and Enter 

> **Program**    
> 
> ```groovy
> def file      = new File('/home/vishalprajapati/Desktop/Bootcamp/groovy_1/groovy_file_handling/remove_example/orignal.txt')
> def new_file = new File('/home/vishalprajapati/Desktop/Bootcamp/groovy_1/groovy_file_handling/remove_example/processed.txt')
> new_file.createNewFile();
> 
> int line_num = 1;
> 
> def remove_space_and_tab = {
>   String line ->
>   String res;
>   for (int i = 0; i < line.size(); i++) {
>     if (line[i] == ' ' || line[i] == '\t')
>       continue;
>     res += line[i];
>   }
>   return res;
> }
> 
> file.eachLine {
>   line -> 
>   // enter (\n) is removed as we iterate through line
>   new_file.append(remove_space_and_tab(line));
> }
> ```

---

**Question12.**  Make copy of an image type file byte by byte.

> **Program**    
> 
>```groovy
> def image = new File('/home/vishalprajapati/Desktop/Bootcamp/groovy_1/groovy_file_handling/images/orignal.png')
> def copied = new File('/home/vishalprajapati/Desktop/Bootcamp/groovy_1/groovy_file_handling/images/copied.png')
> copied.createNewFile();
> 
> byte[] image_as_bytes = image.bytes;
> 
> int x = 0;
> for (int i = 0; i < image_as_bytes.size(); i++) {
>   byte[] temp = [image_as_bytes[i]];
>   copied.append(temp)
> }
> ```

---

*end*