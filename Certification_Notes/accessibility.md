# Accessibility

- A meta element for accessibility and SEO is the `description` definition. The value of the content attribute is used by search engines to summarize the page content.
- Navigation is a core part of accessibility, and screen readers rely on you to provide the structure of your page. This is accomplished with semantic HTML elements.
- The child combinator selector > is used between selectors to target only elements that match the second selector and are a direct child of the first selector.

- This can be helpful when you have deeply nested elements and want to control the scope of your styling.
- You can add a text that is only visible to screen readers by using the class of sr-only.
Then you need to give the following css:
```
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
}
```

- There is an address element specifically available for address which helps with SEO and accessibility.

- On the topic of visual accessibility, contrast between elements is a key factor. For example, the contrast between the text and the background of a heading should be at least 4.5:1.