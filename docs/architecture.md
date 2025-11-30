# Synetica Website Technical Architecture

**Created:** 2025-01-27  
**Author:** Architect Agent  
**Version:** 1.0  
**Status:** Draft

---

## Executive Summary

This document defines the technical architecture for the Synetica website — a static marketing site built with Astro, optimized for Indonesian network conditions, and designed to support lead generation through credibility-first content and conversion-optimized user flows.

**Key Technical Decisions:**
- **Framework:** Astro 4.x with static site generation (SSG)
- **Styling:** Tailwind CSS 3.x with shadcn/ui components
- **Hosting:** Netlify with global CDN
- **Analytics:** GA4 + Search Console + Microsoft Clarity
- **Forms:** Netlify Forms with fallback to Formspree
- **Content:** Markdown-based with future n8n automation

---

## 1. System Overview

### 1.1 Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              USER BROWSER                                    │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  Astro Static Site (HTML/CSS/JS)                                     │   │
│  │  - Tailwind CSS (purged, <50KB)                                      │   │
│  │  - Geist Mono typography                                             │   │
│  │  - shadcn/ui components                                              │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
└───────────────────────────────────┬─────────────────────────────────────────┘
                                    │
                    ┌───────────────┴───────────────┐
                    │         NETLIFY CDN           │
                    │   (Global Edge Distribution)  │
                    │   - HTTPS                     │
                    │   - Asset optimization        │
                    │   - Deploy previews           │
                    └───────────────┬───────────────┘
                                    │
        ┌───────────────────────────┼───────────────────────────────┐
        │                           │                               │
        ▼                           ▼                               ▼
┌───────────────┐         ┌─────────────────┐            ┌──────────────────┐
│ NETLIFY FORMS │         │   ANALYTICS     │            │   WHATSAPP       │
│               │         │                 │            │                  │
│ - Form submit │         │ - GA4           │            │ - wa.me links    │
│ - Email notif │         │ - Search Console│            │ - Pre-filled msg │
│ - Spam filter │         │ - MS Clarity    │            │                  │
└───────────────┘         └─────────────────┘            └──────────────────┘

        ┌───────────────────────────────────────────────────────────┐
        │                    BUILD PIPELINE                          │
        │                                                           │
        │  GitHub ──▶ Netlify Build ──▶ Astro SSG ──▶ Deploy       │
        │     │                                                     │
        │     └──▶ Preview Deploy (PRs)                             │
        └───────────────────────────────────────────────────────────┘

        ┌───────────────────────────────────────────────────────────┐
        │              FUTURE: CONTENT AUTOMATION                    │
        │                                                           │
        │  Spreadsheet/DB ──▶ n8n Workflow ──▶ Markdown ──▶ Git    │
        └───────────────────────────────────────────────────────────┘
