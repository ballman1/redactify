# LegalRedact

Secure browser-based document redaction tool for legal intake. Built for business owners uploading lawsuits and demand letters.

## Privacy model

> **Your original document never leaves your browser.** Only the redacted version you approve is submitted.

All processing runs client-side:
- PDF text extraction via PDF.js 3.x
- Scanned PDF / phone-scan image extraction (raw JPEG byte parsing + Tesseract OCR)
- DOCX extraction via Mammoth.js
- Three-layer detection: regex · NER (compromise.js) · custom dictionary
- User review and label editing before any submission

## Detection layers

| Layer | Engine | Catches |
|---|---|---|
| Regex | Built-in | SSN, EIN, CC, phone, email, IP, URL, dates, amounts, case numbers, policy numbers, bar numbers |
| Legal dictionary | Built-in | Courts, law firms, attorneys, named parties |
| NER | compromise.js | People, organizations, places |
| Custom | User-defined | Matter-specific names, businesses, employees |

## Deployment

Hosted on Cloudflare Pages. Single static HTML file — no build step, no server, no database.

## Sprint history

- **Sprint 1** — File extraction pipeline + regex detection + review UI
- **Sprint 2** — NER layer + legal dictionary + custom dictionary UI + confidence scores + label editing + redacted PDF output + audit record
- **Sprint 3** — Submission flow + RBAC intake dashboard + confirmation numbers + submission history + animated progress

## Stack

PDF.js · Mammoth.js · Tesseract.js · compromise.js · jsPDF · Cloudflare Pages
