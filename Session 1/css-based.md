### JSON (JavaScript Object Notation) in JavaScript

#### 1. **What is JSON?**

JSON (JavaScript Object Notation) is a lightweight data interchange format that is easy to read and write for humans and easy to parse and generate for machines. It is commonly used for transmitting data between a server and a client in web applications.

#### 2. **JSON Syntax**

JSON is based on JavaScript object syntax but has strict rules:

- Data is in **key-value pairs** (`"key": value`).
- Keys must be **strings** enclosed in double quotes (`""`).
- Values can be:
  - **String** (`"Hello"`)
  - **Number** (`123`)
  - **Boolean** (`true / false`)
  - **Null** (`null`)
  - **Array** (`[1, 2, 3]`)
  - **Object** (`{"name": "John", "age": 30}`)

Example:

```json
{
  "name": "Alice",
  "age": 25,
  "isStudent": false,
  "courses": ["JavaScript", "Node.js"],
  "address": {
    "city": "New York",
    "zip": "10001"
  }
}
```

#### 3. **JSON in JavaScript**

Since JSON is based on JavaScript object syntax, JavaScript provides built-in methods to work with JSON:

##### **Converting JSON to JavaScript Object**

You can convert a JSON string into a JavaScript object using `JSON.parse()`.

```js
const jsonString = '{"name": "Alice", "age": 25}';
const obj = JSON.parse(jsonString);
console.log(obj.name); // Output: Alice
```

##### **Converting JavaScript Object to JSON**

You can convert a JavaScript object into a JSON string using `JSON.stringify()`.

```js
const person = { name: "Alice", age: 25 };
const jsonString = JSON.stringify(person);
console.log(jsonString); // Output: '{"name":"Alice","age":25}'
```

#### 4. **Use Cases of JSON**

- **Storing Configuration Data** (e.g., `config.json`)
- **Exchanging Data Between Client and Server** (APIs)
- **Storing Data in Local Storage**
- **Reading and Writing Files in Node.js** (`fs` module)

### **CSS: Flex, Display, and Units Explained**

### **1. Display Property in CSS**

The `display` property controls how an element is rendered in the layout.

#### **Common Display Values:**

- **`block`**: The element takes up the full width available, starting on a new line.
  ```css
  div {
    display: block;
  }
  ```
- **`inline`**: The element only takes up as much width as necessary and does not start on a new line.
  ```css
  span {
    display: inline;
  }
  ```
- **`inline-block`**: Similar to `inline`, but allows setting width and height.
  ```css
  button {
    display: inline-block;
  }
  ```
- **`none`**: Hides the element completely.
  ```css
  .hidden {
    display: none;
  }
  ```
- **`flex`**: Enables Flexbox layout (explained below).
- **`grid`**: Enables CSS Grid layout.

---

### **2. Flexbox (`display: flex`)**

Flexbox is a CSS layout model that allows you to align elements efficiently.

#### **Basic Usage:**

```css
.container {
  display: flex;
}
```

#### **Flex Properties**

- **`flex-direction`**: Defines the main axis direction.
  - `row` (default) → Left to right
  - `row-reverse` → Right to left
  - `column` → Top to bottom
  - `column-reverse` → Bottom to top
  ```css
  .container {
    display: flex;
    flex-direction: row;
  }
  ```
- **`justify-content`**: Controls horizontal alignment.

  - `flex-start` (default) → Aligns items to the start
  - `flex-end` → Aligns items to the end
  - `center` → Centers items
  - `space-between` → Spaces items evenly with no gap at ends
  - `space-around` → Spaces items evenly with gaps around them

  ```css
  .container {
    justify-content: center;
  }
  ```

- **`align-items`**: Controls vertical alignment.

  - `stretch` (default) → Items stretch to fill container
  - `flex-start` → Aligns items at the top
  - `flex-end` → Aligns items at the bottom
  - `center` → Centers items

  ```css
  .container {
    align-items: center;
  }
  ```

- **`flex-wrap`**: Defines whether items wrap to the next row.
  - `nowrap` (default) → No wrapping
  - `wrap` → Items wrap to the next row when needed
  ```css
  .container {
    flex-wrap: wrap;
  }
  ```

---

### **3. CSS Units**

