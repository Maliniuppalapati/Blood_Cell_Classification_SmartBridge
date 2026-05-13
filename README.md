🔬 WBC-Vision AI: White Blood Cell Classification Engine 🩸
📌 Project Overview

WBC-Vision AI is a deep learning–based computer vision system designed to automate the classification of white blood cells from microscopic blood smear images.

Manual WBC identification is time-consuming and subject to human variability. This project leverages transfer learning to deliver fast, consistent, and accurate multi-class classification, supporting hematological diagnostics.

🚀 Key Features
🧠 Transfer Learning Architecture: Built on MobileNetV2 (ImageNet pre-trained) for efficient feature extraction.
⚙️ Fine-Tuned Model: Top 50 layers unfrozen to capture domain-specific cellular patterns.
🔄 Data Augmentation Pipeline: Rotation, zoom, shear, and flipping to improve generalization and reduce overfitting.
📊 Model Evaluation: Confusion Matrix & Classification Report (Precision, Recall, F1-Score).

🛠️ Technical Stack
* Framework: TensorFlow / Keras
* Data Processing: NumPy, OpenCV
* Visualization: Matplotlib, Seaborn
* Model Architecture: MobileNetV2
* Optimizer: Adam (Learning Rate: 1e-4)

📊 Dataset Specifications
* Dataset: Blood Cell Images (Kaggle / dataset2-master)
* Total Samples: 12,444 images
* Training Split: 9,957
* Validation Split: 2,487

Target Classes: Eosinophil, Lymphocyte, Monocyte, Neutrophil

📈 Model Performance
* Training Epochs: 25
* Validation Accuracy: 81%

| Class | Precision | Recall | F1-Score |
|---|---|---|---|
| Eosinophil | 0.91 | 0.77 | 0.83 |
| Lymphocyte | 0.99 | 0.78 | 0.87 |
| Monocyte | 0.95 | 0.76 | 0.85 |
| Neutrophil | 0.60 | 0.94 | 0.73 |

✅ Key Insight:
The model achieves 94% recall for Neutrophils, minimizing missed detections of critical infection-fighting cells—an important factor in medical screening systems.

📂 Project Structure
├── Blood_Cell_Classification.ipynb  # Training, visualization & evaluation
├── requirements.txt                 # Dependencies  
├── .gitignore                       # Git ignore file for datasets and models
└── README.md                        # Documentation  

💻 How to Use

1. Clone the repository
```bash
git clone https://github.com/yourusername/Blood_Cell_Classification_SmartBridge.git
cd Blood_Cell_Classification_SmartBridge
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Setup Dataset
Ensure your dataset is placed in the project folder. The code automatically detects if it's running locally or on Google Colab, and adjusts the paths accordingly.

4. Run the Project
Open `Blood_Cell_Classification.ipynb` in Jupyter Notebook or Google Colab and execute the cells sequentially to train the model, visualize the results, and save the `.h5` model.

🛡️ Future Enhancements
* Deploy as a web application using Flask / FastAPI or Streamlit
* Convert model to TensorFlow Lite (.tflite) for mobile diagnostics
* Extend classification to RBCs and Platelets
* Integrate real-time microscope image input
