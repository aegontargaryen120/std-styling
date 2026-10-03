# Standard Web Styling

A lightweight, reusable HTML/CSS/JavaScript styling system for simple personal websites, blogs, portfolios, documentation sites, and other small web projects.

It provides:

- A neutral editorial design
- Light and dark themes
- Responsive layouts
- Reusable buttons and cards
- Navigation styling
- Typography utilities
- Forms
- Image styling
- Scroll-reveal animations
- Active navigation detection
- CSS custom properties for easy theming
- No frameworks or dependencies

The system is intentionally small. It is designed to be copied, customised, and extended rather than treated as a complete framework.

---

## 1. Basic Structure

A project using the standard styling should look roughly like this:

```text
website/
├── index.html
├── styling/
│   ├── style.css
│   └── script.js
└── assets/
    └── images/
```

For a multi-page website:

```text
website/
├── index.html
├── about/
│   └── index.html
├── projects/
│   └── index.html
├── contact/
│   └── index.html
├── styling/
│   ├── style.css
│   └── script.js
└── assets/
    └── images/
```

The styling files are intended to be shared between all pages.

---

# 2. Installation

No installation is required.

Copy:

```text
style.css
script.js
```

into your project.

Then include them in your HTML.

For a root-level page:

```html
<link rel="stylesheet" href="styling/style.css">
<script src="styling/script.js"></script>
```

For a page one directory deeper:

```html
<link rel="stylesheet" href="../styling/style.css">
<script src="../styling/script.js"></script>
```

The JavaScript should normally be placed immediately before `</body>`.

---

# 3. HTML Structure

The styling does not require one enormous fixed HTML structure.

Instead, it provides reusable patterns.

A typical page should contain:

```text
HTML
├── <head>
│   ├── metadata
│   ├── <title>
│   └── style.css
│
├── <body>
│   ├── Header / Navigation
│   ├── Main content
│   │   ├── Hero
│   │   ├── Sections
│   │   ├── Cards / Grids
│   │   └── Other content
│   │
│   ├── Footer
│   └── script.js
```

The header and footer are optional, but recommended for most sites.

---

# 4. Standard Header

The expected navigation structure is:

```html
<header class="site-header">
    <nav class="nav">

        <a href="/" class="logo">
            Your<span>Name</span>
        </a>

        <ul class="nav-links">
            <li>
                <a href="/">Home</a>
            </li>

            <li>
                <a href="/about/">About</a>
            </li>

            <li>
                <a href="/projects/">Projects</a>
            </li>
        </ul>

        <button
            class="theme-toggle"
            aria-label="Switch theme">
            ☾
        </button>

    </nav>
</header>
```

### `.site-header`

Creates the sticky header and translucent background.

### `.nav`

Controls the layout of the navigation.

### `.logo`

Styles the site name or logo.

### `.logo span`

The second part of the logo receives the accent colour.

For example:

```html
<a class="logo" href="/">
    Aegon<span>Targaryen</span>
</a>
```

### `.nav-links`

Styles the navigation links.

### `.theme-toggle`

Provides the button used by `script.js` to switch between light and dark mode.

If the theme button is omitted, the rest of the styling will still work.

---

# 5. Theme Switching

Dark mode is controlled using:

```html
<button class="theme-toggle">
    ☾
</button>
```

JavaScript automatically:

1. Detects the user's system preference.
2. Checks for a previously selected theme.
3. Switches between light and dark mode.
4. Stores the selected theme in `localStorage`.
5. Changes the button icon.

The CSS uses:

```css
:root {
    ...
}

[data-theme="dark"] {
    ...
}
```

Do not remove the `data-theme` mechanism unless you intend to replace the theme system.

---

# 6. Hero Sections

A standard hero section looks like:

```html
<section class="hero">

    <div class="hero-content">

        <p class="eyebrow">
            Author · Programmer · Worldbuilder
        </p>

        <h1>
            Build something
            <span>interesting.</span>
        </h1>

        <p class="hero-description">
            A short description of the website.
        </p>

        <div class="button-group">

            <a href="/about/" class="button">
                About Me
            </a>

            <a href="/projects/" class="button secondary">
                Projects
            </a>

        </div>

    </div>

</section>
```

### `.hero`

Creates a large introductory section.

### `.hero-content`

Constrains the content width.

### `.eyebrow`

Small uppercase introductory text.

