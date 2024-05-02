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
  * ```NON-PII```: O


