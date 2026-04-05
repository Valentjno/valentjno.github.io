# valentinomerlino.com

Personal website for Valentino Merlino — AI security researcher focused on IoT security, energy-based attack detection, and adversarial testing.

**Live:** https://valentjno.github.io

## Overview

A minimal, fast-loading static website built with semantic HTML, embedded CSS, and vanilla JavaScript. No build step, no dependencies, GitHub Pages compatible.

## Project Structure

```
.
├── index.html           Landing page (hero, intro, navigation)
├── about.html           Background, approach, and experience
├── work.html            Research, publications, projects, community
├── contact.html         Contact form and contact options
├── CLAUDE.md            Development guidelines
└── README.md            This file
```

## Local Development

### View locally
```bash
# Python 3.x
python -m http.server 8000

# Or with a simple HTTP server of your choice
# Then visit http://localhost:8000
```

### Edit
- Edit `.html` files directly — all CSS and JS are embedded
- No build step required
- Test in browser locally before deploying

## Deployment

This site is deployed to GitHub Pages from the `main` branch.

```bash
# Make changes, then:
git add -A
git commit -m "describe: your changes"
git push origin main

# Site updates automatically within 1-2 minutes
# https://valentjno.github.io
```

## Tech Stack

- **HTML:** Semantic markup, no frameworks
- **CSS:** Embedded in `<style>` tags, organized by component
- **JavaScript:** Vanilla JS for animations and scroll effects
- **Fonts:** Playfair Display (headings) and Crimson Text (body) via Google Fonts CDN
- **Hosting:** GitHub Pages (static, no build step)

## Design System

### Colors
```css
--color-black: #000000
--color-white: #ffffff
--color-pale-pink: #f78da7        /* accent */
--color-accent-teal: #0d9488      /* secondary */
--color-accent-deep-blue: #1e40af /* tertiary */
--bg-light: #F2F2F2               /* background */
--bg-dark: #1a1a2e                /* footer gradient */
```

### Typography
- **Headings (h1–h3):** Playfair Display (serif, 700 weight) — editorial, refined aesthetic
- **Body:** Crimson Text (serif, 400–700 weight) — readable, professional
- **Line height:** 1.8 for refined readability
- **Aesthetic:** Editorial/scholarly serif system, distinctive and memorable

### Spacing
- Desktop: 40px padding/margin
- Tablet (768px): 24px padding/margin
- Mobile (480px): 16px padding/margin

## Contact Form

The contact form is powered by **Formspree**:
- Form ID: `mwvwwagq`
- Action: `https://formspree.io/f/mwvwwagq`
- Emails sent to: `valentinomerlino@protonmail.com`

**To change:** Create a new Formspree form and update the `action` attribute in `contact.html`.

## Responsiveness

Mobile-first approach with breakpoints:
- **480px:** Mobile devices
- **768px:** Tablets
- **1200px+:** Desktop

All pages tested on mobile and desktop. Navigation adjusts for smaller screens.

## Performance

- **Single-file HTML:** No HTTP requests for JS/CSS bundles
- **Lightweight:** ~150KB total (uncompressed)
- **Fast loading:** Optimized for Core Web Vitals
- **No external dependencies:** Only Google Fonts CDN

## Accessibility

- Semantic HTML (`header`, `nav`, `main`, `footer`, `section`)
- Keyboard-accessible navigation
- Color contrast meets WCAG AA standards
- Readable font sizes and line heights
- Meaningful alt text for images

## Content Guidelines

See [CLAUDE.md](./CLAUDE.md) for detailed content and design rules.

### Key principles
- **Concise:** Short sentences, bullet points, no filler
- **Professional:** Precise, credible, technical but accessible
- **Specific:** Real credentials, real work (no placeholder copy)
- **Action-oriented:** Show what you do, not abstract philosophy

## License

This website is personal and not open-source. © 2025 Valentino Merlino.

## Contact

- **Email:** valentinomerlino@protonmail.com
- **LinkedIn:** https://www.linkedin.com/in/valentinomerlino
- **GitHub:** https://github.com/valentjno

---

Built with care. No frameworks, no build step, just clean HTML.
