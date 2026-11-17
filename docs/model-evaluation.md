# VERIFIX — Model and evaluation note

## Training data and task

- **Training records:** 1,020 synthetic complaint examples.
- **Scenario design:** 340 underlying scenarios represented in English, Hindi and Hinglish.
- **Classifier labels:** 17 complaint categories.
- **Model component:** continued multilingual Sentence-BERT encoder plus a separate 17-class category classifier.

The three language variants for a scenario are translations/rewrites of the same synthetic scenario. The dataset is not a collection of real AICTE complaints.

## Category classification results

| Model checkpoint | Validation accuracy | Test accuracy |
|---|---:|---:|
| Earlier checkpoint | 72.55% | 69.28% |
| Continued checkpoint | 80.39% | 73.86% |

These are category-classification accuracies on the synthetic dataset. They should not be interpreted as duplicate-detection accuracy or expected accuracy on real AICTE data.

## Related-case matching audit

The validation-selected raw cosine similarity threshold was approximately **0.4701**.

| Split | Proxy positive pairs | Proxy negative pairs | Precision | Recall | F1 |
|---|---:|---:|---:|---:|---:|
| Validation | 81 | 702 | 60.75% | 80.25% | 69.15% |
| Test | 108 | 873 | 65.51% | 87.96% | 75.10% |

**Important benchmark limitation:** the related-pair target is a synthetic same-institution/same-category proxy. It is not a human-verified ground-truth label for duplicate or related complaints. Accordingly, these metrics are useful only as an initial prototype audit, not a claim of real-world detection performance.

The threshold applies to the raw semantic cosine similarity, not to the dashboard's weighted `totalPercent` coordination signal.

## Cross-language similarity check

Average cosine similarities observed for translated versions of the same scenarios:

| Language pair | Average cosine similarity |
|---|---:|
| English–Hindi | 0.8836 |
| English–Hinglish | 0.9464 |
| Hindi–Hinglish | 0.8861 |

These values are a synthetic translation consistency check, not a real-world multilingual complaint retrieval evaluation.

## Interpretation and safeguards

- The weighted coordination score is a ranking/coordination signal, **not a probability**.
- The category classifier's top scores are not calibrated probabilities.
- Institution identity and matching signals help identify candidates; they do not prove that two complaints are related.
- Model suggestions are for officer assistance only. Relationship confirmation or dismissal remains a human decision.
- The system does not automatically merge complaints, close cases or make regulatory decisions.
- Further evaluation requires representative, consented/approved real-world data and human-annotated related-case judgments, with institution-level and temporal leakage controls.
