# Personal Site Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Redesign personal site with professional minimalist aesthetic, emphasize Responsible AI as core philosophy, integrate OWASP AI Exchange, and make LinkedIn/contact easily discoverable.

**Architecture:** All pages will share consistent header (with LinkedIn link), footer (with email + LinkedIn), and CSS foundation. Landing page redesigned with professional image + navigation cards. Content pages updated to emphasize Responsible AI. New contact page with form + contact options. Single-file architecture maintained (no bundler).

**Tech Stack:** Static HTML/CSS/JavaScript, GitHub Pages compatible, Formspree (or similar) for contact form backend.

---

## File Structure

**Modified Files:**
- `index.html` — Landing page (major redesign)
- `about.html` — Content updates + consistent header/footer
- `work.html` — Content updates + consistent header/footer
- `research.html` — Content updates + OWASP AI Exchange feature + consistent header/footer
- `style.css` (optional) — If extracting shared CSS, else keep embedded

**New Files:**
- `contact.html` — New contact page with form + contact options

**Assets Needed:**
- Professional headshot image (JPG/PNG) or placeholder icon (to be added to `/images/` or base directory)

---

## Phase 1: CSS Foundation & Design System

### Task 1: Create Shared CSS Resets and Design System

**Files:**
- Modify: `index.html:14-40` (style section)
- Apply to: All other .html files

This task establishes the CSS foundation that all pages will use. Remove animations we don't need, establish better spacing/typography defaults.

- [ ] **Step 1: Update CSS reset and variables in index.html**

Replace the `:root` and base reset styles with cleaner, more minimal versions. In `index.html`, locate the `<style>` tag and update it:

```css
:root {
    --wp--preset--font-size--small: 13px;
    --wp--preset--font-size--normal: 16px;
    --wp--preset--font-size--medium: 20px;
    --wp--preset--font-size--large: 36px;
    --wp--preset--font-size--x-large: 42px;
    --wp--preset--color--black: #000000;
    --wp--preset--color--white: #ffffff;
    --wp--preset--color--pale-pink: #f78da7;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    outline: none;
    -webkit-font-smoothing: antialiased;
}

html {
    scroll-behavior: smooth;
    font-size: 10px;
}

body {
    font-family: 'Inter', sans-serif;
    background-color: #F2F2F2;
    color: var(--wp--preset--color--black);
    line-height: 1.6;
    font-size: var(--wp--preset--font-size--normal);
    position: relative;
}

a {
    color: var(--wp--preset--color--black);
    text-decoration: none;
    transition: opacity 0.2s ease;
}

a:hover {
    opacity: 0.7;
}
```

- [ ] **Step 2: Remove unnecessary animations from global styles**

In the same `<style>` section, locate and remove/simplify these animations:
- Remove `.glow` keyframe (drop-shadow animation on geometric-art)
- Remove `.pulse` keyframe 
- Remove all paragraph-level hover effects that use `transform` or `text-shadow`
- Keep only `fadeInUp`, `fadeInLeft`, `fadeInDown`, `fadeInRight` for scroll reveal

Remove these rules entirely:
```css
/* Remove: */
.section-content p:hover {
    color: var(--wp--preset--color--pale-pink);
    transform: translateX(8px);
    text-shadow: 0 0 8px rgba(247, 141, 167, 0.2);
}

.geometric-art {
    animation: glow 3s ease-in-out infinite;
}

.scroll-anim:hover {
    transform: none;
    color: var(--wp--preset--color--pale-pink);
    font-weight: 500;
    letter-spacing: 1px;
}
```

- [ ] **Step 3: Update typography defaults**

Add these new base styles for better hierarchy:

```css
h1 {
    font-size: 2.4rem;
    font-weight: 700;
    line-height: 1.2;
    margin-bottom: 1rem;
}

h2 {
    font-size: 1.5rem;
    font-weight: 600;
    line-height: 1.3;
    margin-bottom: 1.5rem;
    margin-top: 2rem;
}

h2:first-of-type {
    margin-top: 0;
}

h3 {
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 0.75rem;
}

p {
    font-size: 0.9rem;
    line-height: 1.8;
    margin-bottom: 1rem;
    text-align: left;
}

p:last-child {
    margin-bottom: 0;
}
```

- [ ] **Step 4: Verify changes in browser**

Open `index.html` in a browser and confirm:
- Text is left-aligned (not justified)
- Spacing looks reasonable (not overly spaced)
- No glow or pulse animations on the geometric art
- No transform effects on paragraphs when hovering

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "style: reset CSS foundation, remove micro-animations, improve typography defaults"
```

---

## Phase 2: Create Reusable Header & Footer

### Task 2: Create Consistent Header Component

**Files:**
- Modify: `index.html:69-75` (header styles)
- Reference for: about.html, work.html, research.html, contact.html

This task establishes a header that appears on every page with logo, navigation, and LinkedIn link.

- [ ] **Step 1: Update header styles in index.html**

In `index.html`, find the `/* Header */` section (around line 69) and replace it with:

```css
/* Header */
header {
    padding: 30px 40px;
    max-width: 1200px;
    margin: 0 auto;
    border-bottom: 1px solid #ddd;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 30px;
}

.header-logo {
    font-weight: 700;
    font-size: 14px;
    letter-spacing: 0.05em;
}

.header-logo a {
    display: inline-block;
    color: var(--wp--preset--color--black);
    text-decoration: none;
    transition: opacity 0.2s ease;
}

.header-logo a:hover {
    opacity: 0.7;
}

.header-nav {
    display: flex;
    gap: 30px;
    align-items: center;
    font-size: 12px;
}

.header-nav a {
    color: var(--wp--preset--color--black);
    text-decoration: none;
    transition: opacity 0.2s ease;
    position: relative;
}

