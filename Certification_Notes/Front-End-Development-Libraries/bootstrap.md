# Bootstrap

- In bootstrap, you can easily make an image responsive by adding the `img-responsive` class.

- To center a text, we can simply add the `text-center` class.

- Normally, your button elements with the btn and btn-default classes are only as wide as the text that they contain.

- By making them block elements with the additional class of btn-block, your button will stretch to fill your page's entire horizontal space and any elements following it will flow onto a "new line" below the block.

- The btn-primary class is the main color you'll use in your app. It is useful for highlighting actions you want your user to take.

- Bootstrap comes with several pre-defined colors for buttons. The btn-info class is used to call attention to optional actions that the user can take.

- Create a new block-level Bootstrap button below your Like button with the text Info, and add Bootstrap's btn-info class to it.

- The btn-danger class is the button color you'll use to notify users that the button performs a destructive action, such as deleting a cat photo.

- Create a button with the text Delete and give it the class btn-danger.

- Bootstrap uses a responsive 12-column grid system, which makes it easy to put elements into rows and specify each element's relative width. Most of Bootstrap's classes can be applied to a div element.

- Bootstrap has different column width attributes that it uses depending on how wide the user's screen is. For example, phones have narrow screens, and laptops have wider screens.

- Take for example Bootstrap's col-md-* class. Here, md means medium, and * is a number specifying how many columns wide the element should be. In this case, the column width of an element on a medium-sized screen, such as a laptop, is being specified.

- In the Cat Photo App that we're building, we'll use col-xs-*, where xs means extra small (like an extra-small mobile phone screen), and * is the number of columns specifying how many columns wide the element should be.

- Put the Like, Info and Delete buttons side-by-side by nesting all three of them within one `<div class="row">` element, then each of them within a `<div class="col-xs-4">` element.

- The row class is applied to a div, and the buttons themselves can be nested within it.

- Put the Like, Info and Delete buttons side-by-side by nesting all three of them within one `<div class="row">` element, then each of them within a `<div class="col-xs-4">` element.

- You can use spans to create inline elements.

- Font Awesome is a convenient library of icons. These icons can be webfonts or vector graphics. These icons are treated just like fonts. You can specify their size using pixels, and they will assume the font size of their parent HTML elements.

- You can use Bootstrap's col-xs-* classes on form elements, too! This way, our radio buttons will be evenly spread out across the page, regardless of how wide the screen resolution is.

- In Bootstrap, the .container-fluid class is used to create a full-width container that spans the entire width of the viewport. This class is particularly useful for responsive design, as it allows the layout to adjust fluidly to any screen size without leaving extra space on the sides.

- Bootstrap has a class called well that can create a visual sense of depth for your columns.

- Not every class needs to have corresponding CSS. Sometimes we create classes just for the purpose of selecting these elements more easily using jQuery.