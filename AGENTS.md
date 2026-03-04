# AGENTS.md - Venus Lean Personal Profile Website

## Project Overview

This is a static personal profile website for Venus Lean (練瑞雲), a Global Business Expansion Strategist. The site is built with pure HTML/CSS/JS and deployed to GitHub Pages.

**Live URL:** https://legendv.me  
**GitHub Repo:** https://github.com/simonplmak-cloud/venus-lean

---

## Project Structure

```
legendv_me/
├── index.html          # Main website (all content + styles + scripts)
├── images/             # Profile and event photos
│   ├── Venus Lean.jpg
│   ├── WhatsApp Image 2026-02-24 at 20.18.17.jpeg
│   └── WhatsApp Image 2026-02-25 at 01.36.58.jpeg
├── CNAME              # Custom domain config (legendv.me)
└── .git/
```

---

## Build / Deployment Commands

### Deploy to GitHub Pages

The site uses the `gh-pages` branch for GitHub Pages deployment.

```bash
# Make changes to index.html on main branch
git add .
git commit -m "Description of changes"
git push origin main

# Update gh-pages branch
git checkout gh-pages
git merge main
git push origin gh-pages
git checkout main
```

### Local Development

```bash
# Serve locally
cd /mnt/c/git_repo/legendv_me
python3 -m http.server 8000
# Then open http://localhost:8000
```

### Validate HTML

```bash
# Check HTML syntax
python3 -c "
from html.parser import HTMLParser
with open('index.html', 'r') as f:
    content = f.read()
parser = HTMLParser()
try:
    parser.feed(content)
    print('HTML OK')
except Exception as e:
    print(f'Error: {e}')
"
```

---

## Code Style Guidelines

### General Principles

- Keep it simple - this is a static single-page website
- No external frameworks required
- Maintain responsive design for mobile/tablet/desktop

### HTML Conventions

1. **Doctype & Language**: Use `<!DOCTYPE html>` with `lang="zh-Hant"` for Traditional Chinese
2. **Semantic HTML**: Use `<section>`, `<nav>`, `<header>`, `<footer>`, `<article>`
3. **Accessibility**: 
   - Include `alt` text for all images
   - Use proper heading hierarchy (h1 → h2 → h3)
   - Ensure color contrast meets WCAG standards

### CSS Guidelines

1. **Organization**: All CSS in `<style>` tag in `<head>` (single-file approach)
2. **CSS Variables**: Use CSS custom properties for colors
   ```css
   :root {
       --purple-deep: #4a1259;
       --purple-main: #6b2c7a;
       --pink-accent: #ff6b9d;
   }
   ```
3. **Responsive Design**: Use media queries for breakpoints
   - Mobile: < 640px
   - Tablet: 640px - 1024px  
   - Desktop: > 1024px
4. **Units**: Use `rem` for fonts, `px` for borders/shadows, `%` for widths
5. **Animations**: Keep animations subtle (< 0.5s) and purposeful

### JavaScript Guidelines

1. **Placement**: All JS in `<script>` tag before `</body>`
2. **Vanilla JS**: No jQuery or frameworks
3. **Features used**:
   - `IntersectionObserver` for scroll animations
   - Smooth scroll for navigation
   - Mobile menu toggle

### Image Guidelines

1. **Formats**: JPEG for photos, SVG for icons (if added)
2. **Alt Text**: Always include descriptive alt text
3. **Paths**: Use relative paths from index.html (`images/filename.jpg`)

### Naming Conventions

- **Files**: Use descriptive names with spaces preserved (e.g., `Venus Lean.jpg`)
- **CSS Classes**: Use kebab-case (e.g., `.hero-section`, `.nav-links`)
- **IDs**: Use camelCase for JavaScript hooks (e.g., `id="contact"`)

### Content Standards

1. **Bilingual**: Include both Chinese (Traditional) and English text
2. **Professional tone**: Maintain business-professional language
3. **Contact info**: Keep email and LinkedIn current

---

## Testing Checklist

Before deploying, verify:

- [ ] HTML validates without errors
- [ ] All images load correctly
- [ ] Navigation links work (scroll to sections)
- [ ] Mobile menu functions properly
- [ ] Responsive layout works at all breakpoints
- [ ] Contact email and LinkedIn links work
- [ ] Page loads without console errors

---

## Common Tasks

### Adding a New Section

1. Add section HTML after other sections
2. Add corresponding CSS styles
3. Add navigation link in `<nav>`

### Updating Profile Information

Edit the relevant text in `index.html`:
- Hero section: name, title, tagline
- About section: bio in Chinese and English
- Experience: timeline entries
- Contact: email, social links

### Changing Colors

Update CSS variables in the `:root` section:
```css
:root {
    --purple-deep: #4a1259;
    --purple-main: #6b2c7a;
    --pink-accent: #ff6b9d;
    /* etc */
}
```

---

## Deployment Notes

- GitHub Pages serves from `gh-pages` branch
- Custom domain `legendv.me` configured via CNAME file
- HTTPS auto-provisions after DNS propagation (up to 24 hours)
- A record points to `185.199.108.153` (GitHub Pages IP)
- CNAME for `www` points to `simonplmak-cloud.github.io`
