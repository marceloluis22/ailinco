# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-page website for **Ailinco**, a water delivery company in San Martín de los Andes, Neuquén, Argentina. The entire site lives in a single file: [index.html](index.html).

## Running the Site

No build step. Open `index.html` directly in a browser, or use any static file server:

```
npx serve .
# or
python -m http.server 8080
```

## Architecture

Everything — CSS, HTML, and JavaScript — is inlined in `index.html`. Structure:

- **`<style>`** block (lines 17–1030): all CSS, organized by component with section comments
- **HTML body** (lines 1032–1695): semantic sections in order: `#inicio` (Hero) → `#quienes-somos` (About) → `#productos` (Products) → `#promociones` (Promo Slider) → `#reparto` (Services) → `#contacto` (Contact) → Footer
- **`<script>`** block (lines 1697–1826): vanilla JS for bubbles, ripple effect, hamburger menu, sticky header, product tab filtering, promotions slider, contact form → WhatsApp redirect, scroll reveal

## Key Design Decisions

**WhatsApp as the primary CTA**: The contact form does not send email — on submit it constructs a pre-filled WhatsApp message and opens `wa.me/5492944952161`. All product "Consultar Precio" buttons link directly to WhatsApp with pre-composed text.

**No backend**: Fully static. No API calls, no form submissions to a server.

**CSS variables** (`:root` at line 21): Colors (`--red`, `--blue`, `--sky-*`) and shared values are defined here — change palette from this single location.

**Promotions slider** (`#slider-track`): Hardcoded to 3 slides (`total = 3` at line 1771). When adding/removing slides, update `total` and the `.dot` elements in `#slider-dots`.

**Product tab filtering** (`data-cat` attribute): Each `.product-card` has a `data-cat` attribute (`agua`, `hielo`, `soda`, `dispenser`, `gaseosa`). The JS filters by matching `card.dataset.cat` against the active tab's `data-filter`.

## Pending Image Replacements

The code has inline comments marked `⬇️ REEMPLAZAR` for placeholder elements that should be replaced with real images:

- Logo: `.logo-img-placeholder` → `<img src="logo.png">`
- Hero visual: `.hero-emoji` → `<img src="bidon.png">`
- About section: `.about-img-placeholder` → `<img src="empresa.jpg">`
- Product cards with emoji placeholders → product photos

## External Dependencies (CDN)

- Google Fonts: Pacifico + Poppins
- Font Awesome 6.5.0 (icons)

No npm packages. No local dependencies to install.

## Contact Info in the Code

- WhatsApp: `5492944952161`
- Phone: `(2972) 414-034` / `0294 154-952161`
- Email: `ailincosma@hotmail.com`
