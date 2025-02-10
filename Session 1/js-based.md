### **Functions and Scope in JavaScript**

---

## **1. Functions in JavaScript**

A **function** in JavaScript is a reusable block of code designed to perform a specific task. Functions help in code reusability and modularity.

### **Types of Functions in JavaScript**

1. **Function Declaration (Named Function)**

   ```js
   function greet(name) {
     return `Hello, ${name}!`;
   }
   console.log(greet("Alice")); // Output: Hello, Alice!
   ```

2. **Function Expression (Anonymous Function)**

   ```js
   const greet = function (name) {
     return `Hello, ${name}!`;
   };
   console.log(greet("Bob")); // Output: Hello, Bob!
   ```

3. **Arrow Function (ES6+)**

   ```js
   const greet = (name) => `Hello, ${name}!`;
   console.log(greet("Charlie")); // Output: Hello, Charlie!
   ```

4. **Immediately Invoked Function Expression (IIFE)**
   ```js
   (function () {
     console.log("This function runs immediately!");
   })();
   ```

---

## **2. Scope in JavaScript**

Scope determines the **visibility and accessibility** of variables in JavaScript.

### **Types of Scope**

1. **Global Scope**

   - Variables declared outside any function are in the global scope and accessible anywhere.

   ```js
   let globalVar = "I am global!";
   function show() {
     console.log(globalVar); // Accessible here
   }
   show();
   console.log(globalVar); // Accessible here too
   ```

2. **Function Scope**

   - Variables declared inside a function are accessible **only within** that function.

   ```js
   function example() {
     let localVar = "I am inside a function";
     console.log(localVar); // Accessible here
   }
   example();
   console.log(localVar); // ❌ Error: localVar is not defined
   ```

3. **Block Scope (let & const - ES6+)**

   - Variables declared using `let` or `const` inside `{}` are only accessible inside that block.

   ```js
   {
     let blockScoped = "I exist only inside this block";
     console.log(blockScoped); // ✅ Works here
   }
   console.log(blockScoped); // ❌ Error: blockScoped is not defined
   ```

4. **Lexical Scope (Closures)**
   - Inner functions can access variables from their outer functions.
   ```js
   function outer() {
     let outerVar = "I am from outer";
     function inner() {
       console.log(outerVar); // ✅ Accessible due to lexical scope
     }
     inner();
   }
   outer();
   ```

### **Hoisting in Functions & Scope**

- **Function declarations** are hoisted, meaning they can be called before they are defined.
- **Function expressions** and **arrow functions** are **not hoisted**.

```js
console.log(foo()); // ✅ Works due to hoisting
function foo() {
  return "Hello!";
}

// console.log(bar()); ❌ Error: Cannot access 'bar' before initialization
const bar = () => "Hi!";
```

---

## **Conclusion**

- **Functions** help organize and reuse code efficiently.
- **Scope** controls variable accessibility, with `var` having function scope and `let`/`const` having block scope.
- **Lexical Scope & Closures** allow inner functions to access outer variables.
- **Hoisting** allows function declarations to be called before definition but not function expressions.

### **Closures in JavaScript** 🔥

A **closure** in JavaScript is when a function "remembers" the variables from its outer scope even after the outer function has finished executing. This happens because JavaScript uses **lexical scoping**—functions have access to variables defined in their parent scope.

---

## **🔹 Understanding Closures with an Example**

```js
function outerFunction(outerVariable) {
  return function innerFunction(innerVariable) {
    console.log(`Outer: ${outerVariable}, Inner: ${innerVariable}`);
  };
}

const closureExample = outerFunction("Hello");
closureExample("World"); // Output: Outer: Hello, Inner: World
```

✅ The `innerFunction` still remembers `outerVariable` **even after `outerFunction` has finished executing**.

---

## **🔹 Practical Use Cases of Closures**

### **1️⃣ Data Privacy (Encapsulation)**

Closures help **create private variables** that cannot be accessed from outside the function.

```js
function counter() {
  let count = 0; // Private variable
  return {
    increment: function () {
      count++;
      console.log(`Count: ${count}`);
    },
    decrement: function () {
      count--;
      console.log(`Count: ${count}`);
    },
  };
}

const myCounter = counter();
myCounter.increment(); // Count: 1
myCounter.increment(); // Count: 2
myCounter.decrement(); // Count: 1

// console.log(count); ❌ Error: count is not accessible directly
```

---

### **2️⃣ Function Factories**

Closures can be used to create functions with **preset values**.

```js
function multiplier(factor) {
  return function (num) {
    return num * factor;
  };
}

const double = multiplier(2);
console.log(double(5)); // Output: 10

const triple = multiplier(3);
console.log(triple(5)); // Output: 15
```

✅ `double` and `triple` functions "remember" their `factor` value.

---

### **3️⃣ Maintaining State in Callbacks**

