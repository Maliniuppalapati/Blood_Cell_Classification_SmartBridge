# 🔬 Aetheria-HematoAI: Blood Cell Detection & Classification
Web App | Python | YOLO11 | Flask

A machine learning web app that predicts and classifies blood cells (Red Blood Cells, White Blood Cells, and Platelets) in microscopic images — deployed with an interactive Flask web interface.

## 🌐 Live Demo
🔗 [Click here to try the app](https://github.com/Maliniuppalapati/Blood_Cell_Classification_SmartBridge)

Upload a microscopic blood smear image to get real-time bounding box annotations, cell counts, and an instantly downloadable PDF analysis report.

## 🔍 Problem Statement
Manual counting and classification of blood cells under a microscope is time-consuming, repetitive, and prone to human error, which can delay critical clinical diagnoses. 

This project builds an automated end-to-end computer vision pipeline using YOLO11 to locate and classify blood cells with high precision. By providing a clean web interface, it assists lab technicians, medical students, and counselors in performing rapid cell counting and generating patient reports.

## 📂 Project Structure
```text
Aetheria-HematoAI/
├── app.py                        # Flask web application & server
├── train.py                      # YOLO11 model training pipeline
├── data.yaml                     # YOLO dataset configuration paths
├── yolo11n.pt                    # Pre-trained base YOLO11 weights
├── requirements.txt              # Python dependencies (flask, ultralytics, reportlab...)
├── data/                         # Train/Val microscopic dataset
├── runs/                         # Training logs and weights
│   └── detect/
│       └── train/
│           └── weights/
│               ├── best.pt       # Trained best model weights
│               └── last.pt       # Trained last epoch weights
├── static/                       # CSS files, Javascript, and upload directories
└── templates/                    # HTML template views (index.html)
```

## 🛠 Tech Stack
| Layer | Tools |
| :--- | :--- |
| **Language** | Python 3.13 |
| **Object Detection** | YOLO11 (Ultralytics) |
| **Deep Learning** | PyTorch (CPU-optimized) |
| **Web Server** | Flask |
| **Report Generation** | ReportLab (for PDF exports) |
| **Model Storage** | PyTorch serialized weights (.pt) |
| **Frontend Styling** | Custom CSS |

## 📊 Methodology & Labeled Dataset

### 1. Dataset Characteristics & Labeled Count
The model was validated on a dataset of blood smear images with annotated cell instances. The size of the dataset validation split is:

*   **Total Labeled Images:** 73
*   **Total Cell Instances Labeled:** 967 cells
    *   🔴 **Red Blood Cells (RBC):** 819 instances across 72 images
    *   🟡 **Platelets:** 76 instances across 42 images
    *   ⚪ **White Blood Cells (WBC):** 72 instances across 71 images

### 2. Model Training
* Trained a **YOLO11n** model for **10 epochs** (completed in **0.927 hours**).
* Kept track of loss functions (`box_loss`, `cls_loss`, and `dfl_loss`) to optimize localization boundaries.

### 3. Model Performance Evaluation
Evaluating the `best.pt` model on validation images yielded the following metrics:

| Class | Images | Instances | Precision (P) | Recall (R) | mAP50 | mAP50-95 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **All Classes (Combined)** | **73** | **967** | **85.2%** | **92.2%** | **91.3%** | **64.0%** |
| ⚪ **WBC (White Blood Cells)** | 71 | 72 | 96.7% | 100.0% | 97.0% | 79.5% |
| 🔴 **RBC (Red Blood Cells)** | 72 | 819 | 80.8% | 81.8% | 89.4% | 63.9% |
| 🟡 **Platelets** | 42 | 76 | 78.3% | 94.7% | 87.5% | 48.7% |

### 4. Deployment & Report Generation
* Saved the best weights as `best.pt`.
* Built an interactive Flask application (`app.py`) for drag-and-drop image uploads.
* Implemented a **ReportLab** PDF generation routine to auto-create clinical summary files based on prediction cell counts.

## 🔑 Key Findings
* **White Blood Cells (WBC)** achieved the highest accuracy with **96.7% Precision** and **100% Recall** due to their large morphology and distinct characteristics.
* **Platelets** showed extremely high sensitivity (**94.7% Recall**), ensuring very few platelets go undetected during scans.
* The system performs inference efficiently on standard consumer CPUs, taking only **~109.4ms** per microscopic image.
* Automated bounding boxes allow lab clinicians to obtain instant counts of RBCs, WBCs, and Platelets in seconds rather than minutes.

## 🎯 Inputs & Outputs
* **Input:** Microscopic blood smear image file (`.jpg`, `.jpeg`, `.png`)
* **Output:** Interactive preview of annotated bounding boxes, class count breakdown, and a downloadable PDF analysis report.

## 🚀 Run Locally

```bash
# 1. Clone the repository
git clone https://github.com/Maliniuppalapati/Blood_Cell_Classification_SmartBridge.git
cd Blood_Cell_Classification_SmartBridge

# 2. Set up and activate virtual environment
python -m venv venv
venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch the Flask web server
python app.py
```
*Open your browser and navigate to `http://127.0.0.1:5000` to interact with the application.*

## 🔮 Future Improvements
* Integrate data augmentation to improve Platelet precision.
* Extend detection classes to separate WBC sub-types (e.g., Lymphocytes vs Neutrophils).
* Integrate medical history logging with a secure clinician dashboard database.
* Export report graphs visualizing cell distributions directly in the PDF reports.

## 👤 Author
**Malini Uppalapati**

[GitHub](https://github.com/Maliniuppalapati)
