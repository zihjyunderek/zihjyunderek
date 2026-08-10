# CLAUDE.md — zihjyunderek/zihjyunderek

Context for any agent session that touches this repo.

## What this repo is

The GitHub **profile README**. `README.md` at the root renders on
<https://github.com/zihjyunderek> above the pinned repositories. Nothing else
here is user-visible. The actual portfolio lives in
`zihjyunderek/zihjyunderek.github.io`.

## Hard constraints

1. **The repository must stay public.** Per GitHub's docs, a profile README
   renders only when "the repository is public", and is explicitly *removed*
   from the profile when "the repository is made private". Making this repo
   private does not hide the README — it deletes it from the profile. If that
   ever gets proposed again, this is the answer.

2. **The README is deliberately four lines.** Three link badges and one card.
   Derek cut it to this himself after seeing that a long README pushes
   **Popular repositories** and the contribution graph below the fold — and
   those are the actual proof. Do not add sections, headings, tables, or an
   About paragraph. Do not "improve" it by restoring earlier revisions; a
   focus table, a 13-project table, a toolkit badge row, and a credentials
   block have each already been written and each already been cut.

3. **Do not duplicate the portfolio.** Project write-ups, experience timeline,
   certificates, publications, and the thesis live on
   `zihjyunderek.github.io`. The README links out; it does not restate.

4. **Never link to a private repository.** As of 2026-08 only two repos are
   public: `Python-Notebook-Toolkit` and `zihjyunderek.github.io`. Everything
   else is private and renders as a 404 to logged-out visitors. Confirm by
   opening the URL logged out before adding it.

5. **Left-aligned only.** No `<div align="center">` anywhere.

6. **No badge walls, GIFs, trophies, streak counters, or visitor badges.**

## Card colours — load-bearing

The cards use a transparent background so one file serves both GitHub themes.
That makes the portfolio palette unusable: measured WCAG contrast against
`#FFFFFF` / `#0D1117`.

| Colour | Role | Light | Dark | Verdict |
| :--- | :--- | ---: | ---: | :--- |
| `1D3557` | portfolio brand navy | 12.36 | **1.53** | invisible in dark mode |
| `1C1917` | portfolio body ink | 17.49 | **1.08** | invisible in dark mode |
| `2F6FBF` | **title / icons (in use)** | 5.06 | 3.74 | passes both |
| `6E7781` | **body text (in use)** | 4.55 | 4.16 | passes both |

Re-check both canvases before changing either value. The portfolio palette is
correct for the website and wrong here; that divergence is intentional.

## Automation

One workflow: `.github/workflows/update-cards.yml`. Daily, it renders
`profile/top-langs.svg` and `profile/stats.svg` via
`stats-organization/github-readme-stats-action@v2` and commits them.

**Why committed SVGs, not hot-linked URLs.** Upstream warns the public
`github-readme-stats.vercel.app` endpoint is best-effort and can serve a
"Something went wrong" card under load. A committed SVG degrades to yesterday's
card instead of a broken image. This profile has to survive months unattended.

**Private stats.** With the default `GITHUB_TOKEN` the card sees public repos
only — which, given that all but two repositories are private, understates the
work substantially. Create a PAT with `repo` + `read:user` scope, save it as the
repository secret `GRS_TOKEN`, and `count_private=true` becomes real; the
workflow already prefers `GRS_TOKEN` when present and needs no edit. Use a
no-expiry classic PAT if it has to outlive a period of no access.

**Requires** Settings → Actions → General → Workflow permissions set to
**Read and write**, or the commit step fails with a 403.

Do not add: snake animations, WakaTime, Spotify cards, visitor counters, trophy
walls, auto-committed activity feeds.

## Editing checklist

- [ ] Facts cross-checked against `zihjyunderek.github.io/src/data/profile.ts`
- [ ] Every new link opened logged out and confirmed 200
- [ ] Preview checked in **both** dark and light GitHub themes
- [ ] README still ends above the fold
- [ ] No claim about repo counts or commit volume the card visibly contradicts

## Known future edits

- **2026/12** — military service ends.
- **2027/02** — CTBC Bank MA (Risk Management) starts; update `profile.ts` in
  the portfolio repo in the same pass.
- **On thesis publication** — if NCCU lifts the embargo and `G7_VaR` goes
  public, it becomes linkable.
