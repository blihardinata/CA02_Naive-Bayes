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
Counter: to count the number of words in a given sentence/file.

*from sklearn.naive_bayes import GaussianNB*
GaussianNB: to build a feature matrix using the Naive Bayes Theorem calculation

*from sklearn.metrics import accuracy_score*
accuracy_score: to predict how accurate the model is

### Step 1: Create a function to build dictionary of the most common 3000 words from the email content.
- Create a function called **build_Dictionary()** to add all words and characters into **dictionary**
- os.path.join is used to create a list of emails
- line.split() is used to split a sentence into a list of **words**
- **Dictionary** contains all words from **content** including stop words and non-alpha-numeric words. Hence, I named this list as **junk**
- Non-alpha-numeric such as + : ! and words with one alphabet such as a, I, U need to be removed to improve accuracy rate.  
- Once all non-alpha-numeric and one-alphabet words are removed, save the 3000 most common words under a list called **dictionary**

The return value of print(dictionary) is:
[('order', 1414), ('address', 1299), ('report', 1217), ('mail', 1133), ('language', 1099), ('send', 1080), ('email', 1066)....

### **Step 2: Create a function to extract features then build a feature matrix by analyzing filepaths and filenames as well as the content of each email. This function uses naming conventions to separate spam Emails from non-spam Emails** 
- Create a function called **extract_features** to separate spam emails from non-spam emails 
- **features_matrix** is a matrix of total number of files in either training or testing folder along with the 3000 most common words
- For every document or (**doc**), we label the sentence with index, split the sentence and save the list of words under **words**
- Please note: **doc** is a filepath name. Since we need to filter out spam Emails from non-spam Emails based on naming convention, we split filepaths as lists of words and save them as **filepath**

Example of print(filepath): ['', 'content', 'drive', 'MyDrive', 'MSBA_Colab_2020', 'ML Algorithms', 'CA02', 'train-mails', 'spmsga10.txt']

- Spam emails are categorized with filenames starting with "spmsg". Hence, we are saving the last word in **filepath** as **filename**
- Therefore, for every filename starting with "spmsg", the numbers of **count** and **fileID** are increased by one respectively. 


### **Step 3: Testing, training and predicting the accuracy rate of the model (or functions) performance ** 
- The first four lines of code is used to test the function in the Step 1 and the Step 2. 
- We use extract_feature function to save both training and test folders into the corresponding matrix. 
- The model uses gaussianNB assuming that the features follow a normal distribution characteristics.
- Based on the training and the prediction model, we conduct the accuracy score

**The Accuracy Score for comparing the Predicted Labels with the Test Labels: 96.15%**
