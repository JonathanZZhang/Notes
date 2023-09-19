# HTML 5 
## Style Guide

1. Always declare the document type as the first line in your document:
   ```html
   <!DOCTYPE html>
   ```
2. Always use **lower case** in the following cases:  
   1. Element names  
   2. Attribute names
3. Always close HTML elements, because when XML/XHTML software access your page, the clossing slash `/` is required 
4. Always double quote attribute values, unless there is quote in the values
5. Always Specify alt, width, and height for image
6. Do not add blank lines, spaces, or indentations without a reason. Space-less is easier to read and groups entities better together. 
7. Avoid Long Code Lines. For readability, add blank lines to separate large or logical code blocks. For readability, add two spaces of indentation. Do not use the tab key.
8. Never skip the `<title>` **Element**
9. always add the `<html>` and `<body>` tags! Omitting `<body>` can produce errors in older browsers. Omitting `<html>` and `<body>` can also crash DOM and XML software. 
    >Browsers will add all elements before `<body>`, to a default `<head>` element.
10.  To ensure proper interpretation and correct search engine indexing, both the language and the character encoding should be defined
     ```html
     <html lang="en-US">
     <html lang="zh-Hans">
     <meta charset="utf-8">
     ``` 
     > charset is UTF8 by default
11. You should include the following <meta> element in all your web pages:
    ```html
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    ```
12. Use simple syntax for linking to style sheets (the type attribute is not necessary):
    ```
    <link rel="stylesheet" href="styles.css">
    ```
13. Short CSS rules can be written compressed, like this:
    ```
    p.intro {font-family:Verdana;font-size:16em;}
    ```
14. Long CSS rules should be written like this:
    ```css
    body {
      background-color: lightgrey;
      font-family: "Arial Black", Helvetica, sans-serif;
      font-size: 16em;
      color: black;
    }
    ```
    Only use quotes around values if the value contains spaces  
15.   Use simple syntax for loading external scripts (the type attribute is not necessary):  
      ```html
      <script src="myscript.js">
      ```
16.  Some web servers (Apache, Unix) are case sensitive about file names: "london.jpg" cannot be accessed as "London.jpg".
     Other web servers (Microsoft, IIS) are not case sensitive: "london.jpg" can be accessed as "London.jpg".
17.  If you use a mix of uppercase and lowercase, you have to be aware of this.
     If you move from a case-insensitive to a case-sensitive server, even small errors will break your web!
18.  Short Comment:
     ```html
     <!-- This is a short comment>
     ```
19.  Long Comment:
     ```html
     <!-- 
       This is a long comment example. This is a long comment example.
       This is a long comment example. This is a long comment example.
     -->
     ```
20. HTML files should have a .html extension (.htm is allowed).  
    >There is no difference between the .htm and .html file extensions!
21. If your server is configured only with "index.html" as the default filename, your file must be named "index.html", and not "default.html".  
    >When a URL does not specify a filename at the end (like "https://www.w3schools.com/"), the server just adds a default filename, such as "index.html", "index.htm", "default.html", or "default.htm".  
    >
    >However, servers can be configured with more than one default filename; usually you can set up as many default filenames as you want.?????

## What's New
HTML5 is well supported by browsers, to ensure correct behavior in old browsers:
```css
head, section, footer, aside, nav, main, article, figure {
    display: block;
}
```

> If used in less than IE8, use the shiv library


HTML5 introduces 5 block level semantic elements

The following elements and attributes are depreciated:

元素/属性|	描述
|-|-|
`<center>`|	定义居中的内容。
`<font>` 和 `<basefont>`	|定义 HTML 字体。
`<s>` 和 `<strike>`	|定义删除线文本
`<u>`	|定义下划线文本
`align`	|定义文本的对齐方式
`bgcolor`	|定义背景颜色
`color`	|定义文本颜色
> `bgcolor` is replaced by `style= "background-color:red`
> 
## HTML elements
HTML element can be categorized as:
1. empty and nonempty elements
   1. empty: `<img>`
2. block and inline elements
   1. block: `<p>` `<h>` `<hr>`
   > Browsers automatically add some white space (a margin) before and after a block element by default.
   2. inline

