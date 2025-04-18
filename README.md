
# 🚀 Duality-HackByte Object Detection using YOLOv8s

This project presents an optimized lightweight object detection pipeline built using **YOLOv8s** on the **HackByte Dataset**. It leverages advanced augmentation, tuned training parameters, and visual comparison scripts to evaluate model performance.

---

## 1. Dataset Download

Download and extract the official HackByte dataset from:

🔗 [HackByte_Dataset.zip](https://storage.googleapis.com/duality-public-share/Datasets/HackByte_Dataset.zip)

After extraction, you will find folders like:
- `ENV_SETUP`
---

## 2. Environment Setup

### For Windows Users:
1. Install [Anaconda](https://www.anaconda.com/products/distribution) (if not already installed).
2. Open **Anaconda Prompt**.
3. Navigate to the `ENV_SETUP` folder inside the dataset directory.
4. Run:
   ```bash
   setup_env.bat
   ```

This creates a Conda environment named `EDU` with all dependencies installed (YOLOv8, PyTorch, Albumentations, etc.).

### 🐧 For Mac/Linux Users:
Create a script named `setup_env.sh` with equivalent installation commands from `setup_env.bat` and execute:
```bash
bash setup_env.sh
```

> Or install dependencies manually using:
```bash
pip install -r requirements.txt
```

---

## 3. Model Training

### Steps to Train the YOLOv8s Model:

1. Activate the `EDU` environment.
2. Navigate to the directory containing `new_train.py`.
3. Run:
   ```bash
   python new_train.py
   ```

### 🔧 What This Does:
- Loads YOLOv8s with pretrained weights.
- Applies robust **Albumentations-based augmentations**.
- Uses **AdamW**, **Cosine LR decay**, and **early stopping**.
- Trains with custom augmentations and hyperparameters.

### Output:
- Final weights:  
  ```
  training_output/watermark_boosted/weights/best.pt
  ```
---

## 4. Prediction and Visual Comparison

### Run the Prediction Script:

```bash
python new_predict.py
```

This will:
- Load both the **base** and **optimized** models.

### 🖼️ Expected Output:
Side-by-side **visual comparison plots** of how each model performs on the same test images — no confidence scores, just **pure bounding box detection**.

---

## ⚠️ Requirements (Manual Install)

If you aren’t using the `.bat` or `.sh` scripts, install dependencies manually:

```bash
pip install ultralytics>=8.0.168
pip install albumentations opencv-python matplotlib
```

Ensure:
- Python ≥ 3.10
- PyTorch ≥ 2.0
- CUDA-compatible GPU (optional but recommended)

---

## 📈 How to Reproduce Final Results

1. Download and extract dataset.
2. Set up the environment using `setup_env.bat` or `setup_env.sh`.
3. Run training:
   ```bash
   python new_train.py
   ```
4. Run predictions:
   ```bash
   python new_predict.py
   ```
5. Check visual results in `comparisons/visual_comparisons`.

---

## 📊 Results Summary

| Model         | Training mAP | Valid mAP | Remarks                     |
|---------------|--------------|----------|------------------------------|
| Base YOLOv8s  | ~91.3%       | ~83%     | Strong baseline              |
| Optimized     | ~95%         | ~90.7%   | Faster, more robust visuals  |



## 📬 Final Thoughts

- The optimized YOLOv8s model balances **speed, accuracy, and simplicity**.
- Visual comparison helped validate that predictions were **qualitatively** stronger even when mAPs were similar.
- The pipeline is **easy to reproduce**, lightweight, and **customizable** for other detection tasks.