Closures are useful in **event listeners** and **callbacks**.

```js
function createButton(label) {
  let count = 0;
  const button = document.createElement("button");
  button.innerText = `${label} (Clicked: ${count})`;

  button.addEventListener("click", function () {
    count++;
    button.innerText = `${label} (Clicked: ${count})`;
  });

  document.body.appendChild(button);
}

createButton("Click Me");
```

✅ Each button **maintains its own count**, thanks to closures.

---

### **🔹 Key Takeaways**

- **Closures occur when an inner function "remembers" variables from its outer function.**
- They **help create private variables**, function factories, and stateful callbacks.
- Common use cases include **encapsulation, memoization, and event handling**.

## **DOM Manipulation in JavaScript** 🏗️

### **🔹 What is the DOM?**

The **DOM (Document Object Model)** is a programming interface for web documents. It represents the HTML structure of a webpage as a tree of objects that JavaScript can manipulate.

👉 With **DOM Manipulation**, we can dynamically change the content, structure, and styles of a webpage.

---

## **1️⃣ Selecting Elements in the DOM**

To manipulate the DOM, we first need to **select** elements.

### **📌 Methods to Select Elements**

| Method                                     | Description                                                           | Example                                  |
| ------------------------------------------ | --------------------------------------------------------------------- | ---------------------------------------- |
| `document.getElementById("id")`            | Selects an element by ID                                              | `document.getElementById("myDiv")`       |
| `document.getElementsByClassName("class")` | Selects elements by class name (returns a collection)                 | `document.getElementsByClassName("btn")` |
| `document.getElementsByTagName("tag")`     | Selects elements by tag name (returns a collection)                   | `document.getElementsByTagName("p")`     |
| `document.querySelector("selector")`       | Selects the **first** element matching a CSS selector                 | `document.querySelector(".box")`         |
| `document.querySelectorAll("selector")`    | Selects **all** elements matching a CSS selector (returns a NodeList) | `document.querySelectorAll("li")`        |

### **🛠 Example**

```js
const heading = document.getElementById("title");
const allParagraphs = document.querySelectorAll("p");

console.log(heading.textContent); // Logs the text inside the element with id "title"
console.log(allParagraphs.length); // Logs number of <p> elements
```

---

## **2️⃣ Modifying Elements in the DOM**

Once selected, elements can be modified.

### **📌 Changing Content**

| Property/Method                         | Description                 | Example                                 |
| --------------------------------------- | --------------------------- | --------------------------------------- |
| `element.textContent`                   | Changes text (ignores HTML) | `el.textContent = "New Text"`           |
| `element.innerHTML`                     | Changes text (parses HTML)  | `el.innerHTML = "<b>Bold Text</b>"`     |
| `element.setAttribute("attr", "value")` | Sets an attribute           | `el.setAttribute("class", "new-class")` |
| `element.getAttribute("attr")`          | Gets an attribute value     | `el.getAttribute("href")`               |

### **🛠 Example**

```js
const title = document.getElementById("title");
title.textContent = "New Title!"; // Changes text
title.style.color = "red"; // Changes color
title.setAttribute("class", "highlight"); // Adds a class
```

---

## **3️⃣ Adding and Removing Elements**

### **📌 Creating Elements**

```js
const newDiv = document.createElement("div");
newDiv.textContent = "I am a new div!";
document.body.appendChild(newDiv); // Adds newDiv to the end of <body>
```

### **📌 Removing Elements**

```js
const removeMe = document.getElementById("oldElement");
removeMe.remove(); // Removes the element
```

---

## **4️⃣ Event Handling in the DOM**

### **📌 Adding Event Listeners**

```js
const button = document.querySelector("button");

button.addEventListener("click", function () {
  alert("Button clicked!");
});
```

✅ When the button is clicked, an alert pops up.

### **📌 Removing Event Listeners**

```js
function sayHello() {
  console.log("Hello!");
}

button.addEventListener("click", sayHello);
button.removeEventListener("click", sayHello); // Removes the event listener
```

---

## **5️⃣ Manipulating CSS with JavaScript**

### **📌 Changing Styles Directly**

```js
const box = document.querySelector(".box");
box.style.backgroundColor = "blue";
box.style.padding = "20px";
```

### **📌 Adding & Removing CSS Classes**

```js
const element = document.getElementById("myElement");
element.classList.add("new-class"); // Adds a class
element.classList.remove("old-class"); // Removes a class
element.classList.toggle("active"); // Toggles a class
```

---

## **6️⃣ Traversing the DOM**

We can move **between** elements using parent-child relationships.

| Property                 | Description              |
| ------------------------ | ------------------------ |
| `parentElement`          | Gets the parent element  |
| `children`               | Gets all child elements  |
| `firstElementChild`      | First child element      |
| `lastElementChild`       | Last child element       |
| `nextElementSibling`     | Next sibling element     |
| `previousElementSibling` | Previous sibling element |