.header-nav a:hover {
    opacity: 0.6;
}

.header-nav a.active {
    text-decoration: underline;
}

.header-nav-linkedin {
    margin-left: 15px;
    padding-left: 15px;
    border-left: 1px solid #ddd;
}

.header-nav-linkedin a {
    display: inline-flex;
    align-items: center;
    font-size: 13px;
}

@media (max-width: 768px) {
    header {
        padding: 24px;
        flex-direction: column;
        align-items: flex-start;
    }

    .header-nav {
        gap: 20px;
        font-size: 11px;
        width: 100%;
        flex-wrap: wrap;
    }
}

@media (max-width: 480px) {
    header {
        padding: 20px 16px;
    }

    .header-nav {
        gap: 12px;
    }

    .header-nav-linkedin {
        margin-left: 0;
        padding-left: 0;
        border-left: none;
    }
}
```

- [ ] **Step 2: Update header HTML in index.html**

Replace the current `<header>` block (lines 533-575) with:

```html
<!-- Header -->
<header>
    <div class="header-logo">
        <a href="index.html">VM</a>
    </div>
    <nav class="header-nav">
        <a href="index.html">home</a>
        <a href="about.html">about</a>
        <a href="work.html">work</a>
        <a href="research.html">research</a>
        <a href="contact.html">contact</a>
        <div class="header-nav-linkedin">
            <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank" title="LinkedIn">LinkedIn ↗</a>
        </div>
    </nav>
</header>
```

- [ ] **Step 3: Verify header rendering**

Open `index.html` in browser. Confirm:
- Logo "VM" on left, clickable
- Navigation links in row: home | about | work | research | contact
- LinkedIn link visible on right
- Clean divider below header
- Responsive: stacks on mobile

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add consistent header with navigation and LinkedIn link"
```

---

### Task 3: Create Consistent Footer Component

**Files:**
- Modify: `index.html:383-432` (footer section)
- Reference for: about.html, work.html, research.html, contact.html

- [ ] **Step 1: Update footer styles in index.html**

In `index.html`, find the `/* Footer */` section and replace it with:

```css
/* Footer */
footer {
    background-color: #1a1a1a;
    color: var(--wp--preset--color--white);
    padding: 60px 40px;
    margin-top: 100px;
}

.footer-content {
    max-width: 1200px;
    margin: 0 auto;
    text-align: center;
}

.footer-text {
    font-size: 16px;
    margin-bottom: 30px;
    line-height: 1.6;
}

.footer-links {
    display: flex;
    justify-content: center;
    gap: 30px;
    flex-wrap: wrap;
    font-size: 12px;
}

.footer-links a {
    color: var(--wp--preset--color--white);
    text-decoration: none;
    transition: opacity 0.2s ease;
}

.footer-links a:hover {
    opacity: 0.7;
}

@media (max-width: 768px) {
    footer {
        padding: 40px 24px;
    }

    .footer-links {
        gap: 20px;
    }
}

@media (max-width: 480px) {
    footer {
        padding: 30px 16px;
    }

    .footer-text {
        font-size: 14px;
    }

    .footer-links {
        gap: 12px;
        font-size: 11px;
    }
}
```

- [ ] **Step 2: Update footer HTML in index.html**

Replace the current `<footer>` block (around line 651-663) with:

```html
<!-- Footer -->
<footer>
    <div class="footer-content">
        <p class="footer-text">Let's talk about AI security.</p>
        <div class="footer-links">
            <a href="mailto:valentino@example.com">email</a>
            <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank">LinkedIn</a>
            <a href="https://twitter.com" target="_blank">twitter</a>
            <a href="https://github.com" target="_blank">github</a>
        </div>
    </div>
</footer>
```

- [ ] **Step 3: Verify footer rendering**

Open `index.html` in browser and scroll to bottom. Confirm:
- Dark background (#1a1a1a)
- Tagline "Let's talk about AI security."
- Footer links visible: email, LinkedIn, twitter, github
- Responsive: links wrap on mobile
- All links clickable

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add consistent footer with email and LinkedIn links"
```

---

## Phase 3: Redesign Landing Page

### Task 4: Replace Hero SVG and Update Landing Page Content

**Files:**
- Modify: `index.html:532-607` (header section + nav tabs)
- Note: Professional image will be added as placeholder reference (actual image TBD)

- [ ] **Step 1: Replace geometric SVG with professional image placeholder**

In `index.html`, find the `.header-visual` section and replace the SVG with:

```html
<div class="header-visual">
    <img src="https://via.placeholder.com/280x280/f2f2f2/000000?text=Professional+Photo" alt="Valentino Merlino - AI Security Researcher" class="hero-image" />
    <div class="scroll-explore">
        <p class="scroll-anim">scroll to explore</p>
    </div>
</div>
```

Add CSS for the image:

```css
.hero-image {
    width: 280px;
    height: 280px;
    border-radius: 4px;
    object-fit: cover;
}
```

- [ ] **Step 2: Update hero text and copy**

Update the `.header-intro` and related text in the header. Replace lines around 536-541 with:

```html
<div class="header-text">
    <h1>Hello, I'm Valentino Merlino</h1>
    <p class="header-intro">AI security researcher | Red teaming | Responsible AI</p>
    <p class="header-tagline">Building safer AI through rigorous security research and red-teaming</p>
    <a href="contact.html" class="btn-primary">Get in touch</a>
</div>
```

Add button styles to CSS:

```css
.btn-primary {
    display: inline-block;
    margin-top: 20px;
    padding: 12px 30px;
    background-color: var(--wp--preset--color--pale-pink);
    color: var(--wp--preset--color--black);
    font-size: 12px;
    font-weight: 600;
    border-radius: 4px;
    transition: all 0.3s ease;
    text-decoration: none;
}

.btn-primary:hover {
    background-color: #f06690;
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(247, 141, 167, 0.2);
}

.header-tagline {
    font-size: 14px;
    line-height: 1.7;
    margin-bottom: 20px;
    color: #666;
}
```

- [ ] **Step 3: Remove old navigation tabs, replace with navigation cards**

Remove the `.nav-tabs` section (lines 577-606) and replace with:

```html
<!-- Navigation Cards -->
<div class="nav-cards">
    <a href="about.html" class="nav-card">
        <h3>About</h3>
        <p>Learn about my background, approach, and what drives my work</p>
    </a>
    <a href="work.html" class="nav-card">
        <h3>Work & Research</h3>
        <p>Red-teaming, threat assessment, and AI security research</p>
    </a>
    <a href="contact.html" class="nav-card">
        <h3>Contact</h3>
        <p>Reach out about opportunities, collaborations, or projects</p>
    </a>
</div>
```

Add CSS for nav cards:

```css
/* Navigation Cards */
.nav-cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    max-width: 1200px;
    margin: 60px auto;
    padding: 0 40px;
}

