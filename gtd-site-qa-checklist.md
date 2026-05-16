<!-- import_checklists/gtd-site-qa-checklist.md — Import-ready QA checklist for the TaskBlaster Pro marketing site. -->
# TaskBlaster Pro Marketing Site — QA Testing Checklist

> **App**: TaskBlaster Pro Marketing Site
> **Stack**: Static HTML, CSS, JavaScript
> **Platform**: Browser on macOS
> **Version**: 1.0 site snapshot
> **Working Directory**: /Users/mad/src/active/gtd-site

---

## Legend

| Symbol | Meaning |
|--------|---------|
| `[ ]`  | Test not yet executed |
| `[P]`  | Pass |
| `[F]`  | Fail — file failure report |
| `[S]`  | Skipped (reason noted) |

---

## 1. Local Preview & Asset Integrity

### 1.1 Local Launch

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 1.1.1 | [ ] Start local server | From the site directory, run `cd /Users/mad/src/active/gtd-site && python3 -m http.server 8000`. | Local preview starts without errors and serves `index.html` plus bundled assets. | Capture terminal output and note any missing-file or permission errors. |
| 1.1.2 | [ ] Load homepage | Open `http://127.0.0.1:8000/` in a browser. Hard-refresh once. | Home page loads without broken layout, JS errors, or missing assets. | Capture browser console errors and screenshot the initial render. |
| 1.1.3 | [ ] Core asset availability | Verify `icon.png`, `user-manual.pdf`, and `TaskBlaster-Pro-1.0.dmg` resolve from the page. | App icon displays, manual link downloads/opens, and DMG link resolves to the bundled file. | Note which asset failed and whether the failure is path-related or file-related. |

### 1.2 Metadata & Social Cards

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 1.2.1 | [ ] Document metadata | Inspect the page source for `<title>` and description metadata. | Title is "TaskBlaster Pro — Getting Things Done for Mac" and description reflects the local-first macOS app message. | Capture the mismatched tag values or missing tags. |
| 1.2.2 | [ ] Open Graph tags | Inspect the `og:title`, `og:description`, `og:image`, and `og:url` tags. | All expected Open Graph tags are present and point to intentional values. | Note any missing tags, malformed URLs, or stale release references. |
| 1.2.3 | [ ] Theme and favicon | Verify the page advertises the favicon and theme color. | Favicon resolves and browser tab uses the expected site icon; theme color meta tag is present. | Note missing icon, incorrect icon, or missing theme metadata. |

---

## 2. Navigation & Hero

### 2.1 Top Navigation

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 2.1.1 | [ ] Sticky nav render | Load the page at the top and scroll down through multiple sections. | Navigation stays fixed at the top with readable contrast and no overlap bugs. | Screenshot any clipping, jitter, or content overlap. |
| 2.1.2 | [ ] Anchor links | Click nav links for Features, Focus Overdrive, Workflows, AI, and Releases. | Each link scrolls to the correct section anchor without broken jumps. | Note the broken anchor target or incorrect landing position. |
| 2.1.3 | [ ] Manual and deploy links | Click the nav Manual link and the "Deploy to Mac" CTA. | Manual opens/downloads the PDF; deploy CTA resolves to the DMG file. | Note whether the link is broken, points to the wrong file, or uses a stale filename. |

### 2.2 Hero Section

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 2.2.1 | [ ] Hero branding | Verify the hero icon, headline, subtitle, and trust line on first paint. | Hero content matches the TaskBlaster Pro brand and renders without layout shift. | Screenshot any missing copy, cropped icon, or unstable layout. |
| 2.2.2 | [ ] Hero CTAs | Click the hero DMG and Manual buttons. | Primary CTA resolves to the DMG; secondary CTA opens/downloads the manual PDF. | Record the broken CTA and the resulting HTTP/file behavior. |
| 2.2.3 | [ ] Hero metadata line | Check the macOS/version/free/open-source metadata line below the CTAs. | Metadata line is readable and consistent with the current release messaging. | Note stale version text or broken separators. |

---

## 3. Screenshots & Feature Content

