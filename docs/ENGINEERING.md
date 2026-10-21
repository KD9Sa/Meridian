# Meridian engineering notes

Detailed architecture, data definitions, browser support, and verification notes. Return to the [project showcase](../README.md).

Meridian is a complete, responsive enterprise revenue operations dashboard built with HTML5, CSS3, and inline SVG. It presents the fictional Acme Studio workspace through a calm, cohesive interface: forest-green navigation, warm neutral surfaces, and a fresh lime accent.

This portfolio project demonstrates semantic document architecture, a reusable CSS design system, accessible native interactions, responsive data visualization, and maintainable front-end engineering. It deliberately works without JavaScript, a framework, a backend, package dependencies, or a build step.

## Open the project

Open `index.html` directly in a modern browser. All six pages, styles, icons, and illustrations are local; an internet connection is unnecessary.

Alternatively, serve this directory with any simple static HTTP server. If Python is already installed:

```sh
python -m http.server 8080
```

Then open `http://localhost:8080`. Python is optional and is not a project dependency.

## Pages

| Page | File | Purpose |
| --- | --- | --- |
| Overview | `index.html` | Revenue, business health, customer activity, and operational priorities |
| Analytics | `analytics.html` | Revenue trends, acquisition channels, comparisons, and conversion analysis |
| Transactions | `transactions.html` | Payment records, status presentation views, and native record details |
| Customers | `customers.html` | Accounts, customer tiers, contact details, lifetime value, and recent activity |
| Settings | `settings.html` | Profile, organization, appearance, notification, and privacy preference examples |
| Design system | `design-system.html` | Brand foundations, tokens, typography, component specimens, and native interaction examples |

## Product and data model

Acme Studio is a fictional creative services organization using Meridian to understand recurring customer revenue. Jamie Lee is the workspace administrator. Reporting is fixed to June 2026, and currency values are US dollars.

The headline dataset is shared across the application:

| Metric | June 2026 |
| --- | ---: |
| Completed-payment revenue | $128,430 |
| Revenue in May 2026 | $113,655 |
| Total transactions | 1,482 |
| Completed transactions | 1,356 |
| Pending transactions | 89 |
| Failed transactions | 37 |
| Active customers | 842 |
| Revenue per recorded transaction | $86.66 |

The displayed revenue-per-transaction ratio is completed-payment revenue divided by all recorded transactions, including pending and failed attempts. It is a reporting ratio for this sample dataset. Visible table rows are selected examples, not the complete 1,482-record ledger; their amounts are not expected to sum to the monthly aggregate.

All organizations, names, contacts, account activity, and payment details are fictional sample content. No production account data is included.

## Design philosophy

The interface gives business information a clear hierarchy without overwhelming the reader. Large, quiet numbers establish the main story; restrained charts and status labels provide supporting context. A persistent sidebar makes navigation predictable, while individual page compositions fit the task: analytical charts, a transaction ledger, an account directory, grouped settings, and an editorial component reference.

The palette is intentionally grounded. Forest green carries primary actions and navigation; warm stone reduces glare; lime draws attention to growth and progress. Text labels and symbols accompany semantic colors so that status never depends on color alone. System fonts keep text familiar, fast, and entirely offline.

## CSS architecture

`assets/css/styles.css` is the stylesheet entry point. It imports the shared foundation and page-specific styles. Cascade layers establish a predictable order rather than escalating selector specificity.

