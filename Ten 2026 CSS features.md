<!--
title: "Ten 2026 CSS features"
date: 2025-12-30
author: Piotr Porzuczek
description: "A comprehensive guide to the most exciting CSS features coming in 2026: from squircles and custom shapes to inline conditionals and custom functions. Less JavaScript, more power."
tags: [css, web-development, frontend, css-2026, styling]
-->

## Ten 2026 CSS features

CSS is evolving rapidly, and 2026 brings some genuinely exciting additions. These features reduce JavaScript dependency, unlock creative possibilities, and solve long-standing pain points. Let's dive in.

---

### 1. Corner Shapes (Squircles!)

Finally, we can create corner shapes beyond simple rounded edges. The `corner-shape` property opens up creative possibilities that previously required SVG path clipping.

```css
/* Default rounded corners */
.rounded {
  border-radius: 20px;
  corner-shape: round;
}

/* Straight cut across the corner */
.beveled {
  border-radius: 20px;
  corner-shape: bevel;
}

/* Inward rectangular cut */
.notched {
  border-radius: 20px;
  corner-shape: notch;
}

/* Inward curved cut */
.scooped {
  border-radius: 20px;
  corner-shape: scoop;
}

/* The star of the show: smooth squircle */
.squircle {
  border-radius: 20px;
  corner-shape: squircle;
}

/* Mix different corners */
.creative {
  border-radius: 20px 40px 20px 40px;
  corner-shape: squircle bevel notch scoop;
}
```

