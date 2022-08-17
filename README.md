<div align="center">
	<img src="media/crucial-logo.svg" alt="crucial.css logo">
	<br/>
</div>

# Crucial.css

Crucial CSS sets up your CSS with what you need to start styling and nothing more. Crucial has all the stuff found in [modern normalize](https://github.com/sindresorhus/modern-normalize) to normalize the differences between browsers. It takes things a bit further for you though by implementing a few things that will save you lots of hours of tinkering. Simple things you probably do everytime you make a site, either by yourself or through a framework. From resetting differences between browsers, to fixing the box-sizing, to setting images to be responsive, to font-sizes and more. This saves you time and removes a lot of confusion and pain points.

## Why Crucial?

The year is 2022, there is no need for a bloated framework anymore. Columns are easy to create by yourself with flexbox and CSS grid. And now with the gap property available on both, there is no more need to use padding to come up with some over-complicated math-based column system. And most utilities can be made yourself when you need them.

However, there still are a few issues. Unlike javascript, CSS still cannot be used out of the box in a real project. The reality is, CSS has a few weird quirks that need to be dealt with. Crucial aims to do that, while not being overwhelming.

## Crucial Features

1. We set box-sizing to border-box, using the [css-tricks](https://css-tricks.com/box-sizing/) method for better inheritance. Box-sizing is **crucial** to be set up at the beginning of a project, or it can become a nightmare later on. Trust me.

2. We set the root font-size to 62.5%. This makes it super easy to use rem units for your font-sizing. The rem unit is now using a base of 10. No more math! So 1.6rem is 16px, 2.4rem is 24px etc... It's easy!

3. A default font size of 1.6rem (16px), with a line-height of 1.5 has been set for the body and all things that inherit, including inputs. The default font size can be changed with the CSS variable `--fs-default`.

   The line-height of 1.5 is chosen because that is usually the best design practice for practical, normal font sizes (12px-30px). For your headings and larger fonts, you may need to increase the line-height.

4. Font-family CSS variable for easy changing of default body font. Change `--font-primary` to your chosen font.

5. Sticky Footer. We use this [elegant solution](https://css-tricks.com/a-clever-sticky-footer-technique/) to make sure your footer is always at the bottom of the site, even when you have very little content on the page. This expects your footer to be directly in the body, or directly inside a `.page-wrap` element. If you need a different setup with sticky footer, you can view and implement these [other solutions](https://css-tricks.com/couple-takes-sticky-footer/).

6. Images and SVG's are responsive. All images will shrink to fit in their containers by default.

7. Unordered lists found in a nav element have styles removed.

8. Headings have had their margins removed. This will force you to make conscious decisions for the margins and not rely on the default browsers.

## Utilities

Ok, so maybe a few utilities could be helpful. Only a few! Based on most websites out there, we created **9** utility classes that can be added in optionally by including the utilities file. These provide some basic and nifty layout classes to jumpstart your project, and to get any complexity out of the way. Sizing can be changed through the variables listed down below.

#### `.container-fluid`

Creates your typical everyday container that goes full width. It just gives you padding on both, the right and left, so your content is not up against the viewport edges. This is standard practice.

#### `.container`

Like above, except it's got a max-width of 1200px (you can change this via the CSS variables). It is also centered.

#### `.container-left`

A cool class that makes a container that goes all the way to the left edge, but starts at where a normal container would start on its right side.

#### `.container-right`

A cool class that makes a container that goes all the way to the right edge, but starts at where a normal container would start on its left side.

#### `.screen-reader-text`

For elements that will be read out loud on a screen reader device, but will be hidden on regular browsers. Good for ADA compliance.

#### `.vertical-spacing`

Very helpful for articles. Makes all items inside magically have good vertical rhythm. For some items, like headings, you may want to add styles to get those having more spacing with margins. Pairs well with `.container-content`.

#### `.page-wrap`

The page wrap is a special element when dealing with overflow-x. It's useful when you have absolute items positioned off the screen, but don't want horizontal scrolling, like a hidden mobile menu. This class fixes it, so that it works nicely even on mobile devices, where things can get wonky. You can implement it directly on the body element, or on a div that is a direct child of body. This element should hold everything on the page. It also makes sure position: sticky works as intended on a header or footer as you would expect. :)

```HTML
<body class="page-wrap">
		Everything....
</body>

OR

<body>
	<div class="page-wrap">
		Everything....
	</div>
</body>
```

#### `.card-grid`

The perfect grid of cards! Using CSS Grid can be a bit scary, so we created a grid of cards that reflow nicely and can have a min and max size, changeable through CSS variables. It's cleaner than using flexbox for grids.

How to use:

```HTML
<div class="card-grid custom-class">...</div>
```

Then in your CSS, you can override the card-grids sizing, using a custom class. The defaults are:

```CSS
.custom-class{
  --card-min: 250px;
  --card-max: 1fr;
  --card-stretch: auto-fill; /* can also be auto-fit */
}
```

#### `.container-content`

This one is the last and most complex. It's very helpful for articles or the main content on a blog page. A lot of CMS's simply dump out the article and you have no control over the inner elements and their widths. For example, you may want article text to have a narrow line width for easy reading, but for an image, or slideshow in the middle, you want to break out of that small container and go full width.

Thats where `.container-content` makes this easy. You surround the article with it and it gives each direct child a max-width. When you want to break out of that, simply give a child a class of:

1. `.container` - Breaks out and makes a container as you would expect.

2. `.container-fluid` - Breaks out and makes a container-fluid as you would expect.

3. `.full-width` - Breaks out and gives you the full real estate of the page back.

4. WordPress support - you can use `.alignwide` instead of `.container` and `.alignfull` instead of `.full-width`. The classes do the same thing.

See the demo to understand how it all works.

## CSS Variables

There are variables found at the bottom of Crucial.CSS and Utilities. You can override them in your project, or change them directly. Remember, you can also override variables inside classes and media queries, which is super helpful. Here are all the variables:

```CSS
:root {
  /* font variable */
  --font-primary: system-ui, -apple-system, "Segoe UI", Roboto, Helvetica, Arial,
    sans-serif, "Apple Color Emoji", "Segoe UI Emoji";

  /* Default Font Size 16px */
  --fs-default: 1.6rem;

   /* spacing variables */
  --gutter: 15px;
  --gap: calc(2 * var(--gutter));
  --vertical-spacing: 30px;

  /* container variables */
  --container-width: 1200px;
  --container-padding: var(--gap); /* used on left/right side of containers */

  --container-content-width: 70rem;

  /* z-index variables */
  --z-index-top: 99;
  --z-index-overlay: 95;
  --z-index-header: 80;
  --z-index-behind: -1;
}
```

## Browser support

- Latest Chrome
- Latest Firefox
- Latest Safari
- Latest Edge

## Install With NPM

```
$ npm install crucial.css
```

### Usage With NPM

```css
@import "node_modules/crucial.css/crucial.css";
/* optional */
@import "node_modules/crucial.css/utilities.css";
```

or

```html
<link rel="stylesheet" href="node_modules/crucial.css/crucial.css" />
<link rel="stylesheet" href="node_modules/crucial.css/utilities.css" />
```

## Install With CDN

You can pull it in from a CDN

- [unpkg - Crucial](https://unpkg.com/crucial.css@1.0.8/crucial.css)
- [unpkg - Crucial Utilities](https://unpkg.com/crucial.css@1.0.8/utilities.css)

### Usage With CDN

```html
<link rel="stylesheet" href="https://unpkg.com/crucial.css@1.0.8/crucial.css" />
<link
  rel="stylesheet"
  href="https://unpkg.com/crucial.css@1.0.8/utilities.css"
/>
```

If you feel there is something missing from Crucial, please reach out!

Shout out to Chris Coyer for teaching me CSS tips and tricks over the years. A lot of the major ones made it into Crucial.
