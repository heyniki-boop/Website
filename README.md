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

## `church-eligibility-form.html`

Church plant eligibility check. Paste the whole file (HTML, `<style>`, and
`<script>`) into a single Squarespace **Code Block**. It matches the hero's
dark and purple look and is full-bleed the same way.

### How the rules resolve

Eight yes/no questions are scored in the browser. When several rules fire,
the most severe outcome wins: Not currently eligible, then Different path
(standard sales), then Needs review, then Eligible.

| Answer | Outcome |
| --- | --- |
| Not in the U.S. | Not currently eligible |
| Not willing to do training and reporting | Not currently eligible |
| Not a church plant, and not opening a new campus | Standard sales route |
| Existing church opening a new campus | Needs review (until Legal/leadership confirms policy) |
| Outside the 6-month / 12-month launch window | Needs review |
| No identified leadership | Needs review |
| No 24-month financial plan | Needs review |
| Using another platform | Never a blocker. Sent as a routing tag only |

Judgment calls to confirm: the launch-window "no" goes to review rather than
not eligible, and a "no" on plant combined with a "yes" on new campus goes to
review rather than standard sales. Both live in `evaluate()` in the script.

### Capturing responses

Nothing is sent anywhere by default. To post results to a CRM, Zapier, or
Formspree, set `data-endpoint` on the `<form>`. The JSON payload includes the
answers, the outcome (`eligible`, `needs_review`, `standard_sales`,
`not_eligible`), the competitor platform name, and the optional church name
and email.
