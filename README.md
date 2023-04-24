## Groovy Collections - Exercise

---

**Question1.**  Initialize an empty list and give the output of the following code: 
```groovy
l[11] = "myelement"
println l[11]
printin l.get(5)
printin l
```

> **Output**
> ```
> myelement
> null
> [null, null, null, null, null, null, null, null, null, null, null, myelement]
> ```

---

**Question2.**  Initialize a list using a range and find all elements which are even.

> **Program**
> ```groovy
> List li = 1..10
> 
> List even_elements = li.findAll { it % 2 == 0 }
> 
> println even_elements
> ```

---

**Question3.**  Create a set from a list containing duplicate elements.  
What do you observe?

> **Program**  
> Duplicate elements are removed.
> ```groovy
> List li = [1, 2, 2, 3, 4, 5, 7, 6, 9]
> Set st = li as Set
> println st // duplicate elements are removed
> ```
How can you achieve the same result without converting a list to a set?

> **Program**
> ```groovy
> List li = [1, 2, 2, 3, 4, 5, 7, 6, 9]
> li.unique()
> println li
> ```


---

**Question4.**  Given two lists `[11, 12, 13, 14]` and `[13, 14, 15]`, how would we obtain the list of items from the first that are not in the second?

> **Program**
> ```groovy
> List li1 = [11, 12, 13, 14]
> List li2 = [13, 14, 15]
> 
> List li_res = li1 - li2
> println li_res // 11, 12
> ```


---

**Question5.**  Find whether two lists have a common element or not

> **Program**
> ```groovy
> List li1 = [11, 12, 13, 14]
> List li2 = [13, 14, 15]
> 
> if (li1.intersect(li2))
>     println "Lists contains common elements"
> else
>     println "Lists don't contains common elements"
> ```

---

**Question6.**  Remove all records from a list whose index is odd.

> **Program**
> ```groovy
> List li = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
> List res = []
> 0.step li.size(), 2, {
>     res += li[it]
> }
> 
> println res // [0, 2, 4, 6, 8, 10]
> ```


---

**Question7.**  Consider the following list:
`[1, 2, 3, "element1", 0.3, [2, 4, 6], 0..10]`
Print the class name of each element.

> **Program**
> ```groovy
> List li = [1, 2, 3, "element1", 0.3, [2, 4, 6], 0..10]
> 
> li.each {
>     println "$it -> class: ${it.class}"
> }
> ```

>**Output**
>```
>1 -> class: class java.lang.Integer
>2 -> class: class java.lang.Integer
>3 -> class: class java.lang.Integer
>element1 -> class: class java.lang.String
>0.3 -> class: class java.math.BigDecimal
>[2, 4, 6] -> class: class java.util.ArrayList
>[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10] -> class: class groovy.lang.IntRange
>```



What's the output of the following statement?  
`list.get(6).get(9)`

> **Ouput**
> ```
> 9
> ```


---

**Question8.**  Sort the given list in descending order having distinct elements:  
`[14,12, 11,10, 16, 15, 12, 10, 99, 90, 14, 16, 35]`

> **Program**
> ```groovy
> List li = [14,12, 11,10, 16, 15, 12, 10, 99, 90, 14, 16, 35]
> li.unique().sort {a, b-> a <=> b}
> println li
> ```

---

**Question9.**  Consider a class Employee with following details
* `Name`
* `Age`
* `Salary`  

Create a list consisting of 10 Employee objects.

> **Program**
> ```groovy
> class Employee {
>     String name;
>     int age;
>     int salary;
> 
>     String toString() {
>         return "$name $age $salary";
>     }
> }
> 
> List employees = [
>         new Employee(name: "A", age: 20, salary: 10000),
>         new Employee(name: "B", age: 20, salary: 10000),
>         new Employee(name: "C", age: 20, salary: 10000),
>         new Employee(name: "D", age: 20, salary: 10000),
>         new Employee(name: "E", age: 20, salary: 10000),
>         new Employee(name: "F", age: 20, salary: 10000),
>         new Employee(name: "G", age: 18, salary: 1000),
>         new Employee(name: "H", age: 17, salary: 2000),
>         new Employee(name: "I", age: 16, salary: 3000),
>         new Employee(name: "J", age: 22, salary: 10000),
>         new Employee(name: "K", age: 40, salary: 9999999),
> ]
> ```

* (a). Get a list of employees who earn less than 5000  
> **Program**
> ```groovy
> def employees_earning_less_than_5000 = employees.findAll {it.salary < 5000 }
> println employees_earning_less_than_5000
> ```
* (b). Get the name of the youngest employee and oldest employee

> **Program**
> ```groovy
> def youngest_employee = employees.min {it.age }
> print youngest_employee
> 
> def eldest_employee = employees.max {it.age }
> print eldest_employee
> ```

