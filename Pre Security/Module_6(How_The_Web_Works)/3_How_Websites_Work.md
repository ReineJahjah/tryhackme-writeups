# Room: How Websites Work

**Path:** Web Fundamentals

**Date:** August 2026

**Difficulty:** Easy

---

## Objective

Understand how websites are built and delivered to users, and build the foundational security mindset needed before tackling web vulnerabilities. The room covers client-server communication, HTML, JavaScript, sensitive data exposure, and HTML injection — with the underlying theme that most web attacks exploit misunderstandings between client-side and server-side behavior.

---

## Key Concepts

* **Client-Server Model:** The browser (client) sends requests to a web server, which responds with data the browser renders.
* **Front End (Client-Side):** Runs in the user's browser — HTML, CSS, JavaScript. Visible and modifiable by anyone, including attackers.
* **Back End (Server-Side):** Runs on the server — handles requests, processes logic, talks to databases, sends responses.
* **HTML:** Defines a webpage's structure and content.
* **JavaScript:** Adds interactivity and dynamic logic to a webpage.
* **Sensitive Data Exposure:** Leaking sensitive information (credentials, keys, URLs) in client-visible code.
* **HTML Injection:** Unsanitised user input being rendered and interpreted as HTML by the browser.

---

# Task 1: How Websites Work

When you visit a website, your browser (client) sends a request to a web server asking for information about a specific page. The server responds with data that your browser uses to render the website visually.

A web server is simply a dedicated computer somewhere in the world that listens for requests and responds with data.

## Core Components of a Website

A website is made up of two main parts.

### Front End (Client-Side)

* Runs inside the user's browser
* Responsible for what the user sees and interacts with
* Built using HTML, CSS, and JavaScript

### Back End (Server-Side)

* Runs on the server
* Handles requests
* Processes logic
* Communicates with databases
* Sends responses back to the client

## Security Insight

Anything running on the client-side can be seen, modified, and abused by attackers.

## Question

**Q) What term best describes the component of a web application rendered by your browser?**
A) Front End

---

# Task 2: HTML

## What Is HTML?

Websites are primarily created using:

* **HTML** – Defines structure and content
* **CSS** – Controls visual appearance
* **JavaScript** – Adds interactivity and logic

HTML (HyperText Markup Language) is the foundation of every website. It tells the browser what content exists and how it should be structured.

## Basic HTML Structure

Every HTML page follows a standard structure:

* `<!DOCTYPE html>` – Declares HTML5
* `<html>` – Root element
* `<head>` – Metadata (title, scripts, styles)
* `<body>` – Visible content

Common elements include `<h1>` (headings), `<p>` (paragraphs), `<button>` (buttons), and `<img>` (images).

## HTML Attributes

Elements can include attributes:

* `class` – Used for styling multiple elements
* `id` – Unique identifier for JavaScript or CSS
* `src` – Specifies resource location (images, scripts)

**Example:**

```html
<p class="bold-text" id="example">Hello</p>
<img src="img/cat.jpg">
```

## Security Insight

Viewing page source reveals everything written in HTML.

## Practical Interaction

* Rendered custom HTML
* Fixed broken image paths
* Injected additional image elements

## Questions

**Q) Hidden text after fixing broken image:**
A) `HTMLHERO`

**Q) Text inside dog image:**
A) `DOGHTML`

---

# Task 3: JavaScript

## What Is JavaScript?

JavaScript (JS) allows websites to become interactive and dynamic.

**Without JavaScript:** Websites are static, with no real-time updates or interaction.

**With JavaScript:** Buttons react to clicks, content updates dynamically, and animations/logic execute in real time.

## JavaScript in Action

JavaScript can modify HTML elements dynamically:

```javascript
document.getElementById("demo").innerHTML = "Hack the Planet";
```

HTML elements can also trigger JavaScript using events:

```html
<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>
  Click Me!
</button>
```

## Security Insight

JavaScript runs in the browser — attackers can manipulate it.

## Question

**Q) What text is displayed after modifying the JavaScript?**
A) `JSISFUN`

---

# Task 4: Sensitive Data Exposure

## What Is Sensitive Data Exposure?

Sensitive Data Exposure occurs when a website leaks sensitive information in its frontend code.

Common examples include:

* Hardcoded passwords
* API keys
* Admin URLs
* Test credentials
* Hidden comments

Because HTML and JavaScript are visible to users, attackers often inspect the source code first.

## Why This Is Dangerous

Attackers can discover credentials, access restricted areas, escalate privileges, and move deeper into the application.

## Attacker Mindset

