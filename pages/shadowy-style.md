---
layout: cover
---
# Encapsulating styles 
Because who doesn't want to run two versions of Bootstrap in parallel?
---

# The problem

<v-clicks depth="2">

- <mdi-bank /> Client has a legacy website
  - <mdi-bootstrap /> Bootstrap 3
  - <mdi-jquery /> jQuery
- <mdi-creation-outline /> Client wants new shiny things
- <mdi-emoticon-sad-outline /> *We* don't want to build new shiny things in Bootstrap 3 and jQuery
- <mdi-arrow-up-bold-hexagon-outline /> Site needs upgrading over time
- <game-icons-resting-vampire /> It's **undead** and **immortal**
</v-clicks>

<!--
  - Client has a legacy website using Bootstrap 3 and jQuery
  - But like many clients, they want new and shiny features
  - As developers, we don't like working with legacy tech to build new things
  - A rebuild is not on the horizon, so we need to drag this site into this decade one phase at a time
-->

---

# The plan

- Rebuild header and footer
- Insert new header and footer into legacy pages
- New pages will be built from scratch, using the new header and footer

<v-click>

So, we need:
- A way to insert new components into the legacy site, without everything breaking
- No *"hacks"* in the new pages

</v-click>


---
layout: two-cols-header
---

# What's wrong with `scoped` styles?

::left::

```css
p {
  color: blue;
  text-decoration: underline;
}
```

```html{0|14|2|2-6|8|8,10|8,10,14|all}
<header>
  <style scoped >
    p {
      color: red;
    }
  </style>

  <p>This text is red and underlined.</p>
  <div>
    <p>Still red and underlined.</p>
  </div>
</header>

<p>This text is blue and underlined.</p>
```

::right::

<v-clicks>

- <mdi-check /> Styles in a scoped stylesheet only affect siblings and below
- <mdi-close /> Inline style only (or `@import`)
- <mdi-close /> Global styles still pollute the scoped component
- <mdi-close /> We don't want Bootstrap 3 styles to affect new Bootstrap 5 components
</v-clicks>
---
class: text-center
---

# But Joe, **shadow DOM** encapsulates styles...

<v-click>

<img src="/dont-say-it.webp" alt="&quot;Don't say it!&quot;" class="h-64 mx-auto"/>

</v-click>
<v-click>

# ...so this should be easy!

</v-click>
<v-click>

Oh, you sweet, innocent child.

</v-click>

---
layout: two-cols-header
---

# Why it isn't easy

::left::

- The slots aren't inside the shadow DOM

```html
<my-web-component>
  <p>I'm styled by the parent page as well as by the web component</p>
</my-web-component>
```
<v-click>

- Javascript encapsulation inside the shadow DOM doesn't work when using a framework

```js{1-2|4-7|8|all}
// returns nothing ☹️
document.querySelectorAll('.my-item-inside-shadow-dom');

// If a framework doesn't know to look in the shadow DOM,
// it doesn't know it has to do this:
document.querySelector('my-web-component')
  .shadowRoot.querySelectorAll('.my-item-inside-shadow-dom');
// Also only works in "open" mode
```

</v-click>

::right::
<v-click>

!["Oops"](/oops.webp)

</v-click>

---
class: text-center
---

# So I did something _horrible_...

<v-clicks>

<p><img src="/now-im-a-wizard.webp" alt="&quot;and now I'm a wizard&quot;" class="h-64 mx-auto"/></p>

# Introducing **`shadowy-style`**!

</v-clicks>


---

```js{1-2|4-9|11|12-13|18-21}
const template = document.createElement('template');
template.innerHTML =`<slot></slot><div id="content"></div>`;

class shadowyStyle extends HTMLElement {
  constructor() {
    super();
    var shadow = this.attachShadow({ mode: 'open' })
    shadow.appendChild(template.content.cloneNode(true));
  }

  connectedCallback() {
    const container = this.shadowRoot.querySelector('#content');
    const children = [...this.childNodes];
    if (children.length > 0 && container) {
      while (container.firstChild) {
        container.removeChild(container.firstChild);
      }
      for (let i = 0; i < children.length; i++) {
        // Move the child nodes to the shadow dom, don't clone it
        container.appendChild(children[i]);
      }
    }

    // ...
```

---

```js{8-17|18-21|24}
    // ...

    // Intercept querySelectorAll calls to add children of this wrapper
    const defaultQuerySelectorAll = Element.prototype.querySelectorAll;
    const defaultDocumentQuerySelectorAll = document.querySelectorAll;
    const shadowyStyle = this;

    Element.prototype.querySelectorAll = function (selector) {
      let result = defaultQuerySelectorAll.call(this, selector);
      if (this.contains(shadowyStyle)) {
        result = [...result].concat([...container.querySelectorAll(selector)]);

        // Add the NodeList items missing from Array
        result.item = (i) => [...result][i] || null;
      }
      return result;
    };
    // Replace all these methods too
    Element.prototype.querySelector = // ...
    document.querySelectorAll = // ...
    document.querySelector = // ...
  }
}
window.customElements.define('shadowy-style', shadowyStyle);
```

---
layout: iframe-left
title: Shadowy Styles Demo
# the web page source
url: https://shadowy-style.joe.gl
---

```html{1-6|7-15|all|0}
<div class="example">
  <div class="thing">
    <h2>Outside</h2>
    <!-- etc... -->
  </div>
</div>

<shadowy-style
  class="example"
  stylesheet="/assets/inner-styles.css">
  <div class="thing">
    <h2>Inside</h2>
    <!-- etc... -->
  </div>
</shadowy-style>
```

- <mdi-link /> [shadowy-style.joe.gl](https://shadowy-style.joe.gl)
- <mdi-github /> [glombek/shadowy-style](https://github.com/glombek/shadowy-style)
- <mdi-npm /> `shadowy-style`