# Emotion-FACSCodePrediction_ImageClassification_DL
This project demonstrated the use of DenseNet for predicting emotions and FACS codes from images. By performing data exploration, pre-processing, model training, and evaluation, we developed a robust model capable of predictions. 
### Introduction 
Goal is to anticipate emotions and the Facial Action Coding System (FACS) code that corresponds to each input image. Dataset consists of labels with associated FACS code and their emotion. 
### EDA

1. Checked type of columns present in the dataset- Basic feature understanding.<br/>
2. Checked unique emotion type in the Dataset and its counts of existence. Analysed that dataset is biased towards negative emotion.<br/>
3. Visualised images - Determined the images type i.e.  RGB or grayscale, which was helpful during model architecture.<br/>
4. Checked the number of occurrences of 1’s in each AU codes in the Dataset.  AU codes are imbalanced - few codes above 100 and few below it. Hence need to be handled during model training.<br/>
5. Checked the distribution of contrast in the images. Most of the images are in the frequency of 80 - 100 contrast range.<br/>
6. Relationship between each AU Codes and Emotion Type. We are checking the counts of each FACS code for each type of emotion since the output is based on FACS and emotion type to determine whether the dataset is imbalanced.<br/>

### Approach
<ul><b>1. Custom Data Loader:</b> Generates batches of data and preprocesses it for model training and evaluation.</ul>

<ul><b>2. Train-Test Split:</b>
<li>Dataset split into 70% training, 15% validation, and 15% testing sets.</li>
<li>Ensures sufficient data for training, fine-tuning, and evaluating the model.</li>
</ul>

<ul><b>3.Data Generators Initialization:</b>
<li>Defined batch size as 32 and set image dimensions to (224, 224, 3).</li>
<li>Applied data standardization, normalization, and augmentation (augmentation only for training data).</li>
<li>Set number of classes to 3 for emotion classification.</li>
</ul>

<ul><b>4. Model Definition:</b>
<li>DenseNet Model: Chosen for its efficient layer connectivity and reduced overfitting.</li>
<li>Multi-output model: Handles emotion output, AU output, and image input.</li>
</ul>


<ul><b>5.Experiments & Tuning:</b>
<li>Hyperparameter tuning, regularization, and data augmentation.</li>
<li>Fine-tuning layers and adjusting the number of neurons (added 256 neurons with ReLU activation).</li>
<li>Added L1 and L2 regularization, used GlobalAveragePooling2D, and applied Dropout (0.2).</li>
<li>Set learning rate to 0.001 and used learning rate scheduler.</li>
<li>Performed oversampling to address dataset imbalance.</li>
<li>AdamW Optimizer weight decay to prevent overfitting.</li>
<li>Loss Functions: Categorical cross-entropy for emotion output and binary cross-entropy for AU output.</li>

<li>Evaluation Metrics: Accuracy for both emotion and AU outputs.</li>
</ul>
