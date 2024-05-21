
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
