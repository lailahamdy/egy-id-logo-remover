# Logo Removal from Egyptian ID

## Task by: Laila Masoud

### Introduction
In this task we are given a picture of an Egyptian national id, the task is to remove the logo of جمهورية العربية مصر and replace it with the color of its background.

### Approach
#### Machine Learning Approach
After trying OCR models like tesseract and ArabicOCR, it was found that the logo text wasn't correctly detected and the approach of OCR wasn't the best so opting for an object detection task was found more suitable.

**Steps:**
1. Finding a dataset of Egyptian ids.
2. Annotating the dataset using Roboflow and applying preprocessing and augmentation if needed.
3. Training a YOLOv8 model on the annotated dataset. [The trained model can be found here.](https://drive.google.com/file/d/1umXnJIPCR6dOy6ERogtlfrZko2aq6xea/view?usp=sharing)
4. Using OpenCV for replacing the logo with the background.

#### Feature Detection using SIFT Approach
We can also follow the traditional approach to use well-established CV techniques such as feature descriptors like SIFT, this method is robust to changes in scale, rotation, and affine transformations.

**Steps:**
1. Loading a query image (the id) and a template image (the logo).
2. Extracting keypoints and descriptors in both images using SIFT.
3. Using a feature matching technique like FLANN and performing k-NN to find the best matches.
4. Applying the ratio test to filter out poor matches.
5. Calculating the homography matrix to locate the logo in the query image.
6. Creating a mask for the logo region in the query image.
7. Using OpenCV inpainting to fill the masked region.
8. Applying Gaussian blur to blend the inpainted region with the surrounding area.
