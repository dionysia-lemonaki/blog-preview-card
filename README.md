# Frontend Mentor - Blog preview card solution

This is my solution to the [Blog preview card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/blog-preview-card-ckPaj01IcS).

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshots](#screenshots)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learnt](#what-i-learnt)
  - [Useful resources](#useful-resources)

## Overview

### The challenge

Users should be able to:

- See hover and focus states for all interactive elements on the page

### Screenshots

Mobile:

![](/assets/images/screenshot-mobile.jpeg)

Desktop:

![](/assets/images/screenshot-desktop.jpeg)

### Links

- [Solution URL](https://www.frontendmentor.io/solutions/blog-preview-card-O4_l2MXPyn)
- [Live site URL](https://blog-preview-card-dionysialemonaki.vercel.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow

### What I learnt

I used an `article` element for the card and gave it an accessible name with `aria-labelledby`. Although `article` elements are not landmarks, screen reader users can use a shortcut to find them. So, the article will be announced as `HTML & CSS foundations article`.

In the mobile layout, the font sizes for the category, date, title and description are slightly smaller. To fluidly scale the typography from smaller to larger screens without using media queries, I used the `clamp()` function with values generated from [Utopia](https://utopia.fyi/clamp/calculator?a=360,1240).

```css
:root {
  /* Fluid type scale with clamp() */
  --text-fluid-sm: clamp(var(--fs-xs), 0.7143rem + 0.1786vw, var(--fs-sm));
  --text-fluid-md: clamp(var(--fs-sm), 0.8393rem + 0.1786vw, var(--fs-md));
  --text-fluid-lg: clamp(var(--fs-lg), 1.1786rem + 0.3571vw, var(--fs-xl));
}
```

Lastly, to make the whole card clickable, I relatively positioned the card component, added a pseudo-element to the link inside the heading and absolutely positioned it to cover the entire card.

```css
.card {
  position: relative;
}

.card__link::after {
  content: "";
  position: absolute;
  inset: 0;
}
```

### Useful resources

- [Inclusive Components – Cards](https://inclusive-components.design/cards/) - This chapter from Heydon Pickering's Inclusive Components book helped me make the whole card clickable. Instead of the `top`, `right`, `bottom` and `left` properties mentioned in the book, I used the `inset` property.