.nav-card {
    padding: 30px;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 4px;
    display: block;
    text-decoration: none;
    color: var(--wp--preset--color--black);
    transition: all 0.3s ease;
    animation: fadeInUp 0.8s ease-out backwards;
}

.nav-card:hover {
    border-color: var(--wp--preset--color--pale-pink);
    box-shadow: 0 8px 24px rgba(247, 141, 167, 0.1);
    transform: translateY(-4px);
}

.nav-card h3 {
    font-size: 14px;
    font-weight: 600;
    margin-bottom: 10px;
}

.nav-card p {
    font-size: 12px;
    color: #666;
    line-height: 1.6;
}

@media (max-width: 768px) {
    .nav-cards {
        grid-template-columns: 1fr;
        gap: 16px;
        margin: 40px auto;
        padding: 0 24px;
    }
}

@media (max-width: 480px) {
    .nav-cards {
        grid-template-columns: 1fr;
        gap: 12px;
        margin: 30px auto;
        padding: 0 16px;
    }

    .nav-card {
        padding: 20px;
    }

    .nav-card h3 {
        font-size: 13px;
    }

    .nav-card p {
        font-size: 11px;
    }
}
```

- [ ] **Step 4: Update scroll indicator (minimal)**

Replace the scroll animation with a simpler version. Remove the `.scroll-explore` complex animation and use just:

```css
.scroll-anim {
    font-size: 12px;
    color: #999;
    font-weight: 400;
    opacity: 0.8;
    animation: fadeInUp 0.6s ease-out 0.8s forwards;
}
```

- [ ] **Step 5: Verify landing page in browser**

Open `index.html` and confirm:
- Header shows "Hello, I'm Valentino Merlino" with professional photo placeholder
- Copy shows "AI security researcher | Red teaming | Responsible AI"
- "Get in touch" button visible and clickable
- 3 navigation cards below (About, Work & Research, Contact)
- Subtle scroll indicator at bottom
- Responsive on mobile (cards stack)

- [ ] **Step 6: Commit**

```bash
git add index.html
git commit -m "feat: redesign landing page with professional hero, navigation cards, and clear CTA"
```

---

## Phase 4: Update Content Pages

### Task 5: Update about.html - Emphasize Responsible AI

**Files:**
- Modify: `about.html:69-118` (header/nav sections)
- Modify: `about.html:380-435` (content)

- [ ] **Step 1: Replace header in about.html with consistent header**

Replace lines 370-384 with:

```html
<!-- Header -->
<header>
    <div class="header-logo">
        <a href="index.html">VM</a>
    </div>
    <nav class="header-nav">
        <a href="index.html">home</a>
        <a href="about.html" class="active">about</a>
        <a href="work.html">work</a>
        <a href="research.html">research</a>
        <a href="contact.html">contact</a>
        <div class="header-nav-linkedin">
            <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank" title="LinkedIn">LinkedIn ↗</a>
        </div>
    </nav>
</header>

<!-- Page Intro -->
<div style="max-width: 1200px; margin: 0 auto; padding: 60px 40px; border-bottom: 1px solid #ddd;">
    <h1 style="font-size: 2.4rem; font-weight: 700; margin-bottom: 1rem;">About</h1>
    <p style="font-size: 16px; color: #666; line-height: 1.7; max-width: 600px;">AI security researcher, red teamer, and PhD candidate focused on Responsible AI and adversarial testing.</p>
</div>
```

Copy the header CSS from `index.html` to `about.html` `<style>` section.

- [ ] **Step 2: Update "Who I Am" section to introduce Responsible AI**

Find the "Who I Am" section and update it to:

```html
<section>
    <h2>Who I Am</h2>
    <div class="section-content">
        <p>I'm an AI security researcher and red teamer with a focus on Responsible AI. My work combines rigorous security engineering principles with emerging machine learning concerns to help organizations build safer, more reliable AI systems.</p>
        <p>I'm a PhD candidate at the University of Catania, where my research centers on adversarial robustness and safety mechanisms in large language models. Simultaneously, I work in industry on practical red-teaming initiatives and security assessments informed by Responsible AI principles.</p>
    </div>
