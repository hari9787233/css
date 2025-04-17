# HTML, CSS & JS Comprehensive Guide

## 1. <picture> Element vs. <img> with srcset

### Theory
The <picture> Element:
- Allows specifying multiple image sources based on media conditions
- Uses <source> elements for different media queries and image types
- Useful for art direction - providing different images or croppings for different viewport sizes

The <img> with srcset:
- Provides responsive images by offering image candidates with descriptors (width or pixel density)
- Browser picks the best-fit image based on inherent image conditions
- Cannot change the "art" or composition of the image

When to Use Each:
- Use <picture> when you need to change the image completely (different cropping or composition) based on viewport size
- Use <img> with srcset when you only need multiple resolutions of the same image

### Code Examples

Using <picture> for art direction:
html
<picture>
  <!-- For wide screens -->
  <source media="(min-width: 800px)" srcset="images/landscape-large.jpg">
  <!-- For smaller screens -->
  <source media="(max-width: 799px)" srcset="images/landscape-small.jpg">
  <!-- Fallback image -->
  <img src="images/landscape-small.jpg" alt="A beautiful landscape">
</picture>


Using <img> with srcset for resolution switching:
html
<img src="images/photo-1x.jpg"
     srcset="images/photo-1x.jpg 1x, images/photo-2x.jpg 2x"
     alt="A descriptive photo">


## 2. defer vs. async Attributes in <script>

### Theory
defer:
- Downloads script while continuing to parse HTML
- Executes script only after parsing is complete
- Scripts marked with defer preserve their execution order
- Ideal for scripts that depend on the full DOM

async:
- Downloads script while parsing HTML
- Executes script as soon as it's available, regardless of HTML parsing progress
- Order of execution is not guaranteed with multiple async scripts
- Best for independent scripts (tracking, analytics) that don't rely on the DOM

### Code Examples
html
<!-- Deferred scripts execute in order after HTML parsing -->
<script src="script1.js" defer></script>
<script src="script2.js" defer></script>

<!-- Async script loads and executes as soon as ready -->
<script src="analytics.js" async></script>


## 3. Web Components: Shadow DOM, Custom Elements, and HTML Templates

### Theory
Web Components are a set of standards for creating reusable custom elements with encapsulated functionality and styling:

Custom Elements:
- Define new HTML tags with custom behavior

Shadow DOM:
- Provides encapsulated DOM and style scoping
- Prevents component styles from leaking out or being affected by global styles

HTML Templates:
- Define markup that isn't rendered until explicitly instantiated
- Ideal for repeating structures and reusable content

### Code Example
html
<!-- Define a template -->
<template id="my-component-template">
  <style>
    .container {
      border: 2px solid #333;
      padding: 1rem;
      background-color: #f9f9f9;
    }
  </style>
  <div class="container">
    <h2>Custom Component</h2>
    <p>This is a reusable web component.</p>
  </div>
</template>

<script>
  // Define a custom element class
  class MyComponent extends HTMLElement {
    constructor() {
      super();
      // Attach a shadow DOM tree to this element.
      const shadow = this.attachShadow({mode: 'open'});
      // Find the template and clone its content.
      const template = document.getElementById('my-component-template');
      const templateContent = template.content.cloneNode(true);
      // Append the cloned template to the shadow root.
      shadow.appendChild(templateContent);
    }
  }
  // Register the custom element.
  customElements.define('my-component', MyComponent);
</script>

<!-- Use the custom element -->
<my-component></my-component>


## 4. <datalist> vs. <select> Dropdown

### Theory
*<datalist>:*
- Works as an autocomplete feature for <input> elements
- Provides suggestions while allowing any value to be entered
- More flexible but with less control

*<select> Dropdown:*
- Displays a closed list of predefined options
- User must choose from the provided options
- More structured and controlled

*Limitations of <datalist>:*
- Limited styling options (browser-dependent appearance)
- No guarantee of enforcing selection from the list
- Inconsistent support for features like grouping

### Code Examples

Using <datalist>:
html
<input list="browsers" name="browser">
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
  <option value="Edge">
</datalist>


Using <select>:
html
<select name="browser">
  <option value="Chrome">Chrome</option>
  <option value="Firefox">Firefox</option>
  <option value="Safari">Safari</option>
  <option value="Edge">Edge</option>
</select>


## 5. Resource Hints: rel="preload", rel="preconnect", and rel="prefetch"

### Theory
preload:
- Instructs browser to load resources as soon as possible
- Used for critical assets like fonts, scripts, or stylesheets
- Prioritizes resources regardless of where they appear in the document

preconnect:
- Establishes early connections (DNS, TCP, TLS) to specified domains
- Reduces latency when resources are later fetched from those domains

