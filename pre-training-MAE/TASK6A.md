# Specific Test VI: Foundation Model  

## Task VI.A: Masked Autoencoder (MAE) Pre-Training and Fine-Tuning  

### Description  
Train a **Masked Autoencoder (MAE)** on the **no_sub** samples from the provided dataset to learn a **feature representation** of strong lensing images. The MAE should be trained to **reconstruct masked portions** of input images.  

Once this **pre-training** phase is complete, fine-tune the model on the **full dataset** for a **multi-class classification task** to distinguish between the three classes:  
- **no_sub** (no substructure)  
- **cdm** (cold dark matter substructure)  
- **axion** (axion-like particle substructure)  

### Implementation  
- Use **PyTorch** or **Keras** to implement both the **MAE pre-training** and the **classification fine-tuning**.  
- Discuss your **training strategy**, including model architecture, data preprocessing, loss functions, and optimization techniques.  

### Dataset  
[Download Here](https://drive.google.com/file/d/1znqUeFzYz-DeAE3dYXD17qoMPK82Whji/view?usp=sharing)  

#### Dataset Description  
The dataset consists of **simulated strong lensing images** categorized into three classes:  
1. **no_sub** – No substructure  
2. **cdm** – Cold dark matter substructure  
3. **axion** – Axion-like particle substructure  

### Evaluation Metrics  
Your model will be evaluated using the following metrics:  
- **ROC Curve (Receiver Operating Characteristic curve)**  
- **AUC Score (Area Under the ROC Curve)**  

