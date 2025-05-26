# RetinaDetect

**RetinaDetect** is a project coded using **Python** and **Jupyter Notebook**. It is focused on detecting blood vessels
on images of eye fundus. The aim of this project was to create such program that takes image as input and returns
black and white image with blood vessels displayed as white pixels and anything else as black pixels.

## Input

There are **3 types of images** that can be associated with each image:

1. **Original image** - actual photos made in lab
2. **Gold standard** - black and white image where vessels were carefully selected by an expert
3. **Mask** - black and white image used to restrict region of interest to where the eye actually is on the image

## Approaches

### Image Processing

The following processing was applied:

- RGB channel extraction (green channel seemed to carry the most significant information)
- gaussian filter (used for noise reduction)
- frangi filter (used to detect and enhance vessel-like structures)
- pixel normalization (to a 0 to 1 range)
- thresholding (to set as white only pixels which value exceeds a certain threshold)

### Machine Learning

Training set is made of several dozen images from which **5x5** shaped fragments are randomly chosen.

The size of the training set is limited to only **100,000** due to computational resource constraints,
as a larger set would result in excessive processing time.

This data is then fed into **RandomForestClassifier** from **sklearn** library.

## Results

|             | Image Processing | Machine Learning |
| ----------- | ---------------- | ---------------- |
| accuracy    | 96,38 %          | 85,43 %          |
| recall      | 85,5 %           | 63,84 %          |
| specificity | 97,31 %          | 87,27 %          |
| precision   | 72,97 &          | 29,88 %          |