</section>
```

- [ ] **Step 3: Update "My Approach" to emphasize Responsible AI lens**

Replace the "My Approach" section with:

```html
<section>
    <h2>My Approach</h2>
    <div class="section-content">
        <p>I believe AI security isn't just about finding bugs—it's about advancing Responsible AI through rigorous security research. My methodology combines:</p>
        <ul>
            <li><strong>Adversarial Thinking:</strong> Approaching systems as a potential attacker would, but with safety and ethics as the foundation.</li>
            <li><strong>Responsible AI Focus:</strong> Ensuring security research translates into frameworks and practices that promote responsible development.</li>
            <li><strong>Rigor:</strong> Grounding red-teaming exercises in structured threat models and documented methodologies.</li>
            <li><strong>Collaboration:</strong> Working closely with engineers, researchers, and policy makers to translate findings into actionable improvements.</li>
            <li><strong>Continuous Learning:</strong> Staying current with emerging attack vectors, model capabilities, and regulatory developments.</li>
        </ul>
    </div>
</section>
```

- [ ] **Step 4: Update footer in about.html**

Replace the footer with:

```html
<!-- Footer -->
<footer>
    <div class="footer-content">
        <p class="footer-text">Let's talk about AI security.</p>
        <div class="footer-links">
            <a href="mailto:valentino@example.com">email</a>
            <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank">LinkedIn</a>
            <a href="https://twitter.com" target="_blank">twitter</a>
            <a href="https://github.com" target="_blank">github</a>
        </div>
    </div>
