# Joe's unusual use-case

## Why

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
layout: image-right
image: now-im-a-wizard.webp
---

# So I did something _horrible_...

---

Something else

---
layout: iframe

# the web page source
url: https://shadowy-style.joe.gl
---
