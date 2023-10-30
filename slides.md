---
theme: dracula
layout: cover
fonts:
  # like font-family in css, you can use `,` to separate multiple fonts for fallback
  serif: 'Metal Mania'
  sans: 'Atkinson Hyperlegible'
  mono: 'Inconsolata' #'Roboto Mono'
  weights: '200,300,400,500,600'
class: font-serif
title: What we do in the Shadows
---

<h1>
    <span>WHAT WE DO IN THE</span>
    <strong>Shadows</strong>
    <small>Bringing legacy apps back to life with web components</small>
</h1>

---

# What are web components?

> Web Components is a suite of different technologies allowing you to create reusable custom elements — with their functionality encapsulated away from the rest of your code — and utilize them in your web apps.

MDN

<v-clicks depth="2">

- <mdi-toy-brick /> custom, reusable HTML elements
- <mdi-cursor-default-click /> structure and behaviour
- <mdi-view-grid /> Consist of four main technologies:
  - Custom Elements
  - Shadow DOM
  - HTML Templates
  - ES Modules

</v-clicks>

<!--
- Web components are a set of web platform APIs that enable the creation of custom, reusable HTML elements.
- They encapsulate both the structure and behaviour of these elements.

-->

---

# Traditional use cases for web components
<v-clicks>

- <mdi-form-textbox /> custom form controls, such as date pickers, input fields, and dropdowns
- <mdi-select-group/> UI components like accordions, modals, and tabs
- <mdi-share-all /> sharing across projects, fostering consistency and reducing redundancy
- <mdi-library-shelves /> web component libraries

</v-clicks>
<!--
- 
- 
- fostering consistency and reducing redundancy.
- provide pre-built elements for various purposes.
-->

---

# How do web components relate to Umbraco?
- <mdi-hand-okay /> Belissima!
- <mdi-umbraco /> The backoffice is built with web components and the UUI web component library
- You can use UUI in Umbraco and outside Umbraco
- <mdi-recycle /> Reuse of markup in the frontend and backoffice

---

# Shadow DOM

- The Shadow DOM is a critical concept in web components, providing encapsulation.
- It enables the creation of isolated DOM subtrees within an element, preventing CSS and JavaScript conflicts.
- Encapsulation ensures that the styling and functionality of a component do not affect or get affected by the surrounding page.
- It's a fundamental feature for building robust and modular web components.

---

# Slots

- Slots are a feature of web components that allow for flexible content distribution.
- They enable you to define insertion points within a component's template where content can be dynamically placed.
- Useful for creating versatile components with customizable content.
- Great for scenarios like buttons with varying labels or cards with different content structures.

```html
<my-web-component>
  <h1>Here's some content nested inside my web component!</h1>
</my-web-component>
```

---

# Lit

- Lit is a lightweight, highly efficient library for building web components.
- It simplifies web component development by providing a small API for reactive data binding, templates, and rendering.
- Lit's lit-html template system offers a performant way to define and update component templates.
- It's a powerful choice for rapidly creating web components with minimal overhead.
- UUI uses Lit
- *Don't use it* for everything. It's really designed for UI libraries
---

# Joe's unusual use-case

- The slots aren't inside the shadow DOM
  ```html
  <my-web-component>
    <p>I'm styled by the parent page as well as by the web component</p>
  </my-web-component>
  ```
- Javascript encapsulation inside the shadow DOM doesn't work when using a framework
  ```js
  document.querySelectorAll('.my-item-inside-shadow-dom') // returns nothing ☹️
  ```


---

# Jasons's unusual use-case