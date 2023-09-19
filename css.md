# CSS Basics

> Changing one CSS file can change multiple pages, and one page's style can be changed by binding different CSS file

**header vs. heading vs. head**

## CSS Selectors
### Simple selectors  

|Selector|Example|Name
|-:|-:|-:
|#id|#firstname|
|.class|.intro|
|element.class|p.intro|
|*|*|Universal Selector
|element|p|
|element,element|div,p|
### Combinator selectors
### Pseudo-class selectors
### Pseudo-elements selectors
### Attribute selectors

## Insert CSS
```html
<link rel="stylesheet" href="mystyle.css"/>
```
If some properties have been defined for the same selector (element) in different style sheets, the value from the **last** read style sheet will be used.

All the styles in a page will "cascade" into a new "virtual" style sheet by the following rules, where number one has the highest priority:
1. inline style
2. External and internal style sheets
3. Browser default

## CSS Comments
Sinle Line Comments:
```css
/* This is a single-line comment
*/
```
# CSS Properties

## CSS Colors
In CSS, colors can be specified by:
### Predefined color names
> CSS/HTML support 140 standard color names
### RGB values  
`rgb(255, 0, 0)` = red  
`rgb(0,0,0)` = black  
> Shades of gray are often defined using equal values for all the 3 light sources
### HEX values  
`#RRGGBB`  
`#ff0000` = red  
`#000000` = black
> Can be written as 3 digit when both the values are the same for each component
> `#ff00cc` = `#f0c`
### HSL values
Stands for hue, saturation and lightness  
Hue is a degree on the color wheel from 0 to 360, 0 is red, 120 is green and 240 is blue  
Saturation is a percentage 0% is a shade of gray, 100% is full color  
Lightness is also %, 0% is black 100 is white  
### RGBA
values = RGB + Alpha channel (opacity, not transparent at 1.0)
### HSLA values  
Same as RGBA

## CSS Backgrounds properties
### CSS background-color
```css
div {
 background-color: green;
 opacity: 0.3;
}
```
> **Note:** All children of an element inherit the same opacity. This can make the text inside a fully transparent element hard to read. To solve this, use RGBA
### CSS background-image
```css
body {
 background-image: url("paper.gif");
}
```
### CSS background-repeat
By default a background image repeats both vertically and horizontally  
To override this:
```css
body {
 background-image: url("bg.png");
 background-repeat: repeat-x; /* repeat horizontally only */
 background-repeat: no-repeat; 
 background-position: right top;
}
```
### CSS Background Attachment  
`background-attachment: scroll`  
`background-attachment: fixed`
### CSS Background Shorthand
`background red url("img.png") no-repeat right top`:
> The order is: color image repeat attachment position
### Other CSS Background properties  
`background-clip: border-box`  all  
`background-clip: padding-box` behind border  
`background-clip: content-box` behind padding  
`background-size: auto` default original size    
`background-size: 30px` width = 30px height = auto  
`background-size: cover` cover the entire container, might cut the image
`background-size: 50%` width = 50% of the parent element
`background-origin`

## CSS Borders
### CSS Border Style
- dotted
- dashed
- solid
- double
- groove
- ridge
- inset
- outset
- none
- hidden
- Mixed: Can have 1-4 values (top,right,bot,left)  
>
> None of the **OTHER** CSS border properties will effect unless `border-style` is set
### CSS Border Width  
Can have 1-4 values (top,right,bot,left)  
some predefined values are `thin`1px `medium`3px `thick`5px (typically)
### CSS Border Color
Can have 1-4 values
`border-right-color: red;`
### CSS Border Side Cases:
If 3 values: top right=left bot  
If 2 values: top=bot right=left
### CSS Shorthand  
`border: 5px solid red;`  
`border-left: 6px solid red;`
### CSS Rounded Borders
`border-radius: 5px`
 
 ## CSS Margins
- [x] What is the default value for margin?\
usually 0, depends on the brower default CSS
### Shorthand Property  
`margin: 25px 50px 75px 100px;`
Can have 1-4 values
### Individual sides
- margin-top
- margin-right
- margin-bottom
- margin-left
- Can have the following values:
 - auto
 - length
 - %
 - inherit
> Negative values are allowed

use `auto` to horizontally center the element within its container
### Margin Collapse   
Top and bottom margins of elements are **sometimes** collapsed into a single margin that is equal to the largest of the two margins.

## CSS Padding
Default padding is usually 0, depends on default CSS  

Padding is used to create space around an element's content  
> Note: Negative values are **NOT** allowed 
 
padding can either be specified seperately or together using the shorthand

`width` specifies the width of the **content** area, so padding is added to the specified width

To keep the width independent of the padding, use `box-sizing: border-box`  

## CSS Height/Width
the height/width is of the content area
### Max-width  
Max-width is none by default  
When the width of the elementis is bigger than the browser window. The browser then adds a scrollbar to the page, to solve this add `max-width`

if both used, and `width` > `max-width` `width` is ignored

Other properties:  
* `min-width`
* `min-height`
* `max-height`

## CSS Outline
> The outline is drawn outside the **Border** not the margin, might overlap other content  
> 
> the element's total width and height is not affected by the width of the outline.
1. `outline-style`: Same as border, Must be set
2. `outline-width`
3. `outline-color`
4. `outline-offset`\
   Specifies the space between outline and the border

## CSS Text
### Text Color: Use the `color` property
### Text Alignment
* `text-align` sets the **horizontal** alignment  
  * `left` if left-to-right, `right` if right-to-left
  * `justify` strethes the lines to have equal width
* `text-align-last` aligns the last line
* To reverse the text:
  ```
  direction: rtl;
  unicode-bidi: bidi-override;
  ```
* `vertical-align`???
  |Value|Description
  |-|-
  |baseline	|The element is aligned with the baseline of the parent.|
  length	|Raises or lower an element by the specified length. Negative values are allowed. Read about length units
  %	|Raises or lower an element by a percent of the "line-height" property. Negative values are allowed
  sub	|The element is aligned with the subscript baseline of the parent
  super	|The element is aligned with the superscript baseline of the parent
  top	|The element is aligned with the top of the tallest element on the line
  text-top	|The element is aligned with the top of the parent element's font
  middle	|The element is placed in the middle of the parent element
  bottom	|The element is aligned with the lowest element on the line
  text-bottom	|The element is aligned with the bottom of the parent element's font
### Text Decoration
 * `text-decoration-line`
   * `overline`
   * `line-through`
   * `underline`
 * `text-decoration-color`
 * `text-decoration-style`
   * `wavy`
   * `solid`
   * `double`
 * `text-decoration-thickness` requires `text-decoration-line`
   * `auto` by default
   * `5px`
   * `50%`
 * `text-decoration`
   * `text-decoration-line` (required)
   * `text-decoration-color` (optional)
   * `text-decoration-style` (optional)
   * `text-decoration-thickness` (optional)
 > To remove the underline in links:  
 > `a {text-decoration-line: none;}`  
 > Underlining not recommended, confused with links
### Text Transformation
 * `text-transform`
   * `uppercase`
   * `lowercase`
   * `capitalize`
### Text Spacing
 * Text Indentation: `text-indent: 50px;`
 * Letter Spacing: `letter-spacing: -2px;`
 * line Height: `line-height: 0.8;` Vertical Spacing
 * Word Spacing: `word-spacing`
 * White Space: `white-space`
   * `normal` default, collapse, auto wrap, line break -> single spaces.
   * `nowrap` collapse, no auto wrap, line break -> single spaces
   * `pre` like`<pre>`tag, no collapse, no auto wrap, line break preserved
   * `pre-line` collapse, auto wrap, line break preserved
   * `pre-wrap` no collapse, auto wrap, line break preserved
 * Text Shadow
   * `text-shadow: 2px 2px 5px red;` horizontal, vertical, blur
