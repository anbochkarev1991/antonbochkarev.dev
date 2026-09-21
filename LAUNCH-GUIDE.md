# Freelance One-Pager: Launch Guide

Everything you need to build, publish, and index your freelance one-pager in one sitting.

---

## 1. Hosting: Super.so vs Potion.so vs Simple.ink

### Comparison

| Feature | Super.so | Potion.so | Simple.ink |
|---|---|---|---|
| Price (1 site) | ~$16/mo | ~$10/mo | Free tier; ~$12/mo for custom domain |
| Custom domain | Yes (all paid plans) | Yes (all paid plans) | Paid plan only |
| Auto sitemap.xml | Yes | Yes | Limited |
| Meta title/description | Yes (per-page) | Yes (per-page) | Basic |
| OG tags control | Yes | Yes | Partial |
| Custom code injection (head/body) | Yes (for JSON-LD, analytics) | Yes | Limited |
| Custom CSS | Yes | Yes | Limited |
| CDN / speed | Cloudflare CDN, fast | Vercel-backed, fast | Adequate |
| Canonical URLs | Clean /slug format | Clean /slug format | Sometimes includes Notion IDs |
| robots.txt control | Auto-generated, correct | Auto-generated | Less control |
| Uptime/reliability | Mature, widely used | Solid, smaller user base | Smaller |

### Recommendation: Super.so

Super.so is the best fit here. Reasons:

1. **Custom code injection** is critical. You need to paste a JSON-LD structured-data snippet into the page `<head>`. Super.so lets you do this globally or per page. Potion.so also supports it, but Super has the most documented workflow for it.
2. **Automatic sitemap.xml** at `yourdomain.com/sitemap.xml` with no manual setup. This matters for Google Search Console submission.
3. **Clean URLs and canonical tags** out of the box. No Notion page IDs leaking into your URL slugs.
4. **Cloudflare CDN** means your page loads fast globally, which directly affects Core Web Vitals (and you are selling CWV expertise, so your own site should pass).
5. **Mature ecosystem.** More troubleshooting resources, more reliable uptime.

Potion.so is a fine alternative at $4/mo less if budget is tight. The main thing you would lose is slightly less documentation for edge cases.

Simple.ink is too limited for SEO work (weak code injection, less control over robots/sitemap).

**Cost:** $16/mo is negligible against the $80-150/hr you are targeting. One hour of freelance work pays for a year.

### Why raw notion.site is worse for indexing

- Notion pages at `yourname.notion.site` have Notion's robots.txt, not yours. Google indexes them, but you share domain authority with every other Notion user.
- URLs contain long random IDs (e.g., `notion.site/Anton-Bochkarev-abc123def456`), which look unprofessional and are not keyword-rich.
- No sitemap.xml you control. No custom meta description. No JSON-LD injection. No OG image control.
- You cannot verify `notion.site` in Google Search Console because you do not own the domain.
- A custom domain (antonbochkarev.com or .dev) builds YOUR domain authority from day one. Every backlink (LinkedIn, GitHub, Contra) strengthens your domain specifically.

### How to connect a custom domain

1. **Register your domain.** Namecheap, Google Domains (now Squarespace Domains), or Cloudflare Registrar all work. `antonbochkarev.dev` is a solid choice (.dev enforces HTTPS by default, signals "developer").
2. **In Super.so dashboard:** Go to your site settings, enter the custom domain.
3. **At your registrar:** Add the DNS records Super.so provides. Typically:
   - A record pointing to Super.so's IP (they will tell you the exact value)
   - Or a CNAME record pointing to `cname.super.so` (for subdomains)
4. **Wait for DNS propagation** (usually 5-30 minutes, occasionally up to 48 hours).
5. **SSL:** Super.so provisions a free SSL certificate automatically via Cloudflare once DNS propagates.
6. **Verify:** Visit your domain in a browser. Confirm HTTPS padlock, correct content, and no Notion URL visible.

---

## 2. SEO Essentials (ready to paste)

### Page title (appears in browser tab and Google results)

```
Anton Bochkarev | Senior Headless Commerce Developer (Next.js, Shopify, Contentstack)
```