* (c). Get the employee with maximum salary  
> **Program**
> ```groovy
> def employee_with_highest_salary = employees.max {it.salary }
> print employee_with_highest_salary
> ```

* (d). Get the list of names of all the employees  
> **Program**
> ```groovy
> def employee_names = employees*.name
> println employee_names
> 
> // or
> def employee_names_dup = employees.collect { return it.name }
> println employee_names_dup
> ```


---

**Question10.**  Consider the following piece of code:

```groovy
String s = "this string needs to be split"
println s.tokenize(" ")
println s.tokenize()
```

Compare this with the following code:
```groovy
String s = "this string needs to be split"
println s.split(" ")
println s.split(/\s/); 
```

> **Explanation**
> ```
> In 1. both statements prints the same list. Default arguement for tokenize is " ".
> 
> In 2. both print statements prints the same list.  
> /\s/ is a regular expression for whitespace and " " is a whitespace.
> ```


Also try the following exercise:
```groovy
String s = "are.you.trying.to.split.me.mister?" s.tokenize(".")
s.split(".")
```

> **Explanation**
> ```
> s.split() accepts regular expression. "." matches all character other than line terminators (\n).  
> So it'll return an empty list.  
> 
> s.tokainze(".") will return an List of string sepeated by by one full stop.
> 
> ```



---

**Question11.**  Get first, second and last element of Range.

> **Program**
> ```groovy
> Range r = 1..9
> 
> println r.first()
> println r[1]
> println r.last()
> ```


---

**Question12.**  Print the table of a given number: 2 and 12

> **Program**
> ```groovy
> Closure times_table = { int num ->
>     (1..10).each {int i-> println (num * i) }
> }
> 
> times_table(2)
> times_table(12)
> ```


---

**Question13.**  We have a sorted list of alphabets `a-z`, print all alphabets appearing after `j`

> **Program**
> ```groovy
> List li = ('a'..'z').asList()
> li.findAll {it > 'j' }.each {println it}
> ```

---

**Question14.**  Find the number of occurences of a character in a string.

> **Program**
> ```groovy
>Map frequency = [:]
>
>String str = "thequickbrownfoxjumpsoverthelazydog"
>
>str.each {
>    String s ->
>        if (frequency.containsKey(s)) frequency[s] = frequency[s] + 1
>        else frequency[s] = 1
>}
>
>println frequency
> ```


---

**Question15.**  Write a program that prints the numbers from 1 to 100. But for multiples of three print `Fizz` instead of the number and for the multiples of five print `Buzz`. For numbers which are multiples of both three and five print `FizzBuzz`.

> **Program**
> ```groovy
> (1..100).each { int num ->
>     if (num % 3 == 0) print "Fizz"
>     if (num % 5 == 0) print "Buzz"
>     if (num % 3 != 0 && num % 5 != 0) print num
>     println()
> }
> ```


---

**Question16.**  Consider a class named `Stack` that holds a list of objects and has the following operations associated:

* 1) `POP` - Pops the last element off the stack
* 2) `PUSH` - Pushes an element on top of the stack
* 3) `TOP` - Returns the element at the top of the list

Implement the above said class

>**Program**
>```groovy
>class Stack {
>    List elements = []
>    void pop() {
>        if (elements.empty) return
>        elements.pop()
>    }
>    void push(val) {
>        elements.add(val)
>    }
>    def top() {
>        if (elements.empty) return null
>        return elements.last()
>    }
>}
>
>Stack s = new Stack();
>
>s.push(1)
>s.push(2)
>s.push(3)
>s.pop()
>s.pop()
>println s.top()
>
>```

---

**Question17.**  Create a new map consisting of 10 of your friend's name's as keys and their ages as value.

>**Program**
>```groovy
>Map name_to_age = [:]
>
>name_to_age["Alaknanda"] = 20
>name_to_age["Shanti"] = 21
>name_to_age["Binita"] = 22
>name_to_age["Rajesh"] = 23
>name_to_age["Madhavi"] = 24
>name_to_age["Nakul"] = 25
>name_to_age["Preshita"] = 26
>name_to_age["Sumit"] = 27
>name_to_age["Kalpana"] = 28
>name_to_age["Veena"] = 29
>
>println name_to_age
>```

---

**Question18.**  Iterate over the previous map in as many ways as possible

> **Program**
> ```groovy
> Map mp = [1:"a", 2:"b"]
> 
> // first
> mp.each {
>     key, value ->
>         println "$key -> $value"
> }
> 
> // second
> for (key in mp.keySet()) {
>     println "$key -> ${mp[key]}"
> }
> 
> // third
> 
> mp.eachWithIndex {
>     keyValue, index ->
>     println "${keyValue.key} -> ${keyValue.value}"
> }
> ```


