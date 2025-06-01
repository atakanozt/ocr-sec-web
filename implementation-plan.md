## Step-by-Step Implementation Plan

Below is a detailed breakdown of **how** to build the website from scratch. Each major step includes sub‐steps & notes.

---

2. Create Base HTML Template
   In React, our entire “page” is built inside App.jsx and child components. The focus here is to create a skeleton layout, then fill each section in order.

Create src/App.jsx

jsx
Copy
Edit
import React, { useEffect } from 'react';
import AOS from 'aos';
import 'aos/dist/aos.css';

import Navbar from './components/Navbar';
import Hero from './components/Hero';
import CredibilityLogos from './components/CredibilityLogos';
import FeatureFullWidth from './components/FeatureFullWidth';
import FeatureHalfWidth from './components/FeatureHalfWidth';
import WhyChooseUs from './components/WhyChooseUs';
import TestimonialSection from './components/TestimonialSection';
import FAQSection from './components/FAQSection';
import CTASection from './components/CTASection';
import Footer from './components/Footer';

function App() {
useEffect(() => {
AOS.init({ duration: 800, once: true });
}, []);

return (
<div className="flex flex-col min-h-screen bg-light-gray text-primary-navy">
<Navbar />

      <main className="flex-grow">
        <Hero />
        <CredibilityLogos />
        <section id="features" className="py-20 px-4 md:px-8 lg:px-16">
          <FeatureFullWidth />
          <div className="mt-16 grid grid-cols-1 lg:grid-cols-2 gap-12">
            <FeatureHalfWidth
              title="Document Digitization"
              text="Transform scanned financial statements into raw tables using custom OCR models, minimizing line breaks & merged-cell errors."
              imgSrc="/src/assets/poster-digitization-snippet.png"
            />
            <FeatureHalfWidth
              title="Refined Accuracy (LLM Post-Processing)"
              text="Use LLM agents to clean, validate & format extracted data—each tailored for specific document types."
              imgSrc="/src/assets/poster-accuracy-snippet.png"
            />
          </div>
        </section>
        <section id="why-choose-us" className="bg-white py-20 px-4 md:px-8 lg:px-16">
          <WhyChooseUs />
        </section>
        {/* Optional: Testimonials */}
        <section id="testimonials" className="py-20 px-4 md:px-8 lg:px-16">
          <TestimonialSection />
        </section>
        {/* Optional: FAQ */}
        <section id="faq" className="bg-white py-20 px-4 md:px-8 lg:px-16">
          <FAQSection />
        </section>
        <section id="cta" className="py-20 px-4 md:px-8 lg:px-16">
          <CTASection />
        </section>
      </main>

      <Footer />
    </div>

);
}

export default App;
Global Styles

index.css already includes Tailwind base/utility.

This sets bg-light-gray (from tailwind.config) as page background, and text-primary-navy for default text.

3. Build the Navigation Bar
   File: src/components/Navbar.jsx

jsx
Copy
Edit
import React, { useState } from 'react';
import { Transition } from '@headlessui/react'; // optional for mobile menu transitions
import logo from '../assets/logo.svg'; // OCR-SEC logo

