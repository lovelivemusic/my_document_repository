# Image Examples

This document tests every image inclusion pattern that GITMD2PDF should support.

---

## 1. Relative Path — PNG Images

### Basic Image

![Blue sample banner](../images/sample-blue.png)

### Image with Alt Text Only (no title)

![Green sample banner](../images/sample-green.png)

### Image with Title Attribute

![Logo placeholder](../images/logo-placeholder.png "Company Logo Placeholder")

---

## 2. Relative Path — SVG Images

### Pipeline Diagram (SVG)

![GITMD2PDF conversion pipeline](../images/diagram-pipeline.svg)

*Figure 1: The Markdown-to-PDF conversion pipeline*

### Architecture Diagram (SVG)

![System architecture overview](../images/architecture.svg)

*Figure 2: GITMD2PDF internal architecture*

---

## 3. Images in Context

Below is a paragraph followed by an image, followed by another paragraph. The PDF should lay these out naturally with appropriate spacing.

The GITMD2PDF tool processes Markdown files from a Git repository and produces professionally formatted PDF documents. The pipeline diagram below illustrates the high-level flow:

![Pipeline overview](../images/diagram-pipeline.svg)

After conversion, the resulting PDF can be distributed to stakeholders, embedded in documentation portals, or archived for compliance purposes.

---

## 4. Multiple Images in Sequence

These images should appear one after another with consistent spacing:

![Blue banner](../images/sample-blue.png)

![Green banner](../images/sample-green.png)

![Logo](../images/logo-placeholder.png)

---

## 5. Image Inside a Table

| Feature   | Preview                                      | Status   |
|-----------|----------------------------------------------|----------|
| Pipeline  | ![pipeline](../images/diagram-pipeline.svg)  | Complete |
| Blue      | ![blue](../images/sample-blue.png)           | Complete |

---

## 6. Image Inside a List

- Project documentation:
  - Pipeline: ![pipeline](../images/diagram-pipeline.svg)
- Brand assets:
  - Logo: ![logo](../images/logo-placeholder.png)

---

## 7. Image Inside a Blockquote

> The architecture diagram below shows how the system components interact:
>
> ![Architecture](../images/architecture.svg)
>
> — *From the GITMD2PDF technical specification*

---

## 8. Linked Image (Image as a Clickable Link)

[![Click this pipeline diagram to visit the project](../images/diagram-pipeline.svg)](https://example.com)

---

## 9. Image with Missing File (Alt Text Fallback)

The following image references a file that does not exist. The PDF should display the alt text gracefully:

![This image does not exist — alt text should appear](../images/nonexistent-image.png)

---

## 10. Side-by-Side Reference (Using a Table)

| Before | After |
|--------|-------|
| ![Blue](../images/sample-blue.png) | ![Green](../images/sample-green.png) |

---

*This document is part of the GITMD2PDF test repository.*
