---
name: Offer-skills
description: Create privacy-safe editable Chinese resume HTML and PDF files, or a browser-based job-application tracker, from DOCX, pasted text, JSON, screenshots, or an existing resume. Use for polished one-page or two-page layouts, flexible paper sizes, shared left alignment, blue section bands, photo replacement, browser editing, application status tracking, and print-to-PDF export.
---

# Offer Skills

Create reusable Chinese resume HTML files with a restrained visual system, reliable spacing, browser editing, and PDF export. Start from the user's resume information, select one of the numbered HTML templates when appropriate, and generate a finished HTML resume; do not deliver Word templates as the reusable resource.

## Privacy boundary

- Keep real personal data only in task-local working files and the requested final resume.
- Never place the user's names, phone numbers, emails, employers, project URLs, photos, EXIF data, or source metadata in this skill, README, templates, examples, or ZIP package.
- The bundled examples use fictional content only. Replace it with the information provided by the user when generating a resume.
- Do not embed a real user photo in any asset. Replace the fictional photo slot only in the user's generated output.

## Resources

- Use `assets/resume-data-template.json` as the anonymous content schema.
- Use `assets/resume-template-editable.html` for a compact one-page editable resume.
- Use `assets/resume-template-two-page.html` for the two-page reference style with a first-page header and a continuation page.
- Use `assets/application-tracker.html` as a blank, standalone HTML tracker for autumn-recruitment applications. It supports date, company, position, status, next step, notes, search, filtering, local browser storage, CSV/JSON backup, and print-to-PDF.
- Read `references/email-monitoring.md` when the user wants browser-based email checking or a recurring daily progress check.
- Use `assets/template-overview.jpg` to compare the 18 numbered reference styles.
- Use the numbered HTML files under `assets/templates-html/` when the user asks for one of the 18 large-company minimalist styles. These are text-first HTML templates with inline CSS/JavaScript and one shared fictional photo asset; do not convert these resources back to DOCX or replace the text with screenshots.
- If the user uploads a resume screenshot or reference image, treat it as a visual layout reference: inspect its columns, spacing, typography, color hierarchy, photo placement, and page flow, then recreate the layout as editable HTML. A reference image may be used instead of selecting a numbered built-in template.

## Choose a layout

- Choose the one-page template for concise resumes with one or two education rows and a small number of experience bullets.
- Choose the two-page template when long experience, school activities, publications, or self-evaluation cannot fit without shrinking the body text.
- Keep page size configurable. Default to A4 (`210mm × 297mm`); support Letter (`216mm × 279mm`) or a custom size by changing both `@page size` and the `--page-width` / `--page-height` variables in the selected template.
- Keep each `.resume-page` as an explicit page. Do not let a long first page silently push continuation content into an accidental third page.

## Build workflow

### 1. Collect and normalize the user's content

- Ask the user for or extract the resume information: profile, education, work/experience, projects, school activities, awards, skills, self-evaluation, and photo.
- Accept pasted text, JSON, DOCX content, or an existing HTML resume as input, but make the reusable and final generated template HTML.
- Preserve wording unless the user requests rewriting, deletion, or anonymization.
- Remove Word-only zero-width characters, duplicate fallback text, and drawing objects that have no visible content.
- Map content to `profile`, `education`, `experience`, `projects`, `school`, `skills`, and optional `self_evaluation` fields in the JSON template.

### 2. Select and generate the HTML template

- Use the overview image and numbered HTML files to select a visual style based on content density, desired page count, and whether the user wants a photo header, dense single page, or two-page layout.
- Treat the 18 numbered files as genuinely different structures: single-column rules, full-width banner, left/right rail, timeline, cards, two-column, centered portfolio, monochrome academic, and modern two-page styles. Do not collapse them into a color-only variation.
- Copy the selected HTML and the shared `assets/fictional-resume-photo.png` to the output location, then replace the fictional sample text with the user's information.
- Keep all final content in the HTML; do not ask the user to edit a Word file or ship DOCX files from this skill.

### 3. Apply the visual system

- Use a shared `12mm` left baseline and a consistent content width derived from the page width.
- Use `#2F5597` for section rules, title bars, and selected emphasis; use a restrained light-gray fill for two-page section bands.
- Use Microsoft YaHei / 微软雅黑 with a Chinese sans-serif fallback. Use Times New Roman only for long English publication titles when needed.
- Keep the name around `22pt`, section titles around `15pt`, and body text around `9.5–10.5pt`.
- Use CSS grid for education and role rows; use a fixed marker column for bullets so wrapped lines align under the text.
- Keep the photo slot predictable. The two-page reference style places the photo on the left, the name and profile in the header, and a blue rule below the header.
- Reproduce the reference section band with a pale-gray full-width strip, two narrow blue marker bars, and a blue title block with white text.

