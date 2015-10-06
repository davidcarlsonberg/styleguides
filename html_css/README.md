Hook & Loop : Coding Standards



em
Pronounced like the letter “m”.
em is relative to the parent element.
The basic idea: modify the base font-size on the body using a percentage to achieve 10px as the base measurement upon which further em calculations are made.

*Note: Resizing body {font-size } to 62.5% will not necessarily reset the text for a browser to 10px and allow for the calculations below. This is only if the browser’s default settings have not been altered by the user and/or the browser adheres to the default size for ‘medium’ text being 16px. You can circumvent this by declaring a body size in pixels instead of percentage, e.g., body { font-size: 10px; }.

In order to account for User Accessibility, it should be best practice to set em and rem relative to a base unit of 100%. This allows the user to control the initial size.

child pixels / parent pixels = child ems
or
child ems * parent pixels = child pixels

body { font-size: 62.5%; }
h1 { font-size: 2.4em; } /* =24px */
p { font-size: 1.4em; } /* =14px */
li { font-size: 1.4em; } /* =14px */

For nested lists (or any nested item), the font-size percentage increase will cascade and grow the font-size of the child lists. Each child li will compound in size based upon its parent. Fix this with li li { font-size: 1em; }. Declare any child element as  1em  if you do not want it compounded.

em allows for greater control in that you can define multiple base font-sizes for different sections of your page.


rem
rem is relative to the root (html) element. This allows you do define a single font-size on the html element and define all rem units to be a percentage of that.

html { font-size: 62.5%; }
body { font-size: 14px; font-size: 1.4rem; } /* =24px */
h1 { font-size: 24px; font-size: 2.4rem; } /* =24px */

rem allows for easier scaling of type across an entire page.

rem is not supported in IE<9. A proper fallback is declaring a px value just prior to the rem declaration.
e.g.,
h2 { font-size: 18px; font-size: 1.8rem; }

em or rem for padding and margins

Most likely rem is best…because it is based off of the html or root and margins and padding should be percentagers that make sense design-wise site-wide.


line-height
Should be calculated as unitless. A unitless line-height declaration will descend to the children of that element as a multiplier for line-height, multiplying the calculated font-size for each element by itself to calculate the line-height of each element.

e.g.,
<ul>
  <li>I’m a list item with a <span>span text</span>.</li>
</ul>

ul { font-size: 15px; line-height: 1; }
li { font-size: 10px; }
span { font-size: 80%; }

effectively becomes:

ul { font-size: 15px; line-height: 1; }
li { font-size: 10px; line-height: 10px; }
span { font-size: 80%; line-height: 8px; }

letter-spacing
Should also be measured in unitless dimensions as a multiplier of the current font-size.



NOTES
FLOAT
You should always place a width on floated items. Either explicitly or implicitly. Otherwise, it will fill its containing block horizontally, just like non-floated content, leaving no room for other content to flow around it.
CLEAR
Elements positioned after a floated element will necessarily wrap after that floated element unless told to clear that element.
Clear the position of the float above…or clear both.

¿¿¿rem for borders???
