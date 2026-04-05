#Valentino Merlino

# Project Overview
This repository is a personal static website.

Primary goals, in order:
1. Clear personal branding
2. Fast loading and simple deployment
3. Clean, readable layout
4. Accessibility and responsiveness
5. Minimal, maintainable code

This site should remain lightweight and easy to host as plain static files.

# Stack
- Framework: Static HTML (no build step)
- Styling: Embedded CSS
- JavaScript: Vanilla JS, embedded
- Hosting: Static hosting (GitHub Pages / Netlify compatible)
- Fonts: Inter from Google Fonts CDN

# Project Structure

## File Architecture
- `index.html` — Landing page (hero + intro + navigation cards)
- `about.html` — Personal background and approach (no repetition from work.html)
- `work.html` — Combined research & work: publication, projects, community contributions
- `contact.html` — Contact form (Formspree) + email/LinkedIn links

## Technical Structure
- Single-file HTML files (no folders, no bundler)
- Embedded CSS in `<style>` tag (organized by component)
- Embedded vanilla JS in `<script>` tag
- Consistent header/footer on all pages
- Responsive breakpoints: 768px (tablet), 480px (mobile)

# Code Style
- Write semantic HTML first
- Keep CSS organized in clearly labeled sections inside `<style>`
- Keep JavaScript small, readable, and inside `<script>`
- Prefer simple solutions over abstractions
- Do not add dependencies or libraries unless explicitly requested
- Do not split code into external files unless the project clearly outgrows a single-file structure

# Design Rules
- Build a polished personal site, not a generic AI-looking landing page
- Prioritize strong typography, spacing, and hierarchy
- Use a restrained color palette
- Keep layouts clean and uncluttered
- Design mobile-first, then improve for larger screens
- Make sure the site feels personal, confident, and intentional

# Content Philosophy
- **Less is better**: Minimal, direct, no filler — every word purposeful
- **No repetition**: Each page has distinct focus; avoid duplicating content across pages
- **IoT-first messaging**: Lead with IoT security as primary research area
- **Specificity**: Use real credentials (University of Catania, energy-based detection) not generic descriptions

# Content Rules
- **Concise first:** Short sentences, bullet points, no filler
- **Professional tone:** Precise, credible, technical but accessible
- **Specific over generic:** Mention ISO 42001, OWASP, University of Catania, actual roles
- **Action-oriented:** Show what you do, not abstract philosophy
- **Scannable:** Use headings, white space, short paragraphs
- **Avoid:** Marketing jargon, repetition, verbose explanations, placeholder copy

# Accessibility Rules
- Use semantic landmarks: `header`, `main`, `nav`, `section`, `footer`
- Maintain strong color contrast
- Ensure keyboard accessibility for interactive elements
- Provide visible focus states
- Use meaningful alt text for images
- Preserve readable font sizes and line spacing

# Performance Rules
- Keep the page lightweight
- Avoid unnecessary JavaScript
- Avoid large animations or heavy visual effects
- Optimize images before adding them
- Prefer CSS solutions over JavaScript when possible

# SEO Rules
- Every page should have a meaningful `<title>`
- Include a meta description
- Use proper heading hierarchy
- Use descriptive link text
- Add basic social sharing metadata when appropriate

# Workflow
- Before major edits, inspect the existing HTML structure and preserve what is already working
- Prefer editing the current file instead of rewriting everything
- Keep changes scoped and minimal
- After making changes, review the full page for visual consistency
- Always check mobile layout before considering the task done

# Validation Checklist
Before finishing:
- Confirm the HTML is valid and well-structured
- Confirm the layout works on mobile and desktop
- Confirm there are no obvious accessibility regressions
- Confirm links, buttons, and navigation work
- Confirm no unnecessary complexity was introduced

# Things To Avoid
- Do not introduce React, Vue, Tailwind, Bootstrap, or build tools
- Do not add a package manager or npm setup
- Do not add external dependencies unless explicitly requested
- Do not over-engineer a simple section
- Do not create visual clutter
- Do not use placeholder copy unless explicitly requested

# Personal Site Guidance
Common sections to consider:
- Hero / intro
- About
- Projects or selected work
- Writing or notes
- Links / social profiles
- Contact
- Footer

# Personal Branding
This is the personal website of Valentino Merlino.
The site should position him as:
- **IoT Security Researcher** — Energy-based attack detection in resource-constrained devices (primary)
- **Red Team Specialist** — Adversarial testing and vulnerability assessment (supporting)
- **PhD Candidate** — University of Catania, focused on edge system security
- **Community Contributor** — OWASP AI Exchange, CEN-CENELEC JTC 21

When writing copy:
- Keep tone professional, precise, and technical but accessible
- Lead with ISO 42001 and Responsible AI governance expertise
- Emphasize practical security implementation, not theory alone
- Avoid startup jargon; use concrete examples and credentials
- Concise and scannable (not verbose)

# Typography System
**Fonts:** Playfair Display (headings, serif) + Crimson Text (body, serif) via Google Fonts CDN
**Aesthetic:** Editorial/scholarly serif system — distinctive, refined, memorable
**Why:** Avoids generic sans-serif defaults (Inter, Space Mono); creates professional character befitting a researcher

# Design System

## Typography
- **Headings**: Playfair Display (serif, 600–800 weight)
- **Body**: Crimson Text (serif, regular + italic)
- **Line-height**: 1.8 for refined readability
- **Effect**: Editorial/minimalist aesthetic — scholarly, professional, memorable

## CSS Variables
All colors and common values are defined in `:root` CSS variables (no hardcoded colors):

```css
--color-black: #000000
--color-white: #ffffff
--color-pale-pink: #f78da7 (accent)
--color-vivid-purple: #9b51e0
--color-vivid-green: #00d084
--bg-light: #F2F2F2
--bg-dark: #1a1a1a
--color-border: #ddd
--color-text-muted: #666
```

## Color Palette
- **Background:** `#F2F2F2` (light gray)
- **Text:** `#000000` (black)
- **Accent:** `#f78da7` (pale-pink) — use sparingly, hover states only
- **Secondary accents:** purple, green (available but rarely used)
- **Rule:** Restrained palette, 2-3 main colors per page

# Deployment

## GitHub Pages Setup
- Repository: `valentjno.github.io` (must match GitHub username)
- Live URL: `https://valentjno.github.io`
- Branch: `main`, folder: `/` (root)
- No build step required (static files only)

## Deployment Workflow
```bash
# Make changes, then:
git add -A
git commit -m "describe: your changes here"
git push origin main

# Site updates automatically within 1-2 minutes
```

## Contact Form (Formspree)
- Form action: `https://formspree.io/f/mwvwwagq`
- Emails go to: `valentinomerlino@protonmail.com`
- **To change:** Set up new Formspree form, update action URL in `contact.html`

## Notes

- Keep the single-file architecture — no bundlers or build steps
- Maintain the squared corner aesthetic (no pills)
- Animations use fade-in on scroll (minimal, purposeful)
- **index.html is the main landing page** — keep concise and professional
- Update contact details in footer when credentials change

# Instructions for Claude
When making changes:
- Preserve the static-site approach
- Keep everything simple and production-ready
- Favor readability and elegance over novelty
- Make the site feel personal and credible
- Explain major UI changes briefly before applying them