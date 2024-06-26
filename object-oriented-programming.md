
# Object-Oriented Programming

* Definition:
    • OOP is a design pattern that helps break down large, complex problems into simpler, manageable parts
    • It groups related data and behaviours into a single entity called an object

* Key Concepts:
    • __Object__: an item with properties (attributes) and methods (actions)
    • __Properties (Attributes)__: Characteristics of the object (e.g. bodyColor, inkColor)
    • __Methods__: Actions the object can perform (e.g. write, refillInk)

* Advantages of OOP:
    • Improves code readability and maintainability
    • Allows parts of the code to be implemented and tested seperately

* Real-World Analogy:
    • Think of a car factory where each part (fan, motor) is an object, built and tested seperately
    • These parts combine to form subsystems (air conditioning) and eventually the whole vehicle

* Example - Pen API:
    • Properties:
        - bodyColor
        - inkColor
        - inkLevel
        - type (gel, fountain, rollerball)

    • Methods:
        - write
        - refillInk

* Design Principles:
    • No single perfect way to design an API. Iteration and adaptation are key
    • The goal is to create readable, maintainable API that can be easily integrated with others (e.g. Pen and Pencil APIs used by a Person API)

* Benefits of OOP:
    • Breaks down bigger problems into smaller, simpler problems
    • Makes code more readable, testable and maintainable

* Key Takeaway:
    • OOP is a valuable approach for managing complexity in software development
    • It's a skill that improves with practice and experience


# Encapsulation

* Definition:
    • Encapsulation is the practice of hiding the complexity of an object's behaviour and data behind an API
    • It encloses the details within a "black box," so users don't need to understand the inner workings to use it

* Key concepts:
    • __API__: Interface for interacting with the object's data and behaviours without revealing internal implementation
    • __Public vs. Private__:
        - Public: Accessible by other objects
        - Private: Only accessible within its own object

* Examples:

    1. Making Pasta:
        • Steps: Boil water, add pasta, drain pasta
        • Hidden Details: How to boil water (fill pot, heat, wait)

    2. Vending Machine:
        • Steps: Authorise payment, make selection, retreive item
        • Hidden Complexity: Payment processing, item delivery mechanisms

* Benefits:
    • Simplifies user interaction
    • Protects internal data and methods
    • Improves code maintainability and readability

* Classes and Instances:
    • __Class__: Blueprint for creating objects, defining properties (attributes) and methods (behaviours)
        - Example: __`class Computer { ... }`__

    • __Instance__: Specific object created from a class
        - Example: __`let myComputer = new Computer()`__

* Constructor:
    • Special method in a class that sets up initial properties or actions when an instance is created

* Classes vs. JavaScript Objects:
    • Class: Definition of an object, specifying its properties and methods
    • Instance: Use of that object, created from the class
    • POJO (Plain Old JavaScript Object): Simple data structure with key-value pairs

* Key Takeaway:
    • Encapsulation groups data and behaviours, hiding complexity to create a more manageable and maintainable code base
    • Classes define the structure and behaviour of objects, while instances are specific uses of those objects



# Creating a Class, Instance Methods, and Variables in JavaScript

* Introduction to OOP in JavaScript:
    • JavaScript supports Object-Oriented Programming (OOP)
    • OOP involves defining custom object classes beyond built-in ones like `object` and `array`

* Key Concepts:
    1. __Class Definition__:
        • Defines attributes and behaviour for an object type
        • Syntax: __`class ClassName { ... }`__

    2. __Constructor Method__:
        • Special method using the `constructor` keyword
        • Initialises properties of the class

        • Example:
        ```js
        class Book {
            Constructor(title, series, author) {
                this.title = title;
                this.series = series;
                this.author = author;
            }
        }
        ```

    3. __Instantiating a Class__:
        • Use the `new` keyword to create an instance
        • Example:
        ```js
        const fellowshipOfTheRing = new Book(
            `The Fellowship of the Ring`,
            `The Lord of the Rings`,
            `J.R.R. Tolkein`
        );
        console.log(fellowshipOfTheRing);
        ```


    * Instance Methods:
        • Methods are functions defined within a class
        • Invoked on specific instances of the class
        • Syntax: Method name followed by parentheses and curly braces

        • Example:
        ```js
        class Book {
            constructor(title, series, author) {
                this.title = title;
                this.series = series;
                this.author = author;
            }

            getInformation() {
                return `${this.title} by ${this.author}`;
            }
        }

        const fellowshipOfTheRing = new Book(
            `The Fellowship of the Ring`,
            `The Lord of the Rings`.
            `J.R.R. Tolkein`
        );

        console.log(fellowshipOfTheRing.getInformation());
        ```

    * Using `instanceof` Operator:
        • Checks if an object is an instance of a specific class
        • Syntax: __`object instanceof ClassName`__

        • Example:

        ```js
        console.log(fellowshipOfTheRing instanceof book); // true
        ```