### 3.1 Screenshot Rail

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 3.1.1 | [ ] Screenshot images load | Inspect the screenshot rail near the top of the page. | All screenshot images render without broken placeholders or distorted aspect ratios. | Identify the missing file or distorted image and capture a screenshot. |
| 3.1.2 | [ ] Horizontal scrolling | Scroll the screenshot rail horizontally with trackpad or mouse. | Rail scrolls smoothly and all cards remain usable. | Note scroll lockups, clipping, or unresponsive cards. |
| 3.1.3 | [ ] Screenshot alt text quality | Inspect image `alt` text for screenshots and hero icon. | Alt text is present and describes the product surfaces meaningfully. | Note missing, duplicate, or low-signal alt text. |

### 3.2 Main Content Sections

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 3.2.1 | [ ] Section coverage | Scroll through Methodology, Today, Features, Focus Overdrive, Workflows, AI, Native, Shortcuts, Install, and Releases. | All major sections render in the intended order with no empty blocks or abrupt styling breaks. | Note missing sections, duplicate sections, or section ordering problems. |
| 3.2.2 | [ ] Feature card readability | Review the feature grids and cards in the major content sections. | Cards are legible, spacing is consistent, and copy does not overflow or truncate. | Screenshot any clipping, collision, or unreadable contrast. |
| 3.2.3 | [ ] Release notes integrity | Inspect the Releases section for structured release content. | Releases appear readable, complete, and internally consistent with the linked app version. | Note stale content, broken formatting, or mismatched release numbering. |

---

## 4. Footer, Links & Dynamic Behavior

### 4.1 Footer

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 4.1.1 | [ ] Footer links | Click footer links for Release Notes, User Manual, Source Code, and Report a Bug. | Internal link jumps correctly and external links resolve to the expected GitHub destinations. | Note which link is broken or points to the wrong target. |
| 4.1.2 | [ ] Visitor counter display | Inspect the visitor counter area in the footer after page load. | Counter region renders cleanly and does not break footer layout even if the count is unavailable. | Note blank, overlapping, or error-state rendering. |

### 4.2 Background & Scripted Effects

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 4.2.1 | [ ] Background canvas behavior | Inspect the page background effect and scroll through the site. | Canvas/background effect stays behind content and does not interfere with interaction. | Capture flicker, z-index, or performance problems. |
| 4.2.2 | [ ] JavaScript resilience | Disable JavaScript or simulate a script failure, then reload once. | Core page content, navigation anchors, and download links remain usable even if dynamic enhancements degrade. | Note which essential user path breaks without JavaScript. |

---

## 5. Responsive, Keyboard & Accessibility Checks

### 5.1 Responsive Layout

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 5.1.1 | [ ] Tablet width | Resize the browser to an intermediate width such as 900px. | Navigation, hero, screenshots, and content cards reflow cleanly without collisions. | Screenshot any overlapping or clipped content. |
| 5.1.2 | [ ] Mobile width | Resize to a narrow mobile width such as 390px. | Content remains readable, buttons stay tappable, and horizontal overflow is limited to the screenshot rail. | Note non-dismissible overflow, hidden text, or unusable controls. |

### 5.2 Keyboard & Focus

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 5.2.1 | [ ] Keyboard tab order | Use `Tab` and `Shift+Tab` to move through nav and CTA links. | Focus order is logical and every interactive element shows visible focus styling. | Note skipped controls or invisible focus states. |
| 5.2.2 | [ ] Keyboard activation | Use `Enter` on primary nav and CTA links. | Focused links activate correctly without requiring a mouse. | Record any control that cannot be triggered from the keyboard. |

---

## 6. Regression & Smoke Commands

### 6.1 Quick Regression Pass

| # | Step | Instructions | Expected Outcome | Failure Reporting |
|---|------|-------------|-------------------|-------------------|
| 6.1.1 | [ ] File inventory smoke test | From the project directory, run `find /Users/mad/src/active/gtd-site -maxdepth 1 -type f`. | Expected top-level site artifacts are present, including `index.html`, screenshots, manual PDF, icon, and DMG. | Capture the missing file list or unexpected filename drift. |
| 6.1.2 | [ ] HTML sanity check | From the project directory, run `grep -n \"<section\\|<nav\\|<footer\" /Users/mad/src/active/gtd-site/index.html`. | Core structural landmarks are present in the document. | Note any missing major landmark or malformed section structure. |
