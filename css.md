# Cascading Style Sheets Cheat Sheet

## Flex Layout

- one dimensional layout

`display` - sets the flex container if the value flex or inline-flex is passed, the flex containers has default values e.g. that the flex-direction row is used

`flex-direction` - indicates the direction of the flex layout, possible values are row, row-reverse, column, column-reverse

`flex-wrap` - indicates whether elements are wrapped at the end of the layout

```
.box {
	display: flex;
	flex-direction: row-reverse;
	flex-wrap: wrap;
}
```

`flex-flow` - combination of direction and wrap

```
.box {
	display: flex;
	flex-flow: row wrap;
}
```

`flex-grow` - if set to a positive integer, flex items can grow along the main axis from their flex-basis

`flex-shrink` - if set to a positive integer, flex items can shrink along the main axis from their flex basis

`flex-basis` - defines the size of an item in terms of the space it leaves as available space

[Flex Layout MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)

### Align content to the center

The flex layout can be used to align the content of an element to the center:

```html
<div class="container">
  <div class="center">Center</div>
</div>
```

```css
.container {
  display: flex;
  justify-content: center;
}
```

https://stackoverflow.com/questions/953918/how-to-align-a-div-to-the-middle-horizontally-width-of-the-page

## Bootstrap

Bootstrap is a collection of stylesheets which can easily applied to a web development project.

https://getbootstrap.com

https://github.com/twbs/bootstrap

### Button

https://getbootstrap.com/docs/4.0/components/buttons/

### Dropdowns

https://getbootstrap.com/docs/4.0/components/dropdowns/

### Navbar

https://getbootstrap.com/docs/4.0/components/navbar/

## References

[Mozilla Developer Network CSS Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS)

[W3C Cascading Style Sheets Specifications](https://www.w3.org/Style/CSS/Overview.de.html)
