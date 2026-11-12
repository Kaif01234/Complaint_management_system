# Complaint Management System — Verifix (SIH26264)

**Verifix** is an AI-assisted institutional complaint coordination prototype for SIH 2026 problem statement **SIH26264**: an integrated dashboard for monitoring and tracking institution-related complaint cases across AICTE Bureaus/Cells.

## Features
- Five-section dashboard: Overview, Complaint Management, Complaint Details, Relationship Overview, and Analytics.
- Fine-tuned multilingual Sentence-BERT inference for English, Hindi, and Hinglish complaint text.
- Institution-aware candidate matching using AICTE Permanent ID or normalized institution name.
- Related-case ranking and a separate 17-class category suggestion.
- FastAPI service for similarity, related-case suggestions, category prediction, case persistence, metrics, and audit endpoints.
- SQLite persistence for cases, case events, and officer relationship decisions.
- Human-in-the-loop confirmation/dismissal; no automatic merging or regulatory decisions.

## Quick start (Windows)
1. Download or clone this repository.
2. Extract the companion project package into the repository root. It creates the `verifix/` folder containing the application source.
3. Follow `verifix/README_FINAL.txt`.
4. Place your local trained model files in `verifix/backend/models/`: `PS26264_continued_multilingual_model.zip`, `PS26264_category_classifier.joblib`, and `PS26264_audit_summary.json`.
5. Run `verifix/copy_model_files.bat` if your outputs are in `C:\PS26264_Training_Output`.
6. Start `verifix/run_backend.bat`, then in another terminal run `verifix/run_dashboard.bat`.
7. Open `http://127.0.0.1:5500/Verifix_SIH26264_Final_Dashboard.html`.
8. Verify `http://127.0.0.1:8000/api/health` and `http://127.0.0.1:8000/docs`.

## Model and data notes
Model weights, the joblib classifier, audit output, and SQLite data are local artifacts and must not be committed. Training and audit data are synthetic; reported metrics are proof-of-concept results, not validated real-world AICTE performance. The dashboard's 18 visible complaint records are illustrative, not live AICTE records.

## Safety and deployment limitations
- Similarity values and the weighted coordination score are not probabilities.
- Same-institution matching only generates candidates; it does not prove that two complaints are related.
- Every suggested relationship requires authorized human review.
- No automatic case merge, closure, or regulatory decision is performed.
- This is a local demonstration prototype. Do not expose it publicly or process confidential complaint data without authentication, role-based authorization, HTTPS, backups, privacy review, security controls, and approved data access.

## Problem statement
SIH 2026 — **SIH26264**, Integrated Dashboard for Monitoring and Tracking Institution-Related Complaint Cases Across AICTE Bureaus/Cells.

Team: **Verifix** · Team ID: **SIH-2026-493**

> **Repository update note:** The full source package is provided separately as `Complaint_management_system_Verifix_Repo_Update.zip`. Extract its contents into this repository root to add the complete `verifix/` project folder.
