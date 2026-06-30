# Design

This dashboard uses Opendoor's "Calm" visual system. Because this is a standalone
GitHub Pages site (not part of the `projects.simplersell.com` growth-dashboards
monorepo), it carries its own copy of the design system rather than referencing the
shared one.

- `styles/calm.css` is the design layer: color tokens (applied by role, not aesthetic),
  fonts (Inter for UI, JetBrains Mono for data references), and the component rules
  (header chrome, sticky controls, tally tiles, cards, badges, footer).
- `index.html` is page-specific: the embedded roster data, the search/filter/sort logic,
  and the markup that consumes the Calm classes.

## Rules carried from the system
- Page background is slate-50 (`#f8fafc`); cards are white on top of it. Never pure white.
- Color by role: ink = primary/total, blue = info/Large tier, green = good/Mid tier,
  amber = watch/Rising tier and the Sunbelt flag.
- Tier colors are ordered and restrained: Mega = ink, Large = blue, Mid = green, Rising = amber.
- Any number/count gets tabular figures (`.tabular`).
- Flat and quiet at rest. No shadows on cards. Hover = fill, not lift.
- No em dashes anywhere.

## Editing the data
The roster lives in the `<script type="application/json" id="influencer-data">` block in
`index.html`. Each record: `tier, handle, url, followers, location, sunbelt (Y/N), niche,
contact, note, verified`. Update `ROSTER_DATE` in the page script when you refresh the list;
it drives the "Updated" label and the freshness pill (stale after 60 days).