### 4. Control spacing and page flow

- Use normal flow, grid, and flexbox for text. Use absolute positioning only for fixed decoration or a photo slot.
- Keep `2–3mm` between a section rule and its first row, and `4–6mm` between the final line of one section and the next section heading.
- Recalculate downstream sections after every content edit. Never allow wrapped text to overlap a later heading.
- Tighten repeated gaps before reducing font size. Shorten content only with user permission.
- For two-page documents, add an intentional page break after the first page and begin page two with a clean blue continuation rule.

### 5. Keep HTML editable

- Keep toolbar controls outside the resume page so they do not cover content and disappear in print.
- Provide `编辑` / `完成编辑`, `替换照片`, and `导出PDF` controls in editable outputs.
- Provide `字体`, `文字颜色`, and `加粗` controls. Apply them to the current text selection with browser editing commands while preserving the selection when the toolbar receives focus.
- Toggle `contenteditable` on the resume page for direct text editing. Keep `spellcheck` off for Chinese resume layouts.
- Read a selected image with `FileReader` and replace the photo slot with a data URL for the current browser session.
- Implement PDF export with `window.print()` and print CSS that hides the toolbar. Tell the user to choose “Save as PDF” in the browser print dialog.
- Keep the editable HTML standalone with inline CSS and JavaScript; do not rely on a web server for local use.

### 6. Verify

- Open the HTML in Chromium and test edit mode, photo replacement, toolbar placement, and print mode.
- Render the final PDF to PNG with Poppler or the bundled PDF runtime.
- Inspect every page for shared left alignment, rule spacing, clipping, missing Chinese glyphs, image placement, intentional page breaks, and bottom-margin safety.
- Confirm the expected page count and paper dimensions with PDF metadata. Use text extraction only as a secondary check.
- Deliver the requested HTML and optional PDF, not Word files, scratch screenshots, extracted XML, or personal source files.

## Track job applications

- When the user asks to organize application progress, copy `assets/application-tracker.html` to the requested output location instead of building a new tracker from scratch.
- When the user invokes this application-tracking capability, place the working HTML on the user's Desktop by default as `秋招投递进度.html` (resolve the actual Desktop path from the environment), and explicitly tell the user the saved path in the final response.
- Start with the blank tracker. If the user provides email text, screenshots, or portal pages, extract only the visible date, company, position, current status, next step, and useful notes; do not copy application IDs or unrelated personal details unless explicitly requested.
- Merge duplicate “application received” and “thank you for applying” messages for the same company and position. Preserve the latest confirmed status when later evidence is provided.
- Use the source wording for statuses when it is clear, such as `简历已投递`, `投递成功`, `新投递`, `简历筛选中`, `评估中`, `测评中`, `待笔试`, `拒绝`, and `已结束`. If the evidence is ambiguous, use `待确认` only after adding it to the status options or ask the user to confirm.
- Keep the tracker data in the generated output or the browser's local storage. Never write a user's real application history into this skill's bundled files, README, template examples, or ZIP package.
- Tell the user that the tracker can be edited directly in a browser, filtered by status, backed up as JSON/CSV, and printed or saved as PDF.

## Check email notifications

- When the user provides an email provider and the login email address, read `references/email-monitoring.md` and use the browser-control skill to inspect the provider's web mailbox. The account address identifies the mailbox; it is not a password.
- Ask the user to complete sign-in and any verification step in the selected browser when the mailbox is not already open. Do not request, store, or type passwords or verification codes on the user's behalf.
- Search only the mailbox views and messages needed for application progress. Extract sender, subject, date, company, position, and the visible progress signal; ignore advertisements and unrelated mail.
- Merge the result into the Desktop tracker, preserving the latest clearly confirmed status and adding the email date or source note when useful. Report which records were added or updated.
- If the user asks for daily checking, use the Codex automation tool to create or update a recurring daily monitor. Prefer a heartbeat automation, reuse an existing matching automation, and ask for a preferred check time if none is given. Never write raw automation directives or expose schedule syntax in the user-facing response.
- A scheduled run should open the named provider in the browser, check for new application-related messages since the previous run, update the Desktop tracker, and tell the user whether any progress changed. If sign-in is required, report that the user must sign in before the next check can continue.

## Targeted edits

- Interpret requests such as “删除某个词”, “控制间距”, “左边对齐”, or “按钮不要遮挡简历” as focused HTML/CSS edits followed by a fresh render check.
- Keep the toolbar outside the page and preserve print output after every UI change.
- Remove only requested visible words and re-check line wrapping and page fit.
