# AMP Calculus I — Double Pace Tracker

Progress tracker for doing **AMP Calculus I Course A and Course B in one semester**
instead of two, by running Course A at double the normal pace.

- **Semester:** Sep 8, 2026 → Jan 13, 2027
- **Course A:** Sep 8 → Nov 2 — 48 school days, 61 syllabus items
- **Course B:** Nov 3 → Jan 13 — 47 school days (awaiting syllabus)
- **Pace:** 2 items per weekday (1 on Friday, Sunday off). Quizzes and tests get a day to themselves.

The semester splits almost exactly in half at Nov 2, so each course gets its own
half at double the normal pace.

## School calendar

The `BREAKS` array in `index.html` lists date ranges where nothing is scheduled.
It currently assumes Thanksgiving (Nov 25–27, 2026) and winter break (Dec 21, 2026 –
Jan 3, 2027) — **check these against the real school calendar**, since both land in
the Course B half and will shift its schedule.

## Views

- **By Week** (default) — the 9 weeks of Course A. Tapping a week expands it into each
  individual day of that week, with that day's assigned work and its own done count.
- **By Unit** — the syllabus as written, grouped into Units 1–6 with the assigned practice problems.
- **By Day** — one card per calendar day, today highlighted.

The current week and today are expanded automatically, and the chosen view is remembered.

## Progress sync

Checkbox state is stored in Firebase Firestore (`trackers/amp_calc_a_state`), so progress
follows you across phone, laptop, and tablet. `localStorage` mirrors it so the page still
renders and records checks while offline.

## Adding Course B

Append the Course B units to the `units` array in `index.html`. Each entry looks like:

```js
{
  label: "UNIT 7", title: "…",
  tip: "…",
  items: [
    { type: "lesson", name: "…", work: "Pg. … #…" },
    { type: "quiz",   name: "Quiz on …", work: "" },
  ]
}
```

`type` is one of `lesson`, `quiz`, `test`, or `review`. The day schedule rebuilds itself.
