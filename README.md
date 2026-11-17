# VERIFIX — AICTE Complaint Coordination Dashboard (SIH26264)

**Smart India Hackathon 2026 · Problem Statement SIH26264**  
**Team:** VERIFIX · **Team ID:** SIH-2026-493

## Problem and solution

AICTE complaints about the same institution can reach different bureaus or cells. VERIFIX is a decision-support prototype that gives officers a consolidated view of complaints and surfaces potentially related cases for human verification.

## What the prototype demonstrates

- Complaint dashboard with overview, management, case details, relationship analysis and analytics.
- Multilingual semantic representations for English, Hindi and Hinglish complaint text using Sentence-BERT.
- Institution-aware candidate matching using institution Permanent ID, with normalized-name fallback.
- A separate 17-class model category suggestion.
- Officer confirmation or dismissal of suggested relationships with audit history.
- SQLite persistence in the local prototype.

**Human control:** Similarity is a coordination signal, not a probability or proof that two complaints are duplicates. Every suggested relationship requires officer review. The system does not automatically merge, close or decide complaints.

## Repository contents

| Path | Purpose |
|---|---|
| `index.html` | Main dashboard entry point |
| `backend/verifix-backend-source.zip` | Backend source archive containing `api_server.py` and `requirements_api.txt` |
| `backend/models/README.md` | Required local model files and placement |
| `docs/model-evaluation.md` | Training and evaluation results, methodology notes and limitations |
| `.gitignore` | Excludes model binaries, local data and runtime files |

## Run the integrated prototype locally

1. Clone this repository and extract `backend/verifix-backend-source.zip` into the `backend/` folder. It should create `backend/api_server.py` and `backend/requirements_api.txt`.
2. Place the three local model artifacts listed in [backend/models/README.md](backend/models/README.md) into `backend/models/`.
3. In a terminal, run:

   ```bash
   cd backend
   python -m pip install -r requirements_api.txt
   uvicorn api_server:app --host 127.0.0.1 --port 8000
   ```

4. In a second terminal, from the repository root, serve the dashboard:

   ```bash
   python -m http.server 5500
   ```

5. Open `http://127.0.0.1:5500/`. Check the API at `http://127.0.0.1:8000/api/health` and its interactive docs at `http://127.0.0.1:8000/docs`.

The dashboard can be inspected as a static HTML prototype, but live AI inference and SQLite synchronization require the local API and model artifacts. This repository does not host the trained weights or a public inference service.

## Model and data limitations

The training and audit dataset is synthetic (1,020 records across English, Hindi and Hinglish). The reported metrics are proof-of-concept results, not evidence of real-world AICTE performance. The related-case benchmark uses a synthetic same-institution/same-category proxy rather than human-verified duplicate labels. See [the evaluation note](docs/model-evaluation.md).

The complaints preloaded in the dashboard are illustrative samples, not live AICTE records.

## Safety and deployment status

This is a local SIH demonstration prototype, not a production AICTE system. It does not include production authentication, role-based authorization, secure document storage or deployment hardening. Do not use it with confidential real complaints or expose the API publicly without appropriate approvals and security controls.
