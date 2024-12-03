# HTML Comprehensive Guide

## 1. HTML Basics

### What is HTML?

HTML (HyperText Markup Language) is the standard markup language for creating web pages. It defines the structure and content of web documents.

### Basic Structure

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Page Title</title>
  </head>
  <body>
    <!-- Content goes here -->
  </body>
</html>
```

### Essential Tags

- `<h1>` to `<h6>`: Headings
- `<p>`: Paragraphs
- `<div>`: Division or section
- `<span>`: Inline container
- `<a>`: Hyperlinks
- `<img>`: Images
- `<ul>`, `<ol>`, `<li>`: Lists
- `<table>`, `<tr>`, `<td>`: Tables

## 2. Advanced HTML Concepts

### Semantic HTML

Semantic tags provide meaning to the content:

- `<header>`
- `<nav>`
- `<main>`
- `<article>`
- `<section>`
- `<aside>`
- `<footer>`

### Forms and Input Types

```html
<form action="/submit" method="post">
  <input type="text" name="username" />
  <input type="email" name="email" />
  <input type="password" name="password" />
  <select name="country">
    <option value="usa">USA</option>
    <option value="canada">Canada</option>
  </select>
  <textarea name="message"></textarea>
  <input type="submit" value="Submit" />
</form>
```

### HTML5 Multimedia

```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
</audio>

<video controls>
  <source src="video.mp4" type="video/mp4" />
</video>
```

## 3. Interview Questions

1. What's the difference between `<div>` and `<span>`?

   - `<div>` is a block-level element
   - `<span>` is an inline element

2. Explain the purpose of DOCTYPE declaration

   - Tells the browser which HTML version is being used
   - Ensures proper rendering and validation

3. What are data attributes?

```html
<div data-user-id="123" data-role="admin">User Information</div>
```

4. Explain the difference between `href` and `src`
   - `href` (hypertext reference) links to external resources
   - `src` (source) embeds external content

## 4. Best Practices

- Use lowercase tag names
- Always close tags
- Use meaningful class and ID names
- Validate your HTML
- Optimize for accessibility
- Use semantic tags

## 5. Performance Optimization

- Minimize HTTP requests
- Use async and defer for scripts
- Optimize images
- Use lazy loading
- Implement proper caching
