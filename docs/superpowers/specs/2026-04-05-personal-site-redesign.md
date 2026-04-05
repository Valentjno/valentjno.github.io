# Personal Site Redesign — Balanced Integration Approach

**Date:** 2026-04-05  
**Project:** valentinomerlino.com / GitHub Pages  
**Scope:** Full site redesign (index.html, about.html, work.html, research.html + new contact.html)  
**Goals:** Professional minimalist design, clarify Responsible AI as core philosophy, integrate OWASP AI Exchange contribution, make LinkedIn visible, enable easy contact for mixed audience (employers, academics, organizations seeking security services)

---

## 1. Design Philosophy

**Style:** Professional, minimalist, modern. Reduce animation to essentials. Improve visual hierarchy and readability.

**Core Narrative:** Responsible AI is the through-line philosophy that ties together all work—red-teaming, research, OWASP AI Exchange contribution, industry practice.

**Primary Goals:**
1. Make LinkedIn profile immediately discoverable
2. Enable contact through multiple channels (email, form, LinkedIn)
3. Position Responsible AI as core lens for your work
4. Support mixed audience: employers, academics, organizations seeking security services

---

## 2. Visual Direction

### Hero Image/Icon
- Replace current geometric SVG with professional headshot or minimalist professional icon
- Should feel credible and approachable (supports all three audience types)
- Consistent visual element used in header/footer if applicable

### Animation & Effects
- **Keep:** Fade-in on scroll for text and content sections
- **Remove:** Glow effects, pulse animations, rotating scroll indicators, paragraph-level transform effects
- **Scroll indicator:** Subtle arrow pointing down (static or gentle continuous pulse, not rotating)
- **Philosophy:** Animation should guide attention, not distract. Minimalist aesthetic = restraint.

### Color Palette
- Background: #F2F2F2 (light gray) — keep as-is
- Text: #000000 (black) — keep as-is
- Accent: #f78da7 (pale-pink) — use sparingly on CTAs and hover states only
- Reduce palette usage: accent color appears only on primary buttons and interactive hover states

### Typography & Spacing
- **Headings:** Larger, clearer hierarchy (h1 > h2 > h3)
- **Body text:** Left-aligned (not justified) for modern readability
- **Line height:** Maintain 1.6–1.8 for legibility
- **Spacing:** 80–100px gaps between major sections (reduce over-spacing)
- **Reduce micro-animations:** Remove paragraph-level hover effects that translate/transform text

---

## 3. Site Structure

### Pages & Architecture

**All Pages Share:**
- Consistent header with logo (VM), navigation (home | about | work | research | contact), LinkedIn icon link
- Consistent footer with email link + LinkedIn profile link
- Clean divider lines, aligned padding/margins
- Responsive design (mobile-first approach, currently in place)

**Landing Page (index.html)**
- Hero section: Professional image + minimal intro copy
  - Intro: "AI security researcher | Red teaming | Responsible AI"
  - Subheading frames mission: "Building safer AI through rigorous security research and red-teaming"
- Primary CTA: "Get in touch" button (links to contact.html)
- 3 navigation cards below hero:
  - "About" → about.html
  - "Work & Research" → work.html (or both work + research)
  - "Contact" → contact.html
- Subtle scroll indicator (arrow)

**About Page (about.html)**
- Same header/nav/footer
- Page title: "About"
- Subtitle: "AI security researcher, red teamer, and PhD candidate focused on Responsible AI and adversarial testing"
- Sections (existing, refined):
  - "Who I Am" — Introduce Responsible AI as core lens
  - "My Approach" — Show how Responsible AI shapes your methodology
  - "Background & Education" — Timeline of PhD + industry work
  - "What Drives My Work" — Emphasize Responsible AI philosophy
  - "Beyond Work" — Personal context
- Strong closing with contact CTA

**Research Page (research.html)**
- Page title: "Research"
- Subtitle: "Advancing Responsible AI through security research"
- **OWASP AI Exchange** featured prominently as Responsible AI initiative
  - Your contributor role and contributions explained
- Publications, research projects, focus areas
- All positioned under Responsible AI philosophy

**Work Page (work.html)**
- Page title: "Work"
- Subtitle: "Red-teaming, threat assessment, and security frameworks"
- Case studies, project highlights, methodologies
- Frame projects as "advancing Responsible AI through security"
- Show how red-teaming translates research into practice

