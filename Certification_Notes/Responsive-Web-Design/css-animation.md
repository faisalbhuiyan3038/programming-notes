# CSS Animation

- The `transform-origin` property is used to set the point around which a CSS tranformation is applied.

- You can target a second or third element of a single class like `.line` with `.line:nth-of-type(2)` in CSS.

- The `@keyframes` at-rule is used to define the flow of a CSS animation.

- Within the rule, you can create selectors for specific points in the animation sequence, such as 0% or 25%, or use `from` and `to` to define the start of a sequence.

- `@keyframes` rule requires a name to be assigned to them, which you use in other rules for reference. For example, the `@keyframes freeCodeCamp { }` rule would be named `freeCodeCamp`.
```css
@keyframes freeCodeCamp {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
}
```

- The `animation-name` property is used to link a `@keyframes` rule to a CSS selector.

- The `animation-duration` property sets how long the animation should sequence to complete.

- The `animation-iteration-count` property sets how many times the animation should repeat.

- The `animation-timing-function` property sets how the animation should progress over time.