```

### 1.2 Technology Stack

| Layer | Technology | Version | Rationale |
|-------|------------|---------|-----------|
| **Framework** | Astro | 4.x | Ultra-fast SSG, excellent DX, islands architecture |
| **Styling** | Tailwind CSS | 3.x | JIT compilation, utility-first, purged CSS |
| **Components** | shadcn/ui | Latest | Accessible primitives, Tailwind-native |
| **Typography** | Geist Mono | Latest | Monospace for prototyping aesthetic |
| **Hosting** | Netlify | - | Global CDN, forms, deploy previews |
| **Analytics** | GA4 + Clarity | - | Conversion tracking + behavior analysis |
| **Forms** | Netlify Forms | - | Zero-config, spam protection |
| **Automation** | n8n | Future | Content pipeline automation |

---

## 2. Project Structure

### 2.1 Directory Layout

```
synetica-website/
├── src/
│   ├── components/           # Reusable UI components
│   │   ├── ui/              # shadcn/ui primitives
│   │   │   ├── button.astro
│   │   │   ├── card.astro
│   │   │   ├── input.astro
│   │   │   └── ...
│   │   ├── layout/          # Layout components
│   │   │   ├── Header.astro
│   │   │   ├── Footer.astro
│   │   │   ├── Navigation.astro
│   │   │   └── MobileMenu.astro
│   │   ├── sections/        # Page sections
│   │   │   ├── Hero.astro
│   │   │   ├── TrustLogos.astro
│   │   │   ├── CaseStudyCard.astro
│   │   │   ├── ProcessPhase.astro
│   │   │   ├── FooterCTA.astro
│   │   │   └── ...
│   │   └── forms/           # Form components
│   │       ├── ContactForm.astro
│   │       └── ConsultationForm.astro
│   │
│   ├── layouts/             # Page layouts
│   │   ├── BaseLayout.astro
│   │   ├── PageLayout.astro
│   │   └── CaseStudyLayout.astro
│   │
│   ├── pages/               # Route pages
│   │   ├── index.astro      # Homepage
│   │   ├── solutions/
│   │   │   ├── index.astro
│   │   │   ├── blueprint.astro
│   │   │   ├── build-mvp.astro
│   │   │   └── ...
│   │   ├── products/
│   │   │   └── index.astro
│   │   ├── industries/
│   │   │   └── index.astro
│   │   ├── company/
│   │   │   ├── index.astro
│   │   │   ├── about.astro
│   │   │   ├── team.astro
│   │   │   └── careers.astro
│   │   ├── process/
│   │   │   └── index.astro
│   │   ├── case-studies/
│   │   │   ├── index.astro
│   │   │   └── [...slug].astro
│   │   ├── blog/
│   │   │   ├── index.astro
│   │   │   └── [...slug].astro
│   │   ├── resources/
│   │   │   └── index.astro
│   │   ├── contact/
│   │   │   └── index.astro
│   │   ├── partnership/
│   │   │   └── index.astro  # Coming Soon page
│   │   └── 404.astro
│   │
│   ├── content/             # Content collections
│   │   ├── case-studies/    # Case study markdown
│   │   │   ├── astra-setir-kanan.md
│   │   │   ├── holywings-loyalty.md
│   │   │   └── angkasapura-sso.md
│   │   ├── blog/            # Blog posts
│   │   │   └── ...
│   │   └── config.ts        # Collection schemas
│   │
│   ├── styles/              # Global styles
│   │   ├── globals.css      # Tailwind imports + global styles
│   │   └── fonts.css        # Font declarations
│   │
│   └── lib/                 # Utilities
│       ├── utils.ts         # Helper functions
│       └── constants.ts     # Site-wide constants
│
├── public/                  # Static assets
│   ├── fonts/              # Self-hosted fonts
│   │   └── GeistMono/
│   ├── images/
│   │   ├── logos/          # Client logos
│   │   ├── case-studies/   # Case study images
│   │   └── team/           # Team photos
│   ├── favicon.ico
│   ├── robots.txt
│   └── sitemap.xml         # Auto-generated
│
├── tests/                   # Test files
│   ├── e2e/                # End-to-end tests
│   │   ├── navigation.spec.ts
│   │   ├── contact-form.spec.ts
│   │   └── whatsapp.spec.ts
│   └── unit/               # Unit tests
│
├── astro.config.mjs        # Astro configuration
├── tailwind.config.mjs     # Tailwind configuration
├── postcss.config.cjs      # PostCSS configuration
├── tsconfig.json           # TypeScript configuration
├── package.json
├── netlify.toml            # Netlify configuration
└── .env.example            # Environment variables template
```

### 2.2 Content Collections Schema

```typescript
// src/content/config.ts
import { defineCollection, z } from 'astro:content';

const caseStudies = defineCollection({
  type: 'content',
  schema: z.object({
    title: z.string(),
    client: z.string(),
    industry: z.enum(['automotive', 'hospitality', 'aviation', 'fintech', 'logistics', 'retail', 'education', 'healthcare', 'government']),
    description: z.string(),
    challenge: z.string(),
    solution: z.string(),
    outcome: z.string(),
    metrics: z.array(z.object({
      label: z.string(),
      value: z.string(),
    })).optional(),
    techStack: z.array(z.string()),
    image: z.string().optional(),
    featured: z.boolean().default(false),
    publishDate: z.date(),
    draft: z.boolean().default(false),
  }),
});

const blog = defineCollection({
  type: 'content',
  schema: z.object({
    title: z.string(),
    description: z.string(),
    author: z.string(),
    publishDate: z.date(),
    updatedDate: z.date().optional(),
    image: z.string().optional(),
    tags: z.array(z.string()),
    draft: z.boolean().default(false),
  }),
});

