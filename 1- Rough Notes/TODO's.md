

# HTML & CSS

## HTML
HTML (HyperText Markup Language) is used to describe the structure of a webpage.

### HTML5 Tags
- **ol, ul, li**: Ordered and unordered lists.
- **img**: Self-closing tag for images.
  ```html
  <img src="cat.jpg" alt="cat" width="300px">



- Controls width and scales height proportionally.
- **a**: Anchor tag for hyperlinks.
- **table**: Used for tabular data.
    - **thead**: Table header.
    - **th**: Table header cell.
    - **tbody**: Table body.
    - **tr**: Table row.
    - **td**: Table data cell.

### Forms

Forms are used to collect user input.
<form>
  <input type="text" placeholder="Full Name" name="name">
  <input type="submit">
</form>

- **input**: Various types of input fields.
    - Text: `<input name="name" placeholder="userid" type="text">`
    - Password: `<input name="name" placeholder="password" type="password">`
    - Radio buttons: `<input name="color" type="radio" value="red"> Red`
- **datalist**: Dropdown list with filtering options.

## CSS

CSS (Cascading Style Sheets) is used to style the webpage.

### Inline Styling
<h1 style="color: blue;">Welcome to my web page</h1>

### External CSS

Move style code to a separate CSS file and link it in the head section.

### Common CSS Properties

- **background-color**
- **width**: `200px`
- **height**: `400px`
- **padding**: Adds space inside the element.
	- padding: 20px;
- **margin**: Adds space outside the element.
	- margin: 20px;

- **font**: Specify multiple fonts for fallback.
    - `font-family`, `font-weight`, `font-size`, `border`
- **table**: `border`, `border-collapse`, `padding`

### CSS Selectors

- **id**: Unique identifier for an element.
- #id { color: red; }

**class**: Name for multiple elements.
.class { color: red; }

### CSS Specificity

Order of precedence: inline > id > class > type

### Pseudoclass Selector

Used for actions/feedback, e.g., hover effect.

button:hover { background-color:  orange; }

## Responsive Design

Support for various devices and screen sizes.

### Viewport
<meta name="viewport" content="width=device-width, initial-scale=1.0">

### Media Queries

Control page appearance based on screen size.

@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}

### Flexbox and Grids

Used for layout adjustments based on screen size.

### Bootstrap

CSS framework for responsive design.

- **Bootstrap Column Model**: Divides the page into 12 columns.
    
    <div class="col-lg-3 col-sm-6"></div>