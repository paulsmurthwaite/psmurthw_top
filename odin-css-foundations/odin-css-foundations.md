## Selectors

Selectors are the HTML elements to which CSS rules apply.

### Universal Selector

Selects elements of any type.  Example: every element coloured to purple:

```css
* {
  color: purple;
}
```

### Type Selector

Type/Element selector selects all elements of specified element type.  Example: all <div> elements selected, <p> not selected:

```html
<!-- index.html -->

<div>Hello, World!</div>
<div>Hello again!</div>
<p>Hi...</p>
<div>Okay, bye.</div>
```

```css
/* styles.css */

div {
  color: white;
}
```

### Class Selector

Class selectors will select all elements with the given class, which is just an attribute you place on an HTML element.  Example: <div> with class of "alert-text" selected:

```html
<!-- index.html -->

<div class="alert-text">
  Please agree to our terms of service.
</div>
```

```css
/* styles.css */

.alert-text {
  color: red;
}
```

Notes:

1. Class Selector syntax - period followed by case-sensitive value of class attribute.  Classes not required to be unique.

2. Multiple classes can be added to a single element, so class="alert-text severe-alert".  Whitespace is used to separate class names like this.  Multi-worded class names should not include spaces; use hyphens instead.

### ID Selector

ID selectors are similar to class selectors. They select an element with the given ID, which is another attribute you place on an HTML element.  Example: 

```html
<!-- index.html -->

<div id="title">My Awesome 90's Page</div>
```

```css
/* styles.css */

#title {
  background-color: red;
}
```

Notes:

1. Instead of a period, use a hashtag immediately followed by the case-sensitive value of the ID attribute.

2. Use IDs sparingly (if at all).  Common use cases for IDs are: taking advantage of specificity or to have links redirect to a section on the current page.

3. The major difference between classes and IDs is that an element can only have one ID. An ID cannot be repeated on a single page, and the ID attribute should not contain any whitespace at all.

### Grouping Selectors

Two/more groups of elements that share some of their style declarations.

```css
.read {
  color: white;
  background-color: black;
  /* several unique declarations */
}

.unread {
  color: white;
  background-color: black;
  /* several unique declarations */
}
```

Where the selectors share some declarations, to cut down on the repetition, we can group these two selectors together as a comma-separated list:

```css
.read, 
.unread {
  color: white;
  background-color: black;
}

.read {
  /* several unique declarations */
}

.unread {
  /* several unique declarations */
}
```

### Chaining Selectors

Another way to use selectors is to chain them as a list without any separation.

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

We have two elements with the subsection class.  If we only want to apply a separate rule to the element that also has header as a second class, we chain the two class selectors together:

```css
.subsection.header {
  color: red;
}
```

.subsection.header selects any element that has both the subsection and header classes.  This syntax basically works for chaining any combination of selectors, with the exception of chaining more than one type selector.

Can also be used to chain a class and an ID:

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection" id="preview">This is where a preview for a post might go.</p>
</div>
```

So:

```css
.subsection.header {
  color: red;
}

.subsection#preview {
  color: blue;
}
```

### Descendant Combinator

Show a relationship between the selectors.  A descendant combinator is represented by a single space between selectors.  Will only cause elements that match the last selector to be selected if they also have an ancestor that matches the previous selector.

```html
<!-- index.html -->

<div class="ancestor"> <!-- A -->
  <div class="contents"> <!-- B -->
    <div class="contents"> <!-- C -->
    </div>
  </div>
</div>

<div class="contents"></div> <!-- D -->
```

```css
/* styles.css */