CSS units define the sizes of elements. They can be **absolute** or **relative**.

#### **Absolute Units**

These have a fixed size, regardless of the screen size.

- `px` → Pixels (e.g., `width: 100px;`)
- `pt` → Points (e.g., `font-size: 12pt;`)
- `cm`, `mm`, `in` → Not commonly used in web development.

#### **Relative Units**

These depend on the parent element or viewport.

- `%` → Percentage relative to parent (`width: 50%;`)
- `em` → Relative to the font size of the parent (`font-size: 2em;` → 2× parent font size)
- `rem` → Relative to the root (`html`) font size (`font-size: 1.5rem;`)
- `vw` / `vh` → Percentage of the viewport width/height (`width: 50vw;` → 50% of screen width)
- `vmin` / `vmax` → Percentage of the smaller/larger viewport dimension.

#### **Example Usage**

```css
.container {
  width: 80vw; /* 80% of viewport width */
  height: 50vh; /* 50% of viewport height */
  font-size: 1.5rem; /* 1.5 times the root font size */
}
```

---

### **Summary**

| Concept   | Description                                                              |
| --------- | ------------------------------------------------------------------------ |
| `display` | Defines how an element is displayed (block, inline, flex, grid, etc.).   |
| `flex`    | A flexible box layout for better alignment and responsiveness.           |
| Units     | Can be absolute (`px`, `cm`) or relative (`%`, `em`, `rem`, `vh`, `vw`). |

Here’s a simple **HTML & CSS example** demonstrating `display`, `flexbox`, and different alignment properties, including `align-content`, `justify-content`, and `align-items`.

### **📌 Features Covered in This Code:**

✔ `display: flex`  
✔ `justify-content` (horizontal alignment)  
✔ `align-items` (vertical alignment for a single row)  
✔ `align-content` (vertical alignment for multiple rows)  
✔ Various CSS units (`px`, `%`, `vh`, `vw`, `rem`)

---

### **🌐 HTML & CSS Code**

#### **HTML (`index.html`)**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Flexbox Example</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <h1>Flexbox Layout Example</h1>

    <div class="container">
      <div class="item">1</div>
      <div class="item">2</div>
      <div class="item">3</div>
      <div class="item">4</div>
      <div class="item">5</div>
      <div class="item">6</div>
    </div>
  </body>
</html>
```

---

#### **CSS (`styles.css`)**

```css
/* General Styles */
body {
  font-family: Arial, sans-serif;
  text-align: center;
  background-color: #f4f4f4;
  margin: 0;
  padding: 0;
}

/* Flexbox Container */
.container {
  display: flex;
  flex-wrap: wrap; /* Enables multiple rows */
  justify-content: space-between; /* Distributes items evenly */
  align-items: center; /* Centers items vertically */
  align-content: center; /* Centers multiple rows */
  background: #ddd;
  height: 60vh; /* 60% of viewport height */
  width: 80vw; /* 80% of viewport width */
  margin: auto;
  padding: 10px;
  border-radius: 10px;
}