### `.hero-description`

Secondary explanatory text below the heading.

### `.hero h1 span`

Highlights part of the heading using the accent colour.

---

# 7. Sections

Use:

```html
<section class="section">
    ...
</section>
```

for major areas of a page.

A typical section heading:

```html
<div class="section-heading">

    <p class="eyebrow">
        Projects
    </p>

    <h2>
        Things I've built.
    </h2>

    <p>
        A short description of this section.
    </p>

</div>
```

The `.section` class provides:

- Vertical spacing
- A dividing border
- Consistent section proportions

---

# 8. Containers

Use:

```html
<div class="container">
    ...
</div>
```

to constrain content to the site's standard width.

For example:

```html
<section class="section">

    <div class="container">

        <h2>Projects</h2>

        ...

    </div>

</section>
```

The default maximum width is controlled by:

```css
--content-width: 1100px;
```

---

# 9. Narrow Content

For articles, biographies, documentation, and other text-heavy content:

```html
<div class="narrow">
    ...
</div>
```

The width is controlled by:

```css
--text-width: 700px;
```

This prevents paragraphs from becoming absurdly wide.

---

# 10. Cards

The standard card is:

```html
<article class="card">

    <span class="badge accent">
        Featured
    </span>

    <h3>
        Project Name
    </h3>

    <p>
        A description of the project.
    </p>

    <a href="#" class="card-link">
        Read more
    </a>

</article>
```

Cards automatically receive:

- Background
- Border
- Rounded corners
- Shadow
- Hover animation

---

# 11. Card Grids

The grid system provides three basic configurations.

Two columns:

```html
<div class="grid grid-2">
    ...
</div>
```

Three columns:

```html
<div class="grid grid-3">
    ...
</div>
```

Generic grid:

```html
<div class="grid">
    ...
</div>
```

The grids automatically collapse on smaller screens.

---

# 12. Badges

Standard badge:

```html
<span class="badge">
    Draft
</span>
```

Accent badge:

```html
<span class="badge accent">
    Published
</span>
```

Badges are useful for:

- Categories
- Status
- Tags
- Labels
- Technologies
- Dates

---

# 13. Split Layouts

For an About section or similar content:

```html
<div class="split">

    <div>
        <p class="label">
            About
        </p>
    </div>

    <div class="prose">

        <p>
            Your first paragraph.
        </p>

        <p>
            Your second paragraph.
        </p>

    </div>

</div>
```

The layout has two columns on larger screens and collapses to one column on mobile.

---

# 14. Typography

The default font stack is:

```css
font-family:
    -apple-system,
    BlinkMacSystemFont,
    "SF Pro Display",
    "SF Pro Text",
    Aptos,
    Arial,
    sans-serif;
```

This means the browser attempts to use:

1. SF Pro Display
2. SF Pro Text
3. Aptos
4. Arial
5. Generic sans-serif

You do not need to distribute SF Pro with the website.

The browser will simply use the next available font.

Useful classes:

```html
<p class="text-muted">
    Secondary text.
</p>
```

```html
<p class="text-accent">
    Accent text.
</p>
```

```html
<p class="text-center">
    Centered text.
</p>
```

---

# 15. Buttons

Primary button:

```html
<a href="#" class="button">
    Continue
</a>
```

Secondary button:

```html
<a href="#" class="button secondary">
    Cancel
</a>
```

Ghost button:

```html
<a href="#" class="button ghost">
    Learn More
</a>
```

Buttons work with both `<a>` and `<button>` elements.

---

# 16. Images

Basic image:

```html
<div class="image">
    <img
        src="/assets/images/example.jpg"
        alt="Description of the image">
</div>
```

The `.image` class provides:

- Border
- Rounded corners
- Overflow handling
- A subtle hover zoom

Always provide useful `alt` text.

---

# 17. Forms

Basic form:

```html
<form class="form">

    <div class="form-group">

        <label
            class="form-label"
            for="name">
            Name
        </label>

        <input
            id="name"
            type="text"
            placeholder="Your name">

    </div>

    <div class="form-group">

        <label
            class="form-label"
            for="message">
            Message
        </label>

        <textarea
            id="message"
            placeholder="Your message">
        </textarea>

    </div>

    <button class="button" type="submit">
        Submit
    </button>

</form>
```

The styling handles:

- Labels
- Inputs
- Textareas
- Select boxes
- Focus states
- Responsive widths

The stylesheet does not provide form submission functionality.

---

# 18. Prose

For long-form text:

```html
<article class="prose">

    <p>
        Your paragraph.
    </p>

    <p>
        Another paragraph.
    </p>

    <p>
        More text with
        <a href="#">a link</a>.
    </p>

</article>
```

`.prose` is intended for:

- Articles
- Essays
- Documentation
- About pages
- Blog posts
- Long descriptions

---

# 19. Dividers

Use:

```html
<div class="divider"></div>
```

for a standalone horizontal divider.

Most sections do not need one because `.section` already provides a border.

---

# 20. Animations

Add:

```html
class="fade-in"
```

to an element:

```html
<section class="section fade-in">
    ...
</section>
```

JavaScript will reveal it as it enters the viewport.

For a small hover lift:

```html
<div class="card lift">
    ...
</div>
```

The styling respects:

```css
@media (prefers-reduced-motion: reduce)
```

so users who have requested reduced motion are not subjected to unnecessary animation.

---

# 21. Customising the Theme

Most visual customisation should happen at the top of `style.css`.

The main variables are:

```css
:root {
    --bg: #eeeeeb;
    --surface: #f7f7f4;
    --surface-alt: #e4e6e1;

    --text: #20221f;
    --text-muted: #686d66;

    --accent: #3f684d;
    --accent-hover: #31543e;

    --border: #d1d4ce;

    --radius-sm: 8px;
    --radius: 14px;
    --radius-lg: 20px;

    --content-width: 1100px;
    --text-width: 700px;
}
```

These are the primary design tokens.

### Background

```css
--bg: #eeeeeb;
```

Controls the main page background.

### Surface

```css
--surface: #f7f7f4;
```

Controls cards, inputs, and other raised surfaces.

### Text

```css
--text: #20221f;
```

Controls primary text.

### Muted text

```css
--text-muted: #686d66;
```

Controls secondary text.

### Accent

```css
--accent: #3f684d;
```

Controls:

- Links
- Highlighted text
- Buttons
- Labels
- Active navigation
- Decorative elements

### Accent hover

```css
--accent-hover: #31543e;
```

Controls the darker hover state of accent elements.

---

# 22. Creating a Different Colour Scheme

For a blue theme:

```css
--accent: #456a91;
--accent-hover: #355574;
```

For a red theme:

```css
--accent: #914545;
--accent-hover: #703535;
```

For a purple theme:

```css
--accent: #76548f;
--accent-hover: #5d4072;
```

For monochrome:

```css
--accent: #222222;
--accent-hover: #444444;
```

The rest of the stylesheet does not need to change.

---

# 23. Changing the Width

The default content width is:

```css
--content-width: 1100px;
```

A narrower literary layout:

```css
--content-width: 900px;
```

A wider portfolio:

```css
--content-width: 1250px;
```

Text-heavy content can separately use:

```css
--text-width: 700px;
```

---

# 24. Changing Rounded Corners

The defaults are:

```css
--radius-sm: 8px;
--radius: 14px;
--radius-lg: 20px;
```

For a sharper design:

```css
--radius-sm: 2px;
--radius: 4px;
--radius-lg: 8px;
```

For a softer design:

```css
--radius-sm: 12px;
--radius: 20px;
--radius-lg: 30px;
```

---

# 25. Recommended Page Template

A normal page can follow this structure:

```html
<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0">

    <title>Page Title</title>

    <meta
        name="description"
        content="Description of the page.">

    <link
        rel="stylesheet"
        href="styling/style.css">

</head>

<body>

<header class="site-header">

    <nav class="nav">

        <a href="/" class="logo">
            Your<span>Name</span>
        </a>

        <ul class="nav-links">

            <li>
                <a href="/">Home</a>
            </li>

            <li>
                <a href="/about/">About</a>
            </li>

            <li>
                <a href="/projects/">Projects</a>
            </li>

        </ul>

        <button
            class="theme-toggle"
            aria-label="Switch theme">
            ☾
        </button>

    </nav>

</header>

<main>

    <!-- Page content -->

</main>

<footer class="site-footer">

    <div class="footer-inner">

        <span>
            © 2026 Your Name
        </span>

        <span>
            Built with HTML, CSS & JavaScript.
        </span>

    </div>

</footer>

<script src="styling/script.js"></script>

</body>

</html>
```

