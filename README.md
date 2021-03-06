# Javascript Design Patterns
Chances are you have intuitively used design patterns when building things using your favourite js framework or even good old vanilla js. Chances are you can't explicitly describe those patterns and possibly don't have a deep understanding. This repo is for you or anyone that wants to familiarize themselves with essential design pattern concepts.
## Design Patterns:
- [Constructor Pattern](#constructor-pattern)
- [Module Pattern](#module-pattern)
  - [The Module Pattern](#the-module-pattern)
### Constructor Pattern
#### Basic Constructor
- A constructor is a special method for creating and intializing an object created within a class.
- Javascript supports special constructor functions. By prefixing the new keyword to a function we can make it behave like a constructor.

For example:
```javascript
 function Person(name, age, weight) {
            this.name = name
            this.age = age
            this.weight = weight
            this.personDetails = function () {
                return this.name + ' is ' + this.age + ' years old' 
                + ' and weighs ' + this.weight + ' kgs'
            }
        }
        var person1 = new Person('John', 29, 80)
        var person2 = new Person('Jane', 23, 70)
        console.log(person1.personDetails())
        console.log(person2.personDetails())
```
Notice any issues with the code above?
- It makes inheritance difficult.
- The personDetails function is redefined each time you create a new object using the Person constructor, which is not optimal. Ideally a single instance of personDetails() should be shared by all the Person objects. This can be achieved by using prototypes.
#### Constructors with Prototypes
- Almost all javascript objects contain prototype objects, and this also applies to functions. 
- When we call a constructor to create an object, all the properties of the constructor's prototype are available to new objects.
- Therefore several objects can access the same prototype.

We can apply this concept to create a function that is not redefined whenever a new Person object is created. This function can be shared by several objects as shown below:
```javascript
function Person (name, age, weight) {
            this.name = name
            this.age = age
            this.weight = weight
}
Person.prototype.personDetails = function () {
            return this.name + ' is ' + this.age + ' years old'
                + ' and weighs ' + this.weight + ' kgs'

        }
        var person1 = new Person('John', 29, 80)
        var person2 = new Person('Jane', 23, 70)
        console.log(person1.personDetails())
        console.log(person2.personDetails())
```
Of course, we could always use es6 classes:
```javascript
 class Person {
            constructor (name, age, weight) {
                this.name = name
                this.age = age
                this.weight = weight
            }
            personDetails () {
                return this.name + ' is ' + this.age + ' years old'
                    + ' and weighs ' + this.weight + ' kgs'
            }
        }
        const person1 = new Person('John', 29, 80)
        const person2 = new Person('Jane', 23, 70)
        console.log(person1.personDetails())
        console.log(person2.personDetails())
```
### Module Pattern
#### The Module Pattern
- Modules help keep a project's code cleanly separated and organized.
- This pattern uses closures to encapsulate "privacy", state and organization. 
- The pattern utilizes an immediately-invoked function expression (IIFE ), where only an object is returned, keeping everything else within the closure private.
- It protects pieces of your code(public/private methods and variables) from leaking into the global scope and undesirably colliding with another developer's interface.
- Javascript does not have access modifiers therefore you cannot explicitly declare variables as "public" or "private". This concept is simulated using scope.
- Variables or methods declared within the module and not defined in the returning object will be private. Anything defined in the returning object will be publicly available.
# EXAMPLE COMING UP NEXT :-)