export default function Navbar() {
const [isOpen, setIsOpen] = useState(false);

return (
<nav className="bg-white shadow-sm fixed w-full z-50">
<div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
<div className="flex justify-between h-16">
{/_ Logo / Brand _/}
<div className="flex-shrink-0 flex items-center">
<a href="#home">
<img className="h-8 w-auto" src={logo} alt="OCR-SEC Logo" />
</a>
</div>
{/_ Desktop Menu _/}
<div className="hidden md:flex md:items-center md:space-x-8">
<a href="#home" className="text-base font-medium hover:text-accent-gold">
Home
</a>
<a href="#features" className="text-base font-medium hover:text-accent-gold">
Features
</a>
<a href="#why-choose-us" className="text-base font-medium hover:text-accent-gold">
Why OCR-SEC
</a>
<a href="#docs" className="text-base font-medium hover:text-accent-gold">
Docs
</a>
<a href="#contact" className="text-base font-medium hover:text-accent-gold">
Contact
</a>
</div>
{/_ CTA Button _/}
<div className="hidden md:flex md:items-center">
<a
              href="#cta"
              className="btn-primary"
            >
Request Demo
</a>
</div>
{/_ Mobile menu button _/}
<div className="-mr-2 flex items-center md:hidden">
<button
onClick={() => setIsOpen(!isOpen)}
type="button"
className="inline-flex items-center justify-center p-2 rounded-md text-primary-navy hover:text-white hover:bg-accent-gold focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-light-gray focus:ring-white"
aria-controls="mobile-menu"
aria-expanded={isOpen} >
<span className="sr-only">Open main menu</span>
{!isOpen ? (
<svg
                  className="block h-6 w-6"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                  aria-hidden="true"
                >
<path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M4 8h16M4 16h16" />
</svg>
) : (
<svg
                  className="block h-6 w-6"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                  aria-hidden="true"
                >
<path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M6 18L18 6M6 6l12 12" />
</svg>
)}
</button>
</div>
</div>
</div>

      {/* Mobile Menu */}
      <Transition show={isOpen}>
        <Transition.Child
          enter="transition ease-out duration-200 transform"
          enterFrom="opacity-0 -translate-y-2"
          enterTo="opacity-100 translate-y-0"
          leave="transition ease-in duration-150 transform"
          leaveFrom="opacity-100 translate-y-0"
          leaveTo="opacity-0 -translate-y-2"
        >
          <div className="md:hidden" id="mobile-menu">
            <div className="px-2 pt-2 pb-3 space-y-1 sm:px-3">
              <a
                href="#home"
                className="block px-3 py-2 rounded-md text-base font-medium text-primary-navy hover:bg-light-gray"
              >
                Home
              </a>
              <a
                href="#features"
                className="block px-3 py-2 rounded-md text-base font-medium text-primary-navy hover:bg-light-gray"
              >
                Features
              </a>
              <a
                href="#why-choose-us"
                className="block px-3 py-2 rounded-md text-base font-medium text-primary-navy hover:bg-light-gray"
              >
                Why OCR-SEC
              </a>
              <a
                href="#docs"
                className="block px-3 py-2 rounded-md text-base font-medium text-primary-navy hover:bg-light-gray"
              >
                Docs
              </a>
              <a
                href="#contact"
                className="block px-3 py-2 rounded-md text-base font-medium text-primary-navy hover:bg-light-gray"
              >
                Contact
              </a>
              <a
                href="#cta"
                className="block mt-2 px-3 py-2 rounded-md text-base font-heading bg-accent-gold text-white text-center hover:bg-opacity-90"
              >
                Request Demo
              </a>
            </div>
          </div>
        </Transition.Child>
      </Transition>
    </nav>

);
}
Key Points

Fixed position: fixed nav (with z-50) so it stays on top.

Responsive: hidden links on mobile, hamburger menu toggles.

CTA button uses custom Tailwind classes (.btn-primary).

Navigation links use anchor tags pointing to ID‐wrapped sections.

4. Hero/“Above the Fold” Section
   File: src/components/Hero.jsx

jsx
Copy
Edit
import React from 'react';
import heroImage from '../assets/screenshot-hero.png'; // extracted screenshot
import posterSnippet from '../assets/poster-capture-snippet.png';