# HTML URLs
1. Absolute URL - Links to an external image that is hosted on another website. Example: `src="https://www.w3schools.com/images/img_girl.jpg"`.
2. Relative URL - Links to an image that is hosted within the website. Here, the URL does not include the domain name. If the URL begins without a slash, it will be relative to the current page. Example: `src="img_girl.jpg"`. If the URL begins with a slash, it will be relative to the domain. Example: `src="/images/img_girl.jpg”`.??????

>  It is almost always best to use relative URLs. They will not break if you change domain.

3. File Path Examples

Path	|Description
|-|-
`src="picture.jpg"`	|The "picture.jpg" file is located in the same folder as the current page
`src="images/picture.jpg"`	|The "picture.jpg" file is located in the images folder in the current folder
`src="/images/picture.jpg"`	|The "picture.jpg" file is located in the images folder at the root of the current web
`src="../picture.jpg"`	|The "picture.jpg" file is located in the folder one level up from the current folder

# HTML Formatting
1. `<b>` bold text without any extra importance should be last resort
2. `<strong>` text with strong importance
3. `<i>` itatic text without alt voice or mood often a term a phrase from another language, a thought...
4. `<em>` emphasized text a screen reader will use verbal stress
5. `<small>` <del>`<big>`</del>
6. `<mark>` marked/highlighted text
7. `<del>` deleted text
8. `<ins>` inserted text, often underlined
9. `<sub>` subscrpt `<sup>` superscipt
10. `<address>`
    ```html
    <address>
    Written by <a href="mailto:webmaster@example.com">Donald Duck</a>.<br> 
    Visit us at:<br>
    Example.com<br>
    Box 564, Disneyland<br>
    USA
    </address>
    ```
11. `<acronym title="World Wide Web>WWW</acronym>` `<abbr>` `<dfn>`
12. `<blockquote>` `<q>` 
    > blockquote element comes with white spaces and margin

## HTML Comments
```html
<!-- This is a comment -->

<!-- [if IE 8]>
    ...
<![endif]-->
```
## HTML Links
1. `target`
   * `_self` Default. Opens the document in the same window/tab as it was clicked
   * `_blank` - Opens the document in a new window or tab
   * `_parent` - Opens the document in the parent frame
   * `_top` - Opens the document in the full body of the window
   * `framename` - If a browsing context or frame with the given name exists, the linked content opens in that frame.
2. Can use images as a link:
```html
<a href="http://..."><img src=...></a>
<a href="mailto:someone@example.com">Send email</a>
```
3. Button as link
   ```html
   <button onclick="document.location='default.asp'">HTML Tutorial</button>
   ```
4. Links as bookmarks
   ```html
   <h2 id="C4">Chapter 4</h2>
   ...
   <a href="#C4">Jump to Chapter 4</a>
   ```

## HTML Images
Images are not technically inserted into a web page; images are linked to web pages. The <img> tag creates a holding space for the referenced image.

Width and heights are always in pixels, always define otherwise the page flickers

Use style instead is preferred

### HTML Picture
Used for Bandwidth and format purposes\
If you have a small screen or device, it is not necessary to load a large image file. The browser will use the first <source> element with matching attribute values, and ignore any of the following elements.

Some browsers or devices may not support all image formats. By using the `<picture>` element, you can add images of all formats, and the browser will use the first format it recognizes, and ignore any of the following elements.


The browser will use the first <source> element with matching attribute values, and ignore any following <source> elements.

### Image Map
```html
<img src="workplace.jpg alt = "Workspace" usemap="#workmap"/>

<map name="workmap">
    <area shape="rect" coord="34,44,270,350" alt="computer" href="computer.htm"/>
</map>
```
The coordinate (34,44) is 34 from the left margin

Must define the shape, can be one of `rect, circle, poly, default`

> An area can also trigger Javascript function
```html
<area onclick="myFunction()">
```

## HTML Background
1. `background-image`
2. `background-size` `cover` to cover the entire element
3. `background-attachment` `fixed` to make sure it's always covered
4. This way it's covered with no stretching, might crop the image tho
5. If want to stretch to fit the entire element, set 100% 100%

## HTML Favicon
```
<link rel="icon" type="image/x-icon" href="/images/favicon.ico">
```

## HTML Title Element
```html
<head>
  <title>HTML Tutorial</title>
</head>
```
The `<title>` element:
* defines a title in the browser toolbar
* provides a title for the page when it is added to favorites
* displays a title for the page in search engine-results


## HTML Table
A table cell can contain all sorts of HTML elements: text, images, lists, links, other tables, etc.