* Common Bugs with Classes:
    1. Incorrect use of `function` keyword inside a class
    2. Forgetting to use `this` keyword to access properties within methods
    3. Returning values explicitly from a constructor method, which breaks the expected behaviour

* What I've Learned:
    • Define a class using ES6 syntac with a constructor method
    • Define instance methods and variables
    • Create an instance using the `new` keyword
    • Call instance methods on an instance
    • Check if an object is an instance of a class using the `instanceof` operator
    • Debug common issues with classes in JavaScript



# Static Methods and Variables

* Key Concepts:
    • __Static Methods__: Methods called on the class itself, not on instances
    • __Static Variables__: Variables shared across all instances, accessed via the class

* Differences from Instance Counterparts:
    • __Instance Methods__: called on individual instances
    • __Instance Variables__: Unique to each instance

* How to Declare:
    • Static Methods: Use the `static` keyword before the method name
    • Static Variables: Use the `static` keyword before the variable name

* Static Methods
    • Definition: Perform actions that relate to the class, not to a specific instance
    • Usage: Utility functions, operations on groups of instances

    Example:
    ```js
    class Book {
        constructor(title, series, author) {
            this.title = title;
            this.series = series;
            this.author = author;
        }

        // Instance method
        getInformation() {
            return `${this.title} by ${this.author}`;
        }

        // Static method
        static getTitles(...books) {
            return books.map(book => book.title);
        }
    }

    const book1 = new Book('The Fellowship of the Ring', 'The Lord of the Rings', 'J.R.R. Tolkien');
    const book2 = new Book('The Two Towers', 'The Lord of the Rings', 'J.R.R. Tolkien');
    console.log(Book.getTitles(book1, book2)); // Output: The Fellowship of the Ring, The Two Towers
    ```

* Static Variables
    • Definition: Variables not tied to any specific instance, shared across all instances
    • Usage: Cache data, configuration settings

    Example:
    ```js
    class Book {
        constructor(title, series, author) {
            this.title = title;
            this.series = series;
            this.author = author;
            Book.numBooks += 1;
        }

        // Static variable
        static numBooks = 0;
    }

    const book1 = new Book('The Fellowship of the Ring', 'The Lord of the Rings', 'J.R.R. Tolkien');
    const book2 = new Book('The Two Towers', 'The Lord of the Rings', 'J.R.R. Tolkien');
    console.log(Book.numBooks); // Output: 2
    ```

* Summary
    • Static Methods: Use `static` keyword, called on the class
    • Static Variables: Use `static` keyword, shared across instances
    • Common Uses: Utility functions, operations on multiple instances, caching, configuration


# Inheritance

* Definition: Inheritance allows a class (child) to inherit properties and methods from another class (parent), similar to biological inheritance.

* Key Concepts:
    1. Interface vs. Implementation:

        • Interface: How other code interacts with the class (the "what")
        • Implementation: How the class performs its functions (the "how")
        • Example: An interface for 'Car' might state that Porsche "is a" car

    2. Implementation Inheritance:

        • Properties and methods of the parent class are available to the child class
        • Example: A 'WritingInstrument' class can be a parent to 'Pencil' and 'Pen' classes, sharing common properties like 'material', 'bodyColor', and methods like 'write'

    3. Single vs. Multiple Inheritance:

        • Single Inheritance: A class inherits from one parent class
        • Multiple Inheritance: A class inherits from multiple parent classes (not supported by JavaScript)
        • Example: 'Pencil' can inherit from both 'WritingInstrument' and 'Eraser' classes in languages that support multiple inheritance

* Summary:
    • Inheritance: Enables classes to gain behaviour and data from parent classes
    • Single Inheritance: JavaScript supports this, where a child class inherits from one parent
    • Multiple Inheritance: Not supported in JavaScript but allows a class to inherit from multiple parents in some languages


# Inheritance Class Syntax in JavaScript

