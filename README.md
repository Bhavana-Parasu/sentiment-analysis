# sentiment-analysis
Text Extraction by web crawling using Selenium and Text Analysis of the extracted web pages.

Dataset: 
1) An excel file ‘input.xlsx’ consisting of the following columns:
• URL_ID – An ID for the webpage URLs. Values range 37 - 150
• URL – contains URLs for webpage
The text from the webpages is to be extracted and stored in text files whose name should be 
URL_ID.
2) A folder containing stop words 
These stop words are used to clean the data.
3) A master dictionary containing positive and negative words
The positive and negative words are used to create a dictionary which can be used to determine 
the sentiment of the text.

Task description and instructions:
1) Web Crawling:
For web crawling, I have used Selenium.
Note: You can use any browser for web crawling, I have used Chrome. If you are using any other 
browser, install the corresponding webdriver. 
You can either place the drivers in a directory that is already listed in PATH, or you can place 
them in a directory and add it to PATH. 

2) Text Analysis:
The extracted text is analyzed for various metrics. For analysis purpose, I have used NLTK Library 
which is a powerful tool for natural language processing.
Methodology: the text in the text files are converted into a list of word ‘tokens’ on which text 
analysis can be performed.

The following analysis is being performed in this notebook:
• Sentiment Analysis:
There is stop words dictionary available with the NLTK library, however, I have used the 
custom stop words list provided. Same goes for positive and negative words dictionary –
these are used to calculate the sentiment scores. 

We convert the text into a list of tokens using the nltk tokenize module and use these tokens to calculate the 4 variables described below:
1) Positive Score: This score is calculated by assigning the value of +1 for each word if found in the Positive Dictionary and then adding up all the values.
2) Negative Score: This score is calculated by assigning the value of -1 for each word if found in the Negative Dictionary and then adding up all the values. We multiply the score with -1 so that the score is a positive number.
3) Polarity Score: This is the score that determines if a given text is positive or negative in nature. It is calculated by using the formula: 
Polarity Score = (Positive Score – Negative Score)/ ((Positive Score + Negative Score) + 0.000001)
Range is from -1 to +1
4) Subjectivity Score: This is the score that determines if a given text is objective or subjective. It is calculated by using the formula: 
Subjectivity Score = (Positive Score + Negative Score)/ ((Total Words after cleaning) + 0.000001)
Range is from 0 to +1



• Analysis of Readability
Analysis of Readability is calculated using the Gunning Fox index formula described below.
Average Sentence Length = the number of words / the number of sentences
Percentage of Complex words = the number of complex words / the number of words 
Fog Index = 0.4 * (Average Sentence Length + Percentage of Complex words)

• Average Number of Words Per Sentence
The formula for calculating is:
Average Number of Words Per Sentence = the total number of words / the total number of sentences

• Complex Word Count:
Complex words are words in the text that contain more than two syllables.

• Word Count:
The cleaned words list is used for word count.
We count the total cleaned words present in the text by 
1) removing the stop words (using stopwords class of nltk package).
2) removing any punctuations like ? ! , . from the word before counting.


• Syllable Count Per Word
We count the number of Syllables in each word of the text by counting the vowels present in each word. We also handle some exceptions like words ending with "es","ed" by not counting them as a syllable.

• Personal Pronouns
To calculate Personal Pronouns mentioned in the text, we use regex to find the counts of the words - “I,” “we,” “my,” “ours,” and “us”. Special care is taken so that the country name US is not included in the list.

• Average Word Length
Average Word Length is calculated by the formula:
Sum of the total number of characters in each word/Total number of words
