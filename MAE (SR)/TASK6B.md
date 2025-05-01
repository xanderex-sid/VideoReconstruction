## Task VI.B: Super-Resolution Fine-Tuning  

### Description  
Take the pre-trained model from **Task VI.A** and fine-tune it for a **super-resolution task**. The model should be trained to **upscale low-resolution strong lensing images** using the provided high-resolution samples as ground truths.  

### Implementation  
- Use **PyTorch** or **Keras** to implement the fine-tuning approach.  
- Discuss your **training strategy**, including data preprocessing, loss functions, and optimization techniques.  

### Dataset  
[Download Here](https://drive.google.com/file/d/1uJmDZw649XS-r-dYs9WD-OPwF_TIroVw/view?usp=sharing)  

#### Dataset Description  
The dataset consists of **simulated strong lensing images** with no substructure at multiple resolutions:  
- **High-Resolution (HR)** images  
- **Low-Resolution (LR)** images  

### Evaluation Metrics  
Your model will be evaluated using the following metrics:  
- **MSE (Mean Squared Error)**  
- **SSIM (Structural Similarity Index)**  
- **PSNR (Peak Signal-to-Noise Ratio)**  

Ensure that your fine-tuned model effectively reconstructs high-resolution images with minimal distortion and loss of detail.

