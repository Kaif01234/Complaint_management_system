# Local model files (not tracked by Git)

The backend expects the following files in this directory:

1. `PS26264_continued_multilingual_model.zip` — continued multilingual Sentence-BERT model.
2. `PS26264_category_classifier.joblib` — 17-category classifier.
3. `PS26264_audit_summary.json` — validation-selected similarity threshold and audit summary.

Copy these from your local training output folder. The backend reads them from this directory by default. Keep them on your machine; model weights and serialized classifier files are intentionally excluded from the public repository.

The model zip is extracted by the backend on first startup. Do not commit the extracted model directory or generated cache files.
