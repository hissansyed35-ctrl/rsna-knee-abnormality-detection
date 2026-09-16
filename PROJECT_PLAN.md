# Project Plan: RSNA Knee Abnormality Detection

## 1. Motivation / Real-World Impact

Osteoarthritis affects over 600 million people worldwide, and the knee is the joint
most commonly affected. MRI is the diagnostic gold standard for detecting the
underlying abnormalities (ligament tears, meniscal injuries, cartilage loss, bone
marrow lesions, effusion, synovitis, cysts, and more), but reading and reporting on
every exam takes significant radiologist time — especially at the under-resourced
sites represented in this dataset. A model that reliably flags abnormalities could
help prioritize urgent cases and support radiologists globally, not just produce a
leaderboard score.

This project uses the real dataset released by RSNA and Kaggle for their 2026 AI
Challenge, rather than a cleaned-up toy dataset.

## 2. Competition Overview

- **Host:** RSNA (Radiological Society of North America) + Kaggle
- **Task:** Multilabel classification — detect 12 clinically important knee
  abnormalities per MRI exam
- **Data:** 5,000+ knee MRI exams from 16 institutions across 5 continents, each
  paired with its original radiology report (multiple languages)
- **Timeline:**
  - Launched: July 30, 2026
  - Entry / team-merger deadline: **Oct 15, 2026**
  - Final submission deadline: **Oct 22, 2026**
  - Winners announced: November 2026, recognized at the RSNA Annual Meeting
    (Nov 29 – Dec 3, 2026, Chicago)
- **Prizes:** $77,000 total pool, including a new efficiency track for lean models

Competing officially — registering on Kaggle and submitting to the real leaderboard.

## 3. Objectives

1. **Primary:** Build and submit a full 12-label multilabel deep learning model to
   the official Kaggle leaderboard before Oct 22, 2026.
2. **Learning objectives:** hands-on experience with medical imaging deep learning
   (DICOM processing, CNN transfer learning, multi-view MRI handling, class
   imbalance in a multilabel setting), a real git/GitHub workflow, and a
   reproducible ML project structure.
3. **Portfolio objective:** a clean, documented, public GitHub repo showing the full
   pipeline — EDA, preprocessing, modeling, evaluation, error analysis — that's
   ready to show employers.

## 4. Success Metrics

- **Competition metric:** to confirm exactly from the Kaggle "Evaluation" tab once
  data access is set up (typically a mean AUC or mean average precision across the
  12 labels for challenges like this) — first task in Week 1.
- **Personal bar:** a working end-to-end pipeline, at least one submission on the
  leaderboard, a model that clearly beats a naive baseline (e.g. predicting the
  label base rates), and a written report explaining what worked and what didn't.

## 5. Scope & Approach

Modeled on the well-known MRNet-style approach to knee MRI classification: 2D CNN
transfer learning applied per MRI slice/plane, aggregated to an exam-level
prediction, extended here to 12 simultaneous binary outputs instead of one.

- **Phase 1 — Baseline:** single-plane (e.g. sagittal) CNN (ResNet18 or
  EfficientNet, pretrained, fine-tuned) predicting all 12 labels at once.
- **Phase 2 — Multi-view:** ensemble across axial, sagittal, and coronal planes.
- **Phase 3 — Stretch:** bring in the radiology report text as an auxiliary signal
  (simple multimodal fusion).
- **Phase 4 — Stretch:** a compressed/distilled model for the efficiency track.

## 6. Roadmap (Sept 16 – Oct 22, 2026)

**Week 1 (Sept 16–22): Setup**
- GitHub repo live and pushed; Kaggle account created and competition joined
- Data downloaded (or accessed via Kaggle Notebooks)
- EDA: label distribution/imbalance, exam counts by site/language, image
  dimensions, missing data
- Confirm the exact evaluation metric and the official list of 12 abnormalities

**Week 2 (Sept 23–29): Baseline pipeline**
- Data loader for DICOM/MRI volumes, multilabel encoding
- Train/val split (stratified, exam-level — no patient/exam leakage)
- Baseline single-plane CNN trained end-to-end
- First submission to the Kaggle leaderboard

**Week 3 (Sept 30–Oct 6): Model improvement**
- Multi-view ensembling (axial + sagittal + coronal)
- Class imbalance handling (weighted loss / focal loss)
- Augmentation and hyperparameter tuning
- Lightweight experiment tracking (a results CSV or Weights & Biases)

**Week 4 (Oct 7–13): Refinement + error analysis**
- Per-abnormality error analysis — which of the 12 labels are hardest, and why
- Ensembling multiple model runs/architectures
- Cross-validation for robustness
- (Stretch) start on an efficiency-track compressed model

**Week 5 (Oct 14–22): Finalize**
- Oct 15: entry/team-merger deadline (solo entry — no action needed)
- Final model selection and final Kaggle submission before Oct 22
- Clean up the repo, finish the README and written report

## 7. Deliverables

- Public GitHub repo: EDA notebook, training/eval scripts, README, this plan, and a
  final written report
- At least one submission on the official Kaggle leaderboard
- A results write-up: what worked, what didn't, per-abnormality performance, and
  what you'd try next with more time

## 8. Risks / Open Questions to Resolve Early

- Confirm the exact 12 abnormalities and the official evaluation metric from the
  Kaggle "Data" and "Evaluation" tabs directly (not fully visible without being
  logged in) — do this in the first Kaggle session.
- MRI data volume is likely large (tens to hundreds of GB) — plan to do most
  training inside Kaggle Notebooks (free GPU quota, data pre-mounted there) rather
  than downloading everything to a laptop.
- DICOM/medical imaging tooling (pydicom, MONAI) has a learning curve — budget real
  time for this in Week 1, don't skip straight to modeling.
- Multilabel classification with imbalanced classes is genuinely harder than
  single-label problems — a mediocre Week 2 baseline score is normal and expected
  before the Phase 2/3 improvements land.

## 9. Learning Approach

This is a first major project and a genuine learning opportunity, not just a
resume line. Ground rules for how we'll work:

- Every new tool or concept (git, Kaggle, DICOM, CNNs, evaluation metrics, etc.)
  gets a plain-language explanation *before* we use it, not just the command to
  run.
- Decisions get explained, not just made — why a stratified split, why transfer
  learning, why this loss function.
- `docs/LEARNING_LOG.md` tracks what was learned and any mistakes/debugging along
  the way, in your own words where possible. This doubles as great interview
  material later ("tell me about a time you were stuck on a project").
