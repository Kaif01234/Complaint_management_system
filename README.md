# VERIFIX — AI Complaint Coordination Dashboard (SIH26264)

VERIFIX is an AI-assisted institutional complaint coordination prototype for SIH 2026 problem statement **SIH26264**: an integrated dashboard for monitoring and tracking institution-related complaint cases across AICTE Bureaus/Cells.

**Live dashboard:** GitHub Pages serves the final dashboard from `index.html`.

## Repository layout

- `index.html` — GitHub Pages entry point for the final dashboard.
- `verifix/dashboard/Verifix_SIH26264_Final_Dashboard.html` — same dashboard source in the project folder.
- `verifix/README_LOCAL_SETUP.md` — local setup guide for connecting the dashboard to the API and trained model.

## Dashboard features

- Overview, Complaint Management, Complaint Details, Relationship Overview and Analytics.
- Multilingual complaint analysis for English, Hindi and Hinglish through the Sentence-BERT backend.
- Institution-aware candidate matching using Permanent ID or normalized institution name.
- Separate 17-class category suggestions; model suggestions do not overwrite operational categories.
- Officer confirmation/dismissal of suggested relationships with audit history.
- No automatic case merging or regulatory decisions.

## Run with the AI backend (Windows)

The dashboard is also usable as a browser prototype, but live model inference and SQLite persistence require the FastAPI backend and your locally trained model files. Follow [the local setup guide](verifix/README_LOCAL_SETUP.md).

Required local model files (do not commit these to GitHub):
- `PS26264_continued_multilingual_model.zip`
- `PS26264_category_classifier.joblib`
- `PS26264_audit_summary.json`

## Model and evaluation limitations

Training and audit data are synthetic. The classification metrics and similarity threshold are proof-of-concept results, not validated real-world AICTE performance. Similarity and weighted coordination scores are not probabilities. The dashboard's visible sample complaints are illustrative, not live AICTE records.

## Safety and production readiness

Every relationship suggestion requires human review. The system does not automatically merge or close cases and does not make regulatory decisions. This is a local prototype. Production use requires approved data access, authentication, role-based authorization, HTTPS, secure storage, backups, privacy review, and security controls.

## Problem statement

SIH 2026 — **SIH26264**, Integrated Dashboard for Monitoring and Tracking Institution-Related Complaint Cases Across AICTE Bureaus/Cells.

**Team:** VERIFIX · **Team ID:** SIH-2026-493