* Key Concepts:

    1. Extending an Existing Class:
        • Use `extends` keyword to inherit from a parent class
        • Example:
        ```js
        class MyClass extends Object {}
        class MyChildClass extends MyClass {}
        ```

    2. Inheriting Methods:
        • Child classes inherit methods from parent classes
        • Example:
        ```js
        class Animal {
            constructor(name, sound) {
                this.name = name;
                this.sound = sound;
            }

            speak() {
                console.log(this.sound);
            }
            static pet(animal) {
                console.log(`You attempt to pet ${animal.name}`);
            }
        }

        class Dog extends Animal {}

        const fluffy = new Dog('Fluffy', 'woof');
        fluffy.speak(); // woof
        Dog.pet(fluffy); // You attempt to pet Fluffy
        ```

    3. Using __`super`__ Function:
        • Call the parent class constructor from the child class constructor
        • Example
        ```js
        class Dog extends Animal {
            constructor(name) {
                super(name, 'woof');
            }
        }

        const fluffy = new Dog('Fluffy');
        fluffy.speak(); // woof
        Dog.pet(fluffy); // You attempt to pet Fluffy
        ```
        • __`super`__ ensures adherence to the DRY (Don't Repeat Yourself) principle

* Summary:
    • Extending Classes: Use `extends` to make a child class inherit from a parent class
    • Inherited Methods: Child classes can use methods from their parent classes
    • Super Function: use `super` in child constructors to call the parent class constructor, maintaining code simplicity and adherence to the DRY principle


# Polymorphism

Definition: Polymorphism, derived from the Greek words for "many shapes",refers to the ability of different objects to be processed through a common interface. In OOP, this means that a single function or method can operate on different data types or classes.

* Types of Polymorphism

    1. Function Overloading
        • Multiple functions share the same name but differ in the type or number of parameters

        • Example:
        ```py
        def sum(number1, number2):
            return number1 + number2

        def sum(listOfNumbers):
            total = 0
            for num in listOfNumbers:
                total += num
            return total
        ```
        • Here, `sum` is overloaded to handle both individual numbers and lists of numbers

    2. Function Overriding
        • A child class provides its own implementation of a method inherited from a parent class
        • Focus is typically more on overriding than overloading

* Polymorphism in Practice

    • Built-in Example in JavaScript
        - All objects in JavaScript inherit from the `object` class, which has a `toString()` method
        - Different objects can have their own `toString()` implementations:

        ```js
        console.log([1, 2, 3].toString()); // '1, 2, 3'
        console.log("some text".toString()); // 'some text'
        console.log(new Date().toString()); // 'current date and time'
        console.log(new Object().toString()); // '[object Object]'
        ```
        • Objects use their specific `toString()` method, demonstrating polymorphism

* Customising Methods
    • If the default `toString()` method is not useful, you can override it in your own classes

* Conceptual Example
    • Consider different types of writing instruments with erasers:
        - Eraser: A base class for erasing mistakes
        - WritingInstrument: Inherits from Eraser
        - Pen and Pencil: Inherit from WritingInstrument, and thus can erase
        - CalligraphyPen: Inherits from Pen but overrides the `erase` method to use white-out
    • This demonstrates polymorphism as different classes implement the `erase()` method in various ways to achieve the same result

* Key Takeaways
    • Polymorphism allows methods to be used interchangeably across different classes
    • Function Overloading and Function Overriding are two primary types of polymorphism
    • Overriding is more commonly discussed and involves changing the implementation of an inherited method


# Overriding a Method in a Parent Class in JS

* Concept of Method Overriding
    • Polymorphism: A child class overrides a method of its parent class to provide a specific implementation
    • Objective: Achieve the same result using different implementations

* How to Override a Method
    • Create a method in the child class with the same name as the parent method you want to override

    Example: Overriding `speak` method
    ```js
    class Animal {
        constructor(name, sound) {
            this.name = name;
            this.sound = sound;
        }

        speak() {
            console.log(this.sound);
        }
    }

    class Dog extends Animal {
        speak() {
            console.log('bark bark');
        }
    }

    const fluffy = new Dog('Fluffy', 'woof');
    fluffy.speak(); // Output: bark bark
    ```

    Implementing Polymorphism and Inheritance

    ```js
    class Charity {}

    class Business {
        toString() { return 'Give us your money.'; }
    }

    class Restaurant extends Business {
        toString() { return 'Eat at Joe\'s!'; }
    }

    class AutoRepairShop extends Business {}

    class Retail extends Business {
        toString() { return 'Buy some stuff!'; }
    }

    class ClothingStore extends Retail {}

    class PhoneStore extends Retail {
        toString() { 'Upgrade your perfectly good phone, now!; }
    }

    console.log(new PhoneStore().toString()); // Output: Upgrade your perfectly good phonem now!
    console.log(new ClothingStore().toString()); // Output: Buy some stuff!
    console.log(new Restaurant().toString); // Eat at Joe's!
    console.log(new AutoRepairShop().toString()); // Output: Give us your money.
    console.log(new Charity().toString()); // Output: [object object]
    ```

* Key Points
    • Polymorphism via Overriding:
        - `PhoneStore` and `Restaurant` override the `toString()` method
        - They provide specific messages: "Upgrade your perfectly good phone, now!" and "Eat at Joe's!" respectively

    • Inheritance Chain:
        - `AutoRepairShop` and `ClothingStore` inherit and use their parent class' `toString()` method
        - `Charity` relies on the default `toString()` from `Object`, printing "[object Object]"

* Practical Tips
    • Typing Practice: Type code examples manually to practice syntax and reinforce learning
    • Using `super`: To override a method and still call the parent method, use `super.methodName()` in the child class method

* Summary
    • Overriding methods in JavaScript allows child classes to provide specific implementations of methods defined in parent classes
    • This is a core aspect of polymorphism in object-oriented programming