**Contact Page (contact.html) — NEW**
- Page title: "Contact"
- Subtitle: "Let's talk about AI security and Responsible AI"
- Contact form (fields: Name, Email, Message, Submit)
- Below form: "Or reach out directly:" with email link + LinkedIn profile link
- Clear, minimal design

---

## 4. Navigation & Header Design

**Header (consistent across all pages):**
- Left: Logo "VM" (links to index.html)
- Center/Right: Navigation links (home | about | work | research | contact)
- Far right: LinkedIn icon (links to your LinkedIn profile, opens in new tab)
- Clean border-bottom divider

**LinkedIn Integration:**
- Header: LinkedIn icon/link (always visible, subtle styling)
- About page: LinkedIn link in closing section
- Footer: "LinkedIn" text link visible alongside email
- Contact page: LinkedIn link as alternative contact method

---

## 5. Content Positioning

### Responsible AI as Core Philosophy
- Landing page intro establishes Responsible AI as your approach
- About page: Explain how Responsible AI informs your methodology
- Research page: Show how OWASP AI Exchange and your research embody Responsible AI principles
- Work page: Frame security projects as advancing Responsible AI practice

### OWASP AI Exchange
- Featured on research page with explanation of your contributor role
- Positioned as a Responsible AI initiative
- Clear description of what you contribute

### Mixed Audience Support
- **Employers:** About page + LinkedIn link + easy contact
- **Academics:** Research page + publications + contact for collaboration
- **Organizations seeking security:** Work page + red-teaming services + contact form

---

## 6. Contact Strategy

**Multiple Contact Channels:**
1. Landing page CTA button ("Get in touch") → contact.html form
2. Email link (visible in header nav or footer across all pages)
3. LinkedIn profile link (header + throughout site)
4. Dedicated contact form on contact.html

**Contact Form (contact.html):**
- Fields: Name | Email | Message | Submit
- Clean, minimal design (matches site aesthetic)
- Form submission behavior: TBD based on hosting solution (GitHub Pages requires external service)
- Fallback: Direct email link below form

**CTA Language:**
- Landing: "Get in touch"
- Contact page: "Let's talk about AI security and Responsible AI"
- Footer: Email link + "Contact me about opportunities"

---

## 7. Layout & Spacing

### Responsive Design
- Mobile-first approach (already in place, refine)
- Breakpoints: 480px, 768px, 1200px+
- Ensure readability and navigation work on all sizes

### Spacing & Hierarchy
- Section gaps: 80–100px (reduce over-spacing)
- Heading sizes: Clear hierarchy (h1 largest, h2 medium, h3 small)
- Content width: max-width 900px for readability
- Padding: Consistent 40px desktop, 24px tablet, 16px mobile

### Remove Unnecessary Effects
- Paragraph hover effects (transform, text-shadow) — too micro
- Glow animations on geometric art
- Pulse animations on nav tabs
- Rotating scroll indicators

---

## 8. Technical Considerations

**Platform:** GitHub Pages (static HTML/CSS/JS only)  
**Hosting:** valentinomerlino.github.io or custom domain  
**Build:** None required (static files)  
**Form Handling:** Contact form requires external service (Formspree, Netlify Forms, or similar) since GitHub Pages can't process server-side form submissions

**File Structure (maintain):**
- index.html (landing)
- about.html (about)
- work.html (work)
- research.html (research)
- contact.html (NEW)
- Single embedded CSS + JS per file (no bundler)

---

## 9. Success Criteria

- [ ] Landing page clearly establishes your identity and Responsible AI focus
- [ ] LinkedIn profile easily discoverable (header link + multiple mentions)
- [ ] Contact options clear and multiple (form + email + LinkedIn)
- [ ] OWASP AI Exchange contribution prominent on research page
- [ ] Mobile responsive and readable on all devices
- [ ] No animation exceeds purpose (fade-in on scroll only)
- [ ] Visual hierarchy clear: headings > body copy > secondary text
- [ ] Consistent header/footer/nav across all pages
- [ ] Professional, minimalist aesthetic throughout

---

## 10. Implementation Phases

1. **Phase 1:** Redesign landing page (index.html) with new hero, navigation cards, minimal animations
2. **Phase 2:** Update about.html to emphasize Responsible AI philosophy
3. **Phase 3:** Update research.html with OWASP AI Exchange prominence
4. **Phase 4:** Update work.html for consistency
5. **Phase 5:** Create new contact.html with form + contact options
6. **Phase 6:** Implement consistent header/footer across all pages
7. **Phase 7:** Test responsive design, deploy to GitHub Pages
