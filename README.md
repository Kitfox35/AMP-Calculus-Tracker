# AMP Calculus I — Double Pace Tracker

Progress tracker for doing **AMP Calculus I Course A and Course B in one semester**
instead of two, by running Course A at double the normal pace.

- **Semester:** Sep 8 → Dec 18, 2026
- **Course A target:** ~Nov 2, 2026 — the rest of the semester is the Course B window
- **Pace:** 2 items per weekday (1 on Friday, Sunday off). Quizzes and tests get a day to themselves.

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
