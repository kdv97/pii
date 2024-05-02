# PII Detection 

This is a GitHub repository for our project for [Kaggle's PII Detection competition](https://www.kaggle.com/competitions/pii-detection-removal-from-educational-data) sponsored by the Learning Agency Lab. 

### Description
Our goal is to identify which word(s) in a student essay are personally identifiable information, such as a student's name, email, address, ID number, etc., minimizing the F5 score (a metric weighing recall 5 times as high as precision). 

### Data Overview
The data provided in the Kaggle competition consisted of 6807 student samples, given as a dataset with: 
* **Full Text**
* **Tokens**: The words forming the text
* **Trailing Whitespace**: Indicating if a given token (word) is followed by whitespace
* **Labels**: The label of each token (word), which is one of the following 
  * ```PII```: NAME_STUDENT, EMAIL, USERNAME, ID_NUM, PHONE_NUM, URL_PERSONAL, STREET_ADDRESS
     * Indicated with a B or I depending on if it is the first token (word) in the PII or not
  * ```NON-PII```: O

 ### Data/Parameter Exploration
 All of the following files are in the DataExploration folder and outline how we chose various parameters:
 1. Data Preprocessing: In [data-exploration.ipynb](DataExploration/data-exploration.ipynb), we compute a few metrics about the raw data to find distribution of data, and split the data into a training and testing set. We also tokenize the text, and preprocess it for partitioning (one of the methods we use in our fine-tuning) as well as choose which samples to downsample (if we downsample). 
 2. Truncation: In [truncation-cutoff.ipynb](DataExploration/truncation-cutoff.ipynb), we compute the best middle-truncation cutoffs, which is one of hte methods we use in our fine-tuning.

### Models
All of our models fine-tune existing language models, with the two base models we use RoBERTa and DeBERTa. We maintain a folder for each, separating the two base models. Each training file has the form (base_model)-model-(method), where the base_model indicates if deBERTa or roBERTa was used and the method is either partition or truncation. For each training file, there is a separate corresponding inference file named (base-model)-inference-(method), so that each are tune for the method we use to train. Roughly, the two methods are 
1. **Partitioning**: After the text is tokenized, we pre-process it by dividing it into several partitions, each of length the maximum training length(MAX_LENGTH) of the base model.
2. **Truncation**: After the text is tokenized, we pre-process it by removing all but the first k and the last MAX_LENGTH - k tokens. In other words, we remove the middle portion of the tokens if the sample is too long.


