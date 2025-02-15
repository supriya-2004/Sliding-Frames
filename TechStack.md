# 🛠️ Tech Stack Overview

This document provides an in-depth explanation of the technologies and elements used in the **Expanding Cards** project.

## 🌐 HTML – Structure of the Webpage
The project is built using **HTML5**, which defines the structure of the expanding card interface.

### Key HTML Elements:
- `<!DOCTYPE html>` – Declares the document type as HTML5.
  
- `<html lang="en">` – Defines the document language as English.
- `<head>` – Contains metadata and external CSS/JS file links.
  - `<meta charset="UTF-8">` – Ensures character encoding supports all characters.
  - `<meta name="viewport" content="width=device-width, initial-scale=1.0">` – Makes the page responsive.
  - `<link rel="stylesheet" href="ec.css">` – Links the external CSS file.
  - `<title>Expanding Cards</title>` – Sets the title of the webpage.
- `<body>` – Contains all visible content.
  - `<div class="container">` – A wrapper that holds all panels.
  - Multiple `<div class="panel">` elements with `background-image` for different cards.
  - `<h3>` inside panels to display titles.
  - `<script src="ec.js"></script>` – Links the JavaScript file for interactivity.

---

## 🎨 CSS – Styling and Animations
The project uses **CSS3** to style and animate the expanding cards, ensuring a modern and interactive UI.

### Key CSS Properties:
- `@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');`  
  - Imports the **Poppins** font for better typography.
    
- `* { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Poppins', sans-serif; }`  
  - Resets default margins and paddings for consistency.
- `body` – Uses `flexbox` to center the content on the page.
- `.container` – A flex container that holds all the cards.
- `.panel` – Represents individual cards with:
  - `background-size: cover;` – Ensures the image fills the panel.
  - `border-radius: 15px;` – Gives rounded corners.
  - `cursor: pointer;` – Indicates interactivity.
  - `transition: flex 0.7s ease-in;` – Enables smooth expansion animation.
- `.panel.active` – Expands the selected card by setting `flex: 5;`.
- `.panel h3` – The text overlay:
  - Initially **hidden** using `opacity: 0;`.
  - Becomes **visible** when active with `opacity: 1;` and a delay effect.
- `.panel:hover { transform: scale(1.05); }` – Adds a hover effect for better UI.
- `@media (max-width: 480px)` – Ensures responsiveness by hiding extra panels on smaller screens.

---

## ⚡ JavaScript

### 1. Selecting Panels
```js
const panels = document.querySelectorAll(".panel");
```
#### Purpose:
- Selects all elements with the class `.panel` from the HTML document.
- Stores them in a `NodeList` called `panels`.

#### Usage:
- `document.querySelectorAll()` selects multiple elements matching the CSS selector.
- `.panel` is the class selector for targeting panel elements.
- The result is stored in the constant variable `panels`.

### 2. Looping Through Panels
```js
panels.forEach((panel) => { ... });
```
#### Purpose:
- Iterates over each panel element to attach a click event listener.

#### Usage:
- `forEach()` loops through each element in `NodeList`.
- The arrow function `(panel) => { ... }` specifies actions for each panel.
- 
### 3. Adding Click Event Listener
```js
panel.addEventListener("click", () => { ... });
```
#### Purpose:
- Attaches a `click` event handler to each panel.

#### Usage:
- `addEventListener()` registers an event listener.
- `"click"` is the event type.
- The arrow function defines actions when clicked.

### 4. Removing Active Classes
```js
removeActiveClasses();
```
#### Purpose:
- Ensures that only one panel remains active at a time.

#### Usage:
- Calls a function that removes the `"active"` class from all panels.

### 5. Adding Active Class
```js
panel.classList.add("active");
```
#### Purpose:
- Adds the `"active"` class to the clicked panel.

#### Usage:
- `classList.add()` adds the `"active"` class.
- `"active"` likely triggers expanded styles via CSS.

### 6. Defining `removeActiveClasses` Function
```js
const removeActiveClasses = () => { ... };
```
#### Purpose:
- Defines a reusable function to remove `"active"` class from all panels.

#### Usage:
- Uses arrow function syntax.
- No parameters needed as it uses `panels` from the outer scope.

### 7. Removing Active Class from All Panels
```js
panels.forEach((panel) => { panel.classList.remove("active"); });
```
#### Purpose:
- Loops through all panels and removes the `"active"` class.

#### Usage:
- `forEach()` iterates over each panel.
- `classList.remove("active")` removes the `"active"` class.
- Ensures only one panel remains active at a time.

### How It Works Together
1. Selects all `.panel` elements.
2. Attaches a `click` event listener to each.
3. When a panel is clicked:
   - Removes `"active"` from all panels.
   - Adds `"active"` to the clicked panel.
4. Ensures only one panel is active at a time, creating a toggle effect.
