# 🤖 AI Coder Agent Prompt — QA Automation Practice Website

## ROLE
You are an expert frontend developer tasked with building a **deliberately buggy** e-commerce website for QA automation engineers to practice their testing skills. The site must look visually realistic and professional on the surface, but contain a rich set of intentional bugs, broken interactions, inconsistencies, and edge-case traps embedded throughout.

---

## PROJECT OVERVIEW

Build a single-file (`index.html`) e-commerce website called **"ShopBuggy"** — a beauty/lifestyle store selling products across categories like Makeup, Skincare, Fragrance, Hair Care, Apparel, and Books.

The site must:
- Be written entirely in **one HTML file** using inline CSS (`<style>`) and inline JS (`<script>`)
- Use **no external frameworks** (no React, no Bootstrap CDN required — write your own CSS)
- Look like a real online store at first glance
- Contain **at least 35 intentional, clearly documented bugs** (see list below)
- Include a hidden `<!-- BUG: [ID] description -->` HTML comment next to every bug for instructor answer-key purposes
- Have proper semantic HTML structure (header, nav, main, footer, sections)
- Be fully self-contained and openable directly in a browser

---

## SITE STRUCTURE

### Pages / Sections (all in one scrollable page with JS tab/section switching):
1. **Header** — Logo, search bar, cart icon with item count, Login/Register link
2. **Navigation Bar** — Category links: Home, Makeup, Skincare, Fragrance, Hair Care, Apparel, Books, Sale
3. **Hero Banner** — Rotating/static promotional banner
4. **Featured Products Grid** — 8 product cards with image placeholder, name, price, Add to Cart button
5. **Special Offers Section** — Products with original price, discounted price, and % off badge
6. **Newsletter Signup** — Email input + Subscribe button
7. **Login Modal** — Triggered by clicking "Login/Register"
8. **Registration Form** — Full form with validation fields
9. **Shopping Cart Page/Section** — List of added items, quantity, subtotal, total, checkout button
10. **Footer** — Links (About, Contact, Privacy Policy, Return Policy), social icons, copyright

---

## MANDATORY BUG LIST

Implement ALL of the following bugs. Place the HTML comment `<!-- BUG: [ID] ... -->` immediately next to each one.

### 🔴 FORM & VALIDATION BUGS
| ID | Bug Description |
|----|----------------|
| BUG-001 | Login form submits successfully even when both fields are empty |
| BUG-002 | Email field in registration accepts clearly invalid formats (e.g., "notanemail", "a@", "@b.com") — no validation |
| BUG-003 | Password and Confirm Password fields do not check if they match on submit |
| BUG-004 | Phone number field accepts alphabetical characters (e.g., "abcdefgh") |
| BUG-005 | "First Name" field has `maxlength="2"` — can only type 2 characters |
| BUG-006 | Required field asterisk (*) shown on "Middle Name" but the field is not actually required |
| BUG-007 | Newsletter subscribe button does nothing when clicked (event listener missing/detached) |
| BUG-008 | Registration form "Submit" button label says "Reset" visually due to wrong `value` attribute |
| BUG-009 | Login form password field is `type="text"` instead of `type="password"` — password is visible |
| BUG-010 | "Date of Birth" field accepts future dates (e.g., year 2099) with no max date constraint |

### 🟠 CART & PRICING BUGS
| ID | Bug Description |
|----|----------------|
| BUG-011 | "Add to Cart" button on Product Card #3 does nothing (missing `onclick` or broken function call) |
| BUG-012 | Cart total is calculated incorrectly — it multiplies quantity × price but then adds an extra copy of the last item |
| BUG-013 | Removing an item from the cart decreases the item count visually but the subtotal does not update |
| BUG-014 | Cart item count badge in the header shows "0" even after items are added (display not updated) |
| BUG-015 | Product #5 has a "Sale" badge showing "10% OFF" but the displayed new price is higher than the original price |
| BUG-016 | Quantity input in cart allows 0 and negative numbers (no min="1" constraint) |
| BUG-017 | "Checkout" button navigates to `#` instead of the checkout section |
| BUG-018 | Currency symbol shows "$" but one product price is listed as "€45.00" inconsistently |

