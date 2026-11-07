# ✈️ TripBoss

![Status](https://img.shields.io/badge/Status-Completed-1ec6b6?style=for-the-badge)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Font Awesome](https://img.shields.io/badge/Font_Awesome-5.15.3-528DD7?style=for-the-badge&logo=fontawesome&logoColor=white)

TripBoss is a responsive, multi-page website for a travel agency, built with plain HTML, CSS and vanilla JavaScript. It has no framework, no bundler and no dependencies. It has five pages (Home, Gallery, Blog, About and Contact) that share a navbar and footer. The pages include a trip-search hero, hover-reveal destination cards, an image lightbox and a background video that plays only while it's on screen.

> **Note:** This is a front-end-only project. The forms (trip search, contact, newsletter) are UI only and don't submit anywhere, and most body text is placeholder copy.

---

## Features

- **Five-page site**: Home, Gallery, Blog, About and Contact, each with the same navbar, page header and footer.
- **Navbar that changes on scroll**: The fixed navbar starts transparent and switches to a white bar with a shadow once the page scrolls past 40px.
- **Slide-in mobile menu**: Below 992px, a hamburger button opens a side panel that slides in from the right. It closes with its ✕ button or with a click anywhere outside it.
- **Animated hero with trip search**: The home page title drops in with a CSS bounce animation. Below it is a search form with destination, date and price fields.
- **Featured places**: Six destination cards with a dark gradient overlay. On hover, the caption slides up to show the description.
- **Services and testimonials**: Three service blocks over a full-bleed background image, and three testimonial speech bubbles with the client's photo, name and trip.
- **Background video section**: A looping, muted video that plays when at least half of it is on screen and pauses when it scrolls away.
- **Gallery lightbox**: Nine gallery images zoom and show a magnifier icon on hover. Clicking one opens a full-screen modal with previous/next buttons that wrap from the last image to the first, and back.
- **Popular places**: Eight destination tiles with star ratings and review counts. On hover, an info panel slides up from the bottom.
- **Blog grid**: Eight post cards, each with an image, a green date badge, a category/author line, a title link and an excerpt.
- **About page**: An "Our Story" section with an image, and a "Fun Facts" band with four stats (photos taken, beaches visited, mountains climbed, cruises organized).
- **Contact page**: A name, email and message form next to phone, address and email details.
- **Footer**: Brand blurb, social links, popular-place links and a newsletter signup form.

## Tech Stack

The project has no `package.json`. Versions below come from the files and CDN links in the code.

- **HTML5**: Five static pages (`index.html`, `gallery.html`, `blog.html`, `about.html`, `contact.html`).
- **CSS3**: Custom properties, Flexbox, CSS Grid, `@keyframes` animations and mobile-first media queries, split into utility, component and responsive stylesheets.
- **Vanilla JavaScript (ES6+)**: `const`/`let`, arrow functions, template literals and `IntersectionObserver`. No libraries.
- **normalize.css v8.0.1**: A local copy that makes browser default styles consistent.
- **Font Awesome 5.15.3**: Icons, loaded from cdnjs with an SRI `integrity` hash.
- **Google Fonts: Open Sans and Raleway**: Declared in a local `font/fonts.css` as `@font-face` rules (weights 200–900) that point at `fonts.gstatic.com`. Open Sans is the body font and Raleway is used for headings, buttons and form fields.

## Engineering Highlights

- **No transition flicker on resize**: `js/script.js` adds a `resize-animation-stopper` class to `<body>` while the window is being resized. The class turns off every animation and transition, and a 400ms debounce timer removes it afterwards, so the off-canvas menu doesn't visibly slide across the screen when crossing the 992px breakpoint.
- **Video plays only while visible**: The home-page video is controlled by an `IntersectionObserver` with `threshold: 0.5`. It's marked `muted` and `playsinline` so browsers allow it to autoplay. `preload="metadata"` keeps the large MP4 from downloading in full up front. Rejected `play()` promises are caught so the console stays clean.
- **Off-canvas menu moved with transforms**: The side menu is hidden with `transform: translateX(100%)` and shown by toggling one class, not by changing `display` or `right`. This lets the slide-in animate smoothly. At 992px and up the same element is reset to a normal inline nav bar.
- **Design tokens in CSS custom properties**: The brand green (`--green: #1ec6b6`), the greys and a shared `--trans` easing are defined once on `:root` and reused across all components.
- **Hover effects in CSS only**: Card overlays use `::after` gradient layers, and the captions animate with `transform` or `bottom` transitions. No JavaScript is needed for any hover state.
- **Utility-first base layer**: `css/utility.css` has small reusable classes (`.container` capped at 1320px, `.flex`, `.py-4`, `.my-2`, `.shadow`, `.btn`, `.form-control`, `.title-wrap`) that all five pages share.
- **Lightbox based on file names**: The gallery modal works out which image was clicked from its `gallery-N.jpg` file name. Previous/next then rebuild the `src` with a template literal and wrap around using the number of gallery items.
- **Fast font loading**: Every `@font-face` rule uses `font-display: swap` and `unicode-range` subsets, so text appears right away and the browser downloads only the character sets a page needs.
- **Wide browser support**: Flexbox, transforms, transitions and gradients include `-webkit-`, `-ms-` and `-o-` prefixed fallbacks.

## Folder Structure

```
Tripboss/
├── index.html        # Home: hero + search, featured, services, testimonials, video
├── gallery.html      # Gallery grid, image lightbox modal, popular places
├── blog.html         # Recent blog post grid
├── about.html        # Our story and fun-facts stats
├── contact.html      # Contact form and contact details
├── css/
│   ├── normalize.css   # normalize.css v8.0.1 reset
│   ├── utility.css     # Base typography, container, and reusable utility classes
│   ├── style.css       # Design tokens and all component/page styles
│   └── responsive.css  # Mobile-first media queries (460px → 1400px)
├── font/
│   └── fonts.css     # @font-face rules for Open Sans and Raleway
├── js/
│   └── script.js     # Shared navbar scroll, mobile menu, and resize behaviour
├── images/           # Header/section backgrounds, featured, gallery, popular, blog, testimonial images
├── videos/
│   └── video-section.mp4  # Background video for the home page video section
└── README.md         # Project documentation
```

## Getting Started

### Prerequisites

- [Git](https://git-scm.com/)
- A modern web browser (Chrome, Firefox, Edge or Safari)
- *Optional:* [Python 3](https://www.python.org/) or [Node.js](https://nodejs.org/), to run a local static server

### Steps

1. **Clone the repository**

```bash
git clone https://github.com/K01J10W19/Tripboss.git
```

```bash
cd Tripboss
```

2. **Install dependencies**

   There is nothing to install. The project has no `package.json` and no packages. Font Awesome and the font files load from their CDNs at runtime.

3. **Run a local development server**

   You can open `index.html` directly in a browser. A local server is closer to how the site will be hosted. Use either of these:

```bash
python -m http.server 8000
```

```bash
npx serve .
```

4. **Build**

   There is no build step. The HTML, CSS and JS files are served exactly as they are, and the repository root is ready to deploy to any static host (for example GitHub Pages, Netlify or Vercel).

5. **Preview**

   Open the address the server prints in your browser: `http://localhost:8000` for the Python server, or `http://localhost:3000` by default for `serve`. Then go through the pages from the navbar.

## Responsive Strategy

The layout is **mobile-first**. The base styles are a single column with the slide-in menu, and `css/responsive.css` adds layout changes with `min-width` queries. The `.container` is capped at `1320px` with `1rem` side padding.

| Breakpoint | What changes |
| --- | --- |
| **Base (< 678px)** | Single-column layout everywhere. Hamburger button with the slide-in side menu. Hero form fields stacked vertically. Footer centred. |
| **≤ 460px** (`max-width`) | Sets the featured-card caption offset to `translateY(68%)` again. This is the same value as the base style, so nothing visibly changes. |
| **≥ 678px** | Testimonial author block becomes a 2-column grid (photo + name) aligned left, and the speech-bubble arrow moves to the left. |
| **≥ 768px** | 2-column grids for featured places, services, footer, gallery, popular places, blog and fun facts. Footer text and social links align left. Hero paragraph grows to `1.4rem`. |
| **≥ 992px** | Desktop navbar: the hamburger and close buttons are hidden and the links sit in a row on the right (dark text after scrolling). Hero title grows to `4rem` and the search form fields sit in one row. Testimonials, About and Contact become 2 columns. Popular places and blog go to 3 columns, fun facts to 4. Contact details show icon and text side by side. |
| **≥ 1200px** | Testimonials and gallery go to 3 columns. Footer and popular places go to 4 columns. |
| **≥ 1400px** | Featured places and services go to 3 columns. |