export default function Hero() {
return (
<section
      id="home"
      className="relative bg-primary-navy pt-24 pb-16 px-4 md:px-8 lg:px-16 text-white"
    >
<div className="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
{/_ Left Column: Textual Content _/}
<div className="space-y-6" data-aos="fade-right">
<p className="inline-block bg-accent-gold text-primary-navy text-sm font-heading uppercase tracking-wide rounded-full px-3 py-1">
Achievement: Top‐Rated App of 2025
</p>

          <h1 className="text-4xl md:text-5xl lg:text-6xl font-heading font-bold leading-tight">
            Structuring Chaos: <br />
            LLM‐Powered Table Extraction
          </h1>

          <p className="text-lg md:text-xl">
            Transform scanned financial documents into clean, validated, exportable tables—powered by custom OCR & LLM agents.
          </p>

          {/* CTA Buttons */}
          <div className="flex flex-wrap items-center space-x-4">
            <a
              href="/poster-full.png"
              target="_blank"
              rel="noopener noreferrer"
              className="btn-primary"
            >
              Download Poster
            </a>
            <a
              href="#features"
              className="btn-secondary"
            >
              Explore Features
            </a>
          </div>

          {/* Statistic */}
          <div className="flex items-center space-x-2 text-sm font-medium">
            <span>200+ Datasets Processed</span>
            <svg className="h-4 w-4 text-accent-gold" fill="currentColor" viewBox="0 0 20 20">
              <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.537 4.72h4.965c.969 0 1.372 1.24.588 1.81l-4.016 2.917 1.537 4.72c.3.921-.755 1.688-1.54 1.117L10 13.347l-4.08 2.864c-.784.571-1.838-.196-1.539-1.117l1.536-4.72-4.015-2.917c-.784-.57-.38-1.81.588-1.81h4.965l1.538-4.72z" />
            </svg>
            <span>≈99.5% Accuracy</span>
          </div>
        </div>

        {/* Right Column: Visual */}
        <div
          className="relative flex justify-center"
          data-aos="fade-left"
        >
          <div className="w-full max-w-md">
            <img
              src={heroImage}
              alt="OCR-SEC Interface Screenshot"
              className="rounded-xl shadow-lg"
              loading="lazy"
            />
          </div>
        </div>
      </div>
    </section>

);
}
Key Points

Dark navy (bg-primary-navy) background with white text.

On large screens, 2‐column grid: text on left, image on right.

Short “achievement” badge (e.g., “Top‐Rated App of 2025”) above heading—optional but matches design wireframe.

Bold heading + descriptive subtext + dual CTA.

Small “statistic” line under CTAs to add credibility.

data-aos attributes for scroll reveals.

5. “Credibility Logos” Section
   File: src/components/CredibilityLogos.jsx

jsx
Copy
Edit
import React from 'react';
import dukeLogo from '../assets/duke-logo.svg';
import savronikLogo from '../assets/savronik-logo.svg';
import metuLogo from '../assets/metro-logo.svg'; // METU logo (create or fetch)

export default function CredibilityLogos() {
return (
<section className="bg-white py-8 px-4 md:px-8 lg:px-16">
<div className="max-w-7xl mx-auto flex flex-wrap justify-center items-center space-x-10">
<p className="text-sm text-gray-600 font-medium mr-8">
Sponsored by:
</p>
<img src={dukeLogo} alt="Duke University" className="h-8 w-auto grayscale opacity-80 hover:opacity-100 transition" />
<img src={savronikLogo} alt="Savronik" className="h-8 w-auto grayscale opacity-80 hover:opacity-100 transition" />
<img src={metuLogo} alt="METU WINS Lab" className="h-8 w-auto grayscale opacity-80 hover:opacity-100 transition" />
</div>
</section>
);
}
Notes

Logos in grayscale by default; hover restores full color (opacity-80 → opacity-100).

Small caption “Sponsored by” to add context.

Entire section has a white background (bg-white) and slight vertical padding.

6. “Features” Section
   6.1. FeatureFullWidth Component
   File: src/components/FeatureFullWidth.jsx

jsx
Copy
Edit
import React from 'react';
import captureImage from '../assets/poster-capture-snippet.png';

