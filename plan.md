# plan.md

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Goals & Requirements](#goals--requirements)
3. [Technology Stack](#technology-stack)
4. [Design & Layout Strategy](#design--layout-strategy)
5. [Directory Structure](#directory-structure)
6. [Assets Preparation](#assets-preparation)
7. [Step-by-Step Implementation Plan](#step-by-step-implementation-plan)
   - [1. Initialize Project & Set Up Build Tools](#1-initialize-project--set-up-build-tools)
   - [2. Create Base HTML Template](#2-create-base-html-template)
   - [3. Build the Navigation Bar](#3-build-the-navigation-bar)
   - [4. Hero/“Above the Fold” Section](#4-herofabove-the-fold-section)
   - [5. “Features” Section](#5-features-section)
   - [6. “Why Choose Us”/Strengths Section](#6-why-choose-usstrengths-section)
   - [7. “Review/Testimonials” Section (Optional)](#7-reviewtestimonial-section-optional)
   - [8. “FAQ” Section (Optional)](#8-faq-section-optional)
   - [9. Final CTA & Footer](#9-final-cta--footer)
   - [10. Responsiveness & Mobile Optimization](#10-responsiveness--mobile-optimization)
   - [11. Page Load Speed & Performance Best Practices](#11-page-load-speed--performance-best-practices)
   - [12. Accessibility & SEO Considerations](#12-accessibility--seo-considerations)
   - [13. Deployment & Hosting Checklist](#13-deployment--hosting-checklist)
8. [References & Inspirations](#references--inspirations)

---

## Project Overview

**OCR-SEC: Structuring Chaos**  
This graduation‐project website (“OCR‐SEC”) will introduce the OCR-SEC system—a pipeline that takes scanned financial documents and, using OCR + LLMs, transforms them into clean, validated, exportable tables. The website must reflect:

- **Product Description**: What OCR-SEC is, why it exists, and how it works.
- **Technical Depth**: Enough detail that a fellow computer‐engineer can appreciate the main challenges, pipeline stages, and contributions (but no need to dump entire thesis).
- **Visual Appeal**: Modern, minimalistic design that flows, uses whitespace, dynamic scrolling, animations, etc.
- **Responsiveness & Performance**: Must look/feel great on mobile, tablet, desktop; load quickly.

The project poster (OCR‐SEC poster image) provides the core content. We will integrate its sections into a “High Converting App Landing Page” layout (as per the design mockup) and add a few extra modern Web design touches (scroll animations, subtle cursor effects, minimal color palette).

---

## Goals & Requirements

1. **Self‐Explanatory**

   - Must “stand on its own” without requiring the user to read the poster PDF.
   - Use a mix of concise text + visuals (poster snapshots, icons, gifs, short embedded videos).

2. **Concise Yet Technically Informative**

   - Each pipeline stage (Capture → Digitization → LLM Post‐processing → Human‐in‐the‐Loop → Export → Chatbot) appears as a distinct “feature” block.
   - Under “Features,” include:
     - Short descriptive heading (e.g. “Capture Clean Centralize”)
     - One‐sentence summary + 2–3 bullet points of critical technical details (e.g. preprocessing steps, custom OCR model, LLM prompt templates).

3. **Modern Design & UX**

   - Follow current “High Converting Landing Page” layout guidelines: hero + credibility logos + feature spotlight + strengths + reviews + FAQ + final CTA.
   - Aesthetic principles:
     - **Minimalism**: Plenty of whitespace; large, bold headings.
     - **Typography**: Sans‐serif (e.g. Poppins, Inter).
     - **Color Palette**: 2–3 main colors drawn from the poster’s palette (e.g. dark navy background + gold accents + white text).
     - **Dynamic Scrolling**: “Scroll reveal” animations so sections fade/slide into view.
     - **Playful Cursors**: Slight hover effects on links/buttons.
     - **Responsiveness**: Breakpoints at `320px`, `640px`, `1024px`.

4. **Technical Content**

   - Under “Why Choose Us,” highlight 3–4 project strengths (e.g. “Tailored Extraction Models,” “LLM‐Driven Post‐Processing,” “Human‐Validated Accuracy,” “Interactive Chat Interface”).
   - Provide links (anchor tags) to download a one‐pager PDF or view the poster in full resolution if desired.

5. **No Dead Links / Proper Grammar**

   - Proofread all copy.
   - Ensure no broken images or JS errors.

6. **Contemporary Web Technologies**
   - Use a modern front‐end framework or library (e.g. React or Vue) OR a well‐structured vanilla HTML/CSS/JavaScript setup.
   - Use CSS flexbox/grid for layout.
   - Use a minimal CSS library or utility framework (e.g. Tailwind CSS or custom SCSS).
   - Optional: incorporate a lightweight animation library (e.g. AOS.js for scroll animations).

---

## Technology Stack

Below is a recommended stack—feel free to adjust, but **justify** any deviations to fit performance/responsiveness goals:

1. **HTML / SCSS / JavaScript** (Vanilla) **OR** **React + Tailwind CSS**

   - We will outline steps for a **React + Tailwind CSS** setup (recommended for rapid styling & responsiveness).
   - If you prefer vanilla, strip out React steps and use a build system (e.g. Parcel or Vite) with SCSS.

2. **Tailwind CSS**

   - Utility‐first, minimal custom CSS, very fast to prototype.
   - Responsive classes baked in.

3. **Animation Library: AOS (Animate on Scroll)**

   - Small footprint, easy to configure fade/slide effects.

4. **Font Handling**

   - Google Fonts: e.g. `Inter` for body, `Poppins` for headings.
   - Load via `<link>` in `<head>` (preconnect & preload).

5. **Build & Bundler**

   - **Vite** (if React) or **Parcel** (if vanilla).
   - Configure for hot‐reload during development.

6. **Responsive Meta Tags**

   - `<meta name="viewport" content="width=device-width, initial-scale=1" />`

7. **Optional: Favicon & Touch Icons**

   - Export a small cube or magnifying‐glass icon from the poster as favicon.

8. **Optional: Embeds**
   - If embedding a YouTube demo video, use `<iframe>` with `loading="lazy"`.

---

## Design & Layout Strategy

We will follow the “High Converting App Landing Page” wireframe, section by section, mapping each wireframe block to OCR‐SEC poster content:

1. **Nav Bar**

   - Left: OCR‐SEC logo/magnifying glass icon (extracted from poster).
   - Right: Anchor links—“Home,” “Features,” “Why OCR‐SEC,” “Docs,” “Contact.”
   - Rightmost Button (CTA): “Try Demo” or “Request Access” (solid dark‐gold background, white text).

2. **Hero Section (Hook Visitors Instantly)**

   - **Heading**: “Structuring Chaos: LLM‐Powered Table Extraction”
   - **Subheading** (one sentence summary): “Transform scanned financial statements into clean, validated, exportable tables—powered by custom OCR and LLM agents.”
   - **CTA Buttons**:
     - Primary: “Download Whitepaper” (links to PDF of full poster).
     - Secondary: “Watch Demo” (scrolls to embedded YouTube).
   - **Stats** (optional): “200+ Datasets Processed” or “99.5% Extraction Accuracy”
   - **Hero Visual**: On the right, a tall phone/monitor mockup showing a screenshot of OCR‐SEC interface (or poster section).

3. **Credibility Logos Section (Add Instant Credibility)**

   - If the project was sponsored by Duke University & Savronik, show their logos horizontally.
   - Additional: “Supported by METU WINS Lab” if desired.

4. **Features Section (Highlight What Sets the App Apart)**

   - **Highlighted Feature 1 (Full‐width)**:
     - **Heading**: “Capture • Clean • Centralize”
     - **Text** (2–3 lines): “Import multi‐page scanned documents via upload or URL. Apply flexible preprocessing (deskew, denoise, adaptive thresholding), and centralize everything for streamlined access.”
     - **Visual Placeholder**: A stylized document icon or screenshot from poster.
   - **Highlighted Feature 2 (Left, Half‐width)**:
     - **Heading**: “Document Digitization”
     - **Text** (1–2 lines): “Our tailored OCR models transform complex financial layouts into structured raw tables—minimizing errors from line breaks and merged cells.”
     - **Visual Placeholder**: OCR‐SEC poster snippet showing “Document Digitization” block.
   - **Highlighted Feature 3 (Right, Half‐width)**:
     - **Heading**: “Refined Accuracy (LLM Post‐Processing)”
     - **Text** (1–2 lines): “Leverage LLM agents to clean, validate, and format extracted data—each module tuned to specific document types for maximum precision.”
     - **Visual Placeholder**: Poster snippet of “Refined Accuracy” or “Human‐in‐the‐Loop.”

5. **Why Choose Us Section (Make Your Strengths Obvious)**

   - Four columns (icons + title + one sentence):
     1. **“Custom OCR Models”**
        - _Icon_: Microchip or OCR icon.
        - _Text_: “Extraction models trained on financial statements—no one‐size‐fits‐all.”
     2. **“LLM‐Driven Validation”**
        - _Icon_: Brain‐chip hybrid.
        - _Text_: “Post‐OCR cleaning & formatting powered by GPT‐style agents—accuracy meets automation.”
     3. **“Human‐in‐Loop Review”**
        - _Icon_: Person with checkmark.
        - _Text_: “Review & correct digitized tables side by side with the original scans—ensuring total reliability.”
     4. **“Exportable Data & Chatbot”**
        - _Icon_: CSV/file + chatbot icon.
        - _Text_: “Download clean CSVs or query your tables in plain English—no technical skills needed.”

6. **Review/Testimonials Section (Optional)**

   - If you have pilot users (e.g. “Atakan Öztarak – Co‐PI, WINS Lab”), include 2–3 brief quotes about the system’s accuracy & ease of use.
   - Each card: 5‐star rating + 2–3 line testimonial + user name/affiliation.

7. **FAQ Section (Optional but Recommended)**

   - Four collapsible items (common questions):
     1. “What document types does OCR‐SEC support?”
     2. “How do I train OCR‐SEC on a new format?”
     3. “What accuracy can I expect?”
     4. “How do I integrate the chatbot with my CRM?”
   - Use simple `<details><summary>Question</summary>Answer</details>` or a JS toggle.

8. **Final CTA Section (Wrap with a Confident CTA)**

   - **Heading**: “Ready to Structure Your Chaos?”
   - **Subtext**: “Get started with OCR‐SEC today—download the whitepaper or schedule a live demo.”
   - **Buttons**:
     - “Download Poster” (whitepaper)
     - “Request Demo” (link to a contact form or mailto)
   - **Visual**: Small mockup or looping GIF of scrolling through extracted table.

9. **Footer**
   - **Left**: “© 2025 WINS Lab, METU. All Rights Reserved.”
   - **Center** (or below):
     - “Supervisor: Prof. Fatoş Tunay Yarman Vural”
     - “Sponsors: Duke University & Savronik”
     - “Team: Atakan Öztarak, Aybüke Aksoy, Barış Türnüklü, Cem Meriç Şefikoğulları, Emre Kalkan”
   - **Right**: Social icons (LinkedIn, GitHub, maybe YouTube) linking to project repos/bio.
   - **Bottom‐right corner**: QR code linking to full poster PDF or GitHub repo.

---

## Directory Structure

Below is a recommended directory structure for a React + Tailwind project (Vite). If you choose vanilla, adapt accordingly (e.g. `/src/styles.scss`, `/src/index.html`, `/src/main.js`).

ocr-sec-website/
│
├── public/
│ ├── favicon.ico
│ ├── poster-full.png ← Full‐resolution poster image
│ ├── screenshot-hero.png ← Hero mockup screenshot from poster
│ └── qr-code.png ← QR code linking to PDF/GitHub
│
├── src/
│ ├── assets/
│ │ ├── logo.svg ← OCR‐SEC logo / magnifying glass icon
│ │ ├── duke-logo.svg ← Sponsor logos (Duke, Savronik, METU)
│ │ ├── savronik-logo.svg
│ │ ├── metu-logo.svg
│ │ ├── icons/
│ │ │ ├── ocr-icon.svg
│ │ │ ├── llm-icon.svg
│ │ │ ├── human-icon.svg
│ │ │ └── csv-icon.svg
│ │ └── team/
│ │ ├── atakan.jpg
│ │ ├── aybuke.jpg
│ │ ├── baris.jpg
│ │ ├── cem.jpg
│ │ └── emre.jpg
│ │
│ ├── components/
│ │ ├── Navbar.jsx
│ │ ├── Hero.jsx
│ │ ├── CredibilityLogos.jsx
│ │ ├── FeatureFullWidth.jsx
│ │ ├── FeatureHalfWidth.jsx
│ │ ├── StrengthCard.jsx
│ │ ├── TestimonialCard.jsx
│ │ ├── FAQItem.jsx
│ │ ├── CTASection.jsx
│ │ ├── Footer.jsx
│ │ └── … (other reusable UI bits)
│ │
│ ├── pages/
│ │ └── Home.jsx
│ │
│ ├── App.jsx
│ ├── main.jsx
│ └── index.css
│
├── tailwind.config.cjs
├── postcss.config.cjs
├── package.json
├── vite.config.js
└── README.md

> **Notes on Directory**
>
> - All `.svg`/`.png` assets live under `/src/assets`.
> - Each section of the page is its own React component for maintainability.
> - Use `index.css` to import Tailwind’s base, components, and utilities.

---

## Assets Preparation

1. **Extract Poster Snippets**

   - From `Structuring Chaos: LLM‐Powered Table Extraction` poster:
     - **“Capture Clean Centralize”** block → `assets/poster-capture-snippet.png` (crop just that region).
     - **“Document Digitization”** block → `assets/poster-digitization-snippet.png`.
     - **“Refined Accuracy”** & **“Human-in-the-Loop”** blocks → `assets/poster-accuracy-snippet.png`.
     - **“Exportable Financial Data”** & **“Talk to Your Data”** blocks → `assets/poster-export-snippet.png`.
   - Save each snippet at **optimized web resolution** (e.g. ≤200 KB each, `png` or `jpg` if no transparency needed).

2. **Create or Download Icons**

   - OCR icon (magnifying glass) → `assets/icons/ocr-icon.svg`.
   - LLM/brain icon → `assets/icons/llm-icon.svg`.
   - Human‐in‐Loop icon → `assets/icons/human-icon.svg`.
   - CSV export icon → `assets/icons/csv-icon.svg`.
   - Chatbot icon → `assets/icons/chatbot-icon.svg`.
   - Use an open‐source icon library (e.g. [Heroicons](https://heroicons.com/) or [FontAwesome](https://fontawesome.com/)). Download only needed SVGs.

3. **Typography Setup**

   - Add to `<head>` of `index.html`:
     ```html
     <link rel="preconnect" href="https://fonts.googleapis.com" />
     <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
     <link
       href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Poppins:wght@600;700&display=swap"
       rel="stylesheet"
     />
     ```

4. **Sponsor & Team Photos (Optional)**

   - If you want to display team member headshots, place them under `/src/assets/team/`.
   - Otherwise, skip photo usage and simply list names in the footer.

5. **Favicon & Touch Icon**
   - Create a 32×32 pixel “magnifying glass + LLM brain” icon → `public/favicon.ico` (use an online `.ico` converter).
   - Optionally add `public/apple-touch-icon.png` (180×180 px).

---

## Step-by-Step Implementation Plan

Below is a detailed breakdown of **how** to build the website from scratch. Each major step includes sub‐steps & notes.

---

