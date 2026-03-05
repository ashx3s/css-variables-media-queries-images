# Final CSS Demo — Longboard Life

A demonstration site covering key CSS concepts from Web 1. The site is built around a longboarding theme and brings together fonts, CSS variables, flexbox layout, media queries, and background images.

---

## Getting Started

1. Download or clone this repository
2. Add images to `assets/images/` (see the README there for what's needed)
3. Open `index.html` in your browser — no build tools required

---

## Concept 1: Adding Fonts

There are two ways to load a custom font. This project uses **Google Fonts** as the example source.

### Option A — Link tag in HTML (this project uses this)

Add `<link>` tags inside `<head>` in your HTML file:

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Montserrat:wght@700&display=swap"
  rel="stylesheet"
/>
```

Then reference the font in your CSS:

```css
h1 {
  font-family: "Montserrat", sans-serif;
}
```

**When to use:** Simple projects, quick prototypes, or when you want the font loaded as part of the HTML document.

---

### Option B — @import in CSS

Add this at the very top of your `.css` file:

```css
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@700&display=swap");
```

**When to use:** When you want to keep all styling decisions in one place (the CSS file). Note: `@import` must be the first line in your stylesheet.

---

### Key difference

|                 | HTML `<link>`                          | CSS `@import`                           |
| --------------- | -------------------------------------- | --------------------------------------- |
| Where it goes   | Inside `<head>` in HTML                | Top of your `.css` file                 |
| Load order      | Loads in parallel with other resources | Loads after the CSS file starts parsing |
| Recommended for | Most use cases                         | Keeping styles self-contained           |

---

## Concept 2: Media Queries

Media queries let you apply CSS rules only when certain conditions are met — most commonly a minimum or maximum screen width.

### Mobile First (this project uses this)

Write your base styles for small screens. Then use `min-width` queries to add or override styles as the screen gets larger:

```css
/* Base: mobile layout */
.cards {
  flex-direction: column;
}

/* Tablet and up */
@media (min-width: 768px) {
  .cards {
    flex-direction: row;
  }
}
```

**Why mobile first?** You start with the simplest layout and progressively enhance it. This tends to produce cleaner, less redundant CSS.

---

### Desktop First

Write styles for large screens first, then use `max-width` queries to adjust for smaller screens:

```css
/* Base: desktop layout */
.cards {
  flex-direction: row;
}

/* Mobile and smaller */
@media (max-width: 767px) {
  .cards {
    flex-direction: column;
  }
}
```

**When to use desktop first:** Legacy projects, or when your design is primarily a desktop experience and mobile is a secondary concern.

---

### Common Breakpoints

| Name    | Width        |
| ------- | ------------ |
| Mobile  | up to ~480px |
| Tablet  | ~768px       |
| Desktop | ~1024px      |
| Wide    | ~1280px+     |

---

## Concept 3: Background Images vs Foreground Images

These look similar on screen but serve different purposes.

### CSS Background Image

```
# access file in the current directory
./filename.png
# access file in the parent directory of current
../filename
# access file 2 directories back of where you are
../../filename

```

```css
.hero {
  background-image: url("../images/hero-bg.jpg");
  background-size: cover;
  background-position: center;
}
```

- Set with CSS, not HTML
- Cannot have alt text — screen readers ignore it
- Great for decorative or atmospheric images (textures, banners, hero backgrounds)
- Supports `background-size: cover` to fill the container perfectly

---

### HTML `<img>` Tag

```html
<img
  src="assets/images/cruising.jpg"
  alt="Longboarder cruising along a coastal path"
/>
```

- Part of the HTML content
- **Requires `alt` text** for accessibility and SEO
- Use when the image is meaningful content — a photo of a product, a person, an illustration that explains something

---

### Quick Rule of Thumb

> If removing the image would make the content harder to understand, use `<img>`.
> If removing the image just changes the look and feel, use `background-image` in CSS.
