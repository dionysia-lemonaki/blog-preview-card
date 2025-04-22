# Frontend Mentor - Blog preview card solution

This is a solution to the [Blog preview card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/blog-preview-card-ckPaj01IcS). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learnt](#what-i-learnt)

## Overview

### The challenge

Users should be able to:

- See hover and focus states for all interactive elements on the page

### Screenshot

Mobile layout:

![](./assets/images/Screenshot-mobile.png)

Desktop layout:

![](./assets/images/Screenshot-desktop.png)

### Links

- [Solution URL](https://www.frontendmentor.io/solutions/blog-preview-card-using-css-flexbox-5abgps9uwr)
- [Live site URL](https://blog-preview-card-eta-one.vercel.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow

### What I learnt

A lot!

I learnt how to create responsive typography without using media queries.

In the mobile layout, the font sizes for the category, date, title and description are slightly smaller. To fluidly scale the typography between smaller to larger screens without using media queries, I used the `clamp()` function with values generated from [Utopia](https://utopia.fyi/clamp/calculator?a=320,1440).

I also learnt how to make an entire card clickable. I used the code from Heydon Pickering's [Inclusive Components - Cards](https://inclusive-components.design/cards/) article. The snippet below makes the link cover the entire card, making the whole card clickable:

```css
.blog-card {
  position: relative;
}

.blog-card__link::after {
  content: "";
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
```

Lastly, I learnt about the difference between the `:focus`, `:focus-visible` and `:focus-within` pseudo-classes.

The `:focus` pseudo-class matches an element that receives focus. The `:focus-visible` pseudo-class works similarly to `:focus`, but the browser decides whether the focus should be visibly indicated. The `:focus-within` pseudo-class matches an element that contains a focusable element.