### **🛠 Example**

```js
const parent = document.getElementById("container");
console.log(parent.children); // Logs all child elements
console.log(parent.firstElementChild); // Logs first child element
console.log(parent.lastElementChild); // Logs last child element
```

---

## **🔹 Example: Creating a Dynamic List**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>DOM Manipulation</title>
  </head>
  <body>
    <ul id="myList">
      <li>Item 1</li>
      <li>Item 2</li>
    </ul>
    <button id="addBtn">Add Item</button>

    <script>
      const list = document.getElementById("myList");
      const button = document.getElementById("addBtn");

      button.addEventListener("click", function () {
        const newItem = document.createElement("li");
        newItem.textContent = "New Item";
        list.appendChild(newItem);
      });
    </script>
  </body>
</html>
```

✅ Clicking the button dynamically **adds a new list item**.

````


## **Prototype in JavaScript** 🔥

In JavaScript, **prototypes** are the foundation of inheritance. Every object in JavaScript has a **prototype**, which is another object that it inherits properties and methods from.

---

## **1️⃣ What is Prototype?**
- Every JavaScript function has a **prototype property**, which is an object.
- When you create an object using a **constructor function**, the object automatically gets access to the properties and methods defined on the constructor’s `prototype`.

---

## **2️⃣ Understanding Prototype with an Example**
```js
function Person(name, age) {
    this.name = name;
    this.age = age;
}

// Adding a method to the prototype
Person.prototype.greet = function () {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

// Creating objects
const person1 = new Person("Alice", 25);
const person2 = new Person("Bob", 30);

person1.greet(); // Output: Hello, my name is Alice and I am 25 years old.
person2.greet(); // Output: Hello, my name is Bob and I am 30 years old.
````

✅ Both `person1` and `person2` **share** the same `greet` method from the prototype instead of each object having its own copy.

---

## **3️⃣ Prototype Chain**

When we try to access a property or method on an object:

1. JavaScript first looks for the property on the object itself.
2. If not found, it looks up the **prototype chain** to its parent (i.e., `Object.prototype`).

```js
console.log(person1.hasOwnProperty("name")); // ✅ true (exists on the object)
console.log(person1.hasOwnProperty("greet")); // ❌ false (exists on the prototype)
```

👉 Since `greet` is defined on `Person.prototype`, it’s not a direct property of `person1`.

---

## **4️⃣ Modifying Built-in Prototypes**

JavaScript allows modification of built-in prototypes (not recommended but useful sometimes).

```js
Array.prototype.customMethod = function () {
  return "Custom method added!";
};

const arr = [1, 2, 3];
console.log(arr.customMethod()); // Output: Custom method added!
```

⚠️ **Warning:** Modifying built-in prototypes like `Array.prototype` or `Object.prototype` can lead to unexpected behavior in your code.

---

## **5️⃣ Prototypal Inheritance**

We can create a prototype chain to inherit properties.

```js
function Animal(name) {
  this.name = name;
}

Animal.prototype.makeSound = function () {
  console.log(`${this.name} makes a sound`);
};

// Dog "inherits" from Animal
function Dog(name, breed) {
  Animal.call(this, name);
  this.breed = breed;
}

// Linking prototypes
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.bark = function () {
  console.log(`${this.name} barks!`);
};

const dog1 = new Dog("Buddy", "Golden Retriever");
dog1.makeSound(); // Output: Buddy makes a sound
dog1.bark(); // Output: Buddy barks!
```

✅ Here, `Dog` inherits from `Animal` using `Object.create(Animal.prototype)`, making `makeSound` available to `Dog` objects.

---

## **6️⃣ Class-Based Inheritance (ES6)**

ES6 introduced **`class` syntax**, which is a cleaner way to work with prototypes.

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, I am ${this.name}`);
  }
}

// Inheriting from Person
class Developer extends Person {
  constructor(name, age, language) {
    super(name, age);
    this.language = language;
  }

  code() {
    console.log(`${this.name} codes in ${this.language}`);
  }
}

const dev = new Developer("Alice", 28, "JavaScript");
dev.greet(); // Output: Hello, I am Alice
dev.code(); // Output: Alice codes in JavaScript
```

✅ This is **syntactic sugar** over the prototype-based approach.

---

## **🎯 Summary**

- **Every JavaScript object has a prototype**, which allows inheritance.
- **Prototype Chain** enables objects to inherit properties/methods from parent objects.
- **Modifying prototypes** can extend behavior, but modifying built-in prototypes is risky.
- **Prototypal inheritance** allows objects to inherit methods from other objects.
- **ES6 Classes** provide a cleaner syntax for working with prototypes.

---

Do you want a **deep dive** into prototype chaining or performance optimizations? 🚀