---

**Question19.**  Create a new map by adding two existing maps

>**Program**
>```groovy
>Map students_to_age = ["ram": 20, "anuj": 21, "ankita": 20]
>Map teaches_to_age  = ["Manish": 59, "Laxmi": 48]
>
>Map teaches_and_students = students_to_age + teaches_to_age
>println teaches_and_students
>```

---

**Question20.**  Try the following code on a map:
```groovy
println map.class
println map.getClass()
```
What do you observe?

>**Answer**
>
>`println mp.class` -> returns value associated with the key "class" which is `null` if not present in set.  
>
>`println map.getClass()` return class name which is `class java.util.LinkedHashMap
>`
---

**Question21**  Consider the following map:
```groovy
Map m = ['1' : 2, '2' : 3, '3' : 4, '2':5]
```

Is this a valid construction?   

>**Answer**
>```
>The compiles without problem. 
>But it contains two entries for '2'.   
>Map contains unique keys so for key '2' the value is 5 which appeared later.
>```

What is the value of `m['2']`?

> **Answer**
> ```
> 5
> ```

---

**Question22.**  Find if a map contains a particular key.

> **Program**
> ```groovy 
> Map m = ['1' : 2, '2' : 3, '3' : 4, '2':5]
> println m.containsKey(1); // returns true or false
> ```


---

**Question23.**  Consider the following map:
```groovy
Map m = ['Computing': ['Computing': 600, 'Information Systems' : 300], 'Engineering': ['Civil' : 200, 'Mechanical' : 100], 'Management': ['Management' : 800]]
```

* a) How many university departments are there?

> **Program**
> ```groovy
> println m.values()*.size().sum()
> ```


* b) How many programs are delivered by the Computing department?  

> **Program**
> ```groovy
> println m['Computing'].size();
> ```

* c) How many students are enrolled in the Civil Engineering program?  

> **Program**
> ```groovy
> println m['Engineering']['Civil']
> ```

---

**Question24.**  Conside a class named `Employee` which has the following properties: 
* 1) Name
* 2) Age
* 3) DepartmentName
* 4) EmployeeNumber
* 5) Salary  

Let's say that there's a list of 50 employees available.  

Perform the following operations on the list of employees:  
* a) Group the employees on the basis of the bracket in which their salary falls. The ranges are 0-5000, 5001 and 10000, and so on.

> **Program**
> ```groovy
> 
> employees = [new Employee(salary: 10012000), new Employee(salary: 0), new Employee(salary: 5000), new Employee(salary: 5001)]
> println employees.groupBy { Employee e ->
>     if (e.salary == 0) return 1
>     return (int) Math.ceil(e.salary / 5000);
> }
> ```


* b) Get a count of the number of employees in each department

> **Program**
> ```groovy
> def employees_in_department = employees.groupBy {
>   Employee e -> return e.department_name;
> };
> 
> employees_in_department.each {
>     String department, List e ->
>     println "${department} -> ${e.size()}"
> }
> ```


* c) Get the list of employees whose age is between 18 and 35

> **Program**
> ```groovy
> def employees_under_35_and_above_18 = employees.findAll {
>     Employee e ->
>         return e.age >= 18 && e.age <= 35;
> }
> 
> println employees_under_35_and_above_18
> ```


* d) Group the employees according to the alphabet with which their first name starts and display the number of employees in each group whose age is greater than 20

> **Program**
> ```groovy
> def employees_by_initials = employees.groupBy {
>     Employee e ->
>         return e.name[0]
> }
> 
> employees_by_initials.each {
>     String initial, List e ->
>         print "$initial "
>         print e.count { Employee it -> it.age > 20 }
> }
> ```


* e) Group the employees according to their department.  

**Program**
> ```groovy
> def employees_by_department = employees.groupBy {
>     Employee e ->
>         e.department_name;
> }
> 
> println employees_by_department
> ```


---

**Question25.**  Write a method which retruns the value of passed key from a search string of the form `http://www.google.com/?name=johny&age=20&hobby=cricket`  


**Program**
> ```groovy
>def findValue(String url, String key) {
>    String value = null;
>    def (_, params) = url.tokenize('?')
>    params.tokenize('&').each {
>        String key_value ->
>            def (curr_key, curr_value) = key_value.tokenize("=")
>            if (key == curr_key) {
>                value = curr_value
>            }
>    }
>    return value
>}
>
>String url = "http://www.google.com/?name=johny&age=20&hobby=cricket";
>println (findValue(url, "name"))
>println (findValue(url, "age"))
>println (findValue(url, "hobby"))
>
> ```

---

*end*