### 🟡 UI / DISPLAY BUGS
| ID | Bug Description |
|----|----------------|
| BUG-019 | Product card #2 has a broken image (src points to a non-existent path like `images/typo_img.jpg`) |
| BUG-020 | "Sort By" dropdown in the product grid has options but selecting any option does not re-sort products |
| BUG-021 | Search bar placeholder text says "Serach products..." (typo — "Serach" instead of "Search") |
| BUG-022 | Footer copyright year is hardcoded as "2018" (outdated/wrong year) |
| BUG-023 | Mobile hamburger menu icon is visible on desktop due to wrong CSS media query breakpoint (uses `min-width` instead of `max-width`) |
| BUG-024 | Product #7 name is truncated mid-word with no ellipsis — overflows its container |
| BUG-025 | "Sale" badge on Product #6 is positioned off-screen to the right (wrong `left`/`right` CSS values) |
| BUG-026 | Two different navigation links both have `id="nav-home"` (duplicate IDs) |
| BUG-027 | The page `<title>` tag says "Untitled Document" |
| BUG-028 | "Write Review" link on every product card leads to `href="#"` (non-functional dead links) |

### 🔵 JAVASCRIPT / INTERACTION BUGS
| ID | Bug Description |
|----|----------------|
| BUG-029 | Search form on submit redirects to the correct URL but also clears all previously entered text due to a redundant `input.value = ""` call before redirect |
| BUG-030 | Modal "Close" (×) button closes the modal but also submits the login form silently |
| BUG-031 | Clicking "Add to Cart" multiple times on the same product adds duplicate separate entries instead of incrementing quantity |
| BUG-032 | A JS `console.error()` is triggered on page load (introduce a deliberate `undefined.property` reference wrapped in try/catch that logs the error) |
| BUG-033 | "Show More Products" button toggles hidden products but the button label never changes from "Show More" to "Show Less" |
| BUG-034 | Applying a discount/promo code "SAVE10" shows a success message but does NOT actually reduce the cart total |
| BUG-035 | Category navigation highlights the wrong active link — clicking "Skincare" highlights "Makeup" as active instead |

### ⚪ ACCESSIBILITY / SEMANTIC BUGS (Bonus)
| ID | Bug Description |
|----|----------------|
| BUG-036 | All product images have empty `alt=""` attributes (no descriptive alt text) |
| BUG-037 | Form labels are not associated with their inputs (`for` attribute doesn't match any input `id`) |
| BUG-038 | The main "Add to Cart" call-to-action buttons have no accessible text — icon only, no `aria-label` |

---

## PRODUCT DATA

Use the following 8 products in the featured grid:

```
1. Skinsheen Bronzer Stick        - $29.50  (in stock)
2. BeneFit Girl Meets Pearl       - $19.00  (was $30.00) [SALE] ← BUG-019: broken image
3. Benefit Bella Bamba            - $28.00  (in stock)    ← BUG-011: broken Add to Cart
4. Tropiques Loose Bronzer        - $38.50  (in stock)
5. Absolue Eye Precious Cells     - $110.00 (was $105.00) [SALE badge] ← BUG-015: price higher than original
6. Total Moisture Facial Cream    - $38.00  (in stock)    ← BUG-025: sale badge off-screen
7. Flash Bronzer Body Gel         - $29.00  (was $34.50) [SALE] ← BUG-024: name overflow
8. Acqua Di Gio Pour Homme        - €45.00  (was $59.00)  ← BUG-018: wrong currency
```

---

## VISUAL DESIGN REQUIREMENTS

- Color scheme: Dark navy header (`#1a1a2e`), orange accents (`#e94560`), white content area
- Clean product cards with: image area (200×200 placeholder colored box if no real image), product name, price (old/new if on sale), Add to Cart button
- Responsive-ish layout (simple CSS grid, 4 columns desktop, 2 tablet, 1 mobile — but with BUG-023 intentionally breaking the hamburger)
- Modal overlay for login form
- Sticky header with cart count badge

---

## CODE QUALITY REQUIREMENTS

- All bugs must be **subtle enough** that they require actual test automation to catch (not immediately obvious red error boxes)
- Bugs must NOT break the entire page — each is isolated to a specific component
- Use realistic-looking UI (proper spacing, fonts, colors) so the site looks legitimate
- Add a small floating **"🐛 Bug Count: 38"** badge fixed to the bottom-right corner as a teaser/hint to students
- Include a hidden `<div id="bug-answer-key" style="display:none">` containing all bug IDs and descriptions in JSON format for instructor tooling

---

## DELIVERABLE

A single `index.html` file that:
1. Opens in any modern browser without errors blocking the page
2. Contains all 38 bugs listed above
3. Looks visually like a professional e-commerce store
4. Has `<!-- BUG: [ID] -->` comments throughout the source
5. Includes the hidden answer key div
6. Has clear, readable code with section comments (e.g., `<!-- ===== HEADER ===== -->`)
