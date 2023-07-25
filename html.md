# HTML 5 
## Style Guide

1. Always declare the document type as the first line in your document:
```html
<!DOCTYPE html>
```
2. Always use lower case in the following cases:  
   1. Element names  
   2. Attribute names
3. Always close HTML elements, because when XML/XHTML software access your page, the clossing slash `/` is required 
4. Always quote attribute values
5. Always Specify alt, width, and height for
6. Do not add blank lines, spaces, or indentations without a reason. Space-less is easier to read and groups entities better together. 
7. Avoid Long Code Lines. For readability, add blank lines to separate large or logical code blocks. For readability, add two spaces of indentation. Do not use the tab key.
8. Never skip the `<title>` Element
9. always add the `<html>` and `<body>` tags! Omitting `<body>` can produce errors in older browsers. Omitting `<html>` and `<body>` can also crash DOM and XML software. 
    >Browsers will add all elements before `<body>`, to a default `<head>` element.
10.  To ensure proper interpretation and correct search engine indexing, both the language and the character encoding should be defined
    ```html
    <html lang="en-US">
    <html lang="zh-Hans">
    <meta charset="utf-8">
    ``` 
11. You should include the following <meta> element in all your web pages:
    ```html
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    ```
12. Use simple syntax for linking to style sheets (the type attribute is not necessary):
    ```html
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
