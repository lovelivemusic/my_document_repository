# My Plan — Q2 2026 Roadmap

## Vision

Deliver a **unified digital platform** that consolidates the website, blog, and API docs into a cohesive experience — on time and within budget.

---

## Strategic Pillars

| #  | Pillar                   | Description                                                  |
|----|--------------------------|--------------------------------------------------------------|
| 1  | **Performance**          | Sub-second page loads, optimised assets, edge caching        |
| 2  | **Developer Experience** | Markdown-first workflows, CI/CD automation, self-serve docs  |
| 3  | **Accessibility**        | WCAG 2.1 AA compliance across all public surfaces            |
| 4  | **Security**             | Static-first architecture, minimal attack surface            |

---

## Quarterly Objectives & Key Results

### OKR 1 — Launch the Redesigned Website

| Key Result                                     | Target  | Current | Status |
|------------------------------------------------|---------|---------|--------|
| Lighthouse performance score                   | ≥ 95    | 88      | Behind |
| Pages converted to new design system           | 100%    | 65%     | Behind |
| Accessibility issues (critical)                | 0       | 3       | At Risk|
| Time to first contentful paint                 | < 1.2s  | 1.8s    | At Risk|

### OKR 2 — Complete Blog Migration

| Key Result                                     | Target  | Current | Status |
|------------------------------------------------|---------|---------|--------|
| Posts migrated and validated                   | 298     | 210     | Behind |
| Broken links after migration                   | 0       | —       | Not Started |
| Organic traffic retained (30-day post-launch)  | ≥ 95%   | —       | Not Started |

### OKR 3 — Ship API Documentation Portal

| Key Result                                     | Target  | Current | Status |
|------------------------------------------------|---------|---------|--------|
| APIs fully documented                          | 5 / 5   | 2 / 5   | At Risk|
| Internal NPS for portal                        | ≥ 40    | —       | Not Started |
| Average search latency                         | < 200ms | —       | Not Started |

---

## Timeline

```
        January    February    March      April       May        June
           │          │          │          │          │          │
Website    ├──Design──┤          │          │          │          │
           │          ├──Build───┤──QA──┤   │          │          │
           │          │          │      ├──Launch──┤   │          │
           │          │          │          │          │          │
Blog       │  ├─Export─┤─Convert─┤          │          │          │
           │          │          ├──Test──┤──Cutover─┤  │          │
           │          │          │          │          │          │
API Docs   │          │  ├─Spec──┤──Build──┤          │          │
           │          │          │          ├──Launch──┤          │
```

---

## Resource Allocation

### Team Capacity

| Team Member    | Website | Blog | API Docs | Available Hours/Week |
|----------------|:-------:|:----:|:--------:|---------------------:|
| Jane Smith     |   60%   |  20% |   20%    |                   40 |
| Carlos Rivera  |   80%   |  10% |   10%    |                   40 |
| Aisha Patel    |   50%   |  30% |   20%    |                   32 |
| Tomás Andersen |   30%   |  30% |   40%    |                   40 |
| Sarah Chen     |   10%   |  70% |   20%    |                   36 |

### Budget Summary

| Category           | Allocated  | Spent      | Remaining  |
|--------------------|------------|------------|------------|
| Tooling & Licences | $5,000     | $2,100     | $2,900     |
| Infrastructure     | $3,000     | $800       | $2,200     |
| Contractors        | $15,000    | $6,500     | $8,500     |
| Contingency        | $2,000     | $0         | $2,000     |
| **Total**          | **$25,000**| **$9,400** |**$15,600** |

---

## Dependencies

The brand guidelines must be finalised before the website redesign can proceed. The website's shared header/footer components are needed by the blog theme. The API docs portal theme also depends on the website design system. Both the blog migration and API docs portal must be complete before the full platform launch.

---

## Decision Log

| Date       | Decision                                                 | Rationale                                    |
|------------|----------------------------------------------------------|----------------------------------------------|
| 2026-01-08 | Use Next.js over Astro for the website                   | Better Vercel integration, larger ecosystem  |
| 2026-01-22 | Choose Hugo over Gatsby for the blog                     | Faster builds, Go templating, no JS runtime  |
| 2026-02-05 | Hybrid Redocly + Swagger UI for API docs                 | Cost optimisation for internal vs. external  |
| 2026-02-18 | Defer i18n to Q3                                         | Reduces scope risk; current traffic is 94% EN|
| 2026-03-01 | Adopt Pagefind for blog search                           | No server needed, < 50kB client bundle       |

---

## Risks & Mitigations

1. **Scope creep** — Strict change-request process; anything not in this plan goes to the backlog
2. **Key-person dependency** — Cross-training sessions scheduled bi-weekly
3. **Vendor lock-in** — All content stored in Git as Markdown; hosting is swappable
4. **Timeline slip** — Two-week buffer built into each milestone

---

## Communication Cadence

| Meeting                | Frequency | Attendees             | Purpose                        |
|------------------------|-----------|-----------------------|--------------------------------|
| Sprint Planning        | Bi-weekly | Full team             | Scope and assign work          |
| Design Sync            | Weekly    | Jane, Aisha, Carlos   | Review UI/UX progress          |
| Stakeholder Update     | Monthly   | Team leads + execs    | Status, risks, decisions       |
| Retrospective          | Bi-weekly | Full team             | Process improvement            |

---

*Last updated: 2026-03-12*