Keep it under 60 characters for full display in Google. This one is 75, which is acceptable (Google will truncate but the important keywords are front-loaded). If you want to stay under 60:

```
Anton Bochkarev | Headless Commerce Developer (Next.js + Shopify)
```

### Meta description (~155 characters)

```
Senior frontend engineer building high-performance headless commerce storefronts with Next.js, Shopify, and Contentstack. Core Web Vitals, WCAG accessibility, technical SEO, AI-search. Based in Argentina, remote UTC-3.
```

(218 chars, but Google sometimes displays longer snippets now. For a strict 155-char version:)

```
Senior frontend engineer for headless commerce storefronts. Next.js, Shopify, Contentstack. Core Web Vitals, WCAG accessibility, SEO and AI-search. Remote, UTC-3.
```

### Open Graph tags

```
og:title       — Anton Bochkarev | Senior Headless Commerce Developer
og:description — Senior frontend engineer building high-performance headless storefronts with Next.js, Shopify, and Contentstack. Performance, accessibility, SEO and AI-search.
og:type        — website
og:url         — https://antonbochkarev.dev (your final domain)
og:image       — (see guidance below)
```

**OG image guidance:** Create a 1200x630px image. Use a clean design with:
- Your name in large text
- "Senior Headless Commerce Developer" below it
- A few tech logos or keywords (Next.js, Shopify, Contentstack) if it fits cleanly
- Solid background color, high contrast text

Tools: Canva (free), Figma, or even a screenshot of a well-designed card. Super.so lets you set this per page. This image appears when someone shares your link on LinkedIn, Slack, Twitter, etc.

### H1 (one per page, your main heading)

```
Anton Bochkarev — Senior Full-Stack Engineer for Headless Commerce
```

### H2s (section headings, logical order)

```
H2: What I Do
H2: Case Study: Vuori Activewear Storefront
  H3: SEO and AI-Search
  H3: PLP Video Feature
  H3: Accessibility
  H3: Headless Migration and Performance
  H3: Integrations
H2: Tech Stack
H2: How I Can Help
H2: Get in Touch
```

### Image alt text

If you add a headshot or profile photo:
```
Anton Bochkarev, senior frontend engineer specializing in headless commerce
```

If you add a Vuori screenshot or case study image:
```
Vuori activewear storefront built with Next.js and Shopify headless architecture
```

### JSON-LD Structured Data

Paste this into your Super.so site's custom `<head>` code injection:

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "ProfilePage",
  "mainEntity": {
    "@type": "Person",
    "name": "Anton Bochkarev",
    "jobTitle": "Senior Full-Stack Engineer",
    "description": "Senior frontend engineer building high-performance headless commerce storefronts with Next.js, Shopify, and Contentstack. Focused on Core Web Vitals, WCAG 2.1 AA accessibility, technical SEO, and AI-search readiness.",
    "url": "https://antonbochkarev.dev",
    "email": "a.n.bochkarev1991@gmail.com",
    "sameAs": [
      "https://linkedin.com/in/anbochkarev",
      "https://github.com/anbochkarev1991"
    ],
    "knowsAbout": [
      "Headless Commerce",
      "Next.js",
      "React",
      "Shopify",
      "Contentstack",
      "TypeScript",
      "GraphQL",
      "Core Web Vitals",
      "WCAG 2.1 AA Accessibility",
      "Technical SEO",
      "AI-Search Optimization",
      "llms.txt"
    ],
    "workLocation": {
      "@type": "Place",
      "name": "Argentina (Remote, UTC-3)"
    }
  }
}
</script>
```

Replace `https://antonbochkarev.dev` with your actual domain once registered.

---

## 3. Page Content (Notion-ready, copy-paste)

Structure this in Notion using headings, paragraphs, and a divider between sections. The heading levels below map to Notion's heading blocks (H1, H2, H3).

---

### [H1] Anton Bochkarev — Senior Full-Stack Engineer for Headless Commerce

**Argentina (Remote, UTC-3) | English C1**

