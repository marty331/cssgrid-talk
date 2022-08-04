# CSS Grid

## Definition
CSS Grid is a two-dimentional grid-based layout system.  

## Previous Tooling
Before Grid existed there were plenty of options for developers to layout web pages, such as these fairly simple options - tables, floats, positioning, inline-block.  Flexbox is a better option but it only provides one-directional flow.  Each of these elements still have their use cases today and are not irrelavant.

## Advantages
- Grid solves the need for many of the hacks that were needed for the previous elements to work. 
- Provides an easy way to structure elements on a page.

## Layout
Grid allows the develper to either implicitly or explictly define rows and columns.

## 1-start Example
A grid is defined with three columns and two rows.  The rows are 50px in height and the columns are as follows: 1fr 200px 1fr.  The center column is always 200px wide no matter the size of the user's display.  The first and third columns are measureed in fr, fr is shorthand for fraction and adjusts to the available space.  fr can be declared as 2fr, .5fr, and so on.

## 2-media Example
With the use of media queries we can size the rows and columns whenever a smaller device is detected.  The HTML has not changed only the css changed.  The media queries control values of the rows and columns.  When a small screen is detected the row size is set to 100px and the column sizes are set to repeat 3 columns of 1fr each.  When a medium sized screen (such as an iPad) is detected, the row size is set to 100px and the column sizes continue to be 1fr 200px 1fr.

## 3-layout Example

### Standard Layout
This example is making big changes! For the standard layout we are adding 3 additional rows which are 50px 1fr 1fr 1fr 50 px, so the two rows at the beggining and end are set to 50 px in height and the 3 rows in the middle auto-scale based on the screen size.  The columns are now 1fr 1fr 200px, so the first two columns now scale based on the screen width and the last column is fixed at 200px.  In the individual classes now control which row and column they appear in, for example 
```css
.one {
  background-color: red;
  grid-column: 1 / 3;
  grid-row: 2;
  height: 250px;
}
```
grid-column for class one spans from the first column to the start of the third column.
grid-row for class one is set to the second row.

### Medium Layout
For the medium sized layout the rows are now set to auto (they are implictly defined and adjust based on the html and remaining css are defined) and the columns are repeat(3, 1fr) (repeating 3 1fr columns).   What is uniqe about this layout is we are defining the exact row and column placement as:
```css
 .two {
    grid-column: 3;
    grid-row: 3;
    height: 350px;
  }
```
Here the grid-column is set to 3 and the grid-row is set to 3, height is also defined as the rows are defined as auto, so if no height existed then the element would be flat.

### Small Layout
Finally we have the layout for the small screen.  We still have the rows defined as auto and the columns defined as repeat(3, 1fr).  Notice the height is defined differetnly in the class definition for most of the classes.  Again the exact row and column placement are determined by the css:
```css
 .ads {
    grid-column: 1 / 4;
    grid-row: 3;
    height: 200px;
  }
```
grid-column spans from column 1 to the beginning of column 4.  If you notice above, we only defined 3 columns, however for the element to take up the entire width of the viewable area we have to go past the column we want to cover (this applies to rows as well).
grid-row is defined as the third row.

## 4-named Example
Grid Template Areas specifies named grid-areas which estiblish the cells in a grid and assigning them names.  Grid Areas can reference them by name, not by row/column numbers.

### Standard Layout
The standard layout is setup in the format of what you might image a blog page to look like in your browser.  In this example we individually define grid-template-columns (repeat(3, 1fr)) and grid-template-rows (100px repeat(3, 250px) 100px).  Then we define grid-template-areas as:
```css
grid-template-areas:  "header header header"
                        "main main ad"
                        "second second ad"
                        "third third ."
                        "footer footer footer";
```
At this point we have created six individual named areas and one unamed area that will be empty - which is represented by the dot in the row that defines the area named third.  We can now place css elements where we want by assigning them to a grid-area as:
```css
.three {
  background-color: green;
  grid-area: third;
}

.ads {
  background-color: orange;
  grid-area: ad;
}

.header {
  background-color: blue;
  grid-area: header;
}
```

### Medium Layout
To rearrage the layout for a medium sized screen we simply update the rows and columns and add a new media query and redefine the grid-template-areas - 
```css
@media only screen and (max-width: 960px) {
  .container {
    display: grid;
    grid-template-columns: 1fr .5fr;
    grid-template-rows: 50px repeat(3, 200px) 50px;
    grid-template-areas:  "header header"
                          "main ad"
                          "second ad"
                          "third ."
                          "footer footer";
  }
}
```
Now when  medium sized screen is detected the layout adjusts to two columns and retains the original six named areas but layed out slightly different.

### Small Layout
Finally we adjust the layout for small screens to have a single column, multiple rows that are given a specific height each and adjust our named areas to display properly on a small screen -
```css
@media only screen and (max-width: 540px) {
  .container {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 50px repeat(4, 200px) 50px;
    grid-template-areas:  "header"
                          "main"
                          "ad"
                          "second"
                          "third"
                          "footer";
  }
}
```
