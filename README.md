# AICTE__INTERNSHIP
# Garbage_classification
#WEEK-1
1.**Dataset Extraction:** The dataset (garbage_dataset.zip) is unzipped into the /garbage_dataset directory using Python's zipfile module.

2.**Image Dataset Loading:** The dataset is loaded from /garbage_dataset/archive/TrashType_Image_Dataset using TensorFlow’s image_dataset_from_directory:

  -600 images are found, divided into 6 classes.
  
  -80% (480 images) used for training.
  
  -20% (120 images) initially used as validation.
  
3.**Validation Split for Testing:**
  The original validation set is split into:
  
  -Test Set: First half (60 images)
  
  -Final Validation Set: Second half (60 images)
  
  -The test set is optimized using caching and prefetching for efficient evaluation.
  
4.**Class Names Check:**
    Class names are printed and confirmed to match:
    
    *['cardboard', 'glass', 'metal', 'paper', 'plastic', 'trash']*
    
5.**Visualizing Sample Images:**
  A batch of 12 images from the training dataset is displayed in a 4×3 grid using matplotlib. Each image is labeled with its class name to verify correct labeling    and   loading.
  
#WEEK-2

---

## ✅ 5. Visualizing Sample Images:

- Displayed a batch of **12 sample images from the training dataset**.
- Plotted using **matplotlib (4×3 grid)**.
- Each image labeled with its respective class name to verify correct labeling.

---

## ✅ 6. Data Preprocessing and Normalization:

- **Pixel Scaling:**  
  All image pixel values normalized from **[0, 255] to [0, 1]**.

- **Data Pipeline Enhancements (for training & validation sets):**
  - **Caching**
  - **Shuffling**
  - **Batching**
  - **Prefetching**

---

## ✅ 7. Model Building – CNN using EfficientNetV2B2:

- Utilized **EfficientNetV2B2** from TensorFlow Keras Applications.

- **Base Model Settings:**
  - `include_top=False` → Removed original classification head.
  - Using **pre-trained weights** for feature extraction.

- **Custom Layers Added:**
  - **GlobalAveragePooling2D**
  - **Dropout (0.2)**
  - **Dense (6 units + softmax activation)** for 6-class garbage classification.

- **Model Summary:**
  - Total Trainable Parameters: Approximately **7 million**

---

## ✅ 8. Model Compilation:

- **Optimizer:** Adam  
- **Loss Function:** Sparse Categorical Crossentropy  
- **Metric:** Accuracy  

```python
model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)
---


## ✅ 9. Model Training:

Model trained for **15 epochs** using the prepared **training** and **validation datasets**.

```python
history = model.fit(
    train_ds,
    validation_data=val_ds,
    epochs=15
)
---


## ✅ 10. Performance Evaluation:
Evaluated the final model on the Test Set (60 images).

python
Copy
Edit
test_loss, test_accuracy = model.evaluate(test_ds)
print(f"Test Accuracy: {test_accuracy}")
print(f"Test Loss: {test_loss}")
---


##✅ 11. Model Saving:
Saved the trained model for later deployment (planned for Week 3: Gradio Web App).

python
Copy
Edit
model.save("Effiicientnetv2b2.keras")
---
