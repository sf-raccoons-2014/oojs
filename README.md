## Object Oriented JavaScript

### OO Concepts

####Namespace

```JavaScript
// global namespace
// If MYAPP exists, add to it.  Otherwise make a new object
var MYAPP = MYAPP || {
 ...
};
```

####Class

```JavaScript
// Defining a class
var Person = function () { ... };

// Instantiating some new people
var derek = new Person();
var casey = new Person();
```

####Constructor

```JavaScript
var Person = function () {
  // Everything defined here gets executed at the time of instantiation
  // Here we can prepare our object for use
};
```

####Property

```JavaScript
var Person = function (firstName) {
  // Setting the first name property on this instance
  this.firstName = firstName;
};
```

####Method

This adds methods to the prototype.

```JavaScript
Person.prototype.sayHello = function() {
  console.log("Hello, I'm " + this.firstName);
};

var derek = new Person("Derek");
derek.sayHello(); // logs Hello, I'm Derek
```

Here is a cleaner way to add methods to the prototype. This overrides the whole prototype.

```JavaScript
Person.prototype = {
  goForAWalk: function() {
    console.log(this.firstName + "is going for a walk");
  },
  sayGoodbye: function() {
    console.log("Kthxbai");
  }
}
```

We can also use object literal notation to construct new objects

```JavaScript
// object literal notation
student = {
  name: "Masha",
  sayGoodbye: function() {
    console.log("Kthxbai");
  }
}
// student does not need to be instantiated, since we used OLN.
student.name          // Masha
student.sayGoodBye()  // Kthxbai
```

####Inheritance

```JavaScript
// Define the Student constructor
function Student(firstName, subject) {
  // Call the parent constructor, making sure (using Function#call)
  Person.call(firstName);

  // Initialize our Student-specific properties
  this.subject = subject;
};

// Create a Student.prototype object that inherits from Person.prototype.
Student.prototype = Object.create(Person.prototype);

// Set the "constructor" property to refer to Student
Student.prototype.constructor = Student;

// Replace the "sayHello" method
Student.prototype.sayHello = function(){
  console.log("Hello, I'm " + this.firstName + ". I'm studying "
              + this.subject + ".");
};

var derek = new Student("Derek", "Shoes");
derek.firstName;    // Derek
derek.sayHello();   // "Hello, I'm Derek. I'm studying Shoes."

// Check that instanceof works correctly
console.log(derek instanceof Person);  // true
console.log(derek instanceof Student); // true
```


## Resources

- MDN Intro to OOJS: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript

