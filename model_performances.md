Model Type | Train Data | Accuracy | Sensitivity | Specificity | AUC | F1 | mtry

rf.cv(100trees/25nodesize/10folds/0.63threshold)| downsampled | 0.7798205 | 0.7708548 | 0.7820084 | 0.8504582 | 0.5922998 | 28

rf.cv(100trees/25nodesize/10folds/0.62threshold)| downsampled 1hot dummies| 0.7796437 | 0.7703399| 0.7819141 | 0.8508873 | 0.5935158 | 35

Both of my rfs are just slightly worse (like 0.01) for both AUC and F1 - Harrison

xgb.cv(10folds/5tuneLength/.611...threshold) | downsampled | 0.8156416 | 0.6955458 | 0.8449492 | 0.8562062 | 0.5968023 | N/A

xgb.cv(10folds/5tuneLength/.644...threshold) | downsampled 1 hot dummies | 0.823972 | 0.6708290 | 0.8613009 | 0.8562651 | 0.5991721 | N/A

xgb.cv(5folds,5tuneLength) | downsampled | 0.8289 | 0.6453 | 0.8738 | 0.855 | 0.59 | N/A
