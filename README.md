# RSNA Knee Abnormality Detection

A deep learning project detecting 12 clinically important knee abnormalities from
MRI exams, built for the [RSNA Knee Abnormality Detection AI Challenge](https://www.kaggle.com/competitions/rsna-knee-abnormality-detection)
(RSNA + Kaggle, 2026).

## Why this project

Knee osteoarthritis affects over 600 million people worldwide, and MRI is the
diagnostic gold standard for the underlying injuries and conditions that cause it.
This project builds a multilabel classifier over a real, multi-institutional MRI
dataset (5,000+ exams from 16 sites across 5 continents) to flag 12 clinically
important abnormalities — the same task and data RSNA released for their 2026 AI
Challenge, with a $77,000 prize pool.

See [`PROJECT_PLAN.md`](PROJECT_PLAN.md) for the full objectives, scope, and
week-by-week roadmap through the competition's Oct 22, 2026 deadline.

## Status

🚧 In progress — project kicked off Sept 16, 2026. See `PROJECT_PLAN.md` for the
current phase.

## Project structure

```
.
├── PROJECT_PLAN.md      # objectives, scope, roadmap
├── data/
│   ├── raw/              # untouched competition data (gitignored)
│   └── processed/        # cleaned/preprocessed data (gitignored)
├── notebooks/             # EDA and exploratory notebooks
├── src/
│   ├── data/              # data loading & preprocessing code
│   ├── models/            # model architectures, training loops
│   └── utils/              # shared helpers
├── outputs/
│   ├── checkpoints/       # saved model weights (gitignored)
│   └── predictions/       # submission files (gitignored)
└── requirements.txt
```

Raw data and model weights are gitignored — this repo holds code, notebooks, and
documentation, not the (large) MRI dataset itself.

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# Kaggle API access (needed to download competition data)
# 1. Get an API token from https://www.kaggle.com/settings -> "Create New Token"
# 2. Save it to ~/.kaggle/kaggle.json
kaggle competitions download -c rsna-knee-abnormality-detection
```

## Results

_To be filled in as the project progresses — see `PROJECT_PLAN.md` for the current
roadmap phase._

## Acknowledgments

Dataset and competition: RSNA Knee Abnormality Detection AI Challenge, hosted on
Kaggle by RSNA in partnership with Kaggle, 2026.

## Author

Hissan Syed
