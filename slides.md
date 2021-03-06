name: inverse

layout: true
class: center, middle, inverse

---

#.red[Taiko]

## Reliable Browser Automation

.footnote[Harmeet Singh
&
Divya Rakhiani]

---

layout: false
class: center,middle
#Not this Taiko

<img src="https://cdn.shopify.com/s/files/1/1242/9508/products/nagado_keyaki_grande_grande_42fda3ee-ee4c-4938-8858-c5300ffe2f30.png?v=1467337836">

---

class: center,middle

## What is it then?

<img src="https://gauge.org/assets/images/blog/gauge_blog_image_introducing_taiko.jpg" width=80%>

---

.left-column[

## What is it?

]

.right-column[

- ## Open source browser automation tool
- ## An npm library
- ## Built on Chrome DevTools API
- ## Free for use

]

---

.left-column[

## What is it?

## Who built it?

]

.right-column[

- ## The team behind Gauge by ThoughtWorks
- ## A growing community

]

---

.left-column[

## What is it?

## Who built it?

## Key features

]

.right-column[

- ## Smart selectors
- ## Ability to handle XHR and dynamic content
- ## Request/Response stubbing and mocking
- ## Interactive Recorder
  ]

---

template: inverse

# Installation

---

layout: false

### Installing globally

```bash
npm install -g taiko
```

### Adding to a javascript project

```bash
npm add taiko --save-dev
```

### or, if using yarn

```bash
yarn add taiko --dev
```

---

### The First Interaction

Launching interactive recorder

```bash
taiko
```

Getting help regarding the APIs

```bash
.api

Browser actions
    openBrowser, closeBrowser, client, switchTo, openTab, closeTab

Page actions
    goto, reload, title, click, doubleClick, rightClick, dragAndDrop

...
```

Getting help on particular function

```bash
.api openBrowser

Launches a browser with a tab.
The browser will be closed when the parent node.js process is closed.

...
```

---

template: inverse

# Features

---

layout: false

### Smart Selectors

Click on a button by its text

```bash
click("Google Search")
```

Write into a field with default focus

```bash
write("taiko test automation")
```

Using proximity

```bash
click(checkbox(near("Username")))
```

Be specific where to element

```bash
write("something", into(textField({placeholder: "Username"})))
```

Using XPaths

```bash
click(checkbox(near("Username")))
```

---

### XHR and Dynamic Content Handling

#### Reduce flackiness by relying on page events rather than explicit waits

Waiting for page to load meaningful content

```bash
goto(`https://pagethatloadsdynamic.com`, {timeout: 10000,

    waitForEvents: ["firstMeaningfulPaint", "firstContentfulPaint"]

  })
```

Other options for events to wait for -

- DOMContentLoaded
- loadEventFired
- networkAlmostIdle
- networkIdle
- firstPaint
- firstContentfulPaint
- firstMeaningfulPaint

---

### Request Stubbing and Mocking

Blocking network requests

```bash
intercept("https://www.google-analytics.com/analytics.js")
```

Redirection

```bash
intercept("https://fetchdata.com", "http://fetchtestdata.com")
```

Stubbing

```bash
intercept("https://fetchdata.com", {"test": data })
```

Request modification

```bash
intercept("https://fetchdata.com", (request) =>
  {request.continue({"custom": "data"})}))
```

---

### Other Interesting Stuff

Geolocation Mocking

```bash
  overridePermissions("https://test.com/geolocation",['geolocation'])

  setLocation({ latitude: 27.1752868, longitude: 78.040009, accuracy:20 })
```

Emulate network

```bash
  emulateNetwork("WiFi")
```

Emulate device

```bash
  emulateDevice('iPhone 6')
```

Set Cookies

```bash
  setCookie("CSRFToken","csrfToken", {url: "http://test.com"})
```

---

### The "Hello World" of Taiko

```bash
openBrowser()

goto("google.com")

write("taiko test automation")

click("Google Search")
```

Getting the recorded code

```bash
.code

const { openBrowser, goto, write, click } = require('taiko');
(async () => {
  try {
    await openBrowser();
    await goto("google.com");
    await write("taiko test automation");
    await click("Google Search");
  } catch (e) {
      console.error(e);
  } finally {
    closeBrowser();
  }
})();
```

---

template: inverse

# Installation with Gauge

---

layout: false
class: middle

.center[
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ4zZb4WyWVIBX14bep8ZEAbt0FjXG3mqc3NSzauV32yXKT-hE6bQ">
]

- ### Free and open source test automation framework by ThoughtWorks
- ### Recommended test runner for Taiko

---

Installing Gauge

```bash
  npm install @getgauge/cli
```

Initializing a Taiko project

```bash
  gauge init js

```

Create a Step Implementation

```bash
  .step("When I search for taiko", async () => {
    try {
      await openBrowser();
      await goto("google.com");
      await write("taiko test automation");
      await click("Google Search");
    } catch (e) {
        console.error(e);
    } finally {
      closeBrowser();
    }
  });
```

---

class: middle, center

# DEMO

---

template: inverse

# Questions???

---
