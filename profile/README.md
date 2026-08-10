# profile/

Generated assets. **Do not edit by hand.**

`.github/workflows/update-cards.yml` renders these daily and commits them:

| File | Card | Referenced by README.md |
| :--- | :--- | :--- |
| `top-langs.svg` | Most used languages | yes |
| `stats.svg` | GitHub stats | no — kept for easy reinstatement |

Both use a **transparent background** (`bg_color=00000000`) so a single file
works on GitHub's light and dark themes, with title `#2F6FBF` and body text
`#6E7781` — the only colours in the palette that clear 3:1 contrast against
both `#FFFFFF` and `#0D1117`. The portfolio's brand navy would be invisible in
dark mode.

They are committed rather than hot-linked so a rate limit or outage at
`github-readme-stats` can never render a broken card on the profile.