export default function FeatureFullWidth() {
return (
<div className="w-full flex flex-col lg:flex-row items-center lg:space-x-12" data-aos="fade-up">
{/_ Text Column _/}
<div className="lg:w-1/2 space-y-4">
<h2 className="text-3xl md:text-4xl font-heading font-bold">
Capture • Clean • Centralize
</h2>
<p className="text-lg">
Import documents via upload or URL, apply flexible preprocessing (deskew, denoise, adaptive thresholding), and keep everything centralized for streamlined access.
</p>
<ul className="list-disc list-inside text-base text-gray-700 space-y-2">
<li>Supports multi-page PDF & image imports (JPEG, PNG, TIFF).</li>
<li>Automated preprocessing: deskew, contrast enhancement, noise reduction.</li>
<li>Centralized storage with tagging & metadata for easy retrieval.</li>
</ul>
</div>
{/_ Image Column _/}
<div className="lg:w-1/2 mt-8 lg:mt-0 flex justify-center">
<img
          src={captureImage}
          alt="Capture • Clean • Centralize"
          className="rounded-lg shadow-xl w-full max-w-sm"
          loading="lazy"
        />
</div>
</div>
);
}
Key Points

Full‐width section with two columns on large screens; single column on mobile.

Bold heading, paragraph, bullet list to deliver both overview + a few critical technical points.

Image snippet from the poster on the right for visual support.

6.2. FeatureHalfWidth Component
File: src/components/FeatureHalfWidth.jsx

jsx
Copy
Edit
import React from 'react';

export default function FeatureHalfWidth({ title, text, imgSrc }) {
return (
<div className="flex flex-col lg:flex-row items-center lg:items-start space-y-4 lg:space-y-0 lg:space-x-8" data-aos="fade-up">
<div className="lg:w-1/2 space-y-3">
<h3 className="text-2xl font-heading font-semibold">{title}</h3>
<p className="text-base text-gray-700">{text}</p>
</div>
<div className="lg:w-1/2 flex justify-center">
<img
          src={imgSrc}
          alt={title}
          className="rounded-lg shadow-lg w-full max-w-xs"
          loading="lazy"
        />
</div>
</div>
);
}
Use Cases

Called twice within the Features section (Document Digitization & Refined Accuracy).

On mobile, stack vertically; on desktop, side by side.

7. “Why Choose Us”/Strengths Section
   File: src/components/WhyChooseUs.jsx

jsx
Copy
Edit
import React from 'react';
import ocrIcon from '../assets/icons/ocr-icon.svg';
import llmIcon from '../assets/icons/llm-icon.svg';
import humanIcon from '../assets/icons/human-icon.svg';
import csvIcon from '../assets/icons/csv-icon.svg';

const strengths = [
{
icon: ocrIcon,
title: 'Custom OCR Models',
description: 'Extraction models trained on financial statements—no one-size-fits-all.',
},
{
icon: llmIcon,
title: 'LLM-Driven Validation',
description: 'Post-OCR cleaning & formatting powered by GPT‐style agents—accuracy meets automation.',
},
{
icon: humanIcon,
title: 'Human-in-Loop Review',
description: 'Review & correct digitized tables side by side with the original scans—ensuring total reliability.',
},
{
icon: csvIcon,
title: 'Exportable Data & Chatbot',
description: 'Download clean CSVs or query your tables in plain English—no technical skills needed.',
},
];

export default function WhyChooseUs() {
return (
<div className="max-w-7xl mx-auto">
<div className="text-center mb-12" data-aos="fade-down">
<h2 className="text-3xl md:text-4xl font-heading font-bold">
Why OCR‐SEC?
</h2>
<p className="mt-2 text-base text-gray-600">
Discover the unique strengths that set our pipeline apart.
</p>
</div>
<div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
{strengths.map((item, idx) => (
<div
key={idx}
className="bg-white p-6 rounded-lg shadow-md hover:shadow-lg transition"
data-aos="zoom-in"
data-aos-delay={idx \* 100} >
<img src={item.icon} alt={item.title} className="h-12 w-12 mb-4" />
<h3 className="text-xl font-heading font-semibold mb-2">
{item.title}
</h3>
<p className="text-sm text-gray-700">{item.description}</p>
</div>
))}
</div>
</div>
);
}
Key Points

Four cards in a responsive grid.

Each card has an icon, heading, paragraph.

Hover elevation effect to add subtle interactivity.

