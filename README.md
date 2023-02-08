# E-commerce Text Classification

## E-commerce Product Categorization

**E-commerce** (electronic commerce) is the activity of electronically buying or selling of products on online services or over the [**Internet**](https://en.wikipedia.org/wiki/Internet). It frequently uses the [**web**](https://en.wikipedia.org/wiki/World_Wide_Web), if not entirely, for at least some of the life cycle of a transaction, while it may also use other technologies like [**e-mail**](https://en.wikipedia.org/wiki/Email). Typical e-commerce transactions include the purchase of products (like books from Amazon) or services (such as music downloads in the form of digital distribution such as the iTunes Store). [**Online retail**](https://en.wikipedia.org/wiki/Online_shopping), [**electronic markets**](https://en.wikipedia.org/wiki/Electronic_markets), and [**online auctions**](https://en.wikipedia.org/wiki/Online_auction) are the three areas of e-commerce. E-commerce is supported by [**electronic business**](https://en.wikipedia.org/wiki/Electronic_business). The purpose of e-commerce is to enable customers to shop and pay online over the Internet, saving both time and space for consumers and businesses while also significantly improving transaction efficiency.

**Product categorization** or [**product classification**](https://en.wikipedia.org/wiki/Product_classification) is a type of [**economic taxonomy**](https://en.wikipedia.org/wiki/Economic_taxonomy) that refers to a system of categories into which a collection of products would fall under. Product categorization involves two separate tasks:

- Create, support, and expand the catalogue structure for the offered products

- Tagging products with the correct categories and attributes

While machine learning does not have much potential for use in the first task, it is possible to automate the second task, which is relatively laborious and time-consuming. **The problem considered in this notebook involves the categorization of products offered on e-commerce platforms based on the descriptions of the products mentioned therein.** The purpose of such categorization is to enhance the user experience and achieve better results with external search engines. Visitors can quickly find the products they need by navigating the catalogue or using the website's search engine.

## Text Classification

**Text classification** is a widely used [**natural language processing**](https://en.wikipedia.org/wiki/Natural_language_processing) task in different business problems. Given a statement or document, the task involves assigning to it an appropriate category from a pre-defined set of categories. The dataset of choice determines the set of categories. Text classification has applications in emotion classification, news classification, spam email detection, auto-tagging of customer queries etc.

In the present problem, the statements are the product descriptions and the categories are `Electronics`, `Household`, `Books` and `Clothing & Accessories`.

## Data

**Original source:** **https://doi.org/10.5281/zenodo.3355823**

**Kaggle dataset:** **https://www.kaggle.com/datasets/saurabhshahane/ecommerce-text-classification**

The dataset has been scraped from Indian e-commerce platform(s). It contains e-commerce text data for four categories: `Electronics`, `Household`, `Books` and `Clothing & Accessories`. Roughly speaking, these four categories cover $80$% of any e-commerce website, by and large. The dataset is in *.csv* format and consists of two columns. The first column gives the target class name and the second column gives the datapoint, which is the description of the product from the e-commerce website.

## Project Objective

The objective of the project is to classify a product into the four categories `Electronics`, `Household`, `Books` and `Clothing & Accessories`, based on its description available in the e-commerce platform.

## Overview of Part 1. EDA and Text Normalization

- Performed basic [**exploratory data analysis**](https://en.wikipedia.org/wiki/Exploratory_data_analysis), comparing the distributions of the number of characters, number of words, and average word-length of descriptions of products from different categories

- Employed several [**text normalization**](https://en.wikipedia.org/wiki/Text_normalization) techniques, namely *convertion to lowercase*, *removal of whitespaces*, *removal of punctuations*, *removal of unicode characters*, *substitution of acronyms*, *substitution of contractions*, *removal of stop words*, *stemming and lemmatization*, *discardment of non-alphabetic words*, *retainment of relevant parts of speech*, *removal of additional stop words*

- Combined the processes in an appropriate order into a single function that takes a text as input and outputs a normalized version of that text

- Implemented text normalization on product descriptions in the given dataset

## Overview of Part 2. TF-IDF Modeling

- Loaded the normalized dataset obtained from **Part 1. EDA and Text Normalization**

- Used [**TF-IDF**](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) vectorizer on normalized descriptions for **text vectorization**

- Used several classifiers, namely *logistic regression*, *k-nearest neighbors classifier*, *decision tree*, *support vector machine with linear kernel*, *random forest*, *stochastic gradient descent classifier*, *ridge classifier*, *XGBoost* and *AdaBoost* for **baseline modeling**

- Performed [**hyperparameter tuning**](https://en.wikipedia.org/wiki/Hyperparameter_optimization) on the [**support vector machine**](https://en.wikipedia.org/wiki/Support-vector_machine) classifier with **linear kernel**

- Employed the model with the highest validation accuracy to predict the labels of the test observations and obtained a test accuracy of $0.957965$

## Overview of Part 3. Word2Vec Modeling

- Employed a few selected [**text normalization**](https://en.wikipedia.org/wiki/Text_normalization) processes, namely **convertion to lowercase** and **substitution of [contractions](https://en.wikipedia.org/wiki/Wikipedia:List_of_English_contractions)** on the raw data on product descriptions

- Used Google's pre-trained [**Word2Vec**](https://en.wikipedia.org/wiki/Word2vec) model on the tokens, obtained from the partially normalized descriptions, to get the [**embeddings**](https://en.wikipedia.org/wiki/Word_embedding)

- The embeddings are then converted to [**compressed sparse row**](https://en.wikipedia.org/wiki/Sparse_matrix) (CSR) format

- Used several classifiers, namely *logistic regression*, *k-nearest neighbors classifier*, *decision tree*, *support vector machine with linear kernel*, *naive Bayes*, *random forest*, *linear discriminant analysis classifier*, *stochastic gradient descent classifier*, *ridge classifier*, *XGBoost*, *AdaBoost*, *CatBoost*, *neural network* for **baseline modeling**

- Performed [**hyperparameter tuning**](https://en.wikipedia.org/wiki/Hyperparameter_optimization) on [**XGBoost**](https://en.wikipedia.org/wiki/XGBoost) classifier

- Employed the model with the highest validation accuracy to predict the labels of the test observations and obtained a test accuracy of $0.941748$