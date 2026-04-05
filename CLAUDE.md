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
- `index.html` is the main entry point
- Additional pages should be plain `.html` files
- Keep the structure simple and flat unless there is a strong reason to add folders
- Avoid introducing tooling, bundlers, preprocessors, or frameworks

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

# Content Rules
- Copy should be concise, human, and specific
- Avoid buzzwords, filler, and exaggerated marketing language
- Emphasize clarity over cleverness
- Each section should have a clear purpose
- Personal bio, work, links, and contact info should be easy to find

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
- an AI security and Responsible AI professional
- an AI Red Team practitioner
- a PhD candidate at the University of Catania
- someone combining industry work with research

When writing copy:
- keep the tone precise, credible, and technical but approachable
- emphasize AI security, red teaming, Responsible AI, and research
- avoid generic startup-style marketing language
- prefer concrete evidence such as role, institution, and publication topics
Prefer reusable section patterns, but keep implementation simple.

# Fonts
Use Inter via Google Fonts CDN unless explicitly changed.

# Color Palette
From the design reference, use these colors:
- Background: `#F2F2F2` (light gray)
- Text: `#000000` (black)
- Accent colors available: `#abb8c3` (cyan-bluish-gray), `#f78da7` (pale-pink), `#9b51e0` (vivid-purple), `#00d084` (vivid-green-cyan)
- Use a restrained palette - prefer 2-3 main colors per page

# Deployment
This site must stay deployable as plain static files with no build step.
Any solution should work when the repository is served directly by static hosting.

## Notes

- Keep the single-file architecture — no bundlers or build steps
- Maintain the squared corner aesthetic (no pills)
- Test scroll animations after content changes
- Counter animations trigger on scroll into view
- **index.html is the main landing page** — don't overwrite with feature content

# Instructions for Claude
When making changes:
- Preserve the static-site approach
- Keep everything simple and production-ready
- Favor readability and elegance over novelty
- Make the site feel personal and credible
- Explain major UI changes briefly before applying them