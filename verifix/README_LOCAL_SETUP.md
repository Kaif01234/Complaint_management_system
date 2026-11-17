# VERIFIX local setup (Windows)

This guide connects the final dashboard to the FastAPI backend and your already-trained model. It does not require retraining.

## 1. Get the backend package

Use the previously prepared `Verifix_SIH26264_Final_Integrated_Package.zip` from this conversation. Extract its contents into a folder such as `C:\Verifix_SIH26264_Final`.

That package contains:
- `backend/api_server.py`
- `backend/requirements_api.txt`
- `audit/audit_multilingual_and_related_cases.py`
- `run_backend.bat`, `run_dashboard.bat`, and `copy_model_files.bat`
- `README_FINAL.txt`

The dashboard in that package is the same final build committed to this repository.

## 2. Copy your existing model files

Copy these three files from `C:\PS26264_Training_Output` into `C:\Verifix_SIH26264_Final\backend\models\`:

- `PS26264_continued_multilingual_model.zip`
- `PS26264_category_classifier.joblib`
- `PS26264_audit_summary.json`

Run `copy_model_files.bat` from the extracted package if the source folder is still `C:\PS26264_Training_Output`. Do not upload these model files to this public repository.

## 3. Start the backend

Open CMD in the extracted package root. Activate the existing training environment (adjust the path only if yours differs):

```bat
call "C:\PS26264_Local_Training_Kit\PS26264_Local_Training_Kit\.venv\Scripts\activate.bat"
python -m pip install -r backend\requirements_api.txt
run_backend.bat
```

Verify:
- `http://127.0.0.1:8000/api/health`
- `http://127.0.0.1:8000/docs`

Health should report that the encoder, classifier, SQLite database and validation threshold are loaded.

## 4. Start the dashboard

In a second CMD window:

```bat
cd /d C:\Verifix_SIH26264_Final
run_dashboard.bat
```

Open:
`http://127.0.0.1:5500/Verifix_SIH26264_Final_Dashboard.html`

## 5. Important limitations

- Training and evaluation data are synthetic; results are not real-world AICTE validation.
- Similarity and coordination scores are not probabilities.
- The model suggestion is decision support only. Human review remains mandatory.
- No automatic merge/closure or regulatory decisions are made.
- This is a local demo. Do not expose it publicly with real confidential complaints without authentication, role authorization, HTTPS, secure storage, privacy/security review and approved data access.