export const collections = {
  'case-studies': caseStudies,
  'blog': blog,
};
```

---

## 3. Frontend Architecture

### 3.1 Astro Configuration

```javascript
// astro.config.mjs
import { defineConfig } from 'astro/config';
import tailwind from '@astrojs/tailwind';
import sitemap from '@astrojs/sitemap';
import compress from 'astro-compress';

export default defineConfig({
  site: 'https://synetica.com',
  integrations: [
    tailwind({
      applyBaseStyles: false, // Use custom global styles
    }),
    sitemap(),
    compress({
      CSS: true,
      HTML: true,
      JavaScript: true,
      Image: true,
      SVG: true,
    }),
  ],
  output: 'static',
  build: {
    inlineStylesheets: 'auto',
  },
  vite: {
    build: {
      cssMinify: 'lightningcss',
    },
  },
});
```

### 3.2 Tailwind Configuration

```javascript
// tailwind.config.mjs
import defaultTheme from 'tailwindcss/defaultTheme';

/** @type {import('tailwindcss').Config} */
export default {
  darkMode: ['class'],
  content: ['./src/**/*.{astro,html,js,jsx,md,mdx,svelte,ts,tsx,vue}'],
  theme: {
    extend: {
      colors: {
        // Tweakcn Graphite Theme (OKLCH)
        background: 'oklch(0.9551 0 0)',
        foreground: 'oklch(0.3211 0 0)',
        card: {
          DEFAULT: 'oklch(1.0000 0 0)',
          foreground: 'oklch(0.3211 0 0)',
        },
        primary: {
          DEFAULT: 'oklch(0.4891 0 0)',
          foreground: 'oklch(1.0000 0 0)',
        },
        secondary: {
          DEFAULT: 'oklch(0.9067 0 0)',
          foreground: 'oklch(0.3211 0 0)',
        },
        muted: {
          DEFAULT: 'oklch(0.8853 0 0)',
          foreground: 'oklch(0.5486 0 0)',
        },
        accent: {
          DEFAULT: 'oklch(0.8078 0 0)',
          foreground: 'oklch(0.3211 0 0)',
        },
        destructive: {
          DEFAULT: 'oklch(0.5594 0.1900 25.8625)',
          foreground: 'oklch(1.0000 0 0)',
        },
        border: 'oklch(0.8576 0 0)',
        input: 'oklch(0.9067 0 0)',
        ring: 'oklch(0.4891 0 0)',
      },
      fontFamily: {
        sans: ['Montserrat', ...defaultTheme.fontFamily.sans],
        serif: ['Georgia', ...defaultTheme.fontFamily.serif],
        mono: ['Geist Mono', ...defaultTheme.fontFamily.mono],
      },
      borderRadius: {
        DEFAULT: '0.35rem',
      },
      animation: {
        'scroll-left': 'scroll-left 30s linear infinite',
        'fade-in': 'fade-in 0.5s ease-out',
        'slide-up': 'slide-up 0.5s ease-out',
      },
      keyframes: {
        'scroll-left': {
          '0%': { transform: 'translateX(0)' },
          '100%': { transform: 'translateX(-50%)' },
        },
        'fade-in': {
          '0%': { opacity: '0' },
          '100%': { opacity: '1' },
        },
        'slide-up': {
          '0%': { opacity: '0', transform: 'translateY(20px)' },
          '100%': { opacity: '1', transform: 'translateY(0)' },
        },
      },
    },
  },
  plugins: [
    require('@tailwindcss/typography'),
    require('tailwindcss-animate'),
  ],
};
```

### 3.3 Global Styles

```css
/* src/styles/globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  :root {
    --radius: 0.35rem;
  }

  html {
    scroll-behavior: smooth;
  }

  body {
    @apply font-mono bg-background text-foreground antialiased;
  }

  /* Grid background pattern */
  .grid-background {
    background-image: 
      linear-gradient(to right, oklch(0.8576 0 0) 1px, transparent 1px),
      linear-gradient(to bottom, oklch(0.8576 0 0) 1px, transparent 1px);
    background-size: 24px 24px;
    opacity: 0.3;
  }
}

