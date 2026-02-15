
# Glaucoma Detection with ResNet50

This project focuses on automated glaucoma detection from retinal fundus images
using a deep learning approach.

## Model
- Architecture: ResNet50
- Output: Binary classification (glaucoma / normal)

## Dataset
- Source: ACRIMA
- Split: 80% training / 20% testing
- Split lists saved for reproducibility

## Training Strategy
- Initial training with standard split
- Evaluation on independent test set
- False Negative analysis
- Hard Example Mining
- Mini fine-tuning on FN samples

## Final Results (Test Set)
- Accuracy: 100%
- Precision: 100%
- Recall: 100%
- F1-score: 100%
- ROC-AUC: 100%

## Files
- glaucoma_resnet50.pth              → base model
- glaucoma_resnet50_finetuned.pth    → final model
- train_files.txt / test_files.txt   → data split
- results.txt                        → evaluation results
- experiment.json                    → experiment configuration

## Notes
Results are obtained on same-source data.
External validation is recommended for generalization.
