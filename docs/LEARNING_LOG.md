# Learning Log

A running log of concepts learned, decisions made, and things that went wrong
(and how they got fixed) while building this project. Interviewers love hearing
about the debugging, not just the final result — so don't skip the messy parts.

## Format for each entry

```
### [Date] Topic

**What I learned / did:**

**Why it matters:**

**What confused me / what I'd do differently:**
```

---

<!-- Add entries below as the project progresses -->

### Sept 19, 2026 — First real EDA, and a major plan pivot

**What I learned / did:**

Created a Kaggle Notebook and connected the competition dataset to it (had to
debug the actual mount path — it was `/kaggle/input/competitions/<slug>/`, not
the `/kaggle/input/<slug>/` I first guessed). Loaded `train.csv` and
`train_series.csv` and looked at the real data for the first time: 4,407 studies,
24,371 series. Ran language detection on the report text and found 9 different
languages. Found that only 58 studies (1.3%) have real labels — the rest only have
a radiology report.

**Why it matters:**

The original plan assumed there'd be enough labeled data to fine-tune a CNN
directly. There isn't — 58 examples is nowhere near enough. This is a weak
supervision problem: build something that extracts labels from the report text,
validate it against the 58 known-correct examples, then use it to generate
training labels at scale for the image model. Also learned about negation in
clinical text (e.g. "no evidence of a tear" vs "a tear") — a real, well-known NLP
challenge, not something I'd have thought to check for without looking at real
report text closely.

**What confused me / what I'd do differently:**

<!-- fill in your own take here -->

