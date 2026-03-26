# Monthly Status Report — March 2026

**Prepared by:** Jane Smith, Project Lead
**Date:** 2026-03-25
**Period:** 1 March – 25 March 2026

---

## Executive Summary

March saw strong progress on the **Website Redesign** (Project 1), with the homepage and three key landing pages reaching feature-complete status. The **Blog Migration** (Project 2) is tracking slightly behind schedule due to complexities with legacy shortcode conversion. The **API Documentation Portal** (Project 3) completed its spec-gathering phase and build work has begun.

Overall programme health: **On Track** with minor risks.

---

## Project Status Overview

| Project                    | Status      | Progress | Trend     | Risk Level |
|----------------------------|-------------|:--------:|-----------|------------|
| Website Redesign           | In Progress |   65%    | Improving | Low        |
| Blog Migration             | In Progress |   45%    | Steady    | Medium     |
| API Documentation Portal   | In Progress |   30%    | Improving | Low        |

---

## Project 1 — Website Redesign

### Accomplishments This Month

- Homepage build complete and deployed to staging
- Product page template finalised with responsive breakpoints
- Lighthouse CI integrated into GitLab pipeline
- Accessibility audit started (3 critical issues identified, 2 resolved)

### Key Metrics

| Metric                          | Target  | Actual  | Delta   |
|---------------------------------|---------|---------|---------|
| Lighthouse Performance          | 95      | 88      | -7      |
| Pages on new design system      | 12      | 8       | -4      |
| Critical accessibility issues   | 0       | 1       | -1      |
| Average page load (staging)     | 1.2s    | 1.8s    | +0.6s   |

### Next Steps

1. Complete remaining 4 page conversions
2. Resolve final critical accessibility issue (colour contrast on CTAs)
3. Performance optimisation sprint (image lazy-loading, font subsetting)
4. Begin internal UAT with 5 team members

---

## Project 2 — Blog Migration

### Accomplishments This Month

- 210 of 298 posts successfully converted to Markdown
- Hugo theme integrated with new website header/footer
- Pagefind search deployed to staging (< 150ms response time)
- Redirect mapping complete for all published URLs

### Challenges

> **Shortcode Complexity:** 34 legacy posts use custom WordPress shortcodes (`[gallery]`, `[accordion]`, `[tabs]`) that required hand-built Hugo equivalents. This added approximately **1.5 weeks** to the timeline.

### Content Migration Progress

```
Total Posts:  298
Converted:    ████████████████████░░░░░░░░░░  210 (70%)
Validated:    ██████████████░░░░░░░░░░░░░░░░  145 (49%)
Remaining:    ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░   88 (30%)
```

### Next Steps

1. Complete remaining 88 post conversions
2. Full QA pass on all 298 posts (visual comparison with WordPress)
3. DNS cutover plan review with infrastructure team
4. 301 redirect testing in staging environment

---

## Project 3 — API Documentation Portal

### Accomplishments This Month

- OpenAPI spec reviews completed for Users API and Analytics API
- Redocly licence procured and configured
- Swagger UI theme customised to match brand guidelines
- CI pipeline scaffolded (build on push to `docs/**` paths)

### API Documentation Status

| API               | Spec Complete | Docs Generated | Reviewed |
|-------------------|:------------:|:--------------:|:--------:|
| Users API         |      Yes     |      Yes       |   Yes    |
| Payments API      |      Yes     |      Yes       |   No     |
| Analytics API     |      Yes     |      Yes       |   Yes    |
| Notifications API |      No      |      No        |   No     |
| Inventory API     |      No      |      No        |   No     |

### Next Steps

1. Complete Notifications API and Inventory API specs
2. Deploy portal to internal staging URL
3. Begin engineering team beta programme (target: 15 users)
4. Gather feedback via internal survey

---

## Budget Update

| Category           | Q2 Budget  | Spent to Date | Remaining  | Burn Rate |
|--------------------|------------|---------------|------------|-----------|
| Tooling & Licences | $5,000     | $2,100        | $2,900     | 42%       |
| Infrastructure     | $3,000     | $800          | $2,200     | 27%       |
| Contractors        | $15,000    | $6,500        | $8,500     | 43%       |
| Contingency        | $2,000     | $0            | $2,000     | 0%        |
| **Total**          | **$25,000**| **$9,400**    |**$15,600** | **38%**   |

Budget is tracking within expectations. No overruns anticipated.

---

## Risks & Issues

| # | Type  | Description                                          | Impact | Likelihood | Owner          | Status |
|---|-------|------------------------------------------------------|--------|------------|----------------|--------|
| 1 | Risk  | Blog shortcode conversion delays                    | Medium | Confirmed  | Sarah Chen     | Mitigating |
| 2 | Risk  | Performance targets not met before April launch      | High   | Medium     | Carlos Rivera  | Monitoring |
| 3 | Issue | Aisha on reduced hours (32h/wk) through April       | Low    | Confirmed  | Jane Smith     | Accepted |
| 4 | Risk  | Notifications API team unresponsive to spec requests | Medium | High       | Tomas Andersen | Escalated |

---

## Team Highlights

- **Carlos Rivera** implemented automated Lighthouse CI — catches performance regressions before merge
- **Sarah Chen** built 8 custom Hugo shortcodes to match legacy WordPress functionality
- **Aisha Patel** completed the accessibility audit toolkit and documented all findings
- **Tomas Andersen** wrote 13 end-to-end test cases for the GITMD2PDF conversion pipeline

---

## Decisions Made This Month

| Date       | Decision                                  | Decided By     | Impact                              |
|------------|-------------------------------------------|----------------|-------------------------------------|
| 2026-03-01 | Adopt Pagefind for blog search            | Jane + Sarah   | Eliminates server-side search costs |
| 2026-03-08 | Defer i18n to Q3                          | Stakeholders   | Reduces Q2 scope by ~15%           |
| 2026-03-15 | Use Redocly for external API docs         | Carlos + Tomas | $1,200/quarter licence cost        |
| 2026-03-20 | Extend blog migration deadline by 1 week  | Jane           | New target: April 15               |

---

## Next Month Preview (April 2026)

- [ ] Website: Production launch (target April 10)
- [ ] Blog: Complete QA and DNS cutover (target April 15)
- [ ] API Docs: Internal beta launch (target April 20)
- [ ] Retrospective for all three projects
- [ ] Q2 mid-quarter stakeholder presentation

---

*Next report due: 2026-04-25*
