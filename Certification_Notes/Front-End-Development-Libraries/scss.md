# SCSS

- One feature of Sass that's different than CSS is it uses variables. They are declared and set to store data, similar to JavaScript.

- In JavaScript, variables are defined using the let and const keywords. In Sass, variables start with a $ followed by the variable name.

```scss
$main-fonts: Arial, sans-serif;
$headings-color: green;
```

- One example where variables are useful is when a number of elements need to be the same color. If that color is changed, the only place to edit the code is the variable value.

- Sass allows nesting of CSS rules, which is a useful way of organizing a style sheet.

example:
```scss
article {
  height: 200px;

  p {
    color: white;
  }

  ul {
    color: blue;
  }
}
```

- n Sass, a mixin is a group of CSS declarations that can be reused throughout the style sheet. The definition starts with the @mixin at-rule, followed by a custom name. You apply the mixin using the @include at-rule.
```scss
@mixin reset-list {
  margin: 0;
  padding: 0;
  list-style: none;
}

nav ul {
  @include reset-list;
}
```

- Your mixins can also take arguments, which allows their behavior to be customized. The arguments are required when using the mixin.
```scss
@mixin prose($font-size, $spacing) {
  font-size: $font-size;
  margin: 0;
  margin-block-end: $spacing;
}

p {
  @include prose(1.25rem, 1rem);
}

h2 {
  @include prose(2.4rem, 1.5rem);
}
```

- You can make arguments optional by giving the parameters default values.
```scss
@mixin text-color($color: black) {
  color: $color;
}

p {
  @include text-color(); /* color: black */
}

nav a {
  @include text-color(orange);
}
```

- The @if directive in Sass is useful to test for a specific case - it works just like the if statement in JavaScript.

```scss
@mixin make-bold($bool) {
  @if $bool == true {
    font-weight: bold;
  }
}
```

- And just like in JavaScript, the @else if and @else directives test for more conditions:

- The @for directive adds styles in a loop, very similar to a for loop in JavaScript.

- @for is used in two ways: "start through end" or "start to end". The main difference is that the "start to end" excludes the end number as part of the count, and "start through end" includes the end number as part of the count.

- Example start through end
    ```scss
    @for $i from 1 through 12 {
  .col-#{$i} { width: 100%/12 * $i; }
    }
    ```
- The #{$i} part is the syntax to combine a variable (i) with text to make a string.

- Sass also offers the @each directive which loops over each item in a list or map. On each iteration, the variable gets assigned to the current value from the list or map.

```scss
@each $color in blue, red, green {
  .#{$color}-text {color: $color;}
}
```

- A map has slightly different syntax. Here's an example:
    ```scss
    $colors: (blue:  #1e90ff, red:   #ff6347, green: #32cd32);

    @each $color, $value in $colors {
      .#{$color}-text { color: $value; }
    }
    ```

- Note that the $key variable is needed to reference the keys in the map.

- The @while directive is an option with similar functionality to the JavaScript while loop. It creates CSS rules until a condition is met.

- The @for challenge gave an example to create a simple grid system. This can also work with @while.

- Partials in Sass are separate files that hold segments of CSS code. These are imported and used in other Sass files. This is a great way to group similar code into a module to keep it organized.

- Names for partials start with the underscore (_) character, which tells Sass it is a small segment of CSS and not to convert it into a CSS file. Also, Sass files end with the .scss file extension. To bring the code in the partial into another Sass file, use the @import directive.

- Sass has a feature called extend that makes it easy to borrow the CSS rules from one element and build upon them in another.

- For example, the below block of CSS rules style a .panel class. It has a background-color, height and border.

- Now you want another panel called .big-panel. It has the same base properties as .panel, but also needs a width and font-size. It's possible to copy and paste the initial CSS rules from .panel, but the code becomes repetitive as you add more types of panels. The extend directive is a simple way to reuse the rules written for one element, then add more for another:

```scss
.big-panel{
  @extend .panel;
  width: 150px;
  font-size: 2em;
}
```