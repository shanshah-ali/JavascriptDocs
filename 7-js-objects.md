### Objects
A JavaScript object is a collection of named values. The values are written as name : value pairs (name and value separated by a colon).
* javascript objects are mutable


##### Creating javascript objects:
1. ###### Using object literal
```
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```
2. ###### Using javascript keyword new
```
var person = new Object();
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue";
```
3. ###### Using Object.create()
```
const Animal = {
  type: 'Invertebrates',
  displayType: function() {
    console.log(this.type);
  }
};

let animal1 = Object.create(Animal);
animal1.displayType(); // Invertebrates
```