/* Flexbox Items */
.item {
  width: 100px;
  height: 100px;
  background: steelblue;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem; /* Relative to root font size */
  border-radius: 8px;
  margin: 5px;
}
```

---

### **🎯 Explanation**

1. **`display: flex`** → Makes the container a flexbox.
2. **`flex-wrap: wrap`** → Allows items to move to a new row if needed.
3. **`justify-content: space-between`** → Distributes items evenly across the row.
4. **`align-items: center`** → Centers items vertically in **a single row**.
5. **`align-content: center`** → Centers multiple rows of items within the container.
6. **`vw`, `vh`, `rem` units** → Used for responsive design.

---

### **📌 Expected Output**

- A **flexbox container** with six blue boxes.
- Items are **evenly spaced horizontally** (`justify-content: space-between`).
- If wrapped to multiple rows, they are **centered vertically** (`align-content: center`).

## **CSS `position` Property Explained**

The `position` property in CSS defines how an element is positioned in a document. It controls how elements are placed relative to their normal flow or relative to other elements.

---

### **1. Types of Positioning**

| Position Type      | Description                                                                                              |
| ------------------ | -------------------------------------------------------------------------------------------------------- |
| `static` (default) | Elements appear in the normal document flow.                                                             |
| `relative`         | Moves the element relative to its normal position.                                                       |
| `absolute`         | Removes the element from the document flow and positions it relative to the nearest positioned ancestor. |
| `fixed`            | Positions the element relative to the viewport (stays in place when scrolling).                          |
| `sticky`           | The element toggles between relative and fixed, based on the scroll position.                            |

---

### **2. Explanation with Examples**

#### **🔹 `position: static` (Default)**

- The element follows the normal flow of the document.
- No effect from `top`, `right`, `bottom`, or `left`.

```css
.box {
  position: static;
}
```

#### **🔹 `position: relative`**

- The element stays in the normal document flow but **moves relative** to itself.
- You can use `top`, `left`, `right`, or `bottom` to shift it.

```css
.box {
  position: relative;
  top: 20px; /* Moves down by 20px */
  left: 10px; /* Moves right by 10px */
}
```

✅ **Still affects nearby elements** since it remains in the document flow.

---

#### **🔹 `position: absolute`**

- The element is **removed** from the normal flow.
- It is positioned relative to the nearest **positioned ancestor** (`relative`, `absolute`, `fixed`).
- If no ancestor is positioned, it is relative to `<html>` (the document).

```css
.parent {
  position: relative;
  width: 300px;
  height: 300px;
  background: lightgray;
}

.child {
  position: absolute;
  top: 50px;
  left: 50px;
  background: steelblue;
  padding: 10px;
}
```

✅ **Does not affect other elements**, as it’s out of the normal document flow.

---

#### **🔹 `position: fixed`**

- The element is positioned **relative to the viewport** (browser window).
- **It stays fixed even when scrolling**.

```css
.fixed-box {
  position: fixed;
  top: 0;
  right: 0;
  background: red;
  color: white;
  padding: 10px;
}
```

✅ **Great for sticky headers, floating buttons, or notifications.**

---

#### **🔹 `position: sticky`**

- Acts like `relative` initially but becomes `fixed` when scrolled past a certain point.
- Useful for **sticky headers or sidebars**.

```css
.sticky-box {
  position: sticky;
  top: 10px; /* Becomes fixed when scrolled 10px */
  background: orange;
  padding: 10px;
}
```

✅ **Hybrid behavior:** Moves normally but sticks after scrolling a certain distance.

---

### **3. Example Code (HTML & CSS)**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CSS Positioning</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 20px;
      }

      .parent {
        position: relative;
        width: 400px;
        height: 300px;
        background: lightgray;
        margin-bottom: 20px;
      }

      .absolute-box {
        position: absolute;
        top: 20px;
        left: 30px;
        background: steelblue;
        color: white;
        padding: 10px;
      }

      .fixed-box {
        position: fixed;
        top: 10px;
        right: 10px;
        background: red;
        color: white;
        padding: 10px;
      }

      .sticky-box {
        position: sticky;
        top: 10px;
        background: orange;
        padding: 10px;
        margin-top: 50px;
      }
    </style>
  </head>
  <body>
    <h1>CSS Positioning Example</h1>

    <div class="parent">
      <p>Parent (Relative Positioning)</p>
      <div class="absolute-box">Absolute Box</div>
    </div>

    <div class="fixed-box">Fixed Box (Always Visible)</div>

    <div class="sticky-box">Sticky Box (Sticks on Scroll)</div>

    <p>Scroll down to see how the sticky element behaves.</p>
    <p style="height: 100vh;">Keep scrolling...</p>
  </body>
</html>
```

---

### **4. When to Use Different `position` Values?**

| Position Type | Use Case                                                                            |
| ------------- | ----------------------------------------------------------------------------------- |
| `static`      | Default, when no positioning is needed.                                             |
| `relative`    | When you need to shift an element without affecting others.                         |
| `absolute`    | When you need an element to be precisely positioned inside a container.             |
| `fixed`       | For elements that should stay visible while scrolling (e.g., navbars, pop-ups).     |
| `sticky`      | When an element should move normally but become fixed after scrolling past a point. |

---

# **📌 Media Queries in CSS**

## **What is a Media Query?**

A **Media Query** in CSS allows you to apply different styles based on **screen size, resolution, or device type**. This is essential for **responsive web design**, making websites adaptable to desktops, tablets, and mobile devices.

