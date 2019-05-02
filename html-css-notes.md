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

* The width and height define how much horizontal and vertical space it needs for the content area of the box, which may or may not include the padding and borders. In most cases, the browser can determine the width and height automatically.
* The padding is an area that surrounds the content area of the box and separates the content from its border. It is typically opaque and hides anything that it overlays.
* The border is a boundary that surrounds the padding.
* The margin is a transparent area that lies outside the border and supplies separation between elements.
* The display property determines how the browser lays out an element relative to its neighbors.

### Border Box
```CSS
	div {
  		box-sizing: border-box;
	}
```
* the border-box value alters the box model so that any border or padding property values are included within the width and height of an element. When using the border-box value, if an element has a width of 400 pixels, a padding of 20 pixels around every side, and a border of 10 pixels around every side, the actual width will remain 400 pixels.

# The Visual Formatting Model
* The `display` property has alomst thirty values, but `block`, `inline-block`, and `inline` are most used.

## Block elements
* _block elements_ (headings, paragraphs, sections, tables, forms, etc) by default occupy all horizontal space available within its container, with nothing to its left or right.
* If a page contains 3 block elements directly inside the `body` and nothing else, then all three elements will display one above the other like a stack of blocks.
* `block` elements use the box properties (width, height, margin, padding, border) to determine size of the element.
* Though a block element takes up an entire row, its width is not altered to do so. If a `div` is 500px in a 900px `section`, the remaining 400px will remain empty.
* Most elements are block by default!
* 
## Inline elements
* Inline elements provide some semantic meaning to content (`span`, `b`, `strong`, `em`,*`img`* etc)
* inline elements handle the dimension properties (width, height, padding, border, and margin) differently from the way block elements treat them.
* Browsers handle left and right margins and padding for inline elements in the same way as for block elements, but they process other box model properties differently.
* For inline elements, browsers:
  * ignore the width and height properties (except with the img element), but instead use values computed from the element content.
  * ignore top and bottom margins.
  * padding and borders may extend into rows above and below but will not interfere or shift them but overlap them. See [example](http://d3jtzah944tvom.cloudfront.net/202/images/lesson_2/the-visual-formatting-model-01.png)

## Inline-Block elements
* `inline-block` elements act just like `block` elements except they do *not* take up the entire row by default. Thus, you can place `inline-block` elements side-by-side.
* `inline-block` elements observe the `width` and `height` properties. Padding, margin, and boder all work as they do with `block` elements.
* Note: *`img` elements are NOT `inline-block`. They are `inline` by default.*
* Browsers use the `vertical-align` property to perform vertical alignment for adjacent `inline-block` elements.


## Box Sizing
* The `box-sizing` property can have two values: `content-box` and `border-box`.
* The `content-box` setting is default in all modern browsers. This is the standard box model. Padding and border are not included in element height or width
* With `border-box`, width and height are calculated inclusive of padding and border.
* The `border-box` setting is "best" since it simplifies the math a front-end developer must do. For example, if we have a box with a width of 50% and padding of 12px; border-box ensures that it's precisely 50% of the container width, not 50% plus 24-pixels.
* The code below can be used to set `border-box` everywhere.
  ```CSS
    html {
      box-sizing: border-box;
    }

    *, *::before, *::after {
      box-sizing: inherit;
    }
  ```

# Margins and Padding

## Margin collapse
* Top and bottom margins "collapse" between `block` elements, meaning if you position two adjacent `block`s one above the other, the margin between them isn't thesum of the top and bottom margins. Instead, the margin _collapses_ to the larger of the two.
* Margin collapse only happens with top and bottom, not left and right margins.

# Dimensions
* `px`, `rem`, `%` called measurement units

## Absolute Units
*  CSS distinguishes between a physical pixel (also device pixel or display pixel) and what we call the *CSS reference pixel* (or CSS pixel or reference pixel).
*  The size of a reference pixel is the size of a pixel on a display that has 96 pixels per inch. 

## Relative Units
## Ems and Rems
* Ems and rems are proportional to the calculated and root font sizes, respectively. The calculated font size is the height of the current font in pixels. 
* The root font size is the height of the base font for the document: the font size designated for the html element. 
* If the calculated font size is 20 pixels and the root font size is 16 pixels, then 1.5em is 30px (20 * 1.5), while 1.5rem is 24px (16 * 1.5).
* You may find it easier to work with rems instead of ems since rems are consistent. Once you've set the root font size for a document, `1.5rem` means the same thing everywhere in that document. This relationship isn't true for ems; they compound.

## Auto
* The `auto` specificier, as a `width` or `length` tells the browser to try to fit the entire element including its margins in its container.
* As a left or right `margin` on a block element, it tells the browser to push the element all the way to the right or left.
  * You can center a `block` element by setting right and left `margin` to `auto`.
* As a top or bottom `margin`, `auto` is equal to 0.
* Helpful diagram illustrating difference between `width: auto` and `width: 100` [here](http://d3jtzah944tvom.cloudfront.net/202/images/lesson_2/measurement-units-02.png)

# Images

## JPG
* The jpg format uses a _lossy_ form of compression, in other words, it trades off image quality for file size.
* If you edit a jpg, the resulting file has less detail than the original. If you edit again it loses even more detail.
* You can set loss levels when saving a jpeg.
* In general, jpgs don't work well for CSS backgroung images.

## PNG
* PNGs use compression but it is non-lossy. Lack of lossiness means larger file size.
* pngs are ideal for images that need their details.

## The img element
* `<img>` is a self-closing tag. It has two attributes: `src` and `alt`

### Figure and Figcaption
* If you want a caption for your image, you could use a `<p>` tag or group them in a `<div>` but this would not be semantic.
* The `figure` and `figcaption` elements can help
  ```css
  <figure>
    <img src="masthead.jpg" alt="Sunset over the forest" />
    <figcaption>The sun sets over the dense forest</figcaption>
  </figure>
  ```

# Lists
## Unordered Lists
    ```css
    <ul>
      <li>Red</li>
      <li>Orange</li>
      <li>Yellow</li>
      <li>Green</li>
      <li>Blue</li>
      <li>Indigo</li>
      <li>Violet</li>
    </ul>
    ```
## Ordered Lists
    ```css
    <ol>
      <li>Red</li>
      <li>Orange</li>
      <li>Yellow</li>
      <li>Green</li>
      <li>Blue</li>
      <li>Indigo</li>
      <li>Violet</li>
    </ol>
    ```
## Description Lists
* *_Description Lists_* contain a list of terms and definitions. Each item in the list includeds one or more terms and one or more definitions.
* Examples of description lists include dictionaries and bibliographies.
    ```css
    <dl>
      <dt>Unordered</dt>
      <dd>A simple list with bullets.</dd>
      <dd>A plain list with no bullets or sequence numbers.</dd>
    
      <dt>Ordered</dt>
      <dd>A simple list with sequence numbers or letters.</dd>
    
      <dt>Description</dt>
      <dt>Definition</dt>
      <dd>A list with terms and definitions.</dd>
    </dl>
    ```
## Navigation Menus
* Developers often use unordered lists to construct navigation menues, both vertical and horizontal.
* An example:
    ```css
    <nav>
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">Projects</a></li>
        <li><a href="#">Team</a></li>
        <li><a href="#">Help</a></li>
      </ul>
    </nav>
    ```
* Note the `list-style-type` property can be used to remove bullets from lists in CSS.

## Making Lists Horizontal
* To make a list horizontal:
  1. Set `li` to `display: inline-block`
  2. Distibute the width of `li` to evenly fit the width of the `ul` or `ol` element. For example, if `ol` has a width of `100%`, with four `li`s, set a width of `25%`.
  3. Set `ul` or `ol` `font-size` to `0` to get rid of whitespace between `li`s. Then set the `font-size` for `li` elements.

# Tables
* The <table> tag defines a table.
* The <tr> tag defines a single row in a table.
* The <td> tag defines a single cell of content in a table. Each row includes zero or more cells.
* The <th> tag defines a single heading. The first cell in a row or column is typically a heading, but this is not required.
* <thead>, <tbody>, and <tfoot> each define a set of one or more rows that comprise the header, body, and footer rows of a table. These are also not required.
* You can also add the scope attribute to identify th elements as row (scope="row") or column (scope="col") headings.
* Example:
```html
<table>
  <thead>                              <!-- heading rows -->
    <tr>                                 <!-- row 1 -->
      <th scope="col">Color Name</th>      <!-- column header 1 -->
      <th scope="col">Color Hex</th>       <!-- column header 2 -->
      <th scope="col">Color Decimal</th>   <!-- column header 3 -->
    </tr>
  </thead>

  <tbody>                              <!-- body rows -->
    <tr>                                 <!-- row 2 -->
      <th scope="row">red</th>             <!-- row header (column 1) -->
      <td>#f00</td>                        <!-- data cell 1 (column 2) -->
      <td>255, 0, 0</td>                   <!-- data cell 2 (column 3) -->
    </tr>

    <tr>                                 <!-- row 3 -->
      <th scope="row">green</th>           <!-- row header (column 1) -->
      <td>#0f0</td>                        <!-- data cell 1 (column 2) -->
      <td>0, 255, 0</td>                   <!-- data cell 2 (column 3) -->
    </tr>

    <tr>                                 <!-- row 4 -->
      <th scope="row">blue</th>            <!-- row header (column 1) -->
      <td>#00f</td>                        <!-- data cell 1 (column 2) -->
      <td>0, 0, 255</td>                   <!-- data cell 2 (column 3) -->
    </tr>
  </tbody>

  <tfoot>                              <!-- footer -->
    <tr>                                 <!-- row 5 -->
      <td>name</td>                        <!-- data cell 1 (column 1) -->
      <td>#rrggbb</td>                     <!-- data cell 2 (column 2) -->
      <td>red, green, blue</td>            <!-- data cell 3 (column 3) -->
    </tr>
  </tfoot>
</table>
```
# Forms

## The `form` tag
* The `form` tag is the parent for all form-related tags.
* The most important `form` attributes are `action` and `method`.
* A form should take at least one `input`, `textarea`, or `select` tag. Without one, the form is useless.

### The `method` attribute
* The `method` attribute tells the browser whether it should use the HTTP GET or HTTP POST method when sending the data.
* Use `method="get"` when requesting info from the server. Use `method="post"` when updating data on the server.

### The `action` and `formaction` attributes
* `action` provides the URL to which the browser sends the request.
* Individual action items (`button` and input type="submit" elements) in a form can overrive the form's `action` value by using the `formaction` attribute.

## The `fieldset` tag
* The `fieldset` is an optional tag. It groups related data. Most browsers draw a border around fieldset groups but, of course, this can be undone with CSS.
* Generally, the `fieldset` tag is used to provide semantic data to the browswer and to provide devs with a helpful CSS reference for layout/styling.
* ex: 
  ```html
  <form action="/login" method="post">
    <fieldset>
      <input type="text" name="username" />
      <input type="password" name="password" />
    </fieldset>
    <fieldset>
      <input type="submit" name="Save" />
      <input type="submit" name="Forgot Password" formaction="/forgot" />
    </fieldset>
  </form>
  ```
## The `input` tag
* The input tag is self-closing.
* It describes a "control" or a "widget".
* Each `input` requires a `type` attribute.
* Most `input` widgets require a `name` attribute. This allows the browser to indentify each data item and allows back-end apps to reference them.
  ```html
  <input type="text" name="city" />
  <input type="password" name="password" />
  <input type="submit" value="Save" />
  ```
## The `label` tag
* The `label` tag provides a way to associate some identifying text with an input field.
  ```html
  <label for="phone">Phone</label>
  <input type="text" id="phone" name="phone_number" />
  ```
  In this example, the broswer uses the `for` attribute and the `id` attribute to associate the `label` and the `input`.
* Can also use `label` tags as containers:
  ```html
  <label>
    Phone
    <input type="text" name="phone" />
  </label>
  ```

## A complete form example
  ```html
  <form action="#" method="post">
    <fieldset>
      <h1>Log In</h1>
      <fieldset>
        <label for="username">Username</label>
        <input type="text" name="username" id="username" />
      </fieldset>
  
      <fieldset>
        <label for="password">Password</label>
        <input type="password" name="password" id="password" />
      </fieldset>
  
      <fieldset>
        <input type="submit" value="Log In" />
        <input type="submit" value="Delete account"
               formaction="/account/delete" />
        <input type="submit" value="Forgot password"
               formaction="/account/password" />
        <input type="reset" value="Reset" />
      </fieldset>
    </fieldset>
  </form>
  ```
  
## Common `input` `type`s

### `text`
Simple text entry field. Can use `maxlength` attribute to specify input's maximum length.

### `password`
Single-line text field with obscured input values. Also can use `maxlength` attribute.

### `email`
Allows email addresses of the form `username@domain`. Browsers will try to prevent inaccurately formatted emails. But devs should perform their own validation.

### `tel`
Allows input of a phone number. No validation, as phone numbers vary so much from country to country.

### `checkbox`
Allows the user to choose one or more of a series of yes/no-type options.
The `value` attribute gives the value the form sends to the server. The `checked` attribute pre-selects checkboxes.
The `name` attribute names a set of related checkboxes.
The broswer will send a `name=value` pair for each selected box and no value at all for unselected boxes.

### `radio`
Lets user choose zero or one from a list of options.
Takes `name`, `value`, and `checked` attributes as well.

### `submit`
Creates a button that the user can click to submit the contents of the form to the server.
The `action` attribute in the `form` tag typically provides the URL of the server. This can be overriden with the `formaction` attribute.

### `reset`
A button that the user can click to reset the contents of the form to its default values. *Clicking reset does not send a request to the server.*

## Cool Attributes to Keep in Mind

### `placeholder`
For text, shows display only text when its empty.

### `required`
Form won't submit until a value for this input control is present.

## Select and Textarea

### `textarea`
Lets users input multiple lines of text. Unlike `text` inputs, `textarea` retains all carriage returns, newlines, and other whitespace characters.
No `value` attribute. Default values should be placed within open and closed tags.
```html
<form action="#" method="post">
  <fieldset>
    <label>
      Comment
      <textarea name="tweet" rows="5" cols="40">I got 20% off my first purchase at joesburgers.com! You can too!</textarea>
    </label>
  </fieldset>
</form>
```
`textarea` uses `rows` and `cols` attribute to control the height and width of the box. *This is overriden by the CSS `height` and `width` properties.

### `select` element
`select` creates a drop-down list of options from which the user can select zero or more optios.
Two possible child elements, `option` and `optgroup`.
Uses `name` attribute like other form elements but uses the `option` elements within it to describe the values shown to the user and sent to the server.

* The `option` element
  An `option` defines one of the choices a user can make in a `select` tag. *A `select` element is useless without `option`s.*
  Options can have a `value` attribute. If no `value` attribute is present, the browser sends the text contained by the `option` element to the server instead.
  `select` elemetns often have a disabled placeholder option that says something like "Choose one". Typically the value is an empty string.

  ```html
  <form action="#" method="post">
    <fieldset>
      <label>
        Colors
        <select name="color">
          <option value="" disabled selected>Choose one</option>
          <option value="#f00">Red</option>
          <option value="#0f0">Green</option>
          <option value="#00f">Blue</option>
        </select>
      </label>
    </fieldset>
  </form>
  ```

  By default, select lets the user choose precisely one option or leave the option unselected if it contains a disabled selected option as shown above. 
  If you add the `multiple` attribute, the user can select more than one option.
  
  ```html
  <form action="#" method="post">
    <fieldset>
      <label>
        Choose Your Favorite Movies
        <select name="favorites" multiple size="4">
          <option value="" disabled selected>Select One or More</option>
          <option>2001: A Space Odyssey</option>
          <option>Arrival</option>
          <option>Close Encounters of the Third Kind</option>
          <option>District 9</option>
          <option>Guardians of the Galaxy</option>
          <option>Interstellar</option>
          <option>Serenity</option>
          <option>Silent Running</option>
        </select>
      </label>
    </fieldset>
  </form>
  ```