```text
.
├── index.html
├── analytics.html
├── transactions.html
├── customers.html
├── settings.html
├── design-system.html
├── assets/
│   ├── css/
│   │   ├── styles.css        # Stylesheet entry point and layer ordering
│   │   ├── tokens.css        # Semantic themes and design tokens
│   │   ├── base.css          # Reset, typography, links, focus, native elements
│   │   ├── layout.css        # Application shell and responsive navigation
│   │   ├── components.css    # Shared cards, buttons, forms, tables, badges
│   │   ├── pages.css         # Overview dashboard composition
│   │   ├── insights.css      # Analytics-specific presentation
│   │   ├── data-pages.css    # Transaction and customer presentation
│   │   ├── workspace.css     # Settings and design system reference
│   │   └── utilities.css     # Small shared presentation helpers
│   ├── icons/                # Local SVG favicon
│   └── reports/              # Downloadable June snapshot (CSV)
├── docs/
│   ├── ENGINEERING.md     # Detailed project documentation
│   ├── palette.svg        # README palette reference
│   └── screenshots/      # Genuine application captures and capture notes
├── README.md
└── ASSETS.md
```

Semantic custom properties describe purpose rather than a specific color: surfaces, text, borders, primary actions, and success, warning, error, and information states. Other tokens cover typography, spacing, radii, elevation, transitions, and layout dimensions. Both themes reuse these component contracts.

The repeated application shell is intentional. These are independent HTML documents, not templates that require a build or runtime. Shared appearance lives in CSS. When changing navigation, update each page’s shell and retain the correct `aria-current="page"` marker.

## Features and HTML5 techniques

- A consistent application shell, grouped navigation, breadcrumbs, and descriptive document metadata.
- Semantic landmarks and purposeful `header`, `nav`, `main`, `section`, `article`, `aside`, and `footer` elements.
- Accessible table captions, row and column headers, machine-readable dates, and responsive table containers.
- Inline SVG charts and icons, visible legends, and chart descriptions or data summaries.
- Native `details` and `summary` disclosures for extra context and record information.
- Native popovers for optional contextual information in supporting browsers.
- Labeled form controls, meaningful field groups, required fields, email/URL validation, and native reset actions.
- Native `progress` and `meter` examples for completion and bounded measurements.
- CSS-controlled presentation states using native radio buttons and checkboxes.
- Light and dark appearances, with a page-local native theme switch.
- A dedicated design system with real control states, component examples, and clear implementation boundaries.

## CSS techniques

- Cascade layers and low-specificity, reusable component classes.
- Custom properties for semantic themes and shared visual tokens.
- Grid, Flexbox, intrinsic sizing, and responsive media/container queries.
- Logical properties and fluid sizing with modern sizing functions.
- Sticky positioning for navigation and contextual sections where space allows.
- Modern selectors, including `:is()`, `:where()`, and `:has()`.
- `:focus-visible` treatment and native `:user-invalid` progressive enhancement.
- Pseudo-elements, restrained transitions and popover keyframes, lightweight chart graphics, and reduced-motion overrides.
- Native control styling that preserves keyboard and browser behavior.

## Responsive strategy

The shell adapts to available space rather than scaling the desktop layout down. Navigation becomes mobile-friendly, content grids reduce their column count, actions wrap, charts retain their labels, and long tables scroll inside their own containers. The intended reference widths are approximately 360, 768, 1024, and 1440 pixels, with fluid expansion on larger displays.

Page-level overflow is avoided through `minmax(0, 1fr)`, flexible controls, wrapping groups, and explicit scroll regions for dense data. Keep new table columns inside the table wrapper; do not force the entire document to a desktop minimum width.

## Accessibility

The project follows WCAG 2.2 AA principles where practical. It uses a skip link, visible keyboard focus, descriptive labels, native interactions, a logical heading structure, table semantics, chart alternatives, and textual status indicators. Decorative icons are hidden from assistive technology. Initial avatars supplement visible names rather than replacing them. Motion is reduced for users who request it.

Native controls preserve expected Tab, Space, arrow-key, Enter, and Escape behavior where applicable. Essential information remains visible rather than appearing only on hover. Tables may require horizontal scrolling at small widths; their content remains intact.

The design system includes deliberately disabled and invalid specimens. These illustrate component states and are labeled as examples; they do not indicate an application failure. A full independent accessibility audit has not been claimed.

## Genuine interactions and static boundaries

This is a polished static product demonstration, not a connected financial system.