</footer>
```

Copy footer CSS from `index.html`.

- [ ] **Step 5: Remove old paragraph hover effects from about.html CSS**

In about.html `<style>`, remove:
- `.section-content p:hover` rule (transform, text-shadow)
- Any `.timeline-item:hover h3` color change animations

Simplify timeline-item hover:

```css
.timeline-item:hover {
    background-color: rgba(247, 141, 167, 0.05);
    box-shadow: 0 4px 12px rgba(247, 141, 167, 0.1);
}
```

- [ ] **Step 6: Verify about.html in browser**

Open `about.html` and confirm:
- Consistent header with navigation and LinkedIn link
- Page title "About" with subtitle
- "Who I Am" section emphasizes Responsible AI
- "My Approach" lists methodology points
- Footer shows email + LinkedIn
- Responsive on mobile
- No transform effects on hover

- [ ] **Step 7: Commit**

```bash
git add about.html
git commit -m "feat: update about page to emphasize Responsible AI philosophy"
```

---

### Task 6: Update research.html - Feature OWASP AI Exchange

**Files:**
- Modify: `research.html` (create if doesn't exist, or update existing)

For this task, create a new `research.html` file:

- [ ] **Step 1: Create research.html with header/footer structure**

Create `/home/valentino/Project/VM-CV-Personal-Site/research.html` with:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Research - Valentino Merlino | AI Security & Responsible AI">
    <meta name="author" content="Valentino Merlino">
    <title>Research | Valentino Merlino</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --wp--preset--font-size--small: 13px;
            --wp--preset--font-size--normal: 16px;
            --wp--preset--font-size--medium: 20px;
            --wp--preset--color--black: #000000;
            --wp--preset--color--white: #ffffff;
            --wp--preset--color--pale-pink: #f78da7;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            outline: none;
            -webkit-font-smoothing: antialiased;
        }
        
        html {
            scroll-behavior: smooth;
            font-size: 10px;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F2F2F2;
            color: var(--wp--preset--color--black);
            line-height: 1.6;
            font-size: var(--wp--preset--font-size--normal);
        }
        
        a {
            color: var(--wp--preset--color--black);
            text-decoration: none;
            transition: opacity 0.2s ease;
        }
        
        a:hover {
            opacity: 0.7;
        }
        
        /* Header */
        header {
            padding: 30px 40px;
            max-width: 1200px;
            margin: 0 auto;
            border-bottom: 1px solid #ddd;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 30px;
        }
        
        .header-logo {
            font-weight: 700;
            font-size: 14px;
            letter-spacing: 0.05em;
        }
        
        .header-logo a {
            display: inline-block;
            color: var(--wp--preset--color--black);
            text-decoration: none;
            transition: opacity 0.2s ease;
        }
        
        .header-nav {
            display: flex;
            gap: 30px;
            align-items: center;
            font-size: 12px;
        }
        
        .header-nav a {
            color: var(--wp--preset--color--black);
            text-decoration: none;
            transition: opacity 0.2s ease;
        }
        
        .header-nav a:hover {
            opacity: 0.6;
        }
        
        .header-nav a.active {
            text-decoration: underline;
        }
        
        .header-nav-linkedin {
            margin-left: 15px;
            padding-left: 15px;
            border-left: 1px solid #ddd;
        }
        
        .header-nav-linkedin a {
            display: inline-flex;
            align-items: center;
            font-size: 13px;
        }
        
        /* Page Intro */
        .page-intro {
            max-width: 1200px;
            margin: 0 auto;
            padding: 60px 40px;
            border-bottom: 1px solid #ddd;
        }
        
        .page-intro h1 {
            font-size: 2.4rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }
        
        .page-intro p {
            font-size: 16px;
            color: #666;
            line-height: 1.7;
            max-width: 600px;
        }
        
        /* Main Content */
        main {
            max-width: 900px;
            margin: 0 auto;
            padding: 60px 40px;
        }
        
        section {
            margin-bottom: 80px;
        }
        
        section h2 {
            font-size: 1.5rem;
            font-weight: 600;
            margin-bottom: 1.5rem;
            margin-top: 2rem;
        }
        
        section h2:first-of-type {
            margin-top: 0;
        }
        
        section p {
            font-size: 0.9rem;
            line-height: 1.8;
            margin-bottom: 1rem;
            text-align: left;
        }
        
        section h3 {
            font-size: 1rem;
            font-weight: 600;
            margin-bottom: 0.75rem;
        }
        
        .highlight-box {
            background-color: rgba(247, 141, 167, 0.05);
            border-left: 4px solid var(--wp--preset--color--pale-pink);
            padding: 20px;
            margin: 20px 0;
            border-radius: 4px;
        }
        
        .highlight-box h3 {
            margin-bottom: 10px;
            color: var(--wp--preset--color--pale-pink);
        }
        
        /* Footer */
        footer {
            background-color: #1a1a1a;
            color: var(--wp--preset--color--white);
            padding: 60px 40px;
            margin-top: 100px;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            text-align: center;
        }
        
        .footer-text {
            font-size: 16px;
            margin-bottom: 30px;
            line-height: 1.6;
        }
        
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            font-size: 12px;
        }
        
        .footer-links a {
            color: var(--wp--preset--color--white);
            text-decoration: none;
            transition: opacity 0.2s ease;
        }
        
        .footer-links a:hover {
            opacity: 0.7;
        }
        
        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        section {
            animation: fadeInUp 0.8s ease-out backwards;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            header {
                padding: 24px;
                flex-direction: column;
                align-items: flex-start;
            }
            
            .header-nav {
                gap: 20px;
                font-size: 11px;
                width: 100%;
                flex-wrap: wrap;
            }
            
            .page-intro {
                padding: 40px 24px;
            }
            
            .page-intro h1 {
                font-size: 1.8rem;
            }
            
            main {
                padding: 40px 24px;
            }
        }
        
        @media (max-width: 480px) {
            header {
                padding: 20px 16px;
            }
            
            .header-nav {
                gap: 12px;
            }
            
            .header-nav-linkedin {
                margin-left: 0;
                padding-left: 0;
                border-left: none;
            }
            
            .page-intro {
                padding: 30px 16px;
            }
            
            .page-intro h1 {
                font-size: 1.5rem;
            }
            
            main {
                padding: 30px 16px;
            }
            
            footer {
                padding: 30px 16px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="header-logo">
            <a href="index.html">VM</a>
        </div>
        <nav class="header-nav">
            <a href="index.html">home</a>
            <a href="about.html">about</a>
            <a href="work.html">work</a>
            <a href="research.html" class="active">research</a>
            <a href="contact.html">contact</a>
            <div class="header-nav-linkedin">
                <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank" title="LinkedIn">LinkedIn ↗</a>
            </div>
        </nav>
    </header>
    
    <!-- Page Intro -->
    <div class="page-intro">
        <h1>Research</h1>
        <p>Advancing Responsible AI through security research and adversarial testing.</p>
    </div>
    
    <!-- Main Content -->
    <main>
        <section>
            <h2>OWASP AI Exchange</h2>
            <p>I am a contributor to the OWASP AI Exchange, a collaborative initiative that advances Responsible AI by documenting and sharing knowledge about AI security risks, controls, and best practices.</p>
            <div class="highlight-box">
                <h3>My Contribution</h3>
                <p>As a contributor, I help develop threat models, security controls, and risk frameworks for AI systems. This work bridges academic research and industry practice, ensuring that security considerations are built into AI development from the ground up.</p>
            </div>
            <p>The OWASP AI Exchange embodies Responsible AI principles by promoting transparency, collaboration, and shared standards for AI security across the industry.</p>
        </section>
        
        <section>
            <h2>Research Focus Areas</h2>
            <p>My research centers on understanding and mitigating vulnerabilities in AI systems. Key areas include:</p>
            <ul style="list-style: none; padding-left: 0;">
                <li style="margin-bottom: 12px;"><strong>Adversarial Robustness:</strong> How to make AI models resilient against adversarial examples and evasion attacks.</li>
                <li style="margin-bottom: 12px;"><strong>Prompt Injection & LLM Security:</strong> Identifying and preventing prompt-based attacks on large language models.</li>
                <li style="margin-bottom: 12px;"><strong>AI Safety Mechanisms:</strong> Developing and evaluating safety features that align AI behavior with human values.</li>
                <li style="margin-bottom: 12px;"><strong>Red-Teaming Methodologies:</strong> Structuring adversarial testing to surface realistic risks before deployment.</li>
            </ul>
        </section>
        
        <section>
            <h2>Academic Work</h2>
            <p>My PhD research at the University of Catania focuses on the intersection of adversarial robustness and Responsible AI. I combine classical security thinking with emerging ML concerns to develop frameworks that make AI systems safer and more trustworthy.</p>
        </section>
    </main>
    
    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <p class="footer-text">Let's talk about AI security.</p>
            <div class="footer-links">
                <a href="mailto:valentino@example.com">email</a>
                <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank">LinkedIn</a>
                <a href="https://twitter.com" target="_blank">twitter</a>
                <a href="https://github.com" target="_blank">github</a>
            </div>
        </div>
    </footer>
</body>
</html>
```

- [ ] **Step 2: Verify research.html in browser**

Open `research.html` and confirm:
- Header with consistent navigation
- "Research" title and subtitle
- OWASP AI Exchange prominently featured with "My Contribution" highlight box
- Research focus areas listed
- Footer with email + LinkedIn
- Responsive on mobile

- [ ] **Step 3: Commit**

```bash
git add research.html
git commit -m "feat: create research page with OWASP AI Exchange prominence"
```

---

### Task 7: Create/Update work.html

**Files:**
- Create/Modify: `work.html`

- [ ] **Step 1: Create or update work.html with consistent structure**

