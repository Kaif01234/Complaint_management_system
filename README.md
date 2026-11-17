# Complaint Management System — VERIFIX (SIH26264)

**VERIFIX** is an AI-assisted institutional complaint coordination prototype for SIH 2026 problem statement **SIH26264**: an integrated dashboard for monitoring and tracking institution-related complaint cases across AICTE Bureaus/Cells.

## Repository contents
- `verifix/dashboard/Verifix_SIH26264_Final_Dashboard.html` — final five-section dashboard interface.
- The complete local integration package (FastAPI backend, audit script, SQLite setup, and Windows launchers) is provided separately as `Verifix_SIH26264_Final_Integrated_Package.zip`. Extract it to use the full application.

## Dashboard features
- Overview, Complaint Management, Complaint Details, Relationship Overview, and Analytics.
- Multilingual complaint matching for English, Hindi, and Hinglish through the Sentence-BERT service.
- Institution-aware candidate matching using Permanent ID or normalized institution name.
- Separate 17-class model category suggestion.
- Human review before relationships are confirmed or dismissed; no automatic merge.

## Local setup
For the full FastAPI + SQLite + model integration, follow `README_FINAL.txt` inside the integration package. Place your trained model files in `backend/models/`:
- `PS26264_continued_multilingual_model.zip`
- `PS26264_category_classifier.joblib`
- `PS26264_audit_summary.json`

Do not commit model weights, classifier binaries, private audit data, API tokens, or the local SQLite database. Keep trained model files on your machine.

## Model and evaluation limitations
The training and audit data used for this prototype are synthetic. Reported classification and similarity metrics are proof-of-concept results, not validated real-world AICTE performance. Similarity/coordination scores are not probabilities. Dashboard sample complaints are illustrative, not live AICTE records.

## Safety and deployment
Every relationship suggestion requires human review. The system does not make regulatory decisions or automatically merge/close complaints. This is a local prototype; production deployment requires authentication, role-based access, HTTPS, secure storage, backups, privacy/security review, and approved access to real complaint data.

## Problem statement
SIH 2026 — **SIH26264**, Integrated Dashboard for Monitoring and Tracking Institution-Related Complaint Cases Across AICTE Bureaus/Cells.

**Team:** VERIFIX · **Team ID:** SIH-2026-493
