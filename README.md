# Frontend Mentor - Blog preview card solution

This is a solution to the [Blog preview card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/blog-preview-card-ckPaj01IcS). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)

## Overview

### The challenge

Users should be able to:

- See hover and focus states for all interactive elements on the page

### Screenshot

Mobile view:

![](./assets/images/Screenshot-mobile.png)

Desktop view:

![](./assets/images/Screenshot-desktop.png)

### Links

- [Solution URL](https://www.frontendmentor.io/solutions/blog-preview-card-using-css-grid-and-flexbox-0tskbl_izG)
- [Live site URL](https://blog-preview-card-eta-one.vercel.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid

### What I learnt

A lot!

- How to create responsive typography without using media queries. In the mobile layout, the font sizes of the category, date, title and description are slightly smaller. To achieve this without media queries, I used the `clamp` calculator from [Utopia](https://utopia.fyi/clamp/calculator/?a=0,0) to fluidly scale the typography between smaller to larger screens.
- How to make an entire card clickable, from the [Inclusive Components - Cards](https://inclusive-components.design/cards/) book by Heydon Pickering. The code below makes the link cover the entire card, making the whole card clickable:

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

- About the difference between `:focus` and `:focus-within`. The `:focus` pseudo-class applies _only to the element that receives focus_. The `focus-within` pseudo-class, on the other hand, applies to an element if _any child element inside it receives focus_.
