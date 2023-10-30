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
layout: two-cols-header
---

::left::

<img src="https://cdn.masto.host/umbracocommunitysocial/accounts/avatars/110/588/702/497/186/405/original/6c6676aa9fee4f41.jpg" class="aspect-square h-30 rounded-full mb-2" />

# Jason Elkin

- <mdi-briefcase-variant /> Full-stack web developer at Bump
- <mdi-human-greeting-proximity /> Meetup organiser*
- <mdi-trophy /> 2x Umbraco MVP
- <material-symbols-family-restroom /> 2x Daddy
- <mdi-cross /> Methodist local preacher

<br />

- <mdi-dev-to /> [dev.to/JasonElkin](https://dev.to/jasonelkin)
- <mdi-mastodon /> [@jason@umbracocommunity.social](https://umbracocommunity.social/@jason)
- <mdi-linkedin /> [linkedin.com/in/jason-elkin](https://www.linkedin.com/in/jason-elkin/)
- <ri-twitter-x-fill /> [@JasonElkin86](https://x.com/JasonElkin86)

::right::

<img src="https://cdn.masto.host/umbracocommunitysocial/accounts/avatars/110/588/598/848/640/615/original/a65ff91f10010cf8.png" class="aspect-square h-30 rounded-full mb-2" />

# Joe Glombek

- <mdi-briefcase-variant /> Full-stack web developer at Bump
- <mdi-human-greeting-proximity /> umBristol meetup organiser
- <mdi-trophy /> 3x Umbraco MVP
- <mdi-dog /> Dog owner
- <game-icons-wood-canoe /> Canoe instructor

<br />

- <material-symbols-rss-feed /> [joe.gl/ombek](https://joe.gl/ombek)
- <mdi-mastodon /> [@joe@umbracocommunity.social](https://umbracocommunity.social/@joe)
- <mdi-linkedin /> [linkedin.com/in/glombek](https://www.linkedin.com/in/glombek/)

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

<div class="flex items-start">
  <div>

  - Lit is a lightweight, highly efficient library for building web components.
  - It simplifies web component development by providing a small API for reactive data binding, templates, and rendering.
  - Lit's lit-html template system offers a performant way to define and update component templates.
  - It's a powerful choice for rapidly creating web components with minimal overhead.
  - UUI uses Lit
  - _Don't use it_ for everything. It's really designed for UI libraries

  <div class="mt-10">

  <mdi-link/> [lit.dev](https://lit.dev/)

  </div>
  </div>
  <img src="/lit.svg" class="m-10 w-70"/>
</div>

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
  document.querySelectorAll('.my-item-inside-shadow-dom'); // returns nothing ☹️
  ```

---

# Jasons's unusual use-case

---
layout: two-cols-header
---

# Thank you

Please stay in touch, ask questions and look at the repos.

::left::

<img src="https://cdn.masto.host/umbracocommunitysocial/accounts/avatars/110/588/702/497/186/405/original/6c6676aa9fee4f41.jpg" class="aspect-square h-30 rounded-full mb-2" />

## Jason Elkin

- <mdi-github /> [JasonElkin/maximum-markdown](https://github.com/JasonElkin/maximum-markdown)

<br />

- <mdi-dev-to /> [dev.to/JasonElkin](https://dev.to/jasonelkin)
- <mdi-mastodon /> [@jason@umbracocommunity.social](https://umbracocommunity.social/@jason)
- <mdi-linkedin /> [linkedin.com/in/jason-elkin](https://www.linkedin.com/in/jason-elkin/)
- <ri-twitter-x-fill /> [@JasonElkin86](https://x.com/JasonElkin86)

::right::

<img src="https://cdn.masto.host/umbracocommunitysocial/accounts/avatars/110/588/598/848/640/615/original/a65ff91f10010cf8.png" class="aspect-square h-30 rounded-full mb-2" />

## Joe Glombek

- <mdi-github /> [glombek/shadowy-style](https://github.com/glombek/shadowy-style)

<br />

- <material-symbols-rss-feed /> [joe.gl/ombek](https://joe.gl/ombek)
- <mdi-mastodon /> [@joe@umbracocommunity.social](https://umbracocommunity.social/@joe)
- <mdi-linkedin /> [linkedin.com/in/glombek](https://www.linkedin.com/in/glombek/)

