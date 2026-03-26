# Project 2 — Blog Platform Migration

## Summary

Migrate the existing WordPress blog to a **static-site generator** to improve security, reduce hosting costs, and integrate with the new website (see [Project 1](Project%201.md)).

---

## Objectives

- Zero downtime during the cutover
- Preserve all existing URLs (301 redirects where necessary)
- Maintain full-text search capability
- Support for Markdown-based authoring workflow

## Current vs. Future State

| Aspect            | Current (WordPress)        | Future (Hugo + Netlify)       |
|-------------------|----------------------------|-------------------------------|
| Hosting cost      | $45/month                  | $0 (free tier)                |
| Build time        | N/A (dynamic)              | ~12 seconds                   |
| Security surface  | PHP + MySQL + plugins      | Static HTML only              |
| Content format    | WYSIWYG (Gutenberg)        | Markdown + frontmatter        |
| Search            | Built-in DB queries        | Pagefind (client-side)        |

---

## Migration Checklist

1. **Export** all posts from WordPress using `wp-cli`
2. **Convert** HTML content to Markdown with `turndown`
3. **Map** categories and tags to Hugo taxonomies
4. **Validate** each post renders correctly
5. **Set up** Netlify deployment pipeline
6. **Configure** DNS and SSL certificates
7. **Redirect** old URLs via `_redirects` file
8. **Decommission** WordPress server

### Sample Frontmatter

```markdown
---
title: "Understanding Markdown for Technical Writing"
date: 2026-02-20
author: Sarah Chen
tags: [markdown, writing, documentation]
categories: [Tutorials]
draft: false
---
```

### Sample Redirect Rules

```text
# Old WordPress paths → New Hugo paths
/wp-content/uploads/*  /images/:splat  301
/category/:slug        /tags/:slug     301
/?p=:id                /posts/:id      301
```

---

## Content Statistics

| Metric                  | Count  |
|-------------------------|-------:|
| Total posts             |    342 |
| Published               |    298 |
| Drafts                  |     44 |
| Categories              |     12 |
| Tags                    |     87 |
| Embedded images         |  1,204 |
| Average word count      |    850 |

## Timeline

```
Jan ──── Feb ──── Mar ──── Apr
 │        │        │        │
 ▼        ▼        ▼        ▼
Export   Convert  Testing  Launch
& Audit  & Build  & QA     & Cutover
```

---

## Risks & Dependencies

> **Note:** This project depends on [Project 1](Project%201.md) completing the shared header/footer components before the blog theme can be finalised.

- **Risk:** Some legacy posts contain custom shortcodes that have no Markdown equivalent
  - *Mitigation:* Build Hugo shortcode equivalents for the top 10 most-used patterns
- **Risk:** SEO ranking drop during migration
  - *Mitigation:* Comprehensive redirect map + Search Console monitoring for 30 days post-launch

## Approvals

- [x] Content team sign-off
- [x] SEO review complete
- [ ] Security review
- [ ] Final go/no-go from stakeholders

---

*Last updated: 2026-03-10*