@layer components {
  .container-wide {
    @apply max-w-7xl mx-auto px-4 sm:px-6 lg:px-8;
  }

  .btn-primary {
    @apply bg-primary text-primary-foreground px-6 py-3 font-medium 
           transition-opacity hover:opacity-90 focus:ring-2 focus:ring-ring 
           focus:ring-offset-2 focus:outline-none;
  }

  .btn-secondary {
    @apply bg-transparent text-foreground border border-border px-6 py-3 
           font-medium transition-colors hover:bg-muted focus:ring-2 
           focus:ring-ring focus:ring-offset-2 focus:outline-none;
  }
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

---

## 4. Third-Party Integrations

### 4.1 Analytics Integration

#### Google Analytics 4

```html
<!-- src/components/layout/Analytics.astro -->
---
const GA_MEASUREMENT_ID = import.meta.env.PUBLIC_GA_MEASUREMENT_ID;
---

{GA_MEASUREMENT_ID && (
  <>
    <script
      async
      src={`https://www.googletagmanager.com/gtag/js?id=${GA_MEASUREMENT_ID}`}
    />
    <script define:vars={{ GA_MEASUREMENT_ID }}>
      window.dataLayer = window.dataLayer || [];
      function gtag() {
        dataLayer.push(arguments);
      }
      gtag('js', new Date());
      gtag('config', GA_MEASUREMENT_ID, {
        page_title: document.title,
        page_location: window.location.href,
      });
    </script>
  </>
)}
```

#### Microsoft Clarity

```html
<!-- src/components/layout/Clarity.astro -->
---
const CLARITY_PROJECT_ID = import.meta.env.PUBLIC_CLARITY_PROJECT_ID;
---

{CLARITY_PROJECT_ID && (
  <script define:vars={{ CLARITY_PROJECT_ID }}>
    (function(c,l,a,r,i,t,y){
      c[a]=c[a]||function(){(c[a].q=c[a].q||[]).push(arguments)};
      t=l.createElement(r);t.async=1;t.src="https://www.clarity.ms/tag/"+i;
      y=l.getElementsByTagName(r)[0];y.parentNode.insertBefore(t,y);
    })(window, document, "clarity", "script", CLARITY_PROJECT_ID);
  </script>
)}
```

#### Custom Event Tracking

```typescript
// src/lib/analytics.ts
export function trackEvent(
  eventName: string,
  eventParams?: Record<string, string | number>
) {
  if (typeof window !== 'undefined' && window.gtag) {
    window.gtag('event', eventName, eventParams);
  }
}

// Usage examples:
export const trackCTAClick = (ctaName: string, location: string) => {
  trackEvent('cta_click', {
    cta_name: ctaName,
    location: location,
  });
};

export const trackCaseStudyView = (caseStudyId: string, client: string) => {
  trackEvent('case_study_view', {
    case_study_id: caseStudyId,
    client: client,
  });
};

export const trackFormSubmission = (formName: string) => {
  trackEvent('form_submission', {
    form_name: formName,
  });
};

export const trackWhatsAppClick = (location: string) => {
  trackEvent('whatsapp_click', {
    location: location,
  });
};
```

### 4.2 Form Handling

#### Netlify Forms Configuration

```html
<!-- src/components/forms/ContactForm.astro -->
---
interface Props {
  formName?: string;
}

const { formName = 'contact' } = Astro.props;
---

<form
  name={formName}
  method="POST"
  data-netlify="true"
  netlify-honeypot="bot-field"
  action="/contact/success"
  class="space-y-4"
