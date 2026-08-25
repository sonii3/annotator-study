# Annotator Study — Specimen Bench

`index.html` is a self-contained, single-file build of the Specimen Bench
annotator tool. It needs no backend at all, that is the point of hosting it
here on GitHub Pages: it does not depend on any university VM or server
access.

## What it does, and does not, do

There is no server anywhere in this deployment, so results cannot be
captured automatically. Instead, on the summary screen after a run, an
annotator gets two buttons:

- **Download my results** — saves a `specimen-bench-<name>.json` file, the
  shape the scoring pipeline expects.
- **Email my results to the researcher** — downloads that same file, then
  opens the annotator's own email app with `sonja.kunzmann@fau.de`, a
  subject line, and a short human-readable summary (name, session ID,
  timestamp, points, average match) already filled in. `mailto:` links
  cannot attach a file themselves (no browser allows that, for security
  reasons), so the on-page hint tells the annotator to attach the
  just-downloaded file by hand before hitting send in their email client.

This is a manual step for the annotator, not automatic capture. It is a
deliberate tradeoff for not needing any server at all.

## Live link

Once GitHub Pages finishes its first deploy (usually within a minute or two
of a push), the tool is live at:

**https://sonii3.github.io/annotator-study/**

That is the link to send to annotators.

## Rebuilding after a tool change

The real source of this tool lives in the private research repository, in
`annotator_study/build_specimen_bench.py`. Whenever that script or the
patch/tutorial data changes, from that repo's root:

```bash
python3 annotator_study/build_specimen_bench.py --out annotator_study/github_pages/index.html
```

Then copy the refreshed `index.html` into this repository and push.