data-aos with staggered data-aos-delay for sequential reveal.

8. Review/Testimonials Section (Optional)
   If you have actual user feedback, include it; if not, you can skip or place placeholder text.

File: src/components/TestimonialSection.jsx

jsx
Copy
Edit
import React from 'react';
import TestimonialCard from './TestimonialCard';

const testimonials = [
{
quote: "OCR-SEC transformed our PDF-based accounting reports into ready-to-analyze CSVs in minutes—accuracy is off the charts.",
name: "Dr. Jane Doe",
affiliation: "Duke University, Research Fellow",
avatar: "/src/assets/team/jane.jpg", // or placeholder
rating: 5,
},
{
quote: "The LLM post-processing module cut our manual review time by 80%. Highly recommend!",
name: "John Smith",
affiliation: "Savronik Finance Team",
avatar: "/src/assets/team/john.jpg",
rating: 5,
},
// Add more if available
];

export default function TestimonialSection() {
return (
<div className="max-w-7xl mx-auto">
<div className="text-center mb-12" data-aos="fade-down">
<h2 className="text-3xl md:text-4xl font-heading font-bold">
What Our Users Say
</h2>
</div>
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
{testimonials.map((t, idx) => (
<TestimonialCard key={idx} testimonial={t} aosDelay={idx \* 100} />
))}
</div>
</div>
);
}
TestimonialCard Component

jsx
Copy
Edit
// src/components/TestimonialCard.jsx

import React from 'react';

export default function TestimonialCard({ testimonial, aosDelay }) {
const { quote, name, affiliation, avatar, rating } = testimonial;

return (
<div
      className="bg-white p-6 rounded-lg shadow-md hover:shadow-lg transition"
      data-aos="fade-up"
      data-aos-delay={aosDelay}
    >
{/_ Stars _/}
<div className="flex items-center mb-4">
{[...Array(rating)].map((\_, i) => (
<svg
            key={i}
            className="h-5 w-5 text-accent-gold"
            fill="currentColor"
            viewBox="0 0 20 20"
          >
<path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.537 4.72h4.965c.969 0 1.372 1.24.588 1.81l-4.016 2.917 1.537 4.72c.3.921-.755 1.688-1.54 1.117L10 13.347l-4.08 2.864c-.784.571-1.838-.196-1.539-1.117l1.536-4.72-4.015-2.917c-.784-.57-.38-1.81.588-1.81h4.965l1.538-4.72z" />
</svg>
))}
</div>
{/_ Quote _/}
<p className="text-gray-700 mb-6">"{quote}"</p>
{/_ User Info _/}
<div className="flex items-center">
{avatar && (
<img
            src={avatar}
            alt={name}
            className="h-10 w-10 rounded-full object-cover mr-3"
          />
)}
<div>
<p className="font-medium">{name}</p>
<p className="text-sm text-gray-500">{affiliation}</p>
</div>
</div>
</div>
);
} 9. FAQ Section
File: src/components/FAQSection.jsx

jsx
Copy
Edit
import React from 'react';
import FAQItem from './FAQItem';

const faqs = [
{
question: 'What document types does OCR-SEC support?',
answer: 'OCR-SEC supports multi-page PDFs, high-resolution PNGs, JPEGs, and TIFFs. We handle scanned bank statements, invoices, ledgers, and more.',
},
{
question: 'How do I train OCR-SEC on a new format?',
answer: 'You can upload 10–15 annotated samples of your format in CSV+image pairs. Our fine-tuning pipeline will customize the OCR model to your layout within minutes.',
},
{
question: 'What accuracy can I expect?',
answer: 'On standard financial documents, we achieve ≈99.5% table extraction accuracy. Accuracy may vary slightly depending on image quality and font styles.',
},
{
question: 'How do I integrate the chatbot with my CRM?',
answer: 'We provide a RESTful API endpoint—simply send your query payload, and OCR-SEC returns JSON table data. Our chatbot module can be embedded as a JavaScript widget on any web page.',
},
];