>
  <!-- Honeypot field for spam protection -->
  <input type="hidden" name="form-name" value={formName} />
  <p class="hidden">
    <label>
      Don't fill this out if you're human:
      <input name="bot-field" />
    </label>
  </p>

  <div>
    <label for="name" class="block text-sm font-medium mb-1">
      Name <span class="text-destructive">*</span>
    </label>
    <input
      type="text"
      id="name"
      name="name"
      required
      class="w-full px-4 py-3 border border-border bg-input focus:ring-2 
             focus:ring-ring focus:border-transparent outline-none"
    />
  </div>

  <div>
    <label for="email" class="block text-sm font-medium mb-1">
      Email <span class="text-destructive">*</span>
    </label>
    <input
      type="email"
      id="email"
      name="email"
      required
      class="w-full px-4 py-3 border border-border bg-input focus:ring-2 
             focus:ring-ring focus:border-transparent outline-none"
    />
  </div>

  <div>
    <label for="company" class="block text-sm font-medium mb-1">
      Company
    </label>
    <input
      type="text"
      id="company"
      name="company"
      class="w-full px-4 py-3 border border-border bg-input focus:ring-2 
             focus:ring-ring focus:border-transparent outline-none"
    />
  </div>

  <div>
    <label for="message" class="block text-sm font-medium mb-1">
      How can we help? <span class="text-destructive">*</span>
    </label>
    <textarea
      id="message"
      name="message"
      rows="4"
      required
      class="w-full px-4 py-3 border border-border bg-input focus:ring-2 
             focus:ring-ring focus:border-transparent outline-none resize-none"
    ></textarea>
  </div>

  <button
    type="submit"
    class="btn-primary w-full"
    onclick="trackFormSubmission('contact')"
  >
    Send Message
  </button>
</form>
```

#### Form Submission Success Page

```astro
<!-- src/pages/contact/success.astro -->
---
import PageLayout from '../../layouts/PageLayout.astro';
---

<PageLayout title="Message Sent | Synetica">
  <div class="min-h-[60vh] flex items-center justify-center">
    <div class="text-center max-w-md">
      <div class="text-6xl mb-6">✓</div>
      <h1 class="text-2xl font-bold mb-4">Thank you for reaching out!</h1>
      <p class="text-muted-foreground mb-8">
        We've received your message and will get back to you within 24 hours.
      </p>
      <a href="/" class="btn-primary inline-block">
        Back to Homepage
      </a>
    </div>
  </div>
</PageLayout>
```

### 4.3 WhatsApp Integration

```astro
<!-- src/components/WhatsAppButton.astro -->
---
interface Props {
  message?: string;
  location?: string;
  className?: string;
  variant?: 'primary' | 'secondary' | 'icon';
}

const { 
  message = "Hi Synetica! I'm interested in learning more about your 8-Week Product Launch program.",
  location = 'footer',
  className = '',
  variant = 'secondary'
} = Astro.props;

const WHATSAPP_NUMBER = '6281234567890'; // Replace with actual number
const encodedMessage = encodeURIComponent(message);
const whatsappUrl = `https://wa.me/${WHATSAPP_NUMBER}?text=${encodedMessage}`;
---

<a
  href={whatsappUrl}
  target="_blank"
  rel="noopener noreferrer"
  class:list={[
    variant === 'primary' && 'btn-primary',
    variant === 'secondary' && 'btn-secondary',
    variant === 'icon' && 'p-3 bg-[#25D366] text-white rounded-full hover:bg-[#128C7E] transition-colors',
    className
  ]}
  onclick={`trackWhatsAppClick('${location}')`}
  aria-label="Chat on WhatsApp"
>
  {variant === 'icon' ? (
    <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
      <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
    </svg>
  ) : (
    <slot>Chat on WhatsApp</slot>
  )}
</a>
```

---

## 5. Performance Optimization

### 5.1 Performance Targets

| Metric | Target | Rationale |
|--------|--------|-----------|
| **LCP** | < 2.5s | Core Web Vital for user experience |
| **FID** | < 100ms | Core Web Vital for interactivity |
| **CLS** | < 0.1 | Core Web Vital for visual stability |
| **TTI** | < 3s | Critical for Indonesian mobile networks |
| **Total Page Size** | < 500KB | Optimized for slower connections |
| **CSS Size** | < 50KB | Tailwind purged output |

### 5.2 Optimization Strategies

#### Image Optimization

```astro
<!-- src/components/OptimizedImage.astro -->
---
import { Image } from 'astro:assets';

interface Props {
  src: ImageMetadata;
  alt: string;
  widths?: number[];
  sizes?: string;
  class?: string;
  loading?: 'eager' | 'lazy';
}

const {
  src,
  alt,
  widths = [400, 800, 1200],
  sizes = '(max-width: 768px) 100vw, (max-width: 1200px) 50vw, 33vw',
  class: className = '',
  loading = 'lazy'
} = Astro.props;
---

