# Test Plan — GITMD2PDF Conversion Validation

## 1. Introduction

This test plan defines the strategy for validating **GITMD2PDF**, a tool that converts Git-flavoured Markdown files into professionally formatted PDF documents.

### 1.1 Purpose

Ensure that every supported Markdown element converts accurately, that multi-file repositories are handled correctly, and that the output PDFs meet quality standards for use as customer-facing documents.

### 1.2 Scope

| In Scope                                    | Out of Scope                        |
|---------------------------------------------|-------------------------------------|
| All standard Markdown elements              | LaTeX math rendering                |
| GitLab/GitHub-flavoured extensions          | Custom CSS theme testing            |
| Multi-file repo conversion                  | Performance benchmarking (> 1k files)|
| Table of contents generation                | Concurrent user load testing        |
| Relative link resolution                    | Mobile PDF viewer rendering         |

---

## 2. Test Strategy

### 2.1 Testing Levels

```
┌─────────────────────────────────────────────────────┐
│                   End-to-End Tests                    │
│  Full repo → PDF pipeline with visual verification   │
├─────────────────────────────────────────────────────┤
│                  Integration Tests                    │
│  Markdown parser + PDF renderer + link resolver      │
├─────────────────────────────────────────────────────┤
│                    Unit Tests                         │
│  Individual element parsers and formatters            │
└─────────────────────────────────────────────────────┘
```

### 2.2 Test Types

1. **Functional Testing** — Does each Markdown feature produce correct PDF output?
2. **Regression Testing** — Do fixes and new features break existing conversions?
3. **Boundary Testing** — How does the tool handle edge cases (empty files, huge tables, deeply nested lists)?
4. **Compatibility Testing** — Do output PDFs render correctly across viewers (Acrobat, Preview, Chrome, Firefox)?

### 2.3 Test Environment

| Component        | Version / Detail                  |
|------------------|-----------------------------------|
| OS               | macOS 14, Ubuntu 22.04, Windows 11|
| Node.js          | v22.x LTS                        |
| GITMD2PDF        | Latest `main` branch             |
| PDF Viewers      | Adobe Acrobat, macOS Preview, Chrome built-in |
| Git              | 2.43+                            |

---

## 3. Test Scenarios

### 3.1 Markdown Feature Matrix

Detailed test cases are documented in [Test Cases.md](Test%20Cases.md). Below is the high-level feature coverage:

| Category              | Elements                                              | Priority |
|-----------------------|-------------------------------------------------------|----------|
| **Block Elements**    | Headings, paragraphs, blockquotes, code blocks, lists | P0       |
| **Inline Elements**   | Bold, italic, strikethrough, code, links, images      | P0       |
| **Tables**            | Basic, aligned, wide, nested formatting               | P0       |
| **Extended Syntax**   | Task lists, footnotes, emoji, mermaid diagrams        | P1       |
| **Structural**        | Horizontal rules, page breaks, TOC generation         | P1       |
| **Cross-file**        | Relative links, image paths, repo-level TOC           | P1       |
| **Edge Cases**        | Empty files, special characters, very long lines       | P2       |

### 3.2 Repository Structure Tests

Verify that the following directory structure converts correctly:

```
repo/
├── README.md
├── Planning/
│   └── My Plan.md
├── Projects/
│   ├── Project 1.md
│   ├── Project 2.md
│   └── Project 3.md
├── Testing/
│   ├── Test Cases.md
│   └── Test plan.md
├── Examples/
│   ├── Formatting Showcase.md
│   └── Edge Cases.md
└── Reports/
    └── Monthly Status.md
```

**Checks:**

- [ ] All files included in output
- [ ] Table of contents reflects folder structure
- [ ] Relative links between files resolve correctly
- [ ] File ordering matches directory traversal
- [ ] Empty directories are ignored gracefully

---

## 4. Entry & Exit Criteria

### Entry Criteria

- [ ] All Markdown files committed to the repository
- [ ] GITMD2PDF tool installed and configured
- [ ] Test environment matches specification in section 2.3
- [ ] Baseline PDF output generated for comparison

### Exit Criteria

- [ ] All P0 test cases pass
- [ ] No critical or high-severity defects remain open
- [ ] P1 test cases have at least 90% pass rate
- [ ] Output PDF reviewed and approved by at least one stakeholder
- [ ] Test summary report published

---

## 5. Defect Classification

| Severity    | Definition                                              | Example                                    |
|-------------|----------------------------------------------------------|-------------------------------------------|
| Critical    | Content is missing or unreadable                        | Entire section not rendered                |
| High        | Feature renders incorrectly, affecting comprehension    | Table columns misaligned                   |
| Medium      | Cosmetic issue that doesn't block understanding         | Extra whitespace around headings           |
| Low         | Minor polish item                                       | Font size slightly off for H6              |

---

## 6. Risks

> **Risk:** Mermaid diagrams require a headless browser for rendering, which may not be available in all CI environments.
>
> **Mitigation:** Provide fallback to code-block rendering with a note in the PDF.

> **Risk:** Large repositories (100+ files) may produce PDFs exceeding 200 pages.
>
> **Mitigation:** Test with pagination and configurable file inclusion/exclusion.

---

## 7. Schedule

| Phase                   | Start Date  | End Date    | Owner          |
|-------------------------|-------------|-------------|----------------|
| Test plan review        | 2026-03-01  | 2026-03-05  | Tomas Andersen |
| Test case authoring     | 2026-03-06  | 2026-03-15  | Full QA team   |
| Test execution Round 1  | 2026-03-16  | 2026-03-25  | Tomas Andersen |
| Defect triage           | 2026-03-26  | 2026-03-28  | Jane Smith     |
| Test execution Round 2  | 2026-03-29  | 2026-04-05  | Full QA team   |
| Sign-off                | 2026-04-06  | 2026-04-08  | Stakeholders   |

---

## 8. Approvals

| Role               | Name            | Date       | Signature |
|--------------------|-----------------|------------|-----------|
| QA Lead            | Tomas Andersen  | 2026-03-05 | _pending_ |
| Project Lead       | Jane Smith      | 2026-03-05 | _pending_ |
| Engineering Lead   | Carlos Rivera   | 2026-03-05 | _pending_ |

---

*Last updated: 2026-03-25*