prefetch:
- Provides hints about resources that might be needed in the future
- Browser fetches these resources during idle time
- Useful for resources needed for subsequent navigation

### Code Examples
html
<!-- Preload critical stylesheet -->
<link rel="preload" href="styles/critical.css" as="style">
<link rel="stylesheet" href="styles/critical.css">

<!-- Preconnect to a third-party domain -->
<link rel="preconnect" href="https://api.example.com">

<!-- Prefetch resources for next page -->
<link rel="prefetch" href="next-page-content.html">


## 6. The contenteditable Attribute and Creating a Rich-Text Editor

### Theory
contenteditable:
- Makes an element editable in the browser
- Users can modify content directly on the page

Rich-text editor creation:
- Combine contenteditable with JavaScript toolbars for formatting
- Use document.execCommand() or modern libraries for editing functions

### Code Example
html
<!-- Editable div for rich text -->
<div id="editor" contenteditable="true" style="border: 1px solid #ccc; padding: 10px;">
  <p>Edit this content...</p>
</div>

<!-- Simple toolbar using buttons -->
<button onclick="document.execCommand('bold')">Bold</button>
<button onclick="document.execCommand('italic')">Italic</button>
<button onclick="document.execCommand('underline')">Underline</button>


## 7. <details> and <summary> Elements

### Theory
Usage:
- <details> creates an interactive widget users can open and close
- <summary> provides a visible heading for the details section

Accessibility Considerations:
- Ensure <summary> text is descriptive
- Keyboard accessibility is built-in (Enter/Space to toggle)
- Screen readers announce when a section is expandable

### Code Example
html
<details>
  <summary>More Information</summary>
  <p>Here is the additional content that can be toggled by the user.</p>
</details>


## 8. ARIA Attributes: aria-label, aria-labelledby, and aria-describedby

### Theory
aria-label:
- Provides an invisible label where a visible text label isn't present
- Useful for icons or complex controls

aria-labelledby:
- References the ID of another element that provides a label
- Used when the label is visible elsewhere in the DOM

aria-describedby:
- Identifies elements that describe the object
- Helpful for extra context, instructions, or error messages

Usage Guidelines:
- Use aria-label for simple, standalone labels
- Use aria-labelledby when you already have an associated element acting as a label
- Use aria-describedby for additional explanatory text

### Code Example
html
<!-- Using aria-label -->
<button aria-label="Close" onclick="closeModal()">X</button>

<!-- Using aria-labelledby -->
<label id="usernameLabel" for="username">Username:</label>
<input id="username" type="text" aria-labelledby="usernameLabel">

<!-- Using aria-describedby -->
<input id="email" type="email" aria-describedby="emailHint">
<small id="emailHint">We will not share your email.</small>


## 9. The sandbox Attribute in <iframe>

### Theory
Purpose:
- Adds security restrictions on content rendered inside an <iframe>
- Disables features like form submission, script execution, and same-origin access unless explicitly allowed

Secure Embedding of Third-Party Content:
- Apply the sandbox attribute with appropriate flags to limit what third-party content can do
- Reduces risk of malicious behavior

### Code Example
html
<iframe src="https://trusted-thirdparty.com"
        sandbox="allow-scripts allow-same-origin"
        width="600"
        height="400"
        title="Embedded Third Party Content">
</iframe>


