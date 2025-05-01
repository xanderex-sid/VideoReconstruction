# Fine-tuning a Pretrained Masked Autoencoder (MAE) for Classification

## Introduction
This project utilizes a pretrained **Masked Autoencoder (MAE)** for image classification on a given dataset. The approach consists of 3 stages:
1. **Pre-training** the masked autoencoder with random masking. This model is then finetuned for downstream tasks.
2. **Linear Probing:** Training a classification head while keeping the pretrained MAE frozen.
3. **Full Fine-tuning:** Unfreezing the MAE and optimizing all model parameters for better performance.

## Pretraining Details

The MAE model was pretrained using a self-supervised learning approach by reconstructing masked image patches. The pretraining was conducted in two phases:  

1. **Without Augmentations** (100 epochs)  
2. **With Augmentations** (250 epochs)  

During pretraining with augmentations, validation loss (BCEWithLogitsLoss) quickly stabilized around **0.02** at approximately **20 epochs**, suggesting that augmentations primarily contributed to initial rapid learning but had limited long-term benefits. Consequently, epochs between **20 and 100** appeared ineffective.  

In total, **350 epochs** were run (**100 epochs with augmentations + 250 epochs without augmentations**).
Below are the loss curve and sample reconstructed images from pretraining:

### Pretraining Loss Curve with augmentation ( 1 - 100 epochs)
![Pretraining Loss Curve](../images/Task6A/task6A_loss_curve_withaug.png)

### Pretraining Loss Curve without augmentation ( 101 - 350 epochs)
![Pretraining Loss Curve](../images/Task6A/task6A_loss_curve.png)

### Pretraining (without aug) progression 
![Pretraining Progression](../images/Task6A/task6_pretraining_progression.png)

### Pretraining Output Samples
![Reconstructed Images](../images/Task6A/task6A_pretrain_img_map.png)

## Fine-tuning Approach
### 1. Linear Probing
- The pretrained MAE encoder is **frozen**, and only a newly added classification MLP is trained.
- This step evaluates how well the MAE encoder captures meaningful features.

### 2. Full Fine-tuning
- The entire model, including the MAE encoder, is **unfrozen** and fine-tuned end-to-end.
- This allows the encoder to adapt to the classification task.

### ROC-AUC Curves
#### Linear Probing ROC-AUC
![ROC-AUC Linear Probing](../images/Task6A/task6A_LP_ROC_AUC.png)

#### Full Fine-tuning ROC-AUC
![ROC-AUC Full Fine-tune](../images/Task6A/task6A_FT_ROC_AUC.png)

## Hyperparameters & Training Details
| Phase              | Optimizer  | Learning Rate | Scheduler  | # Parameters |
|-------------------|------------|--------------|------------|-------------|
| Linear Probing    | LARS      | 1e-3 (SGD Base)         | Cosine Annealing | ~200K  |
| Full Fine-tuning  | AdamW      | 9.5e-5 for encoder, 8e-4 for others         | Cosine Annealing | ~6.6M  |



