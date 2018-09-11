# Javascript Design Patterns
Chances are you have intuitively used design patterns when building things using your favourite js framework or even good old vanilla js. Chances are you can't explicitly describe those patterns and possibly don't have a deep understanding. This repo is for you or anyone that wants to familiarize themselves with essential design pattern concepts.
## Design Patterns:
- [Constructor Pattern](#constructor-pattern)
- [Module Pattern](#module)
### Constructor Pattern
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