**Available:** page navigation, anchor navigation, native disclosures and popovers, in-page theme switching, native form controls and validation, reset buttons, implemented CSS presentation toggles, and a downloadable fixed June snapshot at `assets/reports/meridian-june-2026.csv`.

**Not implemented:** authentication, live analytics, transaction processing, remote search, server-side sorting or filtering, backend pagination, account administration, email delivery, persistent settings, or data synchronization. Any unavailable controls are identified as demonstrations or disabled. Status presentation views operate only on the supplied sample records.

The theme switch changes the current page through `:has()`. It has no storage and resets when you navigate or reload. The settings form validates in the browser and returns to the same static document with a clear demonstration message. Profile input values have no `name` attributes and are not submitted. The content-density radio selection may appear in the URL as a non-sensitive presentation parameter; no server handles or saves it. Use fictional values when exploring the examples.

## Browser support and fallbacks

Use a current release of Chrome, Edge, Firefox, or Safari for the complete experience. There is no transpilation or legacy-browser bundle.

- CSS Grid, Flexbox, custom properties, and cascade layers form the shared foundation.
- CSS `:has()` powers the theme and certain presentation controls. Browsers without it retain the light appearance and default content views.
- Container queries improve component adaptation where supported; the base layout and media queries remain usable without them.
- Native popovers require a supporting browser. Disclosures expose equivalent optional component context where needed; essential navigation and data do not depend on popovers.
- `:user-invalid` and modern color functions enhance validation and styling. Native HTML validation still operates when the additional styling is unsupported.
- Browser print and form-control appearance may vary. The project does not require pixel-identical rendering across operating systems.

## Assets

No external images, fonts, scripts, or icon libraries are required. All essential visuals are local CSS, inline SVG, or text initials. There are no image downloads to perform. See [ASSETS.md](../ASSETS.md) for the inventory and guidance on adding optional local customer portraits.

## Verification

Source checks were performed across all six HTML pages and ten stylesheets using Python’s standard-library HTML parser and local reference analysis. The checks covered:

- Balanced markup, duplicate IDs and attributes, and common invalid interactive nesting.
- Local link destinations, cross-page fragment targets, and referenced stylesheet and favicon files.
- Form labels, ARIA ID references, popover targets, table captions, and table-header associations.
- Referenced CSS custom properties, imported stylesheet paths, local CSS URLs, and balanced CSS blocks.
- Absence of script elements, inline event handlers, JavaScript URLs, and JavaScript/TypeScript source files.

These source checks passed after fixing the shared help links’ destination. They are structural checks, not a formal HTML/CSS validator or a complete accessibility conformance audit.

Browser QA used the desktop app’s in-app browser preview. All six pages were checked at 360, 768, 1024, 1440, and 1920 pixels in both appearances; no page-level horizontal overflow remained after repairs. Visual spot checks covered desktop, tablet, phone, dark appearance, and the receipt overlay. Native interaction checks covered the navigation drawer, chart interval and component tabs, payment status views and refund empty state, receipt opening/Escape dismissal with focus return, keyboard customer disclosures, and profile validation/reset/validation feedback. Browser warning and error logs were empty during the final layout matrix. The main and semantic status text color pairs and form-control borders were also checked numerically for contrast. Direct file opening was not exercised because the in-app preview permits HTTP(S) URLs only. All document and asset references are relative and require no server-side behavior. These checks do not replace testing with assistive technologies or other browser engines.

## Extending Meridian

Keep new content in the same fictional business domain and reporting period. Prefer an existing component class over a page-specific replacement. Add tokens when a new visual decision should be shared, and scope page-only styles to that page’s component prefix. Check light and dark appearances, keyboard operation, and small screens after each meaningful change.

Potential future work includes an authenticated backend, a single source of truth for records, server-powered reporting and pagination, persistent preferences, custom report generation, automated accessibility checks, and localization. Those capabilities are intentionally outside this dependency-free HTML/CSS project.
