Model Type | Train Data | Accuracy | Sensitivity | Specificity | AUC | F1 | mtry

rf.cv(100trees/25nodesize/10folds/0.63threshold)| downsampled | 0.7798205 | 0.7708548 | 0.7820084 | 0.8504582 | 0.5922998 | 28

rf.cv(100trees/25nodesize/10folds/0.62threshold)| downsampled 1hot dummies| 0.7796437 | 0.7703399| 0.7819141 | 0.8508873 | 0.5935158 | 35

Both of my rfs are just slightly worse (like 0.01) for both AUC and F1 - Harrison

xgb.cv(10folds/5tuneLength/.611...threshold) | downsampled | 0.8156416 | 0.6955458 | 0.8449492 | 0.8562062 | 0.5968023 | N/A

xgb.cv(10folds/5tuneLength/.644...threshold) | downsampled 1 hot dummies | 0.823972 | 0.6708290 | 0.8613009 | 0.8562651 | 0.5991721 | N/A

xgb.cv(5folds,5tuneLength, 0.618) | better downsampled | 0.8289 | 0.6453 | 0.8738 | 0.855 | 0.59716 | N/A

xgb.cv(5folds,5tuneLength,0.634) | better important downsampled | 0.8224 | 0.6702 | 0.8595 | 0.8556 | 0.5967959 | N/A

xgb.cv(5folds,5tuneLength,0.6703 | downsampled | 0.8289 | 0.6453 | 0.8737 | 0.8558 | 0.5966552 | N/A

Model Type | Train Data | Accuracy | Sensitivity | Specificity | AUC | F1 | threshold
log.cv(10 folds) | original | 0.8104 | 0.6795 | 0.8424 | 0.8422 | 0.5844 | 0.284
log.cv(10 folds) | downsampled | 0.8122 | 0.6755 | 0.8456 | 0.8442 | 0.5853 | 0.6221
log.cv(10 folds) | downsampled dummy-coded | 0.814 | 0.6692 | 0.8493 | 0.8449 | 0.5854 | 0.629
