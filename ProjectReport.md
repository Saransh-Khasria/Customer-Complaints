
# Customer Complaints 
#### Identifying Financial Products from Complaints  <br/><br/>

*There are numerous complaints which are made by customer for variety of issues; having an automated prediction system which can re-direct those complaints to respective departments based on the product which the complaint is about will help a business in operational cost savings by shaving off the time which a person might take to read through and process a complaint. Additionally, an automated prediction system will help in a better turn around time for departments and the organization as a whole*

<img src = 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTU2GFqBFTjEhY72TFR9DWF8c9EbcSHETvPQxnB-bwJY_Mq5S2A0QuvkDzRMEplkboIkl8&usqp=CAU' width=800>

## 1. Data

The Consumer Complaint Database is a collection of complaints about consumer financial products and services that is sent to companies for response. Complaints are published after the company responds, confirming a commercial relationship with the consumer, or after 15 days, whichever comes first.

 - https://cfpb.github.io/api/ccdb/
 

<font color='red'>***Disclaimer*** *The data collected from the above website for this project is only for JP Morgan Chase till 6/30/2021 and has* ***no relevance to internal company data***

## 2. Method

To predict the financial product under which the cusotmer has filed a complaints, I basically breakdown the complaint data using vectorizarion algorithms and use that data to further predict the financial product for which the complaint. Hence, by doing this I was able to convert thisinto a Natural Language Processing problem and use algorithms for predicting the products under whcih a complaint can be classified.

## 3. Data Wrangling
> **Data Type Casting** The available data is not in the correct data type which down the line causes problems in further analysis. All features were correctly identified and types casted to solve for the problem that may arise later

> **Imputation** For this particular problem the data where complaints were missing is removed from ebing moved furthr as it will not add any value while vectorizing



## 4. EDA
> The maximum number of complaints raised have been for customers' credit/preparid cards and is closely followed by complaints related to their accounts

> All of the complaints in scope were raised via web portal
 
<img src='images/Product.png'><br/><br/><br/>
<img src='images/Submittedvia.png'>

## 5. Preprocessing
> **Decontraction** Common contracted words are de-contracted for ease of use while modeling. For example: I'm is de-contracted to I am.

> **Stop word removal** Words which are common and are may times used as filler or conjuctions are removed as these words do not give much information .

> **Cleansing Commnts** The complaints/comments are cleansed of punctuations, masked card/account details, urls, etc

## 6.Vectorization

> **Bag of Words** Also known as Count Vectorizer, this vetorization algorithm buckets the words by their usage within a complaint

> **Tf Idf** Term Frequency Inverse Document Frequency is an efficient algorithm as takes into account the particular usage of words in a particular instance and compare it against the entire corpus. <br/>
Please read more about the algorithm here: https://towardsdatascience.com/tf-term-frequency-idf-inverse-document-frequency-from-scratch-in-python-6c2b61b78558

## 7. Algorithms & Machine Learning

Essentially, I have considered 4 algorithms and worked on the problem as a multiclass classification problem. I trained these models on both the vectorized data and measured the performance of each based on average accuracy while cross validating.

For this problem I am using Precision & Recall as a performance metric and in the final result XG Boost working on a Bag of wrods vector came across as best with ~87% score in both the metrics.

| Model | Vectorization | Precision | Recall | F1-score |
| --- | --- | --- | --- | --- |
| Logistic Regression | BOW | .85 | .85 | .85 | 
| Logistic Regression | Tf Idf | .82 | .82 | .82 | 
| KNN | BOW | .56 | .56 | .56 | 
| KNN | Tf Idf | .82 | .82 | .82 | 
| Random Forest | BOW | .79 | .79 | .79 | 
| Random Forest | Tf Idf | .76 | .76 | .76 | 
| XG Boost | BOW | .87 | .87 | .87 | 
| XG Boost | Tf Idf | .83 | .83 | .83 | 

## 8. Future Improvements
- In the future, I would like to explore other vectorization algorithms like word2vec and see how that impacts the performance of the predition algorithms
- I framed this problem into a 4 way multiclass classification problem due to lack of data points smaller classes, however in future would like to develop more complex models which can predict high number of classes