<Image
  src={src}
  alt={alt}
  widths={widths}
  sizes={sizes}
  format="webp"
  quality={80}
  loading={loading}
  decoding="async"
  class={className}
/>
```

#### Font Loading Strategy

```css
/* src/styles/fonts.css */
@font-face {
  font-family: 'Geist Mono';
  src: url('/fonts/GeistMono/GeistMono-Regular.woff2') format('woff2');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'Geist Mono';
  src: url('/fonts/GeistMono/GeistMono-Medium.woff2') format('woff2');
  font-weight: 500;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'Geist Mono';
  src: url('/fonts/GeistMono/GeistMono-Bold.woff2') format('woff2');
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}
```

#### Preloading Critical Assets

```astro
<!-- src/layouts/BaseLayout.astro head section -->
<head>
  <!-- Preload critical fonts -->
  <link
    rel="preload"
    href="/fonts/GeistMono/GeistMono-Regular.woff2"
    as="font"
    type="font/woff2"
    crossorigin
  />
  
  <!-- Preconnect to analytics -->
  <link rel="preconnect" href="https://www.googletagmanager.com" />
  <link rel="preconnect" href="https://www.clarity.ms" />
  
  <!-- DNS prefetch for external resources -->
  <link rel="dns-prefetch" href="https://fonts.googleapis.com" />
