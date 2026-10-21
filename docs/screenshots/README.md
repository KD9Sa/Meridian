# Application screenshots

Captured on **October 21, 2026** from the actual application served over a temporary loopback HTTP server. The business report shown is the fixed **June 2026** sample dataset. No application HTML, CSS, data, or behavior was changed to compose these images.

The eight desktop captures share a **1,425 × 932px** image frame. The phone capture is **375 × 904px**, kept at its natural portrait aspect ratio. Images contain the application rather than browser chrome, device mockups, or fabricated UI.

Native JPEG exports preserve the original capture resolution without upscaling or another lossy encoding pass. Each image is below 90 KiB; the complete gallery is **632.7 KiB**. Opaque application backgrounds keep the captures readable in GitHub’s light and dark appearances.

| File | Page | Image dimensions | Size | Visible state |
| --- | --- | --- | --- | --- |
| [analytics.jpg](analytics.jpg) | Analytics | 1425 × 932 | 75.1 KiB | Light; monthly revenue interval |
| [customers.jpg](customers.jpg) | Customers | 1425 × 932 | 81.5 KiB | Light; first account disclosure expanded by default |
| [design-system.jpg](design-system.jpg) | Design System | 1425 × 932 | 80.2 KiB | Light; brand banner and semantic color palette |
| [overview-dark.jpg](overview-dark.jpg) | Overview | 1425 × 932 | 86.7 KiB | Dark; native appearance checkbox enabled |
| [overview-light.jpg](overview-light.jpg) | Overview | 1425 × 932 | 83.1 KiB | Light; default reporting snapshot |
| [overview-mobile.jpg](overview-mobile.jpg) | Overview | 375 × 904 | 33.8 KiB | Light; phone layout and labeled monthly meters |
| [receipt-detail.jpg](receipt-detail.jpg) | Transactions | 1425 × 932 | 45.0 KiB | Light; first completed-payment receipt popover open |
| [settings.jpg](settings.jpg) | Settings | 1425 × 932 | 67.0 KiB | Light; default profile form |
| [transactions.jpg](transactions.jpg) | Transactions | 1425 × 932 | 80.1 KiB | Light; all sample payment records |

## Refreshing the gallery

1. Serve the project root with `python -m http.server 8080 --bind 127.0.0.1`, or another static server.
2. Open each page in a browser. Keep a consistent desktop frame and capture from the top; use a separate phone viewport for the mobile example.
3. Use the header’s native appearance checkbox for the dark view. Open the first transaction’s **View** action for the receipt detail. Leave other controls at their default values.
4. Capture the rendered application directly. Preserve text sharpness and aspect ratio; avoid editing the application or reconstructing screen content for a screenshot.
5. Replace the matching JPEG files, verify the image dimensions and file signatures, then check the relative paths in [README.md](../../README.md). Update this inventory when captures change.

The main README leads with the light overview. Optional galleries cover the other five pages and selected interaction/responsive states so the initial project presentation stays concise.
