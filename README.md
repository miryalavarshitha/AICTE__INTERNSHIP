# AICTE__INTERNSHIP
# Garbage_classification

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
