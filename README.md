# Emotion-FACSCodePrediction_ImageClassification_DL
This project demonstrated the use of DenseNet for predicting emotions and FACS codes from images. By performing data exploration, pre-processing, model training, and evaluation, we developed a robust model capable of predictions. 
### Introduction 
Our goal in this assignment was to anticipate emotions and the Facial Action Coding System (FACS) code that corresponds to each input image. Our dataset consists of labels with associated FACS code and their emotion. These labels are useful for developing and testing models. Throughout this study, we explore data exploration and pre-processing techniques to gain a deeper understanding of the dataset's characteristics, including the distribution of emotions and FACS codes. We also detail how to choose an appropriate model architecture, fine-tune its hyperparameters, and evaluate its performance using suitable metrics.
### Evaluation Framework

**a. Checked type of columns present in the dataset** - To understand the dataset features.<br/>
**b. Checked unique emotion type in the Dataset and its counts of existence.** By looking at the count and existence of emotion categories we can determine if the dataset is biased towards any kind and can handle it while doing the model architecture. From the output we realised that the model is biased towards negative emotion.<br/>
**c. Visualised images -** We used visualisation to determine whether the images were in RGB or grayscale, which was helpful in creating our model because some models only take RGB images. We learned from the visualisation that the datset contains few grayscale images. Therefore, this must be addressed during model architecture.<br/>
**d. Checked the number of occurrences of 1’s in each AU codes in the Dataset.** By looking at the count we can determine if the dataset is biased towards any kind and can handle it while doing the model architecture Observing the results, we found that the AU codes are very imbalanced as there are few codes which are above 100 and few below it. Hence need to be handled during model training.<br/>
**e. Checked the distribution of contrast in the images.** From the output we realised that most of the images are in the frequency of 80 - 100 contrast range.<br/>
**f. Relationship between each AU Codes and Emotion Type.** We are checking the counts of each FACS code for each type of emotion since the output is based on FACS and emotion type to determine whether the dataset is imbalanced.<br/>

### Approach
1. Custom Data Loader:
       <li>Generates batches of data and preprocesses it for model training and evaluation.</li>

3. Train-Test Split: 
    <li>Dataset split into 70% training, 15% validation, and 15% testing sets.</li>
    <li>Ensures sufficient data for training, fine-tuning, and evaluating the model.</li>

3.Data Generators Initialization:
    <li>Defined batch size as 32 and set image dimensions to (224, 224, 3).</li>
    <li>Applied data standardization, normalization, and augmentation (augmentation only for training data).</li>
    <li>Set number of classes to 3 for emotion classification.</li>

4. Model Definition:
    <li>DenseNet Model: Chosen for its efficient layer connectivity and reduced overfitting.</li>
    <li>Multi-output model: Handles emotion output, AU output, and image input.</li>
5. Model Compilation:
    <li>Optimizer: AdamW (includes weight decay to prevent overfitting).</li>
    <li>Loss Functions: Categorical cross-entropy for emotion output and binary cross-entropy for AU output.</li>
    <li>Evaluation Metrics: Accuracy for both emotion and AU outputs.</li>

6.Model Training:
    <li>Fitting model parameters: Trained model using training_generator, with validation data and callbacks for early stopping and learning rate scheduling.</li>

7.Experiments & Tuning:
    Addressed overfitting by:
      <li>Hyperparameter tuning, regularization, and data augmentation.</li>
      <li>Fine-tuning layers and adjusting the number of neurons (added 256 neurons with ReLU activation).</li>
      <li>Added L1 and L2 regularization, used GlobalAveragePooling2D, and applied Dropout (0.2).</li>
      <li>Set learning rate to 0.001 and used learning rate scheduler.</li>
Performed oversampling to address dataset imbalance.