> line break is equivalent to `<br/>` in html
## CSS Fonts
### Font Family
   1. Five generic font families:
      1. Serif fonts have a small stroke at the edges of each letter. They create a sense of formality and elegance
      2. Sans-serif fonts have clean lines (no small strokes attached). They create a modern and minimalistic look
      3. Monospace fonts - here all the letters have the same fixed width. They create a mechanical look. 
      4. Cursive fonts imitate human handwriting.
      5. Fantasy fonts are decorative/playful fonts.

      |Generic Font Family	|Examples of Font Names
      |-|-
      |Serif	|Times New Roman <br/>Georgia <br/>Garamond
      |Sans-serif|	Arial <br> Verdana <br> Helvetica
      |Monospace	| Courier New <br> Lucida Console <br>Monaco
      Cursive	|Brush Script MT <br> Lucida Handwriting<br> 
      Fantasy	| Copperplate<br>Papyrus
   2. Web Safe Fonts
      1. Arial (sans-serif) Most widely used Google doc
      2. Verdana (sans-serif) readable even small
      3. Tahoma (sans-serif) less space
      4. Trebuchet MS (sans-serif) not mobile supported
      5. Times New Roman (serif) news/newspaper/Windows
      6. Georgia (serif) Mobile friendly
      7. Garamond (serif) printed book
      8. Courier New (monospace) coding/email/movie screenplays
      9. Brush Script MT (cursive) mimic handwriting
   3. Font Fallbacks `font-family: "Times New Roman", Times, serif;`
### Font Style 
   1. `font-style` `normal` `italic` `oblique` similar but less supported
   2. `font-weight` `bold`
   3. `font-variant` `small-caps`
   4. `font-size` 
      1. normal text is 1em=16px px/16 = em
      2. 1vw = 1% of viewport width
### Google Fonts   
   Request font&effect:  
   `<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Audiowide|Sofia|Trirong&effect=fire">`\
   Use effect:  
   `<h1 class="font-effect-neon">Neon Effect</h1>`
   > Requesting multiple fonts slows the page
### Great Font parings:
      1. Georgia and Verdana
      2. Helvetica and Garamond
### Font Shorthand
`font: font-style font-variant font-weight font-size/line-height font-family`

## CSS Icons
1. How to Add Icons:  
   First insert the `<link>` \
   then add the name of the specified icon class to any inline HTML element (like `<i>` or `<span>`).
2. Font Awesome Icons  
   Go to fontawesome.com, sign in, and get a code to add in the <head> section of your HTML page:
3. Bootstrap Icons
   `<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">`

   `<i class="glyphicon glyphicon-cloud"></i>`
4. Google Icons
   `<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">`

   `<i class="material-icons">cloud</i>`

## CSS Links
### Four link states
   1. `a:link` - a normal, unvisited link
   2. `a:visited` - a link the user has visited
   3. `a:hover` - a link when the user mouses over it
   4. `a:active` - a link the moment it is clicked  
   >When setting the style for several link states, there are some order rules:  
   a:hover MUST come after a:link and a:visited  
   a:active MUST come after a:hover