Create or update `/home/valentino/Project/VM-CV-Personal-Site/work.html`. Use similar structure to `research.html` with this content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Work - Valentino Merlino | AI Security & Red-Teaming">
    <meta name="author" content="Valentino Merlino">
    <title>Work | Valentino Merlino</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- [Use same CSS as research.html above] -->
    <style>
        /* Copy all CSS from research.html <style> section */
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="header-logo">
            <a href="index.html">VM</a>
        </div>
        <nav class="header-nav">
            <a href="index.html">home</a>
            <a href="about.html">about</a>
            <a href="work.html" class="active">work</a>
            <a href="research.html">research</a>
            <a href="contact.html">contact</a>
            <div class="header-nav-linkedin">
                <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank" title="LinkedIn">LinkedIn ↗</a>
            </div>
        </nav>
    </header>
    
    <!-- Page Intro -->
    <div class="page-intro">
        <h1>Work</h1>
        <p>Red-teaming, threat assessment, and advancing Responsible AI through security practice.</p>
    </div>
    
    <!-- Main Content -->
    <main>
        <section>
            <h2>Red-Teaming & Security Research</h2>
            <p>I conduct structured red-teaming exercises and threat assessments to identify vulnerabilities in AI systems before deployment. My approach combines adversarial thinking with rigorous methodology to surface realistic risks.</p>
        </section>
        
        <section>
            <h2>Methodologies</h2>
            <ul style="list-style: none; padding-left: 0;">
                <li style="margin-bottom: 12px;"><strong>Threat Modeling:</strong> Developing comprehensive threat models that identify attack vectors and potential failure modes.</li>
                <li style="margin-bottom: 12px;"><strong>Adversarial Testing:</strong> Designing and executing adversarial examples to evaluate system robustness.</li>
                <li style="margin-bottom: 12px;"><strong>Security Frameworks:</strong> Developing practical security frameworks that translate research into actionable practices.</li>
                <li style="margin-bottom: 12px;"><strong>Responsible AI Integration:</strong> Ensuring security research informs responsible AI development practices.</li>
            </ul>
        </section>
        
        <section>
            <h2>Industries & Clients</h2>
            <p>I work with a range of organizations—from academic institutions to industry partners—helping them understand and mitigate AI-specific security risks. My experience spans:</p>
            <ul style="list-style: none; padding-left: 0;">
                <li style="margin-bottom: 12px;">Research organizations building next-generation AI systems</li>
                <li style="margin-bottom: 12px;">Companies developing AI-powered products and services</li>
                <li style="margin-bottom: 12px;">Policy and regulatory bodies designing AI governance frameworks</li>
            </ul>
        </section>
    </main>
    
    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <p class="footer-text">Let's talk about AI security.</p>
            <div class="footer-links">
                <a href="mailto:valentino@example.com">email</a>
                <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank">LinkedIn</a>
                <a href="https://twitter.com" target="_blank">twitter</a>
                <a href="https://github.com" target="_blank">github</a>
            </div>
        </div>
    </footer>
