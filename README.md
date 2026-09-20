# nicolewight.com

## `nicole-wight-hero.html`

Executive PMM hero block for the Squarespace site. Paste the whole file
(HTML plus the `<style>` block) into a single Squarespace **Code Block**.

### Notes

- SEO title and description live in the comment at the top of the file, but
  comments do not create metadata. Enter them in Squarespace SEO settings.
- The block is full-bleed. It pulls itself out of the Squarespace content
  column with `width: 100vw` and negative margins, and `html, body
  { overflow-x: clip }` keeps that from making the page scroll sideways. If
  the block already sits in a full-width section, that rule can be deleted.
- Squarespace themes inject backgrounds, borders, shadows, and decorative
  pseudo-elements into links, spans, and list items. The "stray-box reset"
  near the top of the stylesheet neutralizes them so no unwanted boxes float
  over the hero.

### Accessibility

Built to WCAG 2.2 AA (most text clears AAA):

- All text meets 7:1 contrast or better against the hero background.
- Purple primary button is `#6d28d9` on white text, 7.1:1.
- Real `<ul>` / `<li>` markup for the stats and capability tags, with
  `role="list"` retained so Safari keeps list semantics under
  `list-style: none`.
- Eyebrow and section labels are sentence case in markup and uppercased in
  CSS, so screen readers do not spell them out letter by letter.
- Visible `:focus-visible` outline on every link, not clipped by the section.
- `aria-label` on the email button contains its visible text (WCAG 2.5.3
  Label in Name).
- Buttons are at least 44px tall (WCAG 2.5.8 Target Size).
- Honors `prefers-reduced-motion` and `forced-colors`.
- Reflows to one column at 400% zoom with no horizontal scroll.
