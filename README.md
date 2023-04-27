## GORM Assignment

```groovy
new Company(name: "Amazon", city: "Noida", pinCode: 1234).save()
new Company(name: "Flipkart", city: "Banglore", pinCode: 1234).save()
new Company(name: "", city: "Delhi", pinCode: 1234).save()
new Company(name: "Abott", city: "Delhi", pinCode: 1234).save()
new Company(name: "Aditya Biral", city: "Pune", pinCode: 1234).save(flush: true, failOnError: true)
```
```groovy
// Populate employees
new Employee(name: "Tulsi", city: "Delhi", phoneNumber: 1234567890, employeeId: 1, company: Company.findByName('Apple')).save();
new Employee(name: "Akhil", city: "Banglore", phoneNumber: 2234567890, employeeId: 1, company: Company.findByName('Amazon')).save();
new Employee(name: "Ankita", city: "Noida", phoneNumber: 3134567890, employeeId: 1, company: Company.findByName('Abbot')).save();
new Employee(name: "Nidhi", city: "Noida", phoneNumber: 34234567890, employeeId: 1, company: Company.findByName('Flipkart')).save();
new Employee(name: "Hemendra", city: "Kolkata", phoneNumber: 9234567890, employeeId: 2, company: Company.findByName('Amazon')).save();
new Employee(name: "Rajesh", city: "Banglore", phoneNumber: 7234567890, employeeId: 2, company: Company.findByName('Apple')).save(flush: true, failOnError: true);
```

**Using Critera**

```grails
// Print names of companies who has office in Noida or Delhi and it's name starts with 'A'

def companiesStartingWithALocatedInNoidaAndDelhi = Company.createCriteria().list() {
ilike('name', 'A%')
'in' ('city', ['Noida', 'Delhi'])

}

println companiesStartingWithALocatedInNoidaAndDelhi*.name
```