👉 [MDN: corner-shape](https://developer.mozilla.org/en-US/docs/Web/CSS/corner-shape)

---

### 2. The Shape Function

The `shape()` function supercharges `clip-path`. Unlike the older `path()` function (limited to pixels), `shape()` supports percentages, `rem`, `em`, and CSS math functions like `calc()` and `max()`.

```css
/* Star shape using lines */
.star {
  clip-path: shape(
    from 50% 0%,
    line to 61% 35%,
    line to 98% 35%,
    line to 68% 57%,
    line to 79% 91%,
    line to 50% 70%,
    line to 21% 91%,
    line to 32% 57%,
    line to 2% 35%,
    line to 39% 35%,
    close
  );
}

/* Rounded star using arcs */
.rounded-star {
  clip-path: shape(
    from 50% 0%,
    arc to 61% 35% of 10%,
    arc to 98% 35% of 10%,
    arc to 68% 57% of 10%,
    close
  );
}

/* Animation along a custom path */
.animated-element {
  offset-path: shape(
    from 0% 50%,
    curve to 50% 0% with 25% 0%,
    curve to 100% 50% with 75% 0%
  );
  animation: move 3s infinite;
}

@keyframes move {
  to {
    offset-distance: 100%;
  }
}
```

👉 [MDN: shape()](https://developer.mozilla.org/en-US/docs/Web/CSS/basic-shape/shape)

---

### 3. Stylable HTML Selects

It's absolutely crazy that it took this long! Native `<select>` elements can finally be fully styled with CSS.

```css
/* Opt into the new styling system */
select {
  appearance: base-select;
  padding: 0.75rem 1rem;
  border: 2px solid #3b82f6;
  border-radius: 8px;
  background: white;
  font-size: 1rem;
}

/* Style the dropdown picker */
select::picker {
  background: white;
  border: 2px solid #3b82f6;
  border-radius: 0 0 8px 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

/* Animate the chevron icon */
select::picker-icon {
  transition: transform 0.2s ease;
}

select:open::picker-icon {
  transform: rotate(180deg);
}

/* Remove bottom radius when open */
select:open {
  border-radius: 8px 8px 0 0;
}

/* Style individual options */
select option {
  padding: 0.75rem 1rem;
  transition: background 0.15s;
}

select option:hover {
  background: #eff6ff;
}

select option:checked {
  background: #3b82f6;
  color: white;
}

/* Custom checkmark */
select option::checkmark {
  content: "✓";
  color: #22c55e;
  margin-right: 0.5rem;
}
```

👉 [MDN: Styling select elements](https://developer.mozilla.org/en-US/docs/Web/CSS/::picker)

---

### 4. Scroll Markers (Zero-JS Carousels)

Create carousel navigation dots without a single line of JavaScript. The `::scroll-marker` pseudo-element acts like anchor links for scroll containers.

```css
/* The carousel container */
.carousel {
  display: flex;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  scroll-marker-group: after;
}

/* Each carousel item */
.carousel-item {
  flex: 0 0 100%;
  scroll-snap-align: center;
}

/* Style the navigation dots */
.carousel-item::scroll-marker {
  content: "";
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #cbd5e1;
  transition: background 0.2s, transform 0.2s;
}

/* Active dot styling */
.carousel-item::scroll-marker:target-current {
  background: #3b82f6;
  transform: scale(1.2);
}

/* Position the marker group */
.carousel::scroll-marker-group {
  display: flex;
  justify-content: center;
  gap: 8px;
  padding: 1rem;
}

/* Add prev/next buttons */
.carousel::scroll-button(prev) {
  content: "←";
  position: absolute;
  left: 1rem;
}

.carousel::scroll-button(next) {
  content: "→";
  position: absolute;
  right: 1rem;
}
```

👉 [MDN: ::scroll-marker](https://developer.mozilla.org/en-US/docs/Web/CSS/::scroll-marker)

---

### 5. Container Scroll State Queries

Style elements based on scroll state: stuck, snapped, or scrollable. No more JavaScript scroll listeners!

```css
/* Enable scroll state queries */
.scroll-container {
  container-type: scroll-state;
  container-name: scroller;
  overflow-y: auto;
  height: 400px;
}

/* Sticky header that changes when stuck */
.sticky-header {
  position: sticky;
  top: 0;
  background: white;
  transition: all 0.3s;
}

@container scroll-state(stuck: top) {
  .sticky-header {
    background: #1e293b;
    color: white;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }
}

/* Carousel items that highlight when snapped */
.carousel-item {
  opacity: 0.5;
  transform: scale(0.9);
  transition: all 0.3s;
}

@container scroll-state(snapped: x) {
  .carousel-item {
    opacity: 1;
    transform: scale(1);
  }
}

/* Show scroll-to-top button when scrollable */
.scroll-to-top {
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s;
}

@container scroll-state(scrollable: top) {
  .scroll-to-top {
    opacity: 1;
    pointer-events: auto;
  }
}
```

👉 [MDN: Scroll State Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_containment/Container_scroll-state_queries)

---

### 6. The Stretch Keyword

The true `100%` value. Unlike percentage-based sizing, `stretch` includes margins in the calculation.

```css
.container {
  width: 400px;
  height: 300px;
  background: #f1f5f9;
}

/* Problem: 100% ignores margin */
.box-broken {
  width: 100%;
  height: 100%;
  margin: 20px;
  background: #3b82f6;
  /* This overflows the container! */
}

/* Solution: stretch respects margin */
.box-fixed {
  width: stretch;
  height: stretch;
  margin: 20px;
  background: #22c55e;
  /* Perfectly fits within container */
}
```

---

### 7. Text Box Trimming

Control whitespace above and below text. Perfect for aligning text with other elements.

```css
/* Default: extra whitespace around text */
.default-text {
  font-size: 4rem;
  border: 1px solid red;
}

/* Trim to capital letter height on top, alphabetic on bottom */
.trimmed-text {
  font-size: 4rem;
  text-box: trim-both cap alphabetic;
  border: 1px solid green;
}

/* Trim only the top to cap height */
.trimmed-top {
  font-size: 4rem;
  text-box-edge: cap;
  text-box-trim: trim-start;
}

/* Perfect alignment with images */
.hero-section {
  display: flex;
  align-items: start;
}

.hero-title {
  font-size: 3rem;
  text-box: trim-both cap alphabetic;
  /* Now aligns perfectly with adjacent image */
}

/*
  Trim values for top: text, cap, ex
  Trim values for bottom: text, alphabetic
*/
```

👉 [MDN: text-box](https://developer.mozilla.org/en-US/docs/Web/CSS/text-box)

---

### 8. Sibling Index Function

Get an element's position among siblings as an integer. Perfect for staggered animations without JavaScript.

```css
/* Staggered widths */
.list-item {
  width: calc(sibling-index() * 50px);
  height: 40px;
  background: #3b82f6;
}
/* Result: 50px, 100px, 150px, 200px... */

/* Staggered animation delays */
.fade-in-item {
  opacity: 0;
  animation: fadeIn 0.5s forwards;
  animation-delay: calc(sibling-index() * 100ms);
}

@keyframes fadeIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Gradient effect across items */
.gradient-item {
  background: hsl(calc(sibling-index() * 30), 70%, 50%);
}

/* Dynamic z-index stacking */
.stacked-card {
  position: absolute;
  z-index: sibling-index();
  transform: translateX(calc(sibling-index() * 20px));
}
```

👉 [MDN: sibling-index()](https://developer.mozilla.org/en-US/docs/Web/CSS/sibling-index)

---

### 9. Inline If() Functions

CSS now has inline conditionals! Check media, style, or support queries right in your property values.

```css
/* Theme-based colors */
:root {
  --theme: dark;
}

.card {
  background: if(
    style(--theme: dark): #1e293b,
    style(--theme: light): #ffffff,
    else: #f8fafc
  );
  
  color: if(
    style(--theme: dark): #f8fafc,
    style(--theme: light): #1e293b,
    else: #334155
  );
}

/* Responsive layout in one line */
.container {
  flex-direction: if(
    media(width < 768px): column,
    else: row
  );
  
  gap: if(
    media(width < 768px): 1rem,
    media(width < 1024px): 1.5rem,
    else: 2rem
  );
}

/* Feature detection */
.grid {
  display: if(
    supports(display: grid): grid,
    else: flex
  );
}
```

👉 [MDN: if()](https://developer.mozilla.org/en-US/docs/Web/CSS/if)

---

### 10. Custom Functions

Define reusable logic with `@function`. CSS is becoming seriously powerful.

```css
/* Color with transparency */
@function --alpha(--color, --transparency) {
  @return oklch(from var(--color) l c h / var(--transparency));
}

.card {
  background: --alpha(#3b82f6, 0.5);
  border: 1px solid --alpha(#3b82f6, 0.8);
}

/* Responsive value helper */
@function --responsive(--narrow, --wide) {
  @return if(
    media(width < 768px): var(--narrow),
    else: var(--wide)
  );
}

.container {
  flex-direction: --responsive(column, row);
  padding: --responsive(1rem, 2rem);
}

.heading {
  font-size: --responsive(1.5rem, 3rem);
}

/* Fluid typography */
@function --fluid(--min, --max, --min-vw, --max-vw) {
  --slope: calc((var(--max) - var(--min)) / (var(--max-vw) - var(--min-vw)));
  --intercept: calc(var(--min) - var(--slope) * var(--min-vw));
  @return clamp(var(--min), calc(var(--intercept) + var(--slope) * 100vw), var(--max));
}

.title {
  font-size: --fluid(1rem, 3rem, 320px, 1200px);
}
```

👉 [MDN: @function](https://developer.mozilla.org/en-US/docs/Web/CSS/@function)

---

## The Bigger Picture

These features share a common theme: CSS is absorbing responsibilities that previously required JavaScript. Scroll state detection, conditional logic, custom functions, carousel navigation... the list goes on.

This isn't just about writing less code. It's about performance, accessibility, and letting the browser do what it does best. CSS handles layout and styling in ways that JavaScript simply cannot match: it's declarative, it's optimized, and it degrades gracefully.

2026 CSS feels less like a styling language and more like a design system engine. And that's exactly where it should be heading.

---

**What's your favorite feature? For me, it's squircles. Sometimes the simplest additions make the biggest difference.**
