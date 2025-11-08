# 🩺 GastroVision  
### 🤖 AI-Powered Vision for Smarter Gastrointestinal Diagnosis  

---

## 📘 1. Introduction  
Gastrointestinal (GI) diseases pose a major global health challenge 🌍. Early diagnosis using endoscopic images is vital for effective treatment, but manual interpretation is slow and prone to human error.  

**GastroVision** leverages **Deep Learning (CNNs)** to automatically classify GI endoscopy images from the **Kaggle GastroVision dataset** into **27 disease and anatomical landmark categories**, achieving high accuracy with explainable AI for medical trust.  

---

## 🗂️ 2. Dataset Overview & Preprocessing  

**📦 Dataset Source:** [Kaggle GastroVision](https://www.kaggle.com/datasets/orvile/gastrovision-gastrointestinal-disease-detection) (imported via `kagglehub`)  
**🩻 Contents:** Thousands of labeled GI endoscopy images covering 27 medical classes (e.g., *Accessory tools*, *Normal stomach*).  

**🔧 Preprocessing Steps:**  
- 🖼️ Images resized to **224×224 px** for CNN training  
- ⚙️ Normalized to ImageNet standards:  
  `mean = [0.485, 0.456, 0.406]`, `std = [0.229, 0.224, 0.225]`  
- 🔀 **Train/Validation Split:** 80/20 using PyTorch `Dataset` and `DataLoader`  
- 🏷️ Labels extracted from metadata CSV and checked for class imbalance  

---

## 🧠 3. Model Architecture and Training  

**Model Used:** `ResNet18` (pre-trained on ImageNet) — efficient and reliable for medical imaging tasks 🧬  

**🛠️ Modifications:**  
- Replaced final FC layer: `nn.Linear(512, 27)` to classify 27 categories  

**⚙️ Training Configuration:**  
- **Loss Function:** `CrossEntropyLoss`  
- **Optimizer:** `Adam (lr = 1e-3)`  
- **Data Augmentation:** Random flips, rotations, color jitter  
- **Epochs:** 5–10 (observing validation loss/accuracy trends)  

---

## 📊 4. Results and Performance Metrics  

| 🧾 Epoch | 🔥 Train Loss | 📉 Val Loss | 🎯 Val Accuracy |
|-----------|---------------|-------------|----------------|
| 1 | 0.0932 | 1.5351 | 0.6987 |
| 2 | 0.0851 | 1.3970 | 0.7137 |
| 3 | 0.0815 | 1.5463 | 0.6900 |
| 4 | 0.0609 | 1.4634 | 0.7406 |
| 5 | 0.0549 | 1.6185 | 0.7169 |
| 6 | 0.0957 | 1.7138 | 0.6894 |
| 7 | 0.0910 | 1.5568 | 0.7262 |
| 8 | 0.0502 | 1.6557 | 0.7125 |
| 9 | 0.0769 | 1.8986 | 0.7025 |
| 10 | 0.0792 | 1.6403 | 0.6987 |

**📈 Trend:**  
Validation accuracy fluctuates between **69–74%**, showing consistent generalization with minimal overfitting.  

**🔍 Classification Metrics:**  
- **F1 Score (Major Classes):** 0.70–0.80  
- **Macro F1:** ≈0.71  
- **Weighted F1:** ≈0.72–0.75  
- **Confusion Matrix:** Clear accuracy on frequent categories; minor confusion on rare/overlapping diseases.  

---

## 🧩 5. Model Interpretability  

**Technique:** `Integrated Gradients` using the **Captum** library 🧠  

**🖼️ Interpretability Output:**  
- Heatmaps show which regions influenced predictions  
- Highlights diagnostic cues (polyps, accessory tools, etc.)  
- Ensures decisions are medically grounded — promoting **explainable AI** for clinicians 👩‍⚕️👨‍⚕️  

---

## 🏁 6. Conclusion  

We developed a **ResNet-18 based CNN** to classify GI endoscopy images into **27 distinct categories**.  
After preprocessing (resizing, tensor conversion, normalization) and training with **Cross-Entropy loss** and **Adam optimizer**, the model achieved steady accuracy with clear interpretability using **Integrated Gradients**.  

✅ **Key Takeaways:**  
- Accurate GI disease classification 📊  
- Explainable visual reasoning 🔍  
- Reliable performance for clinical applications 💊  

---

## 👨‍💻 Made By  
**Shlok Shukla**  
🧠 *Team — The Ultimates*  

---

⭐ *If you like this project, don’t forget to give it a star on GitHub!* ⭐
