# Cherry-Leaf-Disease-Classification-with-AlexNet-Modified-CNN
A deep learning project that classifies photos of cherry leaves into 5 conditions (four disease categories and healthy leaves) using a Convolutional Neural Network built from scratch. The project compares a manually implemented **AlexNet baseline** with a modified version using **Batch Normalization** and a smaller fully connected head.

## 📌 Project Overview

The project covers:

* Exploratory analysis of class distribution and image dimensions
* Stratified **70:15:15** train/validation/test split
* Image preprocessing and augmentation
* AlexNet implementation from scratch
* Modified AlexNet with Batch Normalization
* Model training and performance comparison

## 📊 Dataset

The dataset contains **3,642 images** across five classes:

| Class                    | Images |
| ------------------------ | -----: |
| Cherry Leaf Scorch       |  1,101 |
| Cherry purple leaf spot  |    987 |
| Cherry brown spot        |    614 |
| Cherry Normal leaf       |    500 |
| Cherry shot hole disease |    440 |

All images were **800×1000 pixels** in portrait orientation.

After splitting:

* Train: **2,547**
* Validation: **546**
* Test: **549**

The dataset is stored in a **Google Drive folder** and mounted directly to the notebook during execution.

## 🔧 Preprocessing

* Resized images to **224×224**
* Normalized pixel values to `[0,1]`
* Batch size: **32**
* Training augmentation with rotation, shifting, shear, zoom, and horizontal flipping
* Validation and test sets were only rescaled

## 🧠 Models

### Baseline AlexNet

* Convolutional layers: 96 → 256 → 384 → 384 → 256 filters
* Fully connected layers: 4096 → 4096 → 5
* Dropout: 0.5
* **46.8M parameters**
* Adam optimizer
* 10 epochs

### Modified AlexNet

The modified model adds **Batch Normalization** and reduces the dense layers:

* Fully connected layers: 1024 → 512 → 5
* Dropout: 0.5
* **~10.8M parameters**
* Early Stopping

## 📈 Results

| Model            | Best Val. Accuracy |              Test Accuracy |
| ---------------- | -----------------: | -------------------------: |
| Baseline AlexNet |              64.8% |                  **61.0%** |
| Modified AlexNet |          **68.1%** | *Pending final evaluation* |

Baseline test performance:

* Precision: **60.1%**
* Recall: **61.0%**
* F1-score: **58.9%**

The modified model achieved a higher validation accuracy but showed considerable validation instability.

## 🔍 Key Takeaways

* The large **46.8M-parameter** baseline was challenging to train from scratch with limited training data.
* Batch Normalization and a smaller dense head significantly reduced model size.
* The modified model achieved a higher best validation accuracy (**68.1% vs. 64.8%**).
* Further tuning is needed to improve training stability and generalization.

## 🛠️ Tech Stack

**Python · TensorFlow/Keras · scikit-learn · NumPy · Pandas · Matplotlib · Seaborn · Pillow · split-folders**

## 📁 Project Structure

```text
Cherry-Leaf-Disease-Classification/
├── CherryLeavesClassification.ipynb
└── README.md
```

The notebook mounts the Google Drive folder containing the dataset, so the image dataset itself is **not stored in the GitHub repository**.
Google Drive Link: https://drive.google.com/file/d/18pyOingkl0WfblKZdT25eBzZW8VMaWJj/view?usp=sharing

## 🚀 Future Improvements

* Use transfer learning with **EfficientNet, ResNet, or DenseNet**
* Tune learning rate and scheduling
* Apply class weighting
* Preserve image aspect ratio
* Train with more stable hyperparameters
* Add confusion matrix and per-class evaluation
* Repeat experiments with fixed seeds

## 📚 References

* Krizhevsky, Sutskever & Hinton — *ImageNet Classification with Deep Convolutional Neural Networks*
* TensorFlow/Keras documentation
* Cherry leaf disease dataset source