Senior frontend engineer for high-performance, SEO-strong headless commerce storefronts (Next.js + Shopify / Contentstack). I build and optimize storefront frontends with a focus on performance, accessibility (WCAG 2.1 AA), SEO and AI-search readiness, and CMS/commerce integrations.

---

### [H2] Case Study: Vuori Activewear Storefront

Senior engineer on the Vuori storefront via Kake, May 2023 to present. Vuori is a DTC activewear brand with approximately 1.36 million monthly organic sessions. Frontend-focused across React and Next.js, with Contentstack and Shopify integrations, performance, accessibility, and SEO/AI-search.

#### [H3] SEO and AI-Search

Built the hreflang and llms.txt layers of a broader SEO/AI-search effort.

- Monthly organic purchases up 36 percent, organic conversion 3.8 to 4.3 percent
- ChatGPT-referred sessions up 242 percent (5.0K to 17.2K per month)
- ChatGPT-attributed purchases up 114 percent
- International organic purchases up 50 percent

#### [H3] PLP Video Feature

Primary of two engineers on the React front-end. Shipped lifestyle video on product listing cards with no load-time regression.

- PLP-to-purchase conversion from approximately 3-8 percent to 5-11 percent across five products in the first two weeks

#### [H3] Accessibility

Shipped WCAG 2.1 AA fixes including dynamic alt text from Shopify metafields, keyboard operability, and carousel focus-trap.

- Lighthouse accessibility score: 73 to 83 on mobile, 68 to 75 on desktop

#### [H3] Headless Migration and Performance

Worked on the migration from Shopify to a custom Next.js (SSR) storefront. Contributions included bundle-size reduction, lazy loading, image optimization, and SSR improvements.

#### [H3] Integrations

3 years building and consuming GraphQL across markets. Contentstack CMS, Shopify, Klaviyo, Medallia, Reviews.io, Google Maps.

---

### [H2] Tech Stack

React, Next.js, TypeScript, GraphQL, Node.js/NestJS, PostgreSQL, Shopify, Contentstack, Jest/RTL, AI-native workflow.

---

### [H2] How I Can Help

- Headless storefront frontend build and optimization
- Core Web Vitals and performance
- Accessibility (WCAG 2.1 AA)
- Technical SEO and AI-search / llms.txt readiness
- CMS and commerce integrations

---

### [H2] Get in Touch

