# Frontend Mentor - Blog preview card solution

This is my solution to the [Blog preview card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/blog-preview-card-ckPaj01IcS).

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshots](#screenshots)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)

## Overview

### The challenge

Users should be able to:

- See hover and focus states for all interactive elements on the page

### Screenshots

Mobile:

![mobile screenshot](/assets/images/screenshots/screenshot-mobile.jpeg)

Desktop:

![desktop screenshot](/assets/images/screenshots/screenshot-desktop.jpeg)

### Links

- [Solution URL](https://www.frontendmentor.io/solutions/blog-preview-card-JBuA7ZUUyt)
- [Live site URL](https://blog-preview-card-dionysialemonaki.vercel.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Self-hosted variable fonts
- Flexbox
- Mobile-first workflow

### What I learned

For the HTML, I used an `article` element for the card component to semantically represent an independent, standalone blog preview card that can be reused. I then gave the card an accessible name by associating it with its title (`h2`) using `aria-labelledby`.

```html
<article aria-labelledby="html-css-foundations">
  ...
  <h2 id="html-css-foundations">
    <a href="#">HTML & CSS foundations</a>
  </h2>
  ...
</article>
```

For the images, I provided `width` and `height` attributes to reserve space and prevent layout shift. I also treated them as purely decorative as they don't convey any important information to users, so I left the `alt` attribute empty (`alt=""`), effectively hiding them from assistive technologies. For the author avatar specifically, since the author's name is right next to the image, using the name for the alt text would be repetitive and redundant.

Lastly, I used the `time` element with the `datetime` attribute in YYYY-MM-DD format to semantically represent the publication date.

```html
<p>Published <time datetime="2023-12-21">21 Dec 2023</time></p>
```

In the CSS, the font sizes for the blog preview card component – for the category, date, title and description – are slightly smaller on mobile. To fluidly scale the typography from smaller to larger screens without using media queries, I used the `clamp()` function with values generated from [Utopia](https://utopia.fyi/clamp/calculator?a=320,1440,16%E2%80%9448).

```css
:root {
  --fs-xs: 0.75rem; /* 12px */
  --fs-sm: 0.875rem; /* 14px */
  --fs-base: 1rem; /* 16px */
  --fs-xl: 1.25rem; /* 20px */
  --fs-2xl: 1.5rem; /* 24px */

  --fluid-sm: clamp(var(--fs-xs), 0.7143rem + 0.1786vw, var(--fs-sm));
  --fluid-base: clamp(var(--fs-sm), 0.8393rem + 0.1786vw, var(--fs-base));
  --fluid-xl: clamp(var(--fs-xl), 1.1786rem + 0.3571vw, var(--fs-2xl));
}
```

The card acts as a signpost to other content. When a user clicks on it, they should be taken to the actual blog post, so it makes sense to make the whole card clickable rather than just its title. The [Inclusive Components – Cards](https://inclusive-components.design/cards/) chapter taught me how to achieve this – the only difference is that I used the `inset` property instead of `top`, `right`, `bottom` and `left` properties.

```css
.card {
  position: relative;
}

.card__link {
  text-decoration: none;
  color: inherit;

  &::after {
    content: "";
    position: absolute;
    inset: 0;
  }
}
```

Lastly, I added hover and focus states to the card component. For focus styles, I used `:focus-visible` on the link and `:focus-within` on the card itself.

```css
.card {
  box-shadow: var(--shadow);

  &:hover,
  &:focus-within {
    box-shadow: var(--shadow-hover);
  }
}

.card__link {
  color: inherit;

  &:hover {
    color: var(--clr-text-hover);
  }

  &:focus-visible {
    color: var(--clr-text-hover);
    outline: 4px dotted var(--clr-border);
    outline-offset: 2px;
  }
}
```
