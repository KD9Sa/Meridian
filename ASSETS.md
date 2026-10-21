# Meridian asset inventory

Meridian is self-contained. It does not request external images, fonts, scripts, or icon libraries. Customer portraits use text initials, and icons, brand marks, charts, and decorative graphics use local SVG or CSS. This keeps the dashboard readable offline and eliminates broken remote-image states.

## External image inventory

| External URL | Used on | Suggested local filename | Replacement needed |
| --- | --- | --- | --- |
| None | No external images are used | Not applicable | None |

No images have been automatically downloaded. There are no random-image endpoints, remote portrait services, watermark-bearing stock images, or externally hosted font dependencies.

## Local visuals

| Asset type | Location | Notes |
| --- | --- | --- |
| Brand mark | Application shell and design system | Local SVG; decorative repetitions are hidden from assistive technology |
| Navigation and action icons | Inline in the HTML documents | Rounded line icons, no icon font or network request |
| Business charts | Overview and Analytics HTML | SVG and CSS with labels and accessible summaries |
| Customer and profile avatars | HTML text inside `.avatar` elements | Initials remain available when offline; names appear alongside them |
| Theme previews and skeleton specimens | `assets/css/workspace.css` | CSS-only illustrative component specimens |
| Browser favicon | `assets/icons/` | Local SVG brand asset |
| Documentation screenshots | `docs/screenshots/` | Genuine application captures; dimensions, states, and refresh instructions are documented in that directory |
| README palette reference | `docs/palette.svg` | Local SVG swatches matching the implemented light palette |

## Optional customer portraits

The existing initial avatars are intentional and complete. If you later prefer photographic portraits:

1. Obtain appropriately licensed images or explicit permission from the people pictured. Keep a record of each source URL and license here.
2. Put optimized, square local images in `assets/images/`. Suggested names include `jamie-lee.webp`, `olivia-rhye.webp`, `phoenix-baker.webp`, and `lana-steiner.webp`.
3. Use a modest image size, such as 96 × 96 or 128 × 128 pixels, for small avatars. Avoid loading full-resolution originals.
4. Replace the appropriate avatar content with an image that includes explicit dimensions. Preserve the adjacent visible customer name.
5. Apply `object-fit: cover` and the same border radius as the avatar container. Retain the initials as a fallback where appropriate.
6. Add `loading="lazy"` to portraits below the initial viewport. For the small visible profile avatar, eager browser loading is reasonable.

Example local reference:

```html
<span class="avatar">
  <img
    src="assets/images/olivia-rhye.webp"
    alt="Olivia Rhye"
    width="40"
    height="40"
    loading="lazy"
  >
</span>
```

If the visible name already gives all necessary identity and the portrait adds no information, use `alt=""` to avoid repetitive announcements. Keep essential names, account status, and navigation available as text regardless of the image.

If you temporarily use external images, choose stable direct image URLs, document the URL, license, page, and local replacement filename in the inventory above, and ensure all essential content still works when that host is unavailable. Search the HTML files for `src=` to locate image references. Search for `url(` in CSS to find any subsequently added background imagery.

## Updating SVG and CSS visuals

Inline SVG is ordinary source code in the relevant HTML page. Edit its paths or labels in place; do not add a script or charting package. Preserve an accessible chart title/description and a visible legend when changing a data visualization. Keep meaningful values and dates synchronized with the tables and documentation.

The favicon is a separate local file so that browser tabs remain branded without external requests. Update the icon and the repeated inline brand marks together when changing the product identity.
