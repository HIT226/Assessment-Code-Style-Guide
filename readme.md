# Code Guidelines

Following this list of code practices and guidelines will be assessable as part of assignment 1a and 1b.

These guidelines are mostly a derivative of [GitHub's code guidelines](http://primercss.io/guidelines/). You don't have to agree with all of these, but for assignment 1a and 1b, you **will be marked** on your *ability to follow them*.

## HTML

- Paragraphs of text should be placed inside `<p>` tags, never use multiple `<br>` tags.
- Items in list form should always be in `<ul>`, `<ol>`, or `<dl>`. Never use a set of `<div>` or `<p>`.
- Every form input that has text attached should utilize a `<label>` tag. Especially **radio or checkbox elements.**
- Even though quotes around attributes is optional, always put quotes around attributes for readability.
- Avoid trailing slashes in self-closing elements. For example, `<br>`, `<hr>`,` <img>`, and `<input>`
  - i.e.: Don't do this: `<br />` or `<hr />`

### Lean markup

Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. For example:

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

### Tables
Make use of `<thead>`, `<tfoot>`, `<tbody>`, and `<th>` tags (and `scope` attribute) when appropriate.

```html
<table summary="This is a chart of invoices for 2011.">
  <thead>
    <tr>
      <th scope="col">Table header 1</th>
      <th scope="col">Table header 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Table data 1</td>
      <td>Table data 2</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>Table footer 1</td>
      <td>Table footer 2</td>
    </tr>
  </tfoot>
</table>
```

## CSS

### Spacing

- Put spaces after `:` in property declarations.
- Put spaces before `{` in rule declarations.
- Put line breaks between rulesets.
- When grouping selectors, keep individual selectors to a single line.
- Place closing braces of declaration blocks on a new line.
- Each declaration should appear on its own line for more accurate error reporting.

```css
.example__one,
.example__two p {
  font-size: 18px;
  line-height: 1.3;
}

.example__three{
  font-family: sans-serif;
}
```

### Formatting

- Avoid specifying units for zero values, e.g., `margin: 0;` instead of `margin: 0px;`
- Strive to limit use of shorthand declarations to instances where you must explicitly set all the available values.

### Selectors

- Use BEM style class names
  - Classes grouped into Blocks eg: `.nav`
  - Individual items defined as elements eg: `.nav__link`
  - and optionally assigned modifiers eg: `.nav__link--current`
  - Selectors for each group of classes should live in their own file inside `css/lib` and be added to `main.css` via an `@import`
    - i.e.: all `.nav` styles live in `css/lib/nav.css`
- Spaces in class names should be replaced with a single underscore `_` eg: `.example_block`
- As a rule of thumb, avoid unnecessary long selectors. At most, aim for three levels. If you cannot help it, step back and rethink your overall strategy (either the specificity needed, or the layout of the nesting).

### Examples

```css
// Example of good basic formatting practices
.style_guide__example {
  color: #000;
  background-color: rgba(0, 0, 0, .5);
  border: 1px solid #0f0;
}

// Example of individual selectors getting their own lines (for error reporting)
.style_guide,
.style_guide__element,
.style_guide__another_element {
  display: block;
}

// Avoid unnecessary shorthand declarations
.not_so_good {
  margin: 0 0 20px;
}
.good--modifier {
  margin-bottom: 20px;
}
```

## File organisation

- Group related files into folders.
- Folders plus additional `index.html` files may be used to create friendly URLs
  - This is not required, you can have all of your `html` files in the Project root and simply name them differently

```
Project root
├─ index.html
├─ css
|  ├─ main.css
|  ├─ lib
|  |  └─ nav.css
|  └─ vendor
|     └─ normalize.css
├─ js
|  ├─ main.js
|  └─ vendor
|     └─ modernizr.js
├─ images
|  └─ sample.jpg
├─ about
|  ├─ index.html
|  └─ history
|     └─ index.html
└─ References
   └─ index.html
```

## Libraries and plugins

You may find that a library, plugin, or framework you wish to use has class naming conventions or markup standards which does not adhere to this guide, that is fine.

Style sheets inside of `css/vendor` are assumed to be external libraries or frameworks and will not be held to these standards

Markup tied to frameworks, libraries, or JS plugins will not be penalised for differing from these standards. For example CSS Start Grid does not follow the class naming convention covered here.