### Text Decoration (mostly used to remove underlines from links)
   `a:link {text-decoration: none;}
### Link Buttons
   ```css
   a:link, a:visited {
     background-color: #f44336;
     color: white;
     padding: 14px 25px;
     text-align: center; 
     text-decoration: none;
     display: inline-block;
   }

   a:hover, a:active {
     background-color: red;
   }
   ```

## CSS Lists
The CSS list properties allow you to:

Set different list item markers for ordered lists  
Set different list item markers for unordered lists  
Set an image as the list item marker  
Add background colors to lists and list items

1. List Item Markers 
   1. `list-style-type` `circle` `square` `upper-roman`
   2. `list-style-image`
   3. `list-style-position` `inside` `outside`
2. List has margin and padding, set to 0 to remove them
   ```
   ul {
     list-style-type: none;
     margin: 0;
     padding: 0;
   }
   ```
3. `list-style`
   ```
   ul {
     list-style: square inside url("sqpurple.gif");
   }
   ```
   
## CSS Tables
1. Table Borders `border`
   ```
   table, th, td {
     border: 1px solid;
   }
   ```
2. Table Width
3. Collapse Borders `border-collapse: collapse;`
4. Table Height and Width
5. `text-align` `vertical-align`
6. Table Padding
7. Horizontal Divider
   ```
   th, td {
     border-bottom: 1px solid #ddd;
   }
   ```
8. `tr:hover`
9. Striped Tables   
   `tr:nth-child(even) {background-color: #f2f2f2;}`
10. Responsive Table
    ```
    <div style="overflow-x:auto;">

    <table>
    ... table content ...
    </table>

    </div>
    ```
    > Note: In OS X Lion (on Mac), scrollbars are hidden by default and only shown when being used (even though "overflow:scroll" is set).

# CSS Layout
## CSS Display !!!
CSS display is the most important display property

1. `block`
   block elements starts on a new and stretches horitonally as far as it can
   e.g. `<form>`
2. `inline`
   inline elements cannot contain block element\
   examples are `<a>` `<img>`
3. `none`
   > `<script>` by default has `display: none`

### Two ways to hide an element:
1. `display: none`
   hides an element
2. `visibility: hidden`
   still take up place, just not visible

## CSS Max-width

Since block elements takes up the full width available, we can set `width` and `margin:auto` to center it within its parent element

But on very small browser window (mobile devices),
a scrollbar is added, to prevent this, we set `max-width`

## CSS Position
1. `position: static`
default value, display as it is
2. `position: fixed`
   positioned relative to the viewport, no gap left
   ```css 
   div.fixed {
      position: fixed;
      bottom: 0; /* 0 without unit is acceptable */
      right: 0;
   }
   ```
   sticks to the right-bottom
3. `position: relative`
   positioned relative to its original position, may leave gap
4. `position: absolute`
   positioned relative to its nearest positioned ancestor(elements with position set to relative, absolute, fixed, or sticky)\

   if no ancestor is positioned, relative to the document body (the initial containing block, usually equivalent to the viewport) and and moves along with page scrolling.
5. `position: sticky`
   toggles between `relative` and `fixed`, when scrolled out of viewport, becomes `fixed` with the given position properties
   ```css
   div.sticky {
      position: -webkit-sticky; /* Safari */
      position: sticky;
      top: 0;
   }
   ```
> to clip an element: 
`clip: rect(0px,60px,200px,0px);`

Question: how to stick an element to the top left??


## CSS Z-index

`z-index` is to control the stack order of the positioned elements

setting `z-index: -1` makes a image appear behind text
setting `z-index: 1` makes it appear in front

z-index only applies to positioned elements (position: absolute, position: relative, position: fixed, or position: sticky) and flex items (elements that are direct children of display: flex elements).

If 2 posistioned elements overlap each other without a z-index specified, the element defined **last in the HTML code** will be shown on top.

## CSS Overflow

`overflow` controls what happens if content of a element overflows

it only applies to block elements with fixed width and height
### Overflow

1. `overflow: visible`\
   Default
2. `overflow: hidden`
3. `overflow: scroll`
   Forces a scrollbar
4. `overflow: auto`
   similar to `scroll` but only add scrollbar when necessary
5. `overflow-x` `overflow-y`

### Wrap
controls whether browser can break a word when overflow happens

1. `overflow-wrap: anywhere`
   can
2. `overflow-wrap: normal`
   cannot

### CSS Cursor
can be applied to most html elements
```html
<span style="cursor: auto">auto</span><br>
<span style="cursor: crosshair">crosshair</span><br>
<span style="cursor: default">default</span><br>
<span style="cursor: e-resize">e-resize</span><br>
<span style="cursor: help">help</span><br>
<span style="cursor: move">move</span><br>
<span style="cursor: n-resize">n-resize</span><br>
<span style="cursor: ne-resize">ne-resize</span><br>
<span style="cursor: nw-resize">nw-resize</span><br>
<span style="cursor: pointer">pointer</span><br>
<span style="cursor: progress">progress</span><br>
<span style="cursor: s-resize">s-resize</span><br>
<span style="cursor: se-resize">se-resize</span><br>
<span style="cursor: sw-resize">sw-resize</span><br>
<span style="cursor: text">text</span><br>
<span style="cursor: w-resize">w-resize</span><br>
<span style="cursor: wait">wait</span>
```

## CSS Float