export default function FAQSection() {
return (
<div className="max-w-7xl mx-auto">
<div className="text-center mb-12" data-aos="fade-down">
<h2 className="text-3xl md:text-4xl font-heading font-bold">FAQ</h2>
</div>
<div className="space-y-4">
{faqs.map((item, idx) => (
<FAQItem
key={idx}
question={item.question}
answer={item.answer}
aosDelay={idx \* 100}
/>
))}
</div>
</div>
);
}
File: src/components/FAQItem.jsx

jsx
Copy
Edit
import React, { useState } from 'react';
import { ChevronDownIcon, ChevronUpIcon } from '@heroicons/react/solid';

export default function FAQItem({ question, answer, aosDelay }) {
const [isOpen, setIsOpen] = useState(false);

return (
<div
      className="bg-white rounded-lg shadow-md overflow-hidden"
      data-aos="fade-up"
      data-aos-delay={aosDelay}
    >
<button
onClick={() => setIsOpen(!isOpen)}
className="w-full flex justify-between items-center px-6 py-4 text-left focus:outline-none" >
<span className="font-medium text-lg">{question}</span>
{isOpen ? (
<ChevronUpIcon className="h-5 w-5 text-primary-navy" />
) : (
<ChevronDownIcon className="h-5 w-5 text-primary-navy" />
)}
</button>
{isOpen && <div className="px-6 pb-4 text-gray-700">{answer}</div>}
</div>
);
}
Key Points

Use ChevronDownIcon / ChevronUpIcon from Heroicons (install: npm install @heroicons/react).

Collapsible items: toggle open/closed on button click.

Add subtle shadow + rounded corners.

Scroll animation with data-aos.

10. Final CTA Section
    File: src/components/CTASection.jsx

jsx
Copy
Edit
import React from 'react';
import heroImage from '../assets/poster-export-snippet.png';

export default function CTASection() {
return (
<div className="bg-primary-navy text-white rounded-xl p-8 flex flex-col lg:flex-row items-center lg:items-start space-y-8 lg:space-y-0 lg:space-x-12">
{/_ Left: Text + Buttons _/}
<div className="lg:w-1/2 space-y-4" data-aos="fade-right">
<h2 className="text-4xl md:text-5xl font-heading font-bold">
Ready to Structure Your Chaos?
</h2>
<p className="text-lg">
Get started with OCR‐SEC today. Download the full poster or schedule a live demo to see the pipeline in action.
</p>
<div className="flex flex-wrap items-center space-x-4">
<a
            href="/poster-full.png"
            target="_blank"
            rel="noopener noreferrer"
            className="btn-primary"
          >
Download Poster
</a>
<a
            href="mailto:ocr-sec@wins.metu.edu.tr?subject=Request%20OCR-SEC%20Demo"
            className="btn-secondary"
          >
Request Demo
</a>
</div>
</div>
{/_ Right: Visual (small mockup) _/}
<div className="lg:w-1/2 flex justify-center" data-aos="fade-left">
<img
          src={heroImage}
          alt="Exportable Data Preview"
          className="rounded-lg shadow-lg w-full max-w-sm"
          loading="lazy"
        />
</div>
</div>
);
}
Key Points

Dark navy background with contrasting white text.

Slightly larger left column heading.

“Download Poster” (primary) + “Request Demo” (secondary).

Right side: an image snippet illustrating “Exportable Financial Data” or “Talk to Your Data.”

Use mailto: link for demo request (or link to a form if implemented later).

11. Footer
    File: src/components/Footer.jsx

jsx
Copy
Edit
import React from 'react';
import qrCode from '../assets/qr-code.png'; // QR to full poster or GitHub