---

## **🔹 Basic Syntax of Media Queries**

```css
@media (condition) {
  /* CSS rules to apply */
}
```

For example, to change the background color when the screen width is **less than 600px**:

```css
@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

---

## **🔹 Common Media Query Conditions**

| Property       | Description                                  | Example                              |
| -------------- | -------------------------------------------- | ------------------------------------ |
| `max-width`    | Targets screens **up to** a specific width.  | `@media (max-width: 768px) {}`       |
| `min-width`    | Targets screens **from** a specific width.   | `@media (min-width: 1024px) {}`      |
| `max-height`   | Targets screens **up to** a specific height. | `@media (max-height: 500px) {}`      |
| `min-height`   | Targets screens **from** a specific height.  | `@media (min-height: 700px) {}`      |
| `orientation`  | Targets landscape or portrait mode.          | `@media (orientation: portrait) {}`  |
| `aspect-ratio` | Targets screens based on width/height ratio. | `@media (min-aspect-ratio: 16/9) {}` |

---

## **🔹 Example: Responsive Typography**

```css
body {
  font-size: 16px;
}

@media (max-width: 600px) {
  body {
    font-size: 14px;
  }
}

@media (max-width: 400px) {
  body {
    font-size: 12px;
  }
}
```

📌 **Effect:** The text size **decreases** as the screen gets smaller.

---

## **🔹 Example: Responsive Layout (Grid)**

```css
.container {
  display: flex;
  flex-wrap: wrap;
}

.item {
  width: 50%;
}

/* When screen width is less than 600px, items take full width */
@media (max-width: 600px) {
  .item {
    width: 100%;
  }
}
```

📌 **Effect:** The items **stack on smaller screens**.

---

## **🔹 Media Queries for Common Devices**

### **📱 Mobile-First Responsive Design Approach**

A **mobile-first** approach starts with styles for **small screens** and adds styles for **larger screens** using `min-width`.

```css
/* Default styles for mobile (small screens) */
body {
  font-size: 14px;
}

/* Tablet (Portrait) - 600px and above */
@media (min-width: 600px) {
  body {
    font-size: 16px;
  }
}

/* Laptop - 1024px and above */
@media (min-width: 1024px) {
  body {
    font-size: 18px;
  }
}

/* Large Screens - 1200px and above */
@media (min-width: 1200px) {
  body {
    font-size: 20px;
  }
}
```

---

## **🔹 Media Query for Dark Mode**

```css
@media (prefers-color-scheme: dark) {
  body {
    background-color: black;
    color: white;
  }
}
```

📌 **Effect:** The site **automatically switches** to dark mode if the user's device is set to dark mode.

---

## **🔹 Combining Multiple Conditions**

You can **combine** multiple conditions using **`and`**, **`,` (comma for OR)**.

```css
/* Apply styles for screens between 600px and 1024px */
@media (min-width: 600px) and (max-width: 1024px) {
  body {
    background-color: yellow;
  }
}

/* Apply styles for both small screens and portrait orientation */
@media (max-width: 500px), (orientation: portrait) {
  body {
    background-color: pink;
  }
}
```

📌 **Effect:** The background becomes:

- Yellow for screens **between 600px - 1024px**.
- Pink for screens **smaller than 500px** or when the device is in **portrait mode**.

---

## **🔹 Example: Full Responsive Web Page**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Responsive Page</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        text-align: center;
        padding: 20px;
      }

      .container {
        background-color: lightgray;
        padding: 20px;
        border-radius: 10px;
      }

      /* Mobile */
      @media (max-width: 600px) {
        .container {
          background-color: lightblue;
        }
      }

      /* Tablet */
      @media (min-width: 601px) and (max-width: 1024px) {
        .container {
          background-color: lightgreen;
        }
      }

      /* Desktop */
      @media (min-width: 1025px) {
        .container {
          background-color: lightcoral;
        }
      }
    </style>
  </head>
  <body>
    <h1>Responsive Media Query Example</h1>
    <div class="container">
      Resize the screen to see the background color change!
    </div>
  </body>
</html>
```

📌 **Effect:** The background color of `.container` changes based on screen size.

---
