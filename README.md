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

5. Sticky Footer. We use this [elegant solution](https://css-tricks.com/a-clever-sticky-footer-technique/) to make sure your footer is always at the bottom of the site, even when you have very little content on the page. This expects your footer to be directly in the body. If you need your footer inside a div and not directly in the body, you can view and implement these [other solutions](https://css-tricks.com/couple-takes-sticky-footer/).

6. Setting overflow-x so there is no horizontal scrolling. We've all been there... This can happen if an item is absolute and off to the side, even if its hidden. We fix it so that it works nicely even on iOS, where the page sometimes can lose its "springiness".

7. Images are responsive. All images will shrink to fit in their containers by default.

## Utilities

Ok, so maybe a few utilities could be helpful. Only a few! Based on most websites out there, we created 8 utility classes that can be added in optionally by including the utilities file. These provide some basic and nifty layout classes to get you started, and to get any complexity out of the way. Sizing can be changed through the variables listed down below.

#### `.container-fluid`

creates your typical everyday container that goes full width. It just gives you padding on both the right and left, so your content is not up against the viewport edges.

#### `.container`

Like above, except it's got a max-width of 1200px (you can change this via the CSS variables).

#### `.container-left`

A cool class that makes a container that goes all the way to the left edge, but starts at where a normal container would start on its right side.

#### `.container-right`

A cool class that makes a container that goes all the way to the right edge, but starts at where a normal container would start on its left side.

#### `.screen-reader-text`

Important! For elements that will be read out loud on a screen reader device, but will be hidden on regular browsers. Good for ADA compliance.

#### `.vertical-spacing`

Very helpful for articles. Makes all items inside magically have good vertical rhythm. For some items, like headings, you may want to add styles to get those having more spacing with margins. Pairs well with container-content.

#### `.card-grid`

The perfect grid of cards! Using CSS Grid can be a bit scary, so we created a grid of cards that reflow nicely and can have a min and max size, changeable through CSS variables. It's cleaner than using flexbox for grids.

How to use:

```HTML
<div class="card-grid my-elements">...</div>
```

Then in your CSS, you can override the card-grids sizing. The defaults are:

```CSS
.my-elements{
  --card-min: 250px;
  --card-max: 1fr;
  --card-stretch: auto-fill; /* can be auto-fit too */
}
```

#### `.container-content`

This one is the last and most complex. It's very helpful for articles or the main content on a blog page. A lot of CMS's simply dump out the article and you have no control over the inner elements and their widths. For article text, you want a thin line width for easy reading, but for an image, or slideshow in the middle, you want to break out of that small container and go full width.

Thats where `.container-content` makes this easy. You surround the article with it and it gives each direct child a max-width. When you want to break out of that, simply give a child a class of:

1. `.container` - Breaks out and makes a container as you would expect.

2. `.container-fluid` - Breaks out and makes a container-fluid as you would expect.

3. `.full-width` - Breaks out and gives you the full real estate of the page back.

4. WordPress support - you can use `.alignwide` instead of `.container` and `.alignfull` instead of `.full-width`. The classes do the same thing.

## CSS Variables

There are variables found at the bottom of Crucial.CSS and utilities. You can override them in your project, or change them directly. Remember, you can also override variables inside classes and media queries. Here are all the variables:

```CSS
:root {
  /* font variable */
  --font-primary: system-ui, -apple-system, "Segoe UI", Roboto, Helvetica, Arial,
    sans-serif, "Apple Color Emoji", "Segoe UI Emoji";

  /* Default Font Size */
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

You can pull it in from a cdn

- [unpkg](https://unpkg.com/crucial.css@1.0.0/curcial.css)

### Usage With CDN

```html
<link rel="stylesheet" href="https://unpkg.com/crucial.css@1.0.0/crucial.css" />
<link
  rel="stylesheet"
  href="https://unpkg.com/crucial.css@1.0.0/utilities.css"
/>
```