Made of three elements: `<table>` `<td>` `<tr>`

Sometimes you want your cells to be table header cells. In those cases use the <th> tag instead of the <td> tag:\
By default, the text in <th> elements are bold and centered, but you can change that with CSS.

### Table Border
```html
table, th, td {
  border: 1px solid black;
  <!-- For single border -->
  border-collapse: collapse; 
}
```

Invisible Border:
set a background color of each cell, and give the border a white color (the same as the document background), you get the impression of an invisible border `border-color`

### Table Width
Full width table:
```html
<table style="width:100%">
```
Set size of a specific column:
```html
<th style="width:70%">First Name</th>
```

### Column Span
`<th colspan="2">Name</th>`  
`<tr rowspan="2">Cell 1</tr>`

### Table Caption
To add a caption to a table, use the <caption> tag:

The <caption> tag should be inserted immediately after the <table> tag.

### Table Padding and Spacing
```css padding
th, td {
    padding: 15px;
}
```

Cell spacing is 2px by default, to change:
```html
<table style="border-spacing:5px">
```

### Table Styling
```css
tr:nth-child(even) {
    background-color: rgba(150, 212, 212, 0.4);
}

td:nth-child(even), th:nth-child(even) {
    background-color:  rgba(150, 212, 212, 0.4);
}
```

If you specify borders only at the bottom of each table row, you will have a table with horizontal dividers.  
`tr{border-bottom:1px solid #ddd;}`

Hovering effect  
`tr:hover{background-color:#D6EE;}`

### Table Column Grouping

```html
<table>
  <colgroup>
    <col span="2" style="background-color: #D6EEEE">
    <col span="3"><!-- skip the next 3 cols -->
    <col span="2" style="background-color:pink">
  </colgroup>
  ...
</table>
```
> Note: The `<colgroup>` tag must be a child of a `<table>` element and should be placed before any other table elements, like `<thead>`, `<tr>`, `<td>` etc., but after the `<caption>` element, if present.


There is only a very limited selection of CSS properties that are allowed to be used in the colgroup:
* width property
* visibility property
* background properties
* border properties

## HTML List
### `type`
|type|description
|-|-
`disc`	|Sets the list item marker to a bullet (default)
`circle`	|Sets the list item marker to a circle
`square`	|Sets the list item marker to a square
`none`	|The list items will not be marked
`1`	|The list items will be numbered with numbers (default)
`A`	|The list items will be numbered with uppercase letters
`a`	|The list items will be numbered with lowercase letters
`I`	|The list items will be numbered with uppercase roman numbers
`i`	|The list items will be numbered with lowercase roman numbers

### `start`

### Description List
```html
<dl>
  <dt>Coffee</dt>
  <dd>- black hot drink</dd>
  <dt>Milk</dt>
  <dd>- white cold drink</dd>
</dl>
```

## HTML Form
The form-handler is specified in the form action attribute
if the action is omitted, the action is set to the current page.
- [ ] how?
> Note: The form itself is not visible. 

### Form Target
specifies where to display the response that is received after submitting the form.

### Form Method
send form data as URL variables(`method="get"`) or as HTML post transaction(`method="post"`)

### From Autocomplete
When autocomplete is on(`autocomplete="on"`), the browser automatically complete values based on values that the user has entered before.
### Form Novalidate
boolean value, when present(`novalidate`), no validation

### Form Input
An Input element is an empty element, can be displayed in many ways:
```html
<input type="text">
<input type="radio">
<input type="checkbox">
<input type="submit">
<input type="button">
```
the default width of an input field is 20 characters. 
Each input element **MUST** have a name attribute to be submitted

### Form Label
The <label> element is useful for screen-reader users, because the screen-reader will read out loud the label when the user focuses on the input element.

The <label> element also helps users who have difficulty clicking on very small regions (such as radio buttons or checkboxes) - because when the user clicks the text within the <label> element, it toggles the radio button/checkbox.

The for attribute of the <label> tag should be equal to the id attribute of the `<input>` element

### Form Select
```html
<label for="cars">Choose a car:</label>
<select id="cars" name="cars" size="3" multiple> <!-- size specify # of visible values-->
  <option value="volvo">Volvo</option> <!-- by default the first is selected-->
  <option value="saab">Saab</option>
  <option value="fiat" selected>Fiat</option> 
  <option value="audi">Audi</option>
</select>
```

### Form Textarea