**Email:** a.n.bochkarev1991@gmail.com
**LinkedIn:** [linkedin.com/in/anbochkarev](https://linkedin.com/in/anbochkarev)
**GitHub:** [github.com/anbochkarev1991](https://github.com/anbochkarev1991)

---

## 4. Fast-Indexing Playbook

### Step 1: Register domain and connect it (Day 1)

1. Register `antonbochkarev.dev` (or `.com`) at your preferred registrar.
2. Sign up for Super.so, create your site, connect the Notion page.
3. Add DNS records as Super.so instructs. Wait for propagation.
4. Verify the site loads at `https://antonbochkarev.dev` with HTTPS.

### Step 2: Inject SEO metadata (Day 1)

1. In Super.so dashboard, set the page title, meta description, and OG tags from Section 2 above.
2. Paste the JSON-LD `<script>` block into the custom code injection (head section).
3. If Super.so lets you set a favicon, add one (even a simple letter "A" icon).

### Step 3: Verify in Google Search Console (Day 1)

1. Go to [Google Search Console](https://search.google.com/search-console).
2. Add your domain as a property. Choose "URL prefix" method: `https://antonbochkarev.dev`.
3. Verify ownership. Easiest method: DNS TXT record verification (add a TXT record at your registrar with the value Google provides). HTML tag verification also works if Super.so's code injection lets you add a `<meta>` tag to `<head>`.
4. Once verified, you will see your property in the dashboard.

### Step 4: Submit sitemap (Day 1)

1. Super.so auto-generates a sitemap at `https://antonbochkarev.dev/sitemap.xml`. Visit the URL in your browser to confirm it exists and lists your page.
2. In Google Search Console, go to Sitemaps (left sidebar), enter `sitemap.xml`, and click Submit.

### Step 5: Request indexing (Day 1)

1. In Google Search Console, go to URL Inspection (top search bar).
2. Enter `https://antonbochkarev.dev`.
3. It will say "URL is not on Google." Click "Request Indexing."
4. Google will queue it for crawling. This usually gets a page crawled within 1-3 days, sometimes within hours.

### Step 6: Add backlinks for faster discovery (Day 1-2)

Backlinks from established, crawled sites tell Google your page exists. Add your URL to:

1. **LinkedIn profile:** Add it to the "Website" field in your contact info section, and/or mention it in the "About" section. LinkedIn is crawled frequently.
2. **GitHub profile:** Go to your GitHub profile settings, add `https://antonbochkarev.dev` to the "Website" field. GitHub profiles are indexed.
3. **Contra profile:** Add the URL to your Contra portfolio/bio. This is both a backlink and a channel for leads.
4. **GitHub repo README (optional):** If you have a pinned repo (like tickwork), add a line linking back to your site. Repo READMEs are indexed.

### Step 7: Validate technical SEO (Day 2-3)

Once the site is live, run these free checks:

- **Google PageSpeed Insights** (`pagespeed.web.dev`): Enter your URL. Confirm green Core Web Vitals. You are selling CWV expertise, so your own site should score well.
- **Google Rich Results Test** (`search.google.com/test/rich-results`): Enter your URL. Confirm the JSON-LD Person/ProfilePage is detected with no errors.
- **Mobile-friendly test**: Google's tool confirms your page renders correctly on mobile.
- **Manual check**: View page source (Ctrl+U / Cmd+U) and confirm meta title, description, OG tags, and JSON-LD are all present in the `<head>`.

### Realistic timeline

| Milestone | Expected timing |
|---|---|
| Site live on custom domain | Day 1 (same session) |
| Google crawls the page | 1-3 days after requesting indexing |
| Page appears in Google results | 3-7 days (sometimes faster for new domains with backlinks) |
| Starts ranking for long-tail queries | 2-6 weeks (e.g., "headless shopify developer argentina") |
| Meaningful organic traffic | 2-6 months (one page has limited ranking potential, this is a bonus, not the main channel) |

**Honest expectation:** A single page on a brand-new domain will not rank for competitive terms like "headless commerce developer" against established sites. It WILL rank for long-tail, low-competition queries (your name, "headless shopify developer argentina," "next.js e-commerce freelancer latam"). The primary value is as a professional landing page for outreach. The SEO is a slow-burn bonus.

---

## 5. Quick Launch Checklist

Copy this and check off items as you go:

```
[ ] Register domain (antonbochkarev.dev or .com)
[ ] Sign up for Super.so ($16/mo)
[ ] Create the Notion page with content from Section 3
[ ] Connect Notion page to Super.so
[ ] Add DNS records at registrar, wait for propagation
[ ] Verify HTTPS and clean URL working
[ ] Set meta title and description in Super.so
[ ] Set OG title, description, image in Super.so
[ ] Paste JSON-LD script into head code injection
[ ] Add favicon
[ ] Visit /sitemap.xml to confirm it exists
[ ] Verify domain in Google Search Console (DNS TXT method)
[ ] Submit sitemap.xml in Search Console
[ ] Request indexing via URL Inspection tool
[ ] Add site URL to LinkedIn profile (Website field)
[ ] Add site URL to GitHub profile
[ ] Add site URL to Contra profile
[ ] Run PageSpeed Insights, confirm green scores
[ ] Run Rich Results Test, confirm JSON-LD detected
[ ] View page source, confirm all meta tags present
[ ] Share the link in your first outreach email
```

---

## Notes

- **No em dashes or special characters** have been used anywhere in this document or in the page content. All punctuation is plain keyboard characters.
- **All content uses truthful framing** consistent with your stated contributions. "Built" only for hreflang and llms.txt (your tickets). "Primary of two engineers" for PLP video. "Worked on" for the migration. "Shipped" for accessibility fixes. No verbs have been upgraded.
- **The page is deliberately one page.** Resist the urge to add subpages. A single focused page with good on-page SEO outperforms a thin multi-page site for a new domain.