</body>
</html>
```

- [ ] **Step 2: Verify work.html in browser**

Open `work.html` and confirm:
- Header with active "work" link
- "Work" title with subtitle
- Methodologies section clear
- Industries/clients section
- Footer visible
- Responsive on mobile

- [ ] **Step 3: Commit**

```bash
git add work.html
git commit -m "feat: create work page with red-teaming methodologies and Responsible AI framing"
```

---

## Phase 5: Create Contact Page

### Task 8: Create contact.html with Form and Contact Options

**Files:**
- Create: `contact.html`

- [ ] **Step 1: Create contact.html with form**

Create `/home/valentino/Project/VM-CV-Personal-Site/contact.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Contact - Valentino Merlino | AI Security Researcher">
    <meta name="author" content="Valentino Merlino">
    <title>Contact | Valentino Merlino</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --wp--preset--font-size--small: 13px;
            --wp--preset--font-size--normal: 16px;
            --wp--preset--color--black: #000000;
            --wp--preset--color--white: #ffffff;
            --wp--preset--color--pale-pink: #f78da7;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            outline: none;
            -webkit-font-smoothing: antialiased;
        }
        
        html {
            scroll-behavior: smooth;
            font-size: 10px;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F2F2F2;
            color: var(--wp--preset--color--black);
            line-height: 1.6;
            font-size: var(--wp--preset--font-size--normal);
        }
        
        a {
            color: var(--wp--preset--color--black);
            text-decoration: none;
            transition: opacity 0.2s ease;
        }
        
        a:hover {
            opacity: 0.7;
        }
        
        /* Header */
        header {
            padding: 30px 40px;
            max-width: 1200px;
            margin: 0 auto;
            border-bottom: 1px solid #ddd;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 30px;
        }
        
        .header-logo {
            font-weight: 700;
            font-size: 14px;
            letter-spacing: 0.05em;
        }
        
        .header-logo a {
            color: var(--wp--preset--color--black);
            transition: opacity 0.2s ease;
        }
        
        .header-nav {
            display: flex;
            gap: 30px;
            align-items: center;
            font-size: 12px;
        }
        
        .header-nav a {
            color: var(--wp--preset--color--black);
            transition: opacity 0.2s ease;
        }
        
        .header-nav a.active {
            text-decoration: underline;
        }
        
        .header-nav-linkedin {
            margin-left: 15px;
            padding-left: 15px;
            border-left: 1px solid #ddd;
        }
        
        /* Page Intro */
        .page-intro {
            max-width: 1200px;
            margin: 0 auto;
            padding: 60px 40px;
            border-bottom: 1px solid #ddd;
        }
        
        .page-intro h1 {
            font-size: 2.4rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }
        
        .page-intro p {
            font-size: 16px;
            color: #666;
            line-height: 1.7;
            max-width: 600px;
        }
        
        /* Main Content */
        main {
            max-width: 600px;
            margin: 0 auto;
            padding: 60px 40px;
        }
        
        .contact-form {
            background-color: #fff;
            padding: 40px;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-bottom: 40px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            font-size: 12px;
            font-weight: 600;
            margin-bottom: 6px;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            font-family: 'Inter', sans-serif;
            font-size: 14px;
            border: 1px solid #ddd;
            border-radius: 4px;
            transition: border-color 0.3s ease;
        }
        
        .form-group input:focus,
        .form-group textarea:focus {
            border-color: var(--wp--preset--color--pale-pink);
            box-shadow: 0 0 0 3px rgba(247, 141, 167, 0.1);
        }
        
        .form-group textarea {
            resize: vertical;
            min-height: 120px;
        }
        
        .form-submit {
            display: inline-block;
            padding: 12px 30px;
            background-color: var(--wp--preset--color--pale-pink);
            color: var(--wp--preset--color--black);
            font-size: 12px;
            font-weight: 600;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .form-submit:hover {
            background-color: #f06690;
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(247, 141, 167, 0.2);
        }
        
        .contact-divider {
            text-align: center;
            font-size: 12px;
            color: #999;
            margin: 40px 0;
        }
        
        .contact-options {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin-top: 40px;
            padding-top: 40px;
            border-top: 1px solid #ddd;
        }
        
        .contact-option {
            text-align: center;
        }
        
        .contact-option h3 {
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            margin-bottom: 10px;
            color: #666;
        }
        
        .contact-option a {
            font-size: 16px;
            color: var(--wp--preset--color--black);
            font-weight: 500;
        }
        
        /* Footer */
        footer {
            background-color: #1a1a1a;
            color: var(--wp--preset--color--white);
            padding: 60px 40px;
            margin-top: 100px;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            text-align: center;
        }
        
        .footer-text {
            font-size: 16px;
            margin-bottom: 30px;
            line-height: 1.6;
        }
        
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            font-size: 12px;
        }
        
        .footer-links a {
            color: var(--wp--preset--color--white);
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            header {
                padding: 24px;
                flex-direction: column;
                align-items: flex-start;
            }
            
            .header-nav {
                gap: 20px;
                font-size: 11px;
                width: 100%;
                flex-wrap: wrap;
            }
            
            .page-intro {
                padding: 40px 24px;
            }
            
            main {
                padding: 40px 24px;
            }
            
            .contact-form {
                padding: 30px;
            }
        }
        
        @media (max-width: 480px) {
            header {
                padding: 20px 16px;
            }
            
            .header-nav {
                gap: 12px;
            }
            
            .header-nav-linkedin {
                margin-left: 0;
                padding-left: 0;
                border-left: none;
            }
            
            .page-intro {
                padding: 30px 16px;
            }
            
            .page-intro h1 {
                font-size: 1.5rem;
            }
            
            main {
                padding: 30px 16px;
            }
            
            .contact-form {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="header-logo">
            <a href="index.html">VM</a>
        </div>
        <nav class="header-nav">
            <a href="index.html">home</a>
            <a href="about.html">about</a>
            <a href="work.html">work</a>
            <a href="research.html">research</a>
            <a href="contact.html" class="active">contact</a>
            <div class="header-nav-linkedin">
                <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank" title="LinkedIn">LinkedIn ↗</a>
            </div>
        </nav>
    </header>
    
    <!-- Page Intro -->
    <div class="page-intro">
        <h1>Contact</h1>
        <p>Let's talk about AI security, Responsible AI, and advancing the field together.</p>
    </div>
    
    <!-- Main Content -->
    <main>
        <div class="contact-form">
            <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" id="name" name="name" required />
                </div>
                
                <div class="form-group">
                    <label for="email">Email</label>
                    <input type="email" id="email" name="email" required />
                </div>
                
                <div class="form-group">
                    <label for="message">Message</label>
                    <textarea id="message" name="message" required></textarea>
                </div>
                
                <button type="submit" class="form-submit">Send Message</button>
            </form>
        </div>
        
        <div class="contact-divider">or reach out directly</div>
        
        <div class="contact-options">
            <div class="contact-option">
                <h3>Email</h3>
                <a href="mailto:valentino@example.com">valentino@example.com</a>
            </div>
            
            <div class="contact-option">
                <h3>LinkedIn</h3>
                <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank">View Profile ↗</a>
            </div>
        </div>
    </main>
    
    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <p class="footer-text">Let's talk about AI security.</p>
            <div class="footer-links">
                <a href="mailto:valentino@example.com">email</a>
                <a href="https://www.linkedin.com/in/valentinomerlino" target="_blank">LinkedIn</a>
                <a href="https://twitter.com" target="_blank">twitter</a>
                <a href="https://github.com" target="_blank">github</a>
            </div>
        </div>
    </footer>
</body>
</html>
```

- [ ] **Step 2: Set up form backend (Formspree)**

For GitHub Pages, use Formspree to handle form submissions:

1. Go to https://formspree.io
2. Sign up / login
3. Create a new form for your email (valentino@example.com)
4. Copy the form ID provided
5. Replace `YOUR_FORM_ID` in the form action URL above with your actual ID

Example: `action="https://formspree.io/f/myzzzzzz"`

- [ ] **Step 3: Verify contact.html in browser**

Open `contact.html` and confirm:
- Header with active "contact" link
- "Contact" title and subtitle
- Form visible with fields: Name, Email, Message
- Submit button clickable
- "Or reach out directly" section with Email and LinkedIn options
- Footer visible
- Responsive on mobile

- [ ] **Step 4: Test form submission**

Fill out the form and submit. Verify that:
- You receive an email confirmation from Formspree
- The form redirects or shows success message
- Email link works (`mailto:valentino@example.com`)
- LinkedIn link opens correctly

- [ ] **Step 5: Commit**

```bash
git add contact.html
git commit -m "feat: create contact page with form and contact options"
```

---

## Phase 6: Final Polish & Testing

### Task 9: Verify All Pages Use Consistent Styles and Remove Old Styling

**Files:**
- Verify: index.html, about.html, work.html, research.html, contact.html

This task ensures all pages are consistent and removes any leftover old styles.

- [ ] **Step 1: Test all pages in browser**

Open each page in a browser and confirm:
- **index.html:** Landing page with hero, cards, "Get in touch" CTA
- **about.html:** About page with Responsible AI emphasis
- **work.html:** Work page with methodologies
- **research.html:** Research page with OWASP AI Exchange featured
- **contact.html:** Contact page with form + contact options

- [ ] **Step 2: Verify navigation consistency**

On each page, confirm:
- Header shows "VM" logo (clickable)
- Navigation links: home | about | work | research | contact
- Active link underlined
- LinkedIn link visible (↗ icon)
- Footer shows: email | LinkedIn | twitter | github

- [ ] **Step 3: Test responsive design**

Open each page on mobile (browser DevTools, ~375px width):
- Text readable without zooming
- Navigation stacks nicely
- Form fields full width
- Images/cards responsive
- No horizontal scroll

- [ ] **Step 4: Verify animations are minimal**

On each page:
- Text fades in on scroll (subtle)
- No glow effects
- No spinning/rotating elements
- No paragraph hover transforms
- Button hover: slight lift + shadow

- [ ] **Step 5: Commit verification**

```bash
git add .
git commit -m "style: polish and verify consistency across all pages"
```

---

### Task 10: Update Email Addresses and LinkedIn Profile Links

**Files:**
- Modify: All .html files (index, about, work, research, contact)

- [ ] **Step 1: Replace placeholder email**

Search for `valentino@example.com` in all files and replace with your actual email address.

```bash
# Find all occurrences
grep -r "valentino@example.com" *.html

# In each file, replace with your real email
# Example: valentino.merlino@yourdomain.com
```

- [ ] **Step 2: Replace LinkedIn profile URL**

Search for `https://www.linkedin.com/in/valentinomerlino` in all files. This should be correct, but verify it matches your actual LinkedIn profile.

```bash
grep -r "linkedin.com/in" *.html
```

- [ ] **Step 3: Update Formspree form ID in contact.html**

In `contact.html`, replace `YOUR_FORM_ID` with your actual Formspree ID from Step 2 of Task 8.

- [ ] **Step 4: Update social links (optional)**

In footer links, update twitter/github URLs to your actual profiles:
- Twitter: Replace with your Twitter profile URL
- GitHub: Replace with your GitHub profile URL

- [ ] **Step 5: Commit contact updates**

```bash
git add -A
git commit -m "config: update email, LinkedIn, and contact form details"
```

---

### Task 11: Deploy to GitHub Pages

**Files:**
- Repository setup: Push to GitHub

- [ ] **Step 1: Initialize git repository (if not already)**

```bash
cd /home/valentino/Project/VM-CV-Personal-Site
git init
git add .
git commit -m "initial: personal site redesign"
```

- [ ] **Step 2: Create GitHub repository**

1. Go to https://github.com/new
2. Create repository named `valentinomerlino.github.io` (replace with your username)
3. Do NOT initialize with README / .gitignore / license

- [ ] **Step 3: Add remote and push**

```bash
git remote add origin https://github.com/YOUR_USERNAME/valentinomerlino.github.io.git
git branch -M main
git push -u origin main
```

- [ ] **Step 4: Enable GitHub Pages**

1. Go to repository settings
2. Scroll to "GitHub Pages" section
3. Select "Deploy from a branch"
4. Select `main` branch, `/root` folder
5. Click "Save"

- [ ] **Step 5: Verify deployment**

1. Wait 2-3 minutes for GitHub to build
2. Visit `https://valentinomerlino.github.io` in browser
3. Confirm:
   - Landing page loads
   - All links work
   - Images load
   - Mobile responsive

- [ ] **Step 6: Test all pages**

Manually test:
- Click all navigation links
- Fill out contact form
- Click email link
- Click LinkedIn link
- Test on mobile

- [ ] **Step 7: Final commit**

```bash
git log --oneline
# Verify commits are clean and deployment-ready
```

---

## Success Checklist

Before considering this complete, verify:

- [ ] Landing page has professional image, clear copy, "Get in touch" CTA
- [ ] Navigation cards present (About, Work & Research, Contact)
- [ ] Header consistent across all pages with LinkedIn link
- [ ] About page emphasizes Responsible AI philosophy
- [ ] Research page features OWASP AI Exchange prominently
- [ ] Work page frames projects as advancing Responsible AI
- [ ] Contact page has working form + email + LinkedIn options
- [ ] All animations are minimal (fade-in on scroll only)
- [ ] No paragraph hover effects or micro-animations
- [ ] Mobile responsive (tested at 375px+)
- [ ] Deployed to GitHub Pages at `valentinomerlino.github.io`
- [ ] All links work (navigation, email, LinkedIn, form)
- [ ] Form submission working (Formspree)

---

## Notes for Implementation

- **Image:** Placeholder URL used for hero image. Replace `https://via.placeholder.com/...` with actual headshot image URL or upload image to repository.
- **Formspree ID:** Update contact.html with your actual Formspree form ID.
- **Email/LinkedIn:** Replace placeholder values with real contact info.
- **Color Palette:** Maintains existing palette (#F2F2F2, #000000, #f78da7) per spec.
- **Animations:** Reduced to essentials (fade-in on scroll). No glow, pulse, or transform effects.
- **Fonts:** Inter from Google Fonts (CDN-based, no build step required).
