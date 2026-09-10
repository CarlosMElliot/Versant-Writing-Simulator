# Summary & Opinion Writing Test

A no-build, static web app (plain HTML/CSS/JS) for running a timed English placement writing task: students read a short passage, then write a **summary** of the author's opinion and their **own opinion** on the topic — all within an 18-minute timer.

Built for **ERC Academy** by Carlos Mercado.

## Features

- **Three built-in passages** — teen jobs, zoos, and computers — each paired with a summary + opinion prompt
- **18-minute countdown timer** that turns red under 2 minutes and auto-submits when it hits zero
- **Live word counts** with color feedback (green in range, red outside it) for both the summary (25–50 words) and opinion (50+ words) boxes
- **Split-screen layout** — the passage stays visible and scrollable on the left while the student writes on the right, with quick-jump tabs between the Summary and Opinion boxes
- **Inline submit validation** — if a box is under the word minimum, a warning banner (not a blocked browser popup) asks the student to confirm before submitting
- **Results screen** with three ways to hand off a finished test:
  - **Email results to instructor** — opens a pre-filled Gmail compose tab addressed to the instructor's inbox
  - **Download results (.txt)** — saves a plain text copy, useful as a fallback or for non-Gmail users
  - **Print / save as PDF** — opens a clean, print-friendly version of the results

## Getting started

No install, build step, or server required.

1. Clone or download this repository
2. Open `index.html` in any modern browser (Chrome, Safari, Edge, Firefox) — double-clicking the file works fine
3. Enter a student name, pick a passage, and select **Begin test**

The app is plain static HTML/CSS/JS — `index.html` loads `styles.css` and `script.js` alongside it, so keep all three files in the same folder.

## Project structure

```
.
├── index.html    # markup and screen structure
├── styles.css    # all styling
├── script.js     # passages data, timer, word counts, and submission logic
└── README.md
```

## Configuration

**Passages** — edit the `PASSAGES` array near the top of `script.js` to add, remove, or edit passages. Each entry needs an `id`, `title`, `theme`, `heading`, and an array of `paragraphs`.

**Timer length** — change the `TOTAL_SECONDS` constant in `script.js` (defaults to `18 * 60`).

**Word count requirements** — the 25–50 word summary range and 50-word opinion minimum are set in the `refreshCounts()` function in `script.js`.

**Results email** — the destination address is set in `finishTest()` in `script.js`, where the Gmail compose URL is built. Update the `to` address there to change where results are sent.

## How results get to the instructor

This app has no backend, so it can't send email on its own. Instead:

- **Email results to instructor** opens `mail.google.com` in a new tab with the recipient, subject, and full results already filled in — the student (or instructor) just needs to hit Send. This requires being signed into a Gmail account in that browser.
- If Gmail isn't available, use **Download results (.txt)** and attach the file to an email manually, or **Print / save as PDF** to keep a printable copy.

If you'd rather have results sent automatically with no manual step, that requires wiring up a backend or a form service (e.g. Formspree, EmailJS) — not included here by default.

## Browser support

Works in any modern evergreen browser. No dependencies, no `localStorage`/`sessionStorage` usage — all state lives in memory for the duration of the test, so refreshing the page starts over.

## License

Internal tool for ERC Academy. Contact the author for reuse outside the organization.

## Author

**Carlos Mercado** — ERC Academy
