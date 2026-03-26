# Project 1 — Website Redesign

## Overview

The **Website Redesign** project aims to modernise the company's public-facing site, improving performance, accessibility, and visual consistency across all devices.

| Attribute       | Detail                        |
|-----------------|-------------------------------|
| **Status**      | In Progress                   |
| **Lead**        | Jane Smith                    |
| **Start Date**  | 2026-01-15                    |
| **Target Date** | 2026-06-30                    |
| **Priority**    | High                          |

---

## Goals

1. Achieve a Lighthouse score of **95+** across all pages
2. Reduce average page load time to under **1.5 seconds**
3. Meet WCAG 2.1 AA accessibility standards
4. Unify the design language with the new brand guidelines

## Scope

### In Scope

- Homepage, About, Contact, and Product pages
- Responsive layouts (mobile, tablet, desktop)
- Dark mode support
- SEO metadata and structured data

### Out of Scope

- Blog migration (handled by [Project 2](Project%202.md))
- E-commerce checkout flow
- Internationalisation (i18n)

---

## Technical Stack

```yaml
frontend:
  framework: Next.js 14
  styling: Tailwind CSS 4.0
  testing: Playwright + Vitest
hosting:
  provider: Vercel
  cdn: Cloudflare
analytics:
  tool: Plausible
```

## Architecture Diagram

```
┌────────────┐     ┌───────────┐     ┌────────────┐
│   Browser   │────▶│  Vercel    │────▶│  API Layer │
│  (Next.js)  │◀────│  Edge CDN  │◀────│  (Node.js) │
└────────────┘     └───────────┘     └────────────┘
                                           │
                                     ┌─────▼─────┐
                                     │ PostgreSQL │
                                     └───────────┘
```

---

## Milestones

- [x] Design mockups approved
- [x] Component library scaffolded
- [ ] Homepage build complete
- [ ] Internal QA pass
- [ ] Accessibility audit
- [ ] Staging deployment
- [ ] Production launch

## Risk Register

| Risk                          | Likelihood | Impact | Mitigation                          |
|-------------------------------|:----------:|:------:|-------------------------------------|
| Scope creep from stakeholders | High       | Medium | Strict change-request process       |
| Third-party API downtime      | Medium     | High   | Circuit breaker + fallback UI       |
| Design–dev misalignment       | Low        | Medium | Weekly design sync meetings         |
| Performance regression        | Medium     | High   | Automated Lighthouse CI checks      |

## Team

| Name           | Role               | Contact                       |
|----------------|--------------------|------------------------------ |
| Jane Smith     | Project Lead       | jane.smith@example.com        |
| Carlos Rivera  | Frontend Engineer  | carlos.r@example.com          |
| Aisha Patel    | UI/UX Designer     | aisha.p@example.com           |
| Tomás Andersen | QA Engineer        | tomas.a@example.com           |

---

## Notes

> **Decision Log — 2026-02-10**
> After benchmarking Astro, Remix, and Next.js, the team chose **Next.js 14** for its mature ecosystem, built-in image optimisation, and seamless Vercel integration.

### Useful Links

- [Figma Design File](https://figma.com/example)
- [Brand Guidelines PDF](https://example.com/brand.pdf)
- [Lighthouse CI Docs](https://github.com/GoogleChrome/lighthouse-ci)

---

*Last updated: 2026-03-15*
