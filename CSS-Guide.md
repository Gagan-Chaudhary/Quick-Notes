# CSS Comprehensive Guide

## 1. CSS Fundamentals

### What is CSS?

CSS (Cascading Style Sheets) is used to style and layout web pages.

### Basic Syntax

```css
selector {
  property: value;
}

/* Example */
body {
  background-color: white;
  color: black;
}
```

### Selectors

- Element Selector: `p { }`
- Class Selector: `.classname { }`
- ID Selector: `#idname { }`
- Attribute Selector: `[attribute] { }`
- Pseudo-classes: `a:hover { }`

## 2. Advanced CSS Techniques

### Flexbox

```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

### Grid Layout

```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```

### CSS Variables

```css
:root {
  --primary-color: #3498db;
  --secondary-color: #2ecc71;
}

.button {
  background-color: var(--primary-color);
}
```

### Media Queries

```css
@media screen and (max-width: 600px) {
  .container {
    flex-direction: column;
  }
}
```

## 3. Interview Questions

1. What is the CSS box model?

   - Content, Padding, Border, Margin

2. Explain specificity

   - Inline > ID > Class > Element selectors

3. What's the difference between `display: none` and `visibility: hidden`?

   - `display: none` removes element from layout
   - `visibility: hidden` keeps space but hides content

4. What are CSS preprocessors?
   - SASS, LESS, Stylus
   - Allow variables, nesting, mixins

## 4. Best Practices

- Use meaningful class names
- Avoid !important
- Use flexbox/grid for layouts
- Optimize performance
- Use CSS variables
- Implement responsive design

## 5. Performance Optimization

- Minimize CSS file size
- Reduce selector complexity
- Use CSS sprites
- Leverage browser caching
- Avoid unnecessary calculations