export default function Footer() {
return (
<footer className="bg-white py-12 px-4 md:px-8 lg:px-16 text-gray-700">
<div className="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-3 gap-8">
{/_ Left: Copyright & Credits _/}
<div className="space-y-2 text-sm">
<p>© 2025 WINS Lab, METU. All Rights Reserved.</p>
<p>Supervisor: Prof. F. Tunay Yarman Vural</p>
<p>Sponsors: Duke University & Savronik</p>
</div>

        {/* Center: Team Members */}
        <div className="text-center space-y-1 text-sm">
          <p className="font-medium">Team Members:</p>
          <p>Atakan Öztarak</p>
          <p>Aybüke Aksoy</p>
          <p>Barış Türnüklü</p>
          <p>Cem Meriç Şefikoğulları</p>
          <p>Emre Kalkan</p>
        </div>

        {/* Right: QR Code & Social Icons */}
        <div className="flex flex-col items-center space-y-4">
          <img src={qrCode} alt="QR Code to Poster" className="h-24 w-24" />
          <p className="text-sm">Scan to view full poster</p>
          <div className="flex space-x-4">
            <a href="https://linkedin.com/in/your-profile" target="_blank" rel="noopener noreferrer">
              <img src="/src/assets/icons/linkedin.svg" alt="LinkedIn" className="h-6 w-6" />
            </a>
            <a href="https://github.com/your-repo" target="_blank" rel="noopener noreferrer">
              <img src="/src/assets/icons/github.svg" alt="GitHub" className="h-6 w-6" />
            </a>
            <a href="https://youtube.com/your-channel" target="_blank" rel="noopener noreferrer">
              <img src="/src/assets/icons/youtube.svg" alt="YouTube" className="h-6 w-6" />
            </a>
          </div>
        </div>
      </div>
    </footer>

);
}
Key Points

Three‐column grid on desktop; single column stacked on mobile.

Clean typography, left‐justified copyright/credits.

Center: team names.

Right: QR code + social icons.

10. Responsiveness & Mobile Optimization
    Tailwind Breakpoints

sm: – min-width 640px

md: – min-width 768px

lg: – min-width 1024px

Use these to switch from single‐column to multi‐column layouts.

Fluid Typography & Sizing

Use text-lg, text-xl, text-3xl, text-4xl, etc., with responsive modifiers:

Example: <h1 className="text-3xl md:text-4xl lg:text-5xl">…</h1>

Responsive Images

Use max-w-full and h-auto classes so images scale down on small screens.

Set loading="lazy" on all <img> tags to defer off‐screen images.

Touch‐Friendly Buttons

Ensure CTAs have at least px-6 py-3 for tappable area.

Give sufficient spacing between clickable elements.

Navigation Drawer

Already implemented via mobile hamburger menu.

Ensure no overflow issues (test on iPhone/Android emulator).

Padding & Margin Adjustments

Use px-4 for screens < 640px, px-8 for md screens, px-16 for lg&up.

Check Scroll Animations

AOS defaults fine, but test on mobile to confirm no jank.

11. Page Load Speed & Performance Best Practices
    Optimize & Compress Images

Use tools like ImageOptim or TinyPNG to reduce poster snippets → ≤200KB each.

Use next-gen formats (e.g. WebP) if possible. Tailwind+Vite supports .webp easily—rename png→webp and update src.

Minimize Dependencies

Only install needed NPM packages (React, Tailwind, AOS, Heroicons).

Avoid large UI frameworks like Material UI unless needed—Tailwind suffices.

Lazy Loading & Code Splitting

Use React’s dynamic imports if you have heavy components (e.g. testimonials, FAQ).

Example:

jsx
Copy
Edit
import React, { Suspense, lazy } from 'react';

const TestimonialSection = lazy(() => import('./TestimonialSection'));
// In JSX:
<Suspense fallback={<div>Loading…</div>}>
<TestimonialSection />
</Suspense>
Preload Critical Fonts

In index.html, add:

html
Copy
Edit

<link rel="preload" href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap" as="style" />
Enable GZIP/Brotli on Server

If deploying to Netlify, Vercel, or Surge, compression is automatic.

If on a custom VPS, configure NGINX/Apache to serve compressed assets.

Use loading="lazy"

On all non‐hero images. Avoid lazy‐loading hero if above‐the‐fold.

Remove Unused CSS