For pages inside subdirectories, adjust the stylesheet and script paths accordingly.

For example:

```html
<link rel="stylesheet" href="../styling/style.css">
<script src="../styling/script.js"></script>
```

---

# 26. What the JavaScript Expects

The JavaScript looks for the following optional elements:

```text
.theme-toggle
.fade-in
.nav-links a
```

### `.theme-toggle`

Enables light/dark mode.

### `.fade-in`

Enables scroll-reveal animation.

### `.nav-links a`

Allows the script to automatically identify the current page and add:

```html
class="active"
```

to its navigation link.

The rest of the website does not depend on JavaScript.

If JavaScript fails to load, the page should remain usable.

---

# 27. What You Should NOT Need to Change

For normal customisation, you should not need to modify the JavaScript.

Most customisation should happen through:

```text
style.css
```

particularly:

```css
:root { ... }
```

and through the classes provided by the stylesheet.

Modify `script.js` only when adding new interactive behaviour.

---

# 28. Recommended Development Workflow

When creating a new website:

### 1. Copy the styling

```text
styling/
├── style.css
└── script.js
```

### 2. Create your HTML structure.

Start with the standard page template.

### 3. Choose your theme.

Modify the variables at the beginning of `style.css`.

### 4. Build the page using the components.

Use:

```text
hero
section
container
grid
card
button
badge
split
prose
image
form
```

rather than writing new CSS for every individual element.

### 5. Add custom CSS only when necessary.

If the standard system doesn't cover something specific to your website, add a new component rather than modifying an unrelated existing class.

For example:

```css
.book-cover {
    ...
}
```

rather than turning `.card` into something that only makes sense for books.

---

# 29. Design Philosophy

This styling system follows a few principles:

### Keep the HTML semantic.

Prefer:

```html
<article>
<section>
<nav>
<header>
<footer>
```

over a page made entirely from anonymous `<div>` elements.

### Keep the CSS reusable.

Prefer:

```html
<div class="card">
```

over:

```html
<div class="green-box-with-rounded-corners">
```

### Keep the JavaScript optional.

Visual content should not depend on JavaScript.

### Keep the theme centralised.

Use CSS variables rather than scattering colour values throughout the stylesheet.

### Keep dependencies at zero.

The standard styling requires:

- HTML
- CSS
- JavaScript

Nothing else.

---

# 30. Quick Reference

| Class | Purpose |
|---|---|
| `.site-header` | Sticky site header |
| `.nav` | Navigation layout |
| `.logo` | Site logo/name |
| `.nav-links` | Navigation links |
| `.theme-toggle` | Dark/light mode |
| `.container` | Content width |
| `.hero` | Large introductory section |
| `.hero-content` | Hero content wrapper |
| `.hero-description` | Hero subtitle |
| `.section` | Standard page section |
| `.section-heading` | Section heading |
| `.eyebrow` | Small uppercase label |
| `.button` | Primary button |
| `.button.secondary` | Secondary button |
| `.button.ghost` | Minimal button |
| `.grid` | Generic grid |
| `.grid-2` | Two-column grid |
| `.grid-3` | Three-column grid |
| `.card` | Content card |
| `.card-link` | Card action link |
| `.badge` | Small status/tag |
| `.badge.accent` | Accent badge |
| `.split` | Two-column content |
| `.prose` | Long-form text |
| `.image` | Image container |
| `.form` | Form layout |
| `.form-group` | Form field group |
| `.divider` | Horizontal divider |
| `.site-footer` | Footer |
| `.fade-in` | Scroll reveal |
| `.lift` | Hover lift |
| `.text-muted` | Muted text |
| `.text-accent` | Accent text |
| `.text-center` | Centered text |
| `.narrow` | Narrow content width |

---

# 31. Final Notes

This is a **starter design system**, not a framework.

The intended workflow is:

```text
Copy
  ↓
Customise variables
  ↓
Build semantic HTML
  ↓
Use existing components
  ↓
Add project-specific CSS where necessary
```

The system should provide a consistent visual foundation while leaving the actual identity of each website to the content and customisation.

There is deliberately no attempt to make every possible component. Once a website needs a calendar, carousel, dashboard, shopping cart, authentication system, or seventeen varieties of modal dialogue, it has probably graduated from this little stylesheet and should acquire a more appropriate architecture.

