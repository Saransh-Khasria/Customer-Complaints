{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Customer Complaints \n",
    "#### Identifying Financial Products from Complaints  <br/><br/>\n",
    "\n",
    "*There are numerous complaints which are made by customer for variety of issues; having an automated prediction system which can re-direct those complaints to respective departments based on the product which the complaint is about will help a business in operational cost savings by shaving off the time which a person might take to read through and process a complaint. Additionally, an automated prediction system will help in a better turn around time for departments and the organization as a whole*\n",
    "\n",
    "<img src = 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTU2GFqBFTjEhY72TFR9DWF8c9EbcSHETvPQxnB-bwJY_Mq5S2A0QuvkDzRMEplkboIkl8&usqp=CAU' width=800>"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 1. Data\n",
    "\n",
    "The Consumer Complaint Database is a collection of complaints about consumer financial products and services that is sent to companies for response. Complaints are published after the company responds, confirming a commercial relationship with the consumer, or after 15 days, whichever comes first.\n",
    "\n",
    " - https://cfpb.github.io/api/ccdb/\n",
    " \n",
    "\n",
    "<font color='red'>***Disclaimer*** *The data collected from the above website for this project is only for JP Morgan Chase till 6/30/2021 and has* ***no relevance to internal company data***"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 2. Method\n",
    "\n",
    "To predict the financial product under which the cusotmer has filed a complaints, I basically breakdown the complaint data using vectorizarion algorithms and use that data to further predict the financial product for which the complaint. Hence, by doing this I was able to convert thisinto a Natural Language Processing problem and use algorithms for predicting the products under whcih a complaint can be classified."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 3. Data Wrangling\n",
    "> **Data Type Casting** The available data is not in the correct data type which down the line causes problems in further analysis. All features were correctly identified and types casted to solve for the problem that may arise later\n",
    "\n",
    "> **Imputation** For this particular problem the data where complaints were missing is removed from ebing moved furthr as it will not add any value while vectorizing\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "## 4. EDA\n",
    "> "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 5. Preprocessing\n",
    "> **Decontraction** Common contracted words are de-contracted for ease of use while modeling. For example: I'm is de-contracted to I am.\n",
    "\n",
    "> **Stop word removal** Words which are common and are may times used as filler or conjuctions are removed as these words do not give much information .\n",
    "\n",
    "> **Cleansing Commnts** The complaints/comments are cleansed of punctuations, masked card/account details, urls, etc"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 6.Vectorization\n",
    "\n",
    "> **Bag of Words** Also known as Count Vectorizer, this vetorization algorithm buckets the words by their usage within a complaint\n",
    "\n",
    "> **Tf Idf** Term Frequency Inverse Document Frequency is an efficient algorithm as takes into account the particular usage of words in a particular instance and compare it against the entire corpus. <br/>\n",
    "Please read more about the algorithm here: https://towardsdatascience.com/tf-term-frequency-idf-inverse-document-frequency-from-scratch-in-python-6c2b61b78558"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 7. Algorithms & Machine Learning\n",
    "\n",
    "Essentially, I have considered 4 algorithms and worked on the problem as a multiclass classification problem. I trained these models on both the vectorized data and measured the performance of each based on average accuracy while cross validating.\n",
    "\n",
    "For this problem I am using Precision & Recall as a performance metric and in the final result XG Boost working on a Bag of wrods vector came across as best with ~87% score in both the metrics.\n",
    "\n",
    "| Model | Vectorization | Precision | Recall | F1-score |\n",
    "| --- | --- | --- | --- | --- |\n",
    "| Logistic Regression | BOW | .85 | .85 | .85 | \n",
    "| Logistic Regression | Tf Idf | .82 | .82 | .82 | \n",
    "| KNN | BOW | .56 | .56 | .56 | \n",
    "| KNN | Tf Idf | .82 | .82 | .82 | \n",
    "| Random Forest | BOW | .79 | .79 | .79 | \n",
    "| Random Forest | Tf Idf | .76 | .76 | .76 | \n",
    "| XG Boost | BOW | .87 | .87 | .87 | \n",
    "| XG Boost | Tf Idf | .83 | .83 | .83 | "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 8. Future Improvements\n",
    "- In the future, I would like to explore other vectorization algorithms like word2vec and see how that impacts the performance of the predition algorithms\n",
    "- I framed this problem into a 4 way multiclass classification problem due to lack of data points smaller classes, however in future would like to develop more complex models which can predict high number of classes"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