Tailwind purge config automatically removes unused classes in production:

cjs
Copy
Edit
// tailwind.config.cjs
module.exports = {
// ...
purge: ['./index.html', './src/**/*.{js,jsx,ts,tsx}'],
// ...
}
Avoid Large JavaScript Bundles

Vite’s default split is usually sufficient.

Monitor the bundle size in production build via npm run build & inspect dist/ sizes.

12. Accessibility & SEO Considerations
    Semantic HTML

Use <header>, <nav>, <main>, <section>, <footer>, <h1>–<h6>, <p>, <ul>, etc.

In React, wrap high‐level structure in semantic tags where possible.

ALT Text on Images

All <img src="..." alt="Descriptive text" />.

Poster snippet images: alt="Capture Clean Centralize snippet" etc.

ARIA Attributes

For collapsible FAQ items, ensure aria-expanded is set on the toggle button.

Color Contrast

Test combinations (e.g. text-white on bg-primary-navy is fine).

text-gray-700 on bg-white passes contrast.

Keyboard Navigation

Ensure all buttons/links have visible :focus states (Tailwind default ring).

Check focus order manually.

SEO Meta Tags

In index.html, add:

html
Copy
Edit

<meta name="description" content="OCR-SEC: An LLM-powered pipeline that converts scanned financial documents into clean, exportable tables. Learn about our custom OCR models, LLM-driven validation, and human-in-the-loop review." />
<meta name="keywords" content="OCR, LLM, Table Extraction, Financial Data, Document Digitization, METU, Duke, Savronik" />
<meta property="og:title" content="OCR-SEC | Structuring Chaos" />
<meta property="og:description" content="Transform scanned financial statements into clean, validated, exportable tables—powered by custom OCR & LLM agents." />
<meta property="og:image" content="/poster-full.png" />
<meta property="og:url" content="https://your-domain.com" />
<meta name="twitter:card" content="summary_large_image" />
13. Deployment & Hosting Checklist
Build for Production

bash
Copy
Edit
npm run build
Confirm dist/ folder appears with optimized assets.

Verify Broken Links/Images

Open dist/index.html locally (e.g. via npx serve dist) and click through all anchor tags.

Inspect console for 404’s, JS errors.

Choose Hosting Platform

Vercel (one-click deploy for Vite apps).

Netlify (drag‐and‐drop dist/, or connect repo).

GitHub Pages (possibly with gh-pages deploy script).

Set Environment Variables (if any)

If you had an actual API endpoint, store base URLs in .env and configure .env.production.

For static site, mostly none needed.

Configure Redirects / HTTPS

Ensure https:// is forced.

On Netlify, add \_redirects file if you rely on client‐side routing (for React SPA):

bash
Copy
Edit
/\* /index.html 200
Test on Real Devices

Use browser devtools to test on iPhone/Android emulators.

Performance audit (Lighthouse) → aim for 90+ scores in Performance, Accessibility, Best Practices, SEO.

Add Custom Domain (Optional)

Link your domain, configure DNS records.

Monitor Real‐World Performance

Use analytics or error tracking (e.g. Google Analytics, Sentry) if desired.

References & Inspirations
High Converting Landing Page Wireframe

The baseline design provided above (nav bar, hero, features, why choose us, reviews, FAQ, CTA, footer).

Modern Web Design Trends

[1] Modern Web Design Trends: https://www.webfx.com/blog/web-design/modern-web-design/

[2] UX Principles: https://technians.com/blog/ux-principles/

Front-End Framework Suggestions

[3] Top Front-End Frameworks 2021: https://existek.com/blog/top-front-end-frameworks-2021/

[4] 10 Most Popular Web Frameworks 2020: https://medium.com/front-end-weekly/10-most-popular-web-frameworks-in-2020-167b9103e08a

AOS (Animate on Scroll) Library

Documentation: https://michalsnik.github.io/aos/

Tailwind CSS Documentation

Official: https://tailwindcss.com/docs

Heroicons (SVG Iconset)

Official: https://heroicons.com/
