# BSAN6070 Machine_learning
Name: Bryan Lihardinata

**PROJECT: Spam eMail Detection using Naive Bayes Classification Algorithm**

## **Instruction:**
- colab.research.google.com/
- Under GitHub tab, please write the following: blihardinata/CA02_Naive-Bayes

### **Import Packages:**
*import os*
os: to provide function for interacting with 

*import numpy as np*

*from collections import Counter*
Counter: to count the number of words in a given sentence/files.

*from sklearn.naive_bayes import GaussianNB*
GaussianNB: to build a feature matrix used to perform Naive Bayes Theorem calculation

*from sklearn.metrics import accuracy_score*
accuracy_score: to predict how accurate the model is

### **Step 1: Create a function to build dictionary of most common 3000 words from all the email content. **
- Create a function called **build_Dictionary()** to add all words and characters into the dictionary
- os.path.join is used to create a list of emails
- line.split() is used to split all sentence into a collection of *words*
- Therefore, dictionary contains all words from *content* including stop words. Hence, I named this list as *junk*
- Non-alpha-numeric such as + : , and words with one alphabet such as a, I, U need to be removed to improve accuracy rate.  
- Once all non-alpha-numeric and one-alphabet words are removed, save the 3000 most common words under a list called *dictionary*

The returned value of print(dictionary) is:
[('order', 1414), ('address', 1299), ('report', 1217), ('mail', 1133), ('language', 1099), ('send', 1080), ('email', 1066)....

### **Step 2: Create a function to extract features then build a feature matrix by analyzing the file path and name as well as the content of each email. This function uses naming conventions to separate spam Emails from non-spam Emails** 
- Create a function called **extract_features** to separate spam email from non-spam emails 
- features_matrix is a matrix of total number of files in either training or testing folders along with the 3000 most common words
- For every document or (doc), we label the sentence with index, split the sentence and save the list of words under *words*
- Please note: *doc* is a filepath name. Since we need to filter out spam from non-spam based on naming convention, we split the path as a collection of words and save under *filepath*

Example of print(filepath): ['', 'content', 'drive', 'MyDrive', 'MSBA_Colab_2020', 'ML Algorithms', 'CA02', 'train-mails', 'spmsga10.txt']

- Spam email is categorized with filename starting with "spmsg". Hence, we are saving the last word in filepath as *filename*
- Therefore, for every filename starts with "spmsg", the number of count and fileID is increased by one respectively. 


### **Step 3: Testing, training and predicting the accuracy rate of the model (or functions) performance ** 
- The first four lines of code is used to test the function in Step 1 and Step 2. 
- We use extract_feature function to save both training and test folders into the corresponding matrix. 
- The model uses gaussianNB to assume that features follow a normal distribution characteristics. 
- Based on training and prediction model, we are building a table that is similar to confusion matrix. 
- Based on this "confusion matrix", we conduct the accuracy score

**The Accuracy Score for comparing the Predicted Labels with the Test Labels: 96.15%**
