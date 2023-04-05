## cs5293sp23-project1
## Text - Analytics Project 1
## Author - Pranav Vichare
## Project - The Redactor
**About:**  In this project, Enron Email Dataset is used which has various emails in the form of text file. The dataset contains 1.7 Gb and more than 500,000 email messages. We have only considered 5 text files as sample data. The email has sensitive data which is to be redacted. The sensitive data is in terms of Names, Address, Gender, Dates and Phones. This sensitive data should be replaced by Redact character '█'. The redacted data should be stored with extension .redacted with original filenames. Stats files needs to be created which will contain all the data which is redacted and their indexes.

To run the code, Use the commands below in terminal or Visual Studio Code
```python
pipenv --python 3.9  #use your version of python which is installed on your system. This code is also used to create a virtual environment
pipenv install spacy #to install spacy library in virtual environment
pipenv install pytest #to install pytest library in virtual environment
pipenv lock #to create piplock file
```

```python
import argparse
import os
import glob
import spacy
import re
```
To run the code, Import all the libraries listed above in the python code.

To run the code from the terminal use below command:
```
pipenv run python redactor.py --input '*.txt' --names --dates --phones --genders --address --output 'files/' --stats stderr
```

### Code Explanation  
```python
#redactor.py has 6 functions as shown below.
def redact_names()
def redact_dates()
def redact_phones()
def redact_genders()
def redact_addresses()
def main()
```
The main function mentioned above will be executed and calls other functions. The input .txt files in the directory will be read. The text from each file will be sent to the remaining 5 functions from the **main()** function.
The url will be sent to **fetchIncidents.fetchIncidents(url)** fetchIncidents function in fetchIncidents.py file which downloads the pdf file using urllib library.
The download file *incidents.pdf* is then stored in the local directory.
The above function will extract the text using regular expression library and store it in form a list of tuples which has all the 5 fields which are required.
The above code will create an empty database with a table with 5 columns, column for each field and then populate the extract from pdf to the database.
Using status method to print all the values in the nature field with their count. Using **Select** and **Groupby** command to get the count of the incidents.

### Code Output
The code output is stored in stored in stats file with name : **stderr.txt**. The stats file will have the terms redacted and their indexes and count of types of terms redacted.
![image](https://github.com/Pranavv361/cs5293sp23-project1/blob/main/Output%20docs/Stats%20file%20output.png)

### Test Output
![image](https://github.com/Pranavv361/cs5293sp23-project1/blob/main/Output%20docs/test.py%20output.png)



### Assumptions:
1. Nature of Incidents field contains values which are of type Start Case, Title Case, camelCase, sentence case etc. Incidents fields does not start with ALL CAPS word.
2. The Location field is a single line field.

### Bugs:   
1. If the Nature of Incident field starts with a word in ALL CAPS, then the word will be concatenated to the Address field.