## 10. Animated Portfolio Website

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shreyas - Student Porfolio</title>
   <link rel="preconnect" href="https://fonts.google.com/specimen/Poppins">
   <link rel="preconnect" href="https://fonts.google.com/specimen/Playfair+Display">
    <style>
        * {
            margin: 0px;
            padding: 0px;
        }

        body {
            background-color: rgb(0, 0, 33);
            color: azure;
            font-family: 'Poppins', sans-serif;
        }
        nav{
            display:flex;
            justify-content:space-around;
            align-items:center;
            height:80px;
            background-color:rgb(1, 1, 51) ;
        }
        nav ul{
            display:flex;
            justify-content:center;
        }
        nav ul li{
           list-style:none;
           margin: 0 23px;
        }
        nav ul li a{
            text-decoration: none;
            color:white;
        }
        nav ul li a:hover{
          color:rgb(168, 125, 237);
          font-size:1.01rem;
        }
        main hr{
            border:0;
            background:#9c97f1;
            height:1.2px;
            margin:40px 84px;
        }

      
        .left{
            font-size:1.5rem;
        }
        .firstSection{
            display:flex;
            justify-content:space-around;
            margin:10px 0;
        }
        .firstSection > div{
            width:42%;
            
        }
        .leftsection{
            font-size: 2.7rem;
            margin:50px 0;
        }
        .leftsection .buttons{
            padding:50px 0;
        }
        .leftsection .btn{
            padding:12px;
            background:#1e2167;
            color:white;
            border:2px solid white;
            border-radius:6px;
            font-size:20px;
            cursor:pointer;
        }
        .rightsection img{
            width:80%; 
        }
        .purple{
            color:rgb(141, 75, 203);
        }
        .text-gray{
            color:gray;
        }
        #element{
            color:blueviolet;
        }
        .secondSection{
            max-width:80vw;
            margin:auto;
            height:80vh;
        }
        .secondSection h1{
            font-size:1.9rem;
        }
        .secondSection .box {
            background:white;
            width:80vw;
            height:2px;
            margin:56px 0;
            display:flex;
        }
        .secondSection .vertical{
            height:93px;
            width:1px;
            background-color:white;
            margin:0 100px; 
        }
        .image-top{
            width:23px;
            position: relative;
            top:-32px;
            left:-9px;
        }
        .vertical-title{
            position: relative;
            top:75px;
            width:150px;
            font-size: 14px;
        }
        .vertical-desc{
            position: relative;
            top:86px;
            color: grey;
            width: 150px;
            font-size: 9px;

        }
        footer{
            background-color:#0e0e1a;
          

        }
        .footer{
            display:flex;
            padding:23px 122px;
            justify-content:space-evenly ;
        }
        .footer ul{
            list-style:none;
        }
        .footer > div{
            width: 100px;
        }
        
        footer .footer-rights{
            text-align:center;
            color:gray;
            padding:12px 0;
        }
    </style>
</head>

<body>
    <header>
        <nav>
            <div class="left">Shreyas Porfolio</div>
            <div class="right">
                <ul>
                    <li><a href="/">Home</a></li>
                    <li><a href="/">About</a></li>
                    <li><a href="/">Certificates</a></li>
                    <li><a href="/">Projects</a></li>
                    <li><a href="/">Contact Me</a></li>

                </ul>
            </div>
        </nav>
    </header>
    <main>
        <section class="firstSection">
            <div class="leftsection">
                Hi, My name is <span class="purple">Shreyas</span>
                <div>and I am a Student of Sanjivani University </div>
                <span id="element"></span>
                <div class="buttons">
                    <button class="btn">Download Resume</button>
                    <button class="btn">Visit Github</button>
                </div>
            </div>
            <div class="rightsection">
                <img src="https://png.pngtree.com/png-vector/20240312/ourmid/pngtree-smart-college-student-using-computer-at-home-he-is-studying-and-png-image_11716756.png">
               
            </div>
        </section>
        <hr>
        <section class="secondSection">
            <span class="text-gray">What I have done so far</span>
            <h1>Skills</h1>
            <div class="box">
            <div class="vertical">
                <img class="image-top" src="htmlcss3.png" alt="">
                <div class="vertical-title">
                    HTML CSS Developer
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div>
            <div class="vertical">
                <img class="image-top" src="python.png" alt="">
                <div class="vertical-title">
                  Basics Python Coding
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div> <div class="vertical">
                <img class="image-top" src="javascript.png" alt="">
                <div class="vertical-title">
                   Basics Javascript Coding
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div> 
            <div class="vertical">
                <img class="image-top" src="C++.png" alt="">
                <div class="vertical-title">
                    Basics C++ Coding(DSA)
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div>
            <div class="vertical">
                <img class="image-top" src="developer1.png" alt="">
                <div class="vertical-title">
                   UI/UX Designer(Figma)
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div>
         
        </section>
    </main>
    <footer>
        <div class="footer">
            <div class="footer-first">
                Shreyas Kulat Portfolio
            </div>
            <div class="footer-second">
            <ul>
                <li>Home</li>
                <li>About</li>
                <li>Project</li>
                <li>Contact</li>
            </ul>
            </div>
            <div class="footer-third">
            <ul>
                <li>Home</li>
                <li>About</li>
                <li>Project</li>
                <li>Contact</li>
            </ul>
            </div>
            <div class="footer-fourth">
            <ul>
                <li>Home</li>
                <li>About</li>
                <li>Project</li>
                <li>Contact</li>
            </ul>
            </div>
        </div>
            <div class="footer-rights">
                Copyright &#169;.shreyasportfolio.com | All rights reserved
            </div>
        
    </footer>
    <script src="https://unpkg.com/typed.js@2.1.0/dist/typed.umd.js"></script>
    <script>
        var typed = new Typed('#element', {
          strings: ['Studying in CSE', 'Specilization in AIML'],
          typeSpeed: 50,
        });
      </script>
</body>

</html>,