Always check the page source before attacking anything else.

## Question

**Q) What password is hidden in the page source?**
A) `testpasswd`

---

# Task 5: HTML Injection

## What Is HTML Injection?

HTML Injection happens when:

* User input is not sanitised
* Input is directly rendered on the page
* The browser interprets it as HTML

This allows attackers to inject malicious content, modify page structure, insert external links, and potentially escalate to XSS.

## Why This Happens

Developers trust user input, fail to strip HTML tags, and directly inject input into the DOM.

## Golden Rule

Never trust user input.

## Practical Exploitation

Injected a malicious HTML link:

```html
<a href="http://hacker.com">Click Me</a>
```

## Question

**Q) What is the challenge flag after HTML injection?**
A) `HTML_INJ3CTI0N`

---

# Task 6: Conclusion

## Key Takeaways

* Websites rely on client-server communication.
* Frontend code is not secure.
* HTML defines structure.
* JavaScript adds logic and interactivity.
* Sensitive data should never be exposed client-side.
* Unsanitised input leads to injection vulnerabilities.

Understanding how websites work is essential for web exploitation, bug bounty hunting, OWASP Top 10 analysis, secure web development, and defensive security reviews.

---

# Key Terminology

* **Client-Server Model:** The browser (client) requests data; the web server responds with it.
* **Front End:** The client-side portion of a website (HTML, CSS, JavaScript) — visible and modifiable by users/attackers.
* **Back End:** The server-side portion of a website — handles logic, data, and requests.
* **HTML:** Defines a webpage's structure and content.
* **HTML Attribute:** Extra data on an HTML element, e.g. `class`, `id`, `src`.
* **JavaScript:** Adds interactivity and dynamic behavior to a webpage.
* **DOM (Document Object Model):** The in-browser representation of a page's HTML that JavaScript can read/modify.
* **Sensitive Data Exposure:** Leaking secrets (passwords, API keys, admin URLs) in client-visible code.
* **HTML Injection:** Rendering unsanitised user input as HTML, allowing content/structure manipulation.
* **XSS (Cross-Site Scripting):** A more severe escalation of injection where attacker-supplied script executes in the browser.

---

# Key Takeaways

* Every website interaction is fundamentally a **client-server** exchange: the browser requests, the server responds.
* The **front end** (HTML/CSS/JavaScript) is fully visible and modifiable by the user — nothing there should ever be trusted as secure or secret.
* **HTML** defines structure and content; its attributes (`class`, `id`, `src`) connect elements to styling, scripting, and resources.
* **JavaScript** makes pages interactive by modifying the DOM in real time, but because it runs client-side, it can also be inspected and manipulated by attackers.
* **Sensitive Data Exposure** happens when secrets leak into client-visible code — checking page source is often an attacker's first move.
* **HTML Injection** arises from unsanitised, directly-rendered user input, and can escalate toward more serious vulnerabilities like XSS.
* The golden rule underlying all of this: **never trust user input**, and never assume client-side code is hidden from attackers.

---

## What I Learned

This room built the core mental model I'll need before diving into actual web vulnerabilities: that a website is really just a conversation between a client (browser) and a server, and that everything happening on the client side is fundamentally visible and untrustworthy from a security standpoint. That single insight — "anything running on the client-side can be seen, modified, and abused" — ties together almost every task in this room.

Working through HTML reinforced that structure and content are literally sitting in the page source for anyone to read, which is exactly how I found the hidden text (`HTMLHERO`) after fixing a broken image path and the text inside the injected dog image (`DOGHTML`). It made "view source" feel like a genuinely useful first step rather than just a curiosity.

JavaScript showed me how much power actually lives client-side — being able to directly modify the DOM (`document.getElementById(...).innerHTML = ...`) and trigger that through simple HTML events like `onclick` made it obvious why JavaScript is both what makes modern websites interactive and also a prime target for manipulation, since I could just edit it myself to get `JSISFUN`.

The Sensitive Data Exposure task was the most eye-opening — finding a password (`testpasswd`) just sitting in the page source drove home why "check the source first" is basically an attacker's default instinct. It's a very avoidable mistake, but clearly still a common one.

Finally, HTML Injection connected directly back to the "never trust user input" principle. Injecting a raw `<a href="...">` link and having the browser render it as an actual clickable element (earning the flag `HTML_INJ3CTI0N`) made it concrete that failing to sanitise input doesn't just cause visual bugs — it hands an attacker control over part of the page, and is a direct stepping stone toward more serious issues like XSS. This room gave me a solid, practical foundation before moving into deeper web exploitation topics.