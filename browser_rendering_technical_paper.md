# How does a browser render HTML, CSS, JS to DOM? What is the mechanism behind it?
A browser renders HTML, CSS, and JavaScript into a visual webpage through a series of steps involving the construction of the **Document Object Model (DOM)**, the **CSS Object Model (CSSOM)**, and the render tree, followed by layout and painting.

## 1. Parsing HTML and Building the DOM:
- The browser receives HTML data from the server.
- It then **parses this HTML, converting the raw text into a series of tokens** (representing tags, attributes, and content).
- These tokens are used to construct a tree-like data structure called the Document Object Model (DOM). Each HTML element becomes a node in this tree, with parent-child relationships reflecting the document's structure.

## 2. Parsing CSS and Building the CSSOM:
- While the DOM is being built, the browser also processes CSS (from external stylesheets, `<style>` tags, or inline styles).
- It **parses the CSS rules and creates another tree-like structure called the CSS Object Model (CSSOM).** This tree contains all the style information for the elements in the DOM.

## 3. Executing JavaScript:
- When the browser encounters a `<script>` tag, it typically **pauses the DOM construction process until the JavaScript file is fetched, parsed, and executed.**
- This is because JavaScript can dynamically modify both the DOM and the CSSOM. The browser ensures that the DOM and CSSOM are stable before executing scripts.
- Attributes like `async` or `defer` can be used to alter this behavior, allowing the browser to continue parsing the HTML while the script is downloaded in the background.

## 4. Constructing the Render Tree:
- The browser **combines the DOM and CSSOM** to create the Render Tree.
- The Render Tree contains only the elements that will be rendered visually on the page (e.g., `<head>` and `<script>` elements are not included as they are not directly rendered).
- Each node in the Render Tree includes its visual properties derived from the CSSOM.

## 5. Layout (Reflow):
- After the Render Tree is constructed, the browser performs a "layout" or "reflow" step.
- In this phase, the browser **calculates the precise size and position of each element** in the Render Tree within the viewport. This involves determining dimensions, margins, padding, and positioning based on the CSS rules and the natural flow of the document.

## 6. Painting:
- The final step is "painting."
- The browser traverses the Render Tree and uses the **calculated layout information** to **draw the individual pixels of each element onto the screen.** This includes applying colors, borders, text, images, and other visual styles.

<br>

This sequence transforms your code into the interactive visual experience you see when you visit a website. Changes to styles or the DOM after the initial render can trigger a recalculation of styles, layout, and painting (known as reflows and repaints), which can impact performance.

## References
[1] https://medium.com/jspoint/how-the-browser-renders-a-web-page-dom-cssom-and-rendering-df10531c9969

[2] https://www.browserstack.com/guide/dom-in-web-development