# Basic HTML
#### HTML
- The `main` element represents the main and unique content of a page to increase accessibility and SEO optimization. The content in main should not be repeated in another page.
- An element without a closing tag is known as a `void` element.
- The `section` element is used to define sections like chapters, headers or topic in a document. It helps with accessibility and SEO optimization.
- The figure element represents self-contained and allows you to associate image with caption.
---
<br>

- To let users choose a specific value from a set of values use input with type `radio`.
- To make it so that selecting one radio button deselects another, you need to make sure all the radio inputs have the same name attribute.
- To make a radio button act like a checkbox, you need to add the attribute `checked` to the radio button that you want to be checked.
- The fieldset element groups related form elements together and they appear in a new line.
- The legend element is used to label the fields within a fieldset.

### CSS
- For the styling of a page to look similar on mobile, you need to add a meta element with a special content attribute. `<meta name="viewport" content="width=device-width, initial-scale=1.0" />`
- The `article` element in HTML is designed to represent a self-contained composition in a document, page, application, or site, which is intended to be independently distributable or reusable, such as in syndication.
- Examples of content that can be encapsulated within an article element include forum posts, magazine or newspaper articles, blog entries, user-submitted comments, interactive widgets, or any other independent item of content.
- margin adds spacing outside the element and padding adds spacing inside the element.
- On a very wide screen, the styling can appear a bit too wide. To fix that, use max-width to set a maximum width for the element.
- For h1 element, there is a little top-margin by default.
- You can use negative margin to move an element further away from its normal position.
- You can use negative padding to move an element further away from its normal position.

### CSS Colors
- When margin has two values, the first value is for top and bottom and the second value is for left and right.
- When adding multiple classes to a div, the styles of the later classes may override the styles of the earlier classes.
- There are two color models: RGB and CMYK. RGB is used in CSS.
- In RGB, the colors begin as black (0, 0, 0) and the colors end as white (255, 255, 255), and they change as different red, green, and blue values are added.
---
<br>

- A color wheel is a circle where similar colors are near each other, and different ones are futher apart.
- Two colors that are opposite from each other are called complementary colors.
- If two complementary colors are combined, they produce gray.
- But when placed side by side, they produce strong visual contrast and appear brighter.
- It's best practice to avoid using two very bright colors next to each other as it can be distracting if overused.
- It's better practice to choose one color as the dominant color and use its complementary color as an accent to bring attention to certain content.

---
<br>

- Hex values are also used for colors.
- Hex starts with `#` and takes 6 characters from 0-9 and A-F.
- The first 2 characters represent the red value, the next 2 characters represent the green value, and the last 2 characters represent the blue value.
- The first character of each color can be 0-9 or A-F.
- The HSL also represents colors.
- CSS HSL accepts 3 values: a number from 0-360 for hue, a percentage from 0% to 100% for saturation, and a percentage from 0% to 100% for lightness.
- You must add % sign to saturation and lightness values.

---
<br>

- A gradient is when one color transitions to another color.
- CSS linear gradient function actually creates an image element usually paired with the background property which can accept an image as value.
```CSS
linear-gradient(gradientDirection, color1, color2, ...);
```
- gradientDirection is the direction of the line used for the transition. color1 and color2 are color arguments, which are the colors that will be used in the transition itself. These can be any type of color, including color keywords, hex, rgb, or hsl.
- Color-stops allow you to fine-tune where colors are placed along the gradient line. They are a length unit like px or percentages that follow a color in the linear-gradient function.
```css
linear-gradient(90deg, red 90%, black);
```
- You can set the opacity for an element with the `opacity` property or with the alpha channel.
- You can use the rgba function where a is the alpha or opacity, taking values from 0 to 1.
---
<br>

- It's best practice to write out the properties and values even if they are applied by default to make the code readable.
- The box-shadow property is used to add one or more shadow to an element.

```css
box-shadow: offsetX offsetY color;
box-shadow: offsetX offsetY blurRadius color;
box-shadow: offsetX offsetY blurRadius spreadRadius color;
```
Here's how the offsetX and offsetY values work:

  - both offsetX and offsetY accept number values in px and other CSS units
  - a positive offsetX value moves the shadow right and a negative value moves it left
  - a positive offsetY value moves the shadow down and a negative value moves it up
  - if you want a value of zero (0) for any or both offsetX and offsetY, you don't need to add a unit. Every browser understands that zero means no change.
  - If a blurRadius value isn't included, it defaults to 0 and produces sharp edges. The higher the value of blurRadius, the greater the blurring effect is.
  - Like blurRadius, spreadRadius defaults to 0 if it isn't included.

---
---
<br>

- `vh` stands for viewport height and is equal to 1% of the height of the viewport.
- CSS has pseudo classes that can be used to style elements in different states.
- You can remove an earlier applied css by specifying property to be `unset`.
- You can select elements in css with attribute selectors such as input[type="checkbox"].