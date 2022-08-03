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

## 1-Start Example
A grid is defined with three columns and two rows.  The rows are 50px in height and the columns are as follows: 1fr, 200px, 1fr.  The center column is always 200px wide no matter the size of the user's display.  The first and third columns are measureed in fr, fr is shorthand for fraction and adjusts to the available space.  fr can be declared as 2fr, .5fr, and so on.