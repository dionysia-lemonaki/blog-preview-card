# Frontend Mentor - Blog preview card solution

This is my solution to the [Blog preview card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/blog-preview-card-ckPaj01IcS).

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshots](#screenshots)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [Project notes](#project-notes)

## Overview

### The challenge

Users should be able to:

- See hover and focus states for all interactive elements on the page

### Screenshots

Mobile:

![](/assets/images/screenshots/mobile-screenshot.jpeg)

Desktop:

![](/assets/images/screenshots/desktop-screenshot.jpeg)

### Links

- [Solution URL](https://www.frontendmentor.io/solutions/blog-preview-card-KqmUh-8UbT)
- [Live site URL](https://blog-preview-card-dionysialemonaki.vercel.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow

### Project notes

In the HTML, I used an `article` element for the card component to semantically represent an independent, standalone blog preview card. I then gave the card an accessible name by associating the `article` with its title (`h2`) using `aria-labelledby`, which improves accessibility for screen readers.

For the images, since they are purely decorative and don't convey any important information to users, I left the `alt` attribute empty (`alt=""`) effectively hiding them from assistive technologies. Specifically, the author's avatar is decorative and the author's name follows the image. Therefore, using the author's name as alternative text would be redundant.

Lastly, I used the `time` element with the `datetime` attribute in the `YYYY-MM-DD` format to semantically represent the publication date.

```html
<p class="card__date">
  <time datetime="2023-12-21">Published 21 Dec 2023</time>
</p>
```

In the CSS, the font sizes in the blog preview card component – for the category, date, title and description – are slightly smaller on mobile. To fluidly scale the typography from smaller to larger screens _without_ using media queries, I used the `clamp()` function with values generated from [Utopia](https://utopia.fyi/clamp/calculator?a=360,1240).

```css
:root {
  /* typography */

  --fs-xs: 0.75rem; /* 12px */
  --fs-sm: 0.875rem; /* 14px */
  --fs-base: 1rem; /* 16px */
  --fs-lg: 1.25rem; /* 20px */
  --fs-xl: 1.5rem; /* 24px */

  --fs-fluid-xs: clamp(var(--fs-xs), 0.6989rem + 0.2273vw, var(--fs-sm));
  --fs-fluid-sm: clamp(var(--fs-sm), 0.8239rem + 0.2273vw, var(--fs-base));
  --fs-fluid-lg: clamp(var(--fs-lg), 1.1477rem + 0.4545vw, var(--fs-xl));
}
```

For the images, to maintain the main image's aspect ratio and make it responsive – completely covering the available space while fitting its container on smaller screens – I used `object-fit:cover;`. For the author's avatar, since it is a small icon, I specified both its `width` and `height` in `rem` units so it scales appropriately when a user changes their text size preferences in their browser or device settings.

```css
img {
  display: block;
  max-width: 100%;
}

.card__image {
  object-fit: cover;
}

.card__avatar {
  /* --max-avatar is 2rem */
  width: var(--max-avatar);
  height: var(--max-avatar);
}
```

This card acts as a signpost to other content. When a user clicks on it, they should be taken to the actual blog post, so it makes sense to make the whole card clickable rather than just its title. The [Inclusive Components – Cards](https://inclusive-components.design/cards/) chapter from Heydon Pickering's Inclusive Components book taught me how to achieve this – the only difference is that I used the `inset` property instead of the `top`, `right`, `bottom` and `left` properties.

```css
.card {
  position: relative;
}

.card__link::after {
  position: absolute;
  content: "";
  inset: 0;
}
```

Lastly, I added hover and focus states to the card component. For focus styles, I used `:focus-visible` on the link and `:focus-within` on the card itself, since the Figma design indicates that the `box-shadow` changes slightly on hover. I used CSS nesting for these styles:

```css
.card {
  box-shadow: var(--shadow-lg);
  transition: box-shadow 300ms ease-in-out;

  &:hover {
    box-shadow: var(--shadow-lg-hover);
  }
  &:focus-within {
    box-shadow: var(--shadow-lg-hover);
  }
}

.card__link {
  text-decoration: none;

  &:hover {
    color: var(--clr-text-hover);
  }
  &:focus-visible {
    color: var(--clr-text-hover);
    outline: 4px dotted var(--clr-text-primary);
    outline-offset: 2px;
  }
}
```