</head>
```

### 5.3 Caching Strategy

```toml
# netlify.toml
[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"

[[headers]]
  for = "/fonts/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/images/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.css"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.js"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"
```

---

## 6. Testing Architecture

### 6.1 Testing Strategy

| Test Type | Tool | Scope | Frequency |
|-----------|------|-------|-----------|
| **E2E Critical Paths** | Playwright | CTAs, forms, navigation | Every deploy |
| **Visual Regression** | Playwright | Screenshots | Every deploy |
| **Accessibility** | axe-core | WCAG AA compliance | Every deploy |
| **Performance** | Lighthouse CI | Core Web Vitals | Every deploy |
| **Link Checking** | Broken Link Checker | All internal links | Weekly |

### 6.2 E2E Test Examples

```typescript
// tests/e2e/navigation.spec.ts
import { test, expect } from '@playwright/test';

test.describe('Navigation', () => {
  test('should navigate to all main sections', async ({ page }) => {
    await page.goto('/');
    
    // Test Solutions navigation
    await page.click('nav >> text=Solutions');
    await expect(page).toHaveURL(/\/solutions/);
    
    // Test Case Studies navigation
    await page.click('nav >> text=Case Studies');
    await expect(page).toHaveURL(/\/case-studies/);
    
    // Test Contact navigation
    await page.click('nav >> text=Contact');
    await expect(page).toHaveURL(/\/contact/);
  });

  test('should show Coming Soon for Partnership', async ({ page }) => {
    await page.goto('/');
    await page.click('nav >> text=Partnership');
    await expect(page.locator('text=Coming Soon')).toBeVisible();
  });
});
```

```typescript
// tests/e2e/contact-form.spec.ts
import { test, expect } from '@playwright/test';

test.describe('Contact Form', () => {
  test('should submit form successfully', async ({ page }) => {
    await page.goto('/contact');
    
    await page.fill('input[name="name"]', 'Test User');
    await page.fill('input[name="email"]', 'test@example.com');
    await page.fill('input[name="company"]', 'Test Company');
    await page.fill('textarea[name="message"]', 'This is a test message');
    
    await page.click('button[type="submit"]');
    
    await expect(page).toHaveURL(/\/contact\/success/);
    await expect(page.locator('text=Thank you')).toBeVisible();
  });

  test('should show validation errors for required fields', async ({ page }) => {
    await page.goto('/contact');
    
    await page.click('button[type="submit"]');
    
    // HTML5 validation should prevent submission
    const nameInput = page.locator('input[name="name"]');
    await expect(nameInput).toHaveAttribute('required', '');
  });
});
```

```typescript
// tests/e2e/whatsapp.spec.ts
import { test, expect } from '@playwright/test';

test.describe('WhatsApp Integration', () => {
  test('should have correct WhatsApp link', async ({ page }) => {
    await page.goto('/');
    
    const whatsappLink = page.locator('a[href*="wa.me"]').first();
    const href = await whatsappLink.getAttribute('href');
    
    expect(href).toContain('wa.me/');
    expect(href).toContain('text=');
  });
});
```

### 6.3 Accessibility Testing

```typescript
// tests/e2e/accessibility.spec.ts
import { test, expect } from '@playwright/test';
import AxeBuilder from '@axe-core/playwright';

test.describe('Accessibility', () => {
  test('homepage should have no critical accessibility issues', async ({ page }) => {
    await page.goto('/');
    
    const accessibilityScanResults = await new AxeBuilder({ page })
      .withTags(['wcag2a', 'wcag2aa'])
      .analyze();
    
    expect(accessibilityScanResults.violations).toEqual([]);
  });

  test('contact page should have no critical accessibility issues', async ({ page }) => {
    await page.goto('/contact');
    
    const accessibilityScanResults = await new AxeBuilder({ page })
      .withTags(['wcag2a', 'wcag2aa'])
      .analyze();
    
    expect(accessibilityScanResults.violations).toEqual([]);
  });
});
```

---

## 7. Deployment Architecture

### 7.1 Netlify Configuration

```toml
# netlify.toml
[build]
  command = "npm run build"
  publish = "dist"

[build.environment]
  NODE_VERSION = "20"

# Redirect rules
[[redirects]]
  from = "/portfolio/*"
  to = "/case-studies/:splat"
  status = 301

[[redirects]]
  from = "/services/*"
  to = "/solutions/:splat"
  status = 301

# Custom 404
[[redirects]]
  from = "/*"
  to = "/404"
  status = 404

# Forms configuration
[build.processing]
  skip_processing = false

[build.processing.html]
  pretty_urls = true
```

### 7.2 Environment Variables

```bash
# .env.example

# Analytics
PUBLIC_GA_MEASUREMENT_ID=G-XXXXXXXXXX
PUBLIC_CLARITY_PROJECT_ID=xxxxxxxxxx

# WhatsApp
PUBLIC_WHATSAPP_NUMBER=6281234567890

# Site
PUBLIC_SITE_URL=https://synetica.com
```

### 7.3 Deployment Workflow

```yaml
# GitHub Actions workflow for additional checks
# .github/workflows/deploy.yml

name: Deploy

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      
      - run: npm ci
      - run: npm run build
      - run: npm run test:e2e
      
      - name: Run Lighthouse CI
        uses: treosh/lighthouse-ci-action@v10
        with:
          configPath: ./lighthouserc.json
          uploadArtifacts: true
```

### 7.4 Lighthouse CI Configuration

```json
// lighthouserc.json
{
  "ci": {
    "collect": {
      "staticDistDir": "./dist",
      "url": [
        "/",
        "/solutions/",
        "/case-studies/",
        "/contact/"
      ]
    },
    "assert": {
      "assertions": {
        "categories:performance": ["error", {"minScore": 0.9}],
        "categories:accessibility": ["error", {"minScore": 0.9}],
        "categories:best-practices": ["error", {"minScore": 0.9}],
        "categories:seo": ["error", {"minScore": 0.9}]
      }
    }
  }
}
```

---

## 8. Content Automation (Future)

### 8.1 n8n Workflow Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                     CONTENT AUTOMATION PIPELINE                      │
│                                                                     │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐             │
│  │  Data Source│    │   n8n       │    │   Git       │             │
│  │  (Sheets)   │───▶│  Workflow   │───▶│  Commit     │             │
│  └─────────────┘    └─────────────┘    └─────────────┘             │
│                           │                   │                     │
│                           ▼                   ▼                     │
│                    ┌─────────────┐    ┌─────────────┐             │
│                    │  Markdown   │    │  Netlify    │             │
│                    │  Generator  │    │  Deploy     │             │
│                    └─────────────┘    └─────────────┘             │
└─────────────────────────────────────────────────────────────────────┘
```

### 8.2 n8n Workflow Steps

1. **Trigger:** Schedule (daily) or webhook from data source
2. **Fetch:** Pull case study data from Google Sheets/Airtable
3. **Transform:** Convert to markdown frontmatter format
4. **Validate:** Check required fields and content quality
5. **Generate:** Create markdown file with proper naming convention
6. **Commit:** Push to Git repository via GitHub API
7. **Notify:** Send Slack/email notification on success/failure

### 8.3 Markdown Template

```markdown
---
title: "{{title}}"
client: "{{client}}"
industry: "{{industry}}"
description: "{{description}}"
challenge: "{{challenge}}"
solution: "{{solution}}"
outcome: "{{outcome}}"
metrics:
{{#each metrics}}
  - label: "{{label}}"
    value: "{{value}}"
{{/each}}
techStack:
{{#each techStack}}
  - "{{this}}"
{{/each}}
image: "{{image}}"
featured: {{featured}}
publishDate: {{publishDate}}
draft: false
---

## The Challenge

{{challenge_detailed}}

## Our Approach

{{approach_detailed}}

## The Results

{{results_detailed}}

## Key Takeaways

{{takeaways}}
```

---

## 9. Security Considerations

### 9.1 Security Headers

All security headers are configured in `netlify.toml`:

```toml
[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"
    Content-Security-Policy = "default-src 'self'; script-src 'self' 'unsafe-inline' https://www.googletagmanager.com https://www.clarity.ms; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:; font-src 'self'; connect-src 'self' https://www.google-analytics.com https://www.clarity.ms"
    Permissions-Policy = "camera=(), microphone=(), geolocation=()"
```

### 9.2 Data Handling

- **No User Data Storage:** All form data sent directly to Netlify Forms
- **Minimal Data Collection:** Only essential form fields collected
- **HTTPS Enforcement:** Automatic via Netlify
- **Cookie Consent:** Required for analytics (future implementation)

---

## 10. Monitoring & Observability

### 10.1 Monitoring Stack

| Tool | Purpose | Metrics |
|------|---------|---------|
| **Netlify Analytics** | Traffic & performance | Page views, bandwidth, top pages |
| **Google Analytics 4** | User behavior | Sessions, conversions, events |
| **Microsoft Clarity** | UX analysis | Heatmaps, recordings, rage clicks |
| **Search Console** | SEO performance | Rankings, impressions, CTR |
| **Lighthouse CI** | Performance regression | Core Web Vitals per deploy |

### 10.2 Alerting

- **Netlify Build Failures:** Email notification
- **Lighthouse Score Drops:** GitHub Actions failure notification
- **Form Submission Errors:** Netlify Forms notification

---

## 11. Migration Path from index.html

### 11.1 Component Extraction

The existing `index.html` mockup will be decomposed into Astro components:

| HTML Section | Astro Component |
|--------------|-----------------|
| Navigation | `Header.astro`, `Navigation.astro`, `MobileMenu.astro` |
| Hero | `Hero.astro` |
| Trust logos | `TrustLogos.astro` |
| Case studies | `CaseStudyCard.astro`, `CaseStudySection.astro` |
| Process | `ProcessSection.astro`, `ProcessPhase.astro` |
| Footer CTA | `FooterCTA.astro` |
| Footer | `Footer.astro` |

### 11.2 Style Migration

1. Extract CSS variables from `index.html` to `globals.css`
2. Convert inline styles to Tailwind utilities
3. Create reusable component classes in `@layer components`
4. Ensure grid background pattern is implemented consistently

---

## Appendix A: Decision Log

| Date | Decision | Rationale | Alternatives Considered |
|------|----------|-----------|------------------------|
| 2025-01-27 | Astro over Next.js | Better SSG performance, simpler architecture for static site | Next.js, Gatsby |
| 2025-01-27 | Netlify over Vercel | Forms integration, better free tier for this use case | Vercel, GitHub Pages |
| 2025-01-27 | Playwright over Cypress | Better cross-browser support, faster execution | Cypress, TestCafe |
| 2025-01-27 | Geist Mono as primary font | Matches prototyping aesthetic from mockup | Inter, SF Mono |

---

## Appendix B: Related Documents

- [Product Requirements Document](./prd.md)
- [UX Design Specification](./ux-design-specification.md)
- [Brand Guide Brief](./brand-guide-brief.md)
- [Information Architecture](./information-architecture.md)

---

## Version History

| Date | Version | Changes | Author |
|------|---------|---------|--------|
| 2025-01-27 | 1.0 | Initial architecture document | Architect Agent |