.ancestor .contents {
  /* some declarations */
}
```

B & C will be selected, D will not be.

### Properties to get started with

1. color (element text color)
2. background-color (element background color)

Examples:

```css
p {
  /* hex example: */
  color: #1100ff;
  /* rgb example: */
  color: rgb(100, 0, 127);
  /* hsl example: */
  color: hsl(15, 82%, 56%);
}
```

With transparency, last 2 digits of hex are between 00 and FF:

```html
<p class="p1">Red</p>
<p class="p1a">Red transparency</p>
<p class="p2">Green</p>
<p class="p2a">Green transparency</p>
<p class="p3">Blue</p>
<p class="p3a">Blue transparency</p>
<p class="p4">Yellow</p>
<p class="p4a">Yellow transparency</p>
<p class="p5">Cerise</p>
<p class="p5a">Cerise transparency</p>
```

```css
.p1 {background-color:#ff0000;}
.p1a {background-color:#ff000080;}
.p2 {background-color:#00ff00;}
.p2a {background-color:#00ff0080;}
.p3 {background-color:#0000ff;}
.p3a {background-color:#0000ff80;}
.p4 {background-color:#ffff00;}
.p4a {background-color:#ffff0080;}
.p5 {background-color:#ff00ff;}
.p5a {background-color:#ff00ff80;}
```

#### Further reading
[CSS Legal Color Values](https://www.w3schools.com/cssref/css_colors_legal.asp)

### Typography Basics and text-align

Examples:

```css
font-family: "Times New Roman", sans-serif; /* can be a single value or a comma-separated list of values */
```

```css 
font-size 22px /* set the size of the font */
```

```css
font-weight: bold /* set the boldness  of the text; keyword or value 1-1000 */
font-weight: 700 /* equivalent of bold */
```

```css
text-align: center /* align text horizontally within an element */
```

### Image Height and Width

By default, an <img> element’s height and width values will be the same as the actual image file’s height and width.

If you wanted to adjust the size of the image without causing it to lose its proportions, you would use a value of “auto” for the height property and adjust the width value:

```css
img {
  height: auto;
  width: 500px;
}
```

Note:

1. For performance reasons, best to include both of these properties for <img> elements

### The Cascade of CSS

The cascade is what determines which rules actually get applied to our HTML. There are different factors that the cascade uses to determine this.

### Specificity

A CSS declaration that is more specific will take precedence over ones that are less specific.

Inline styles have the highest specificity compared to selectors, while each type of selector has its own specificity level that contributes to how specific a declaration is.

For now, dealing with:

1. ID selectors (most specific)
2. Class selectors
3. Type selectors

Specificity will only be taken into account when an element has multiple, conflicting declarations targeting it, sort of like a tie-breaker.

See above order, however when no declaration has a selector with a higher specificity, a larger AMOUNT of a single selector will beat a smaller amount of that same selector.

Examples:

```css
/* rule 1 */
.subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
```

Rule 2 is more specific because it is using MORE class selectors.  This declaration will be applied.

```css
/* rule 1 */
#subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
```

Rule 1 is more specific because it is using ID which beats Class.  This declaration will be applied.

```css
/* rule 1 */
#subsection .list {
  background-color: yellow;
  color: blue;
}

/* rule 2 */
#subsection .main .list  {
  color: red;
}
```

Rule 2 has more Class selectors and so has higher specificity.  This declaration will be applied, however Rule 1 `background-color` will be applied since there is no conflict for it.

Further examples:

```css
/* rule 1 */
.class.second-class {
  font-size: 12px;
}

/* rule 2 */
.class .second-class {
  font-size: 24px;
}
```
Both Rules have the same specificify.  1=chaining, 2=descendant combinator.  Both have two classes and no other changes to the specificity.

```css
/* rule 1 */
.class.second-class {
  font-size: 12px;
}

/* rule 2 */
.class > .second-class {
  font-size: 24px;
}
```

The child combinator (>) does not change the specificity value.  Both rules have two classes and hence the same specificity.

```css
/* rule 1 */
* {
  color: black;
}

/* rule 2 */
h1 {
  color: orange;
}
```

Rule 2 has higher specificity.  It has a Type selector.  Rule 1 is using the universal selector which has no specificity.

### Inheritance

CSS properties that, when applied to an element, are inherited by that element’s descendants, even if we don’t explicitly write a rule for those descendants.  Typography based properties (`color, font-size, font-family`, etc.) are usually inherited, while most other properties aren’t.

The exception to this is when directly targeting an element, as this always beats inheritance:

```html
<!-- index.html -->

<div id="parent">
  <div class="child"></div>
</div>
```

```css
/* styles.css */

#parent {
  color: red;
}

.child {
  color: blue
}
```

The child element would have the color: blue style applied since that declaration directly targets it, while color: red from the parent is only inherited.

### Rule Breaker

To break any cascade decision, the final factor - whichever rule was *last* defined will be applied.

```css
/* styles.css */

.alert {
  color: red;
}

.warning {
  color: yellow;
}
```

In the above example, there is no inheritance, no specificity is more than the other.  `.warning` was the last defined rule and will be applied.

### Internal CSS

If not using an exernal css stylesheet then in the html file, place `style` tags between the `head` tags and specify the styles to be applied.  Useful for a single page only:

```html
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>...</body>
```

### Inline CSS

Possible to add styles directly to HTML elements within the html file, but not recommended:

```html
<body>
  <div style="color: white; background-color: black;">...</div>
</body>
```

Note:

1. No selectors used here - the styles are being directly added to the `div` tag
2. Use only for adding a *unique* style for a *single* element

