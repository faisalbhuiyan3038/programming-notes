# CSS Positioning

- position property has these available values:
    - static
    - relative
    - absolute
    - fixed
    - sticky

- Once you set the `position` property of the element, you can move the element around by setting a pixel or a percentage value for one or more of the `top`, `right`, `left`, or `bottom` properties.

- `static` is the default positioning for all elements. If you assign it to an element, you won't be able to move it around with `top`, `right`, `left`, or `bottom`.

- When you use the `relative` value, the element is still positioned according to the normal flow of the document, but the `top`, `left`, `bottom`, and `right` values become active.

- When you use the `absolute` value for your position property, the element is taken out of the normal flow of the document, and then its position is determined by the `top`, `right`, `bottom`, and `left` properties.

- `fixed` is a position property value that lets you make an element fixed to the page no matter where the user scrolls to on the page.

- `sticky` positioning is a hybrid of relative and fixed positioning. It allows an element to stick to a specific position within its containing element or viewport, based on the scroll position.

- The `transform` property allows you to modify the shape, position, and size of an element without changing the layout or affecting the surrounding elements. It has functions such as translate(), rotate(), scale(), skew(), and matrix().

- `z-index` is a property you can use to define the order of overlapping HTML elements. Any element with a higher z-index will always be positioned over an element with a lower z-index

