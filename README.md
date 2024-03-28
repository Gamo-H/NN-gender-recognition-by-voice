# NN-gender-recognition-by-voice
---

## Data Overview

### Source
Our project utilizes the [Mozilla Common Voice dataset](https://www.kaggle.com/datasets/mozillaorg/common-voice), a comprehensive corpus of speech data. This dataset is collected through the [Common Voice website](http://voice.mozilla.org/) and comprises a variety of sources, including user-submitted blog posts, historical books, movies, and other public speech corpora. Its primary aim is to facilitate the development and evaluation of Automatic Speech Recognition (ASR) systems.

### Dataset Version
For this project, we are working with a specific 13GB version of the dataset, which can be downloaded [here](https://www.kaggle.com/datasets/mozillaorg/common-voice).

## Data Preparation and Balancing

### Subset Selection
We focus on the “cv-train-other” subset, accompanied by the “cv-train-other.csv” file. This CSV file includes details for each audio recording, such as filename, text, up_votes, down_votes, age, gender, and accent. Our analysis primarily targets audio files with specified gender information.

### Data Cleaning and Balancing Steps
To ensure data quality and balance, we perform the following steps:
- Exclude audio files lacking gender information or labeled with 'other' as gender.
- Remove any silent audio files.
- Achieve an equal representation of male and female voices.
- Store the refined dataset in a new CSV file, “Balanced-data.csv,” which will list the paths of the remaining audio files along with their corresponding gender.

### Processing Notebook
All the above modifications are executed in the “Balancing.ipynb” notebook. This notebook also includes all necessary installation steps.

### Temporary Note
**Important:** For the proper execution of the “Balancing.ipynb” notebook, ensure that the dataset is downloaded as a folder named "archive" and placed on the desktop. The notebook currently contains certain methods and directions that did not yield the expected results. These have been retained temporarily for review and learning purposes. Future updates to the code will aim to enhance its flexibility regarding data location and refine the methodologies used.

---

---

---

## Model Overview

### Approach
In this study, we employ an Artificial Neural Network (ANN) model to classify the gender of audio samples. Our primary focus is on utilizing Mel Spectrogram Frequency features for this classification task. Although we experimented with various other feature types, such as MFCC and Tonnetz, Mel spectrogram analysis consistently yielded the most promising results.

### Data Preparation
The initial step involves balancing the data, which is then stored in a "Balanced_data.csv" file. Following this, we extract the audio features from each sample. It's important to note that this feature extraction process is the most time-consuming step in our workflow.

### Feature Extraction and Model Training
All processes related to feature extraction and model training are comprehensively detailed in the "DeepGender.ipynb" notebook.

### Model Architecture
The architecture of our model is a sequential design comprising five hidden dense layers. These layers range from 256 units down to 64 units, each utilizing the "ReLU" activation function. The output layer is a sigmoid layer, designed to interpret the results as binary classifications: 0 representing female and 1 representing male. The choice of this model architecture was initially arbitrary, but it has demonstrated effective results in our tests.

### Compilation
We compile the model using the "binary_crossentropy" loss function, which is appropriate for binary classification tasks like ours.

### Results
Our model achieves an accuracy of 89%, a result we find highly satisfactory for the objectives of our study.

### Execution Requirements for "DeepGender.ipynb"
For the successful execution of the "DeepGender.ipynb" notebook, it is essential that the "Balanced_data.csv" file, obtained from the "Balancing.ipynb" notebook, be placed in the directory "/Users/mac/Desktop/data/data". The "data" folder will contain all the results, training, and test data.

### Temporary Note
**Important:** The "DeepGender.ipynb" notebook currently includes various experimental approaches and personal comments that did not yield optimal results. These sections are retained temporarily for review and learning purposes. We plan to refine and streamline the notebook in future updates.

---


---
