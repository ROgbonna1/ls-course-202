# Intro to HTML/CSS

## Intro to CSS

* Called _cascade_ because all styles cascade from the top of a stylesheet to the bottom, allowing different styles to be added or overwritten.
  * The _cascade_ works inside individual selectors as well.
   ```CSS
     p {	
	background: orange;
 	background: green;
      }
   ```
   In this example, since the green background declaration comes after the orange, it will override it.

* The type selector has the lowest specificity weight and holds a point value of 0-0-1. The class selector has a medium specificity weight and holds a point value of 0-1-0. Lastly, the ID selector has a high specificity weight and holds a point value of 1-0-0. Specificity points are calculated using three columns. The first column counts ID selectors, the second column counts class selectors, and the third column counts type selectors. 
* The higher the specificity weight of a selector, the more superiority the selector is given when a styling conflict occurs.

* When selectors are combined they should be read from right to left. The selector farthest to the right, directly before the opening curly bracket, is known as the _key selector_. Any selector to the left of the key selector will serve as a _prequalifier_.
  * Example:
    ```CSS
    .hotdog p {
  		background: brown;
	      }	
    .hotdog p.mustard {
  			background: yellow;
		      }
    ```

## The Box Model

* *block* elements occupy any available width, regardless of their content, and begin on a new line
* *inline* elements occupy only the width their content requires and line up on the same line, one after the other.
* Every element has a default display property value; however, as with all other property values, that value may be overwritten. `<p>`, for example is `display: block` by default.
* According to the box model concept, every element on a page is a rectangular box and may have width, height, padding, borders, and margins.
* Each part of the box model corresponds to a CSS property: width, height, padding, border, and margin.
  ```CSS
  div {
  	  border: 6px solid #949599;
       	  height: 100px;
 	  margin: 20px;
	  padding: 20px;
	  width: 400px;
	}
 ```
* According to the box model, the total width of an element can be calculated using the following formula:
  `margin-right + border-right + padding-right + width + padding-left + border-left + margin-left`

* The *margin* property allows us to set the amount of space that surrounds an element. Margins for an element fall outside of any border and are completely transparent in color.
* The *padding* property is very similar to the margin property; however, it falls inside of an element’s border, should an element have a border. The padding property is used to provide spacing directly within an element.

### Border Box
```CSS
	div {
  		box-sizing: border-box;
	}
```
* the border-box value alters the box model so that any border or padding property values are included within the width and height of an element. When using the border-box value, if an element has a width of 400 pixels, a padding of 20 pixels around every side, and a border of 10 pixels around every side, the actual width will remain 400 pixels.

