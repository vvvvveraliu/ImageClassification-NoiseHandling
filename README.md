
# Predictive Modeling for Handling Imperfect Labels in Image Classification

### Project Goal 
This project mainly focuses on carrying out model evaluation and selection for predictive analytics on an imbalanced image data. We deal with a classification problem, where the training labels are not perfect, which is a common phenomenon in data science. Getting accurate ground true labels can be costly and time-consuming, and even impossible sometimes. So in this project, we address the issue with imperfect labels. In particular, we are going to train a predictive model where label noises exist.

### Dataset
We worked on a noisy version of "CIFAR-10" dataset. The original CIFAR-10 dataset consists of 32x32 colour images in 10 classes. For this project, random noises have been added to original dataset and we only have access to a small subset of clean labels. In particular, we have a training set with 50,000 images with:
* noisy labels for all images 
* clean labels for the first 10,000 images 

### Challenge
Our goal is to build a predictive model for image classification using the imperfect dataset provided. Considering practical effectiveness, we concern a lot about the balance between the complexity of variable/features/models used and the predictive performance.

To perform the classification, a baseline logistic regression model that uses RGB color histogram features and treats the training set as if it has clean labels is a common practice. However, 
the overall performance of this baseline model is not satisfactory mainly due to two reasons: 
1. the model and feature extractor used is not sophisticated enough. The toyish model we used for baseline is barely for the purpose of illustrating the workflow of building a predictive models for CIFAR-10 dataset. Therefore, we should consider a more complex model that will give a better prediction performance
2. we treat the noisy labels with error as if they are clean. Therefore, the model is actually learning from a untrustful source. We can address the second issue with a "label-correction" approach - before feeding the training set to the predictive model, they use the small set with both clean and noisy label to train a label-correction model.

### Implementation 
To improve the model performance, we will implement the following two models: 
* Model I: We need a more sophisticated model (e.g. neural networks) than the baseline, while still treats the noisy labels as clean ones;
* Model II: We can use exactly the same predictive model as in Model I, but add some extra models or procedures to address the label noise issue.

You can find more details about the implementation (here)[https://github.com/vvvvveraliu/ImageClassification-NoiseHandling/blob/main/main.ipynb] 

### Results

* Baseline: Logistic Regression model gives a low accuracy of around 24%
* Model I:  We explored different models including Decision Trees, Random Forest, KNN, Naive Bayes, and CNN, and we selected CNN as it gives the best accuracy of about 47.6%
* Model II: We applied a VGG network to clean the noisy labels and then applys same method of Model I. It boosts the perfomance of reaching accuracy to around 58.3%

You can find more details about the result (here)[https://github.com/vvvvveraliu/Predictive-Modeling-Image-Classification/blob/main/Predictive_modeling.pdf] 
