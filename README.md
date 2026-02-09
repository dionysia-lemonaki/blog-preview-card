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

![mobile screenshot](/assets/images/screenshots/mobile-screenshot.jpeg)

Desktop:

![desktop screenshot](/assets/images/screenshots/desktop-screenshot.jpeg)

### Links

- [Solution URL](https://www.frontendmentor.io/solutions/blog-preview-card-OWoG-5ePjI)
- [Live site URL](https://blog-preview-card-dionysialemonaki.vercel.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow

### What I learned

In the HTML, I used an `article` element to semantically represent an independent, standalone blog preview card that can be reused. I then gave the card an accessible name by associating it with its title using `aria-labelledby`.

```html
<article aria-labelledby="html-css-foundations">
  ...
  <h2 class="card__title" id="html-css-foundations">
    <a href="#" class="card__link">HTML & CSS foundations</a>
  </h2>
</article>
```

For the images, I provided `width` and `height` attributes to reserve space and prevent layout shift. I also treated both of them as purely decorative as they don't convey any important information to users. I did this by leaving the `alt` attribute empty (`alt=""`), effectively hiding them from assistive technologies.

Lastly, I used the `time` element with the `datetime` attribute in YYYY-MM-DD format to semantically represent the publication date.

```html
<p>Published <time datetime="2023-12-21">21 Dec 2023</time></p>
```

In the CSS, the font sizes for the category, date, title and description are slightly smaller on mobile. To fluidly scale the typography from smaller to larger screens witout using media queries, I used the `clamp()` function with values generated from [Utopia](https://utopia.fyi/clamp/calculator/?a=320,1440).

```css
--fs-xs: 0.75rem;
--fs-sm: 0.875rem;
--fs-base: 1rem;
--fs-xl: 1.25rem;
--fs-2xl: 1.5rem;

--fluid-sm: clamp(var(--fs-xs), 0.7143rem + 0.1786vw, var(--fs-sm));
--fluid-base: clamp(var(--fs-sm), 0.8393rem + 0.1786vw, var(--fs-base));
--fluid-lg: clamp(var(--fs-xl), 1.1786rem + 0.3571vw, var(--fs-2xl));
```

This blog card acts as a signpost to other content. When a user clicks on it, they should be taken to the actual blog post, so it makes sense to make the whole card clickable rather than just its title. The [Inclusive Components – Cards](https://inclusive-components.design/cards/) chapter taught be how to achieve this, with the only difference that I used the `inset` property instead of `top`, `right`, `bottom` and `left` properties.

```css
.card {
  position: relative;
}

.card__link {
  text-decoration: none;
  color: inherit;

  &::after {
    position: absolute;
    content: "";
    inset: 0;
  }
}
```

Lastly, I added hover and focus states. For focus styles, I used `:focus-visible` on the link and `:focus-within` on the card itself.

```css
.card {
  box-shadow: 8px 8px 0 var(--black);
  display: flex;
  &:hover,
  &:focus-within {
    box-shadow: 16px 16px 0 var(--black);
  }
}

.card__link {
  text-decoration: none;
  color: inherit;

  &:hover,
  &:focus-visible {
    color: var(--yellow);
  }

  &:focus-visible {
    outline: 4px dotted var(--gray-950);
    outline-offset: 2px;
  }
}
```
