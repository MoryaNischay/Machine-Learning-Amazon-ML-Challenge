# Machine-Learning-Amazon-ML-Challenge
Machine learning project made under Dr. Ashutosh Aggarwal for Sem-5
Introduction:
In today’s day and age ecommerce websites have become an integral part of our lives. Be it a student or a businessman, everyone in some capacity interacts with such websites on a daily basis. These websites are filled with endless products, each seeming more attractive than the other. However, sometimes customers are misled due to misinformation or no information, and the product dimension is one of them.
Our project aims to rectify this problem using machine learning techniques on the dataset provided during Amazon ML Challenge 2023 which provides us with a vast amount of data to work with.
Using this data we aim to predict the length of a product which not only makes the customer make a better decision but helps us in further deciding the packaging and shipping requirements of a product. 

Significance of the project:
The primary objective of this project is to build a robust machine-learning model to predict the product length from the Title, Description and Bullet Points of a product which are provided by the seller at the time of listing the product. 
This project can be deployed on any of the e-commerce websites and provide the sellers with the option to recheck their product dimensions in cases of discrepancy and auto-suggest an estimated dimension in cases of missing information so that there is no confusion when buying the product for the customer.
We can also use the dimensions provided by the model to pick the size of the packaging required for the object to be shipped and also how can the product be shipped for e.g. it will help us identify if the product can be delivered on a 2-wheeler or a bigger transport might be required for it even before it leaves the seller's warehouse! Although very niche, this will help us in further optimization of delivery vehicles and will probably help in the long run in saving time, money and fuel for the company.
This problem is relatively new and under-researched. The data is raw and widely varying, and this is our attempt at tackling it.



Methods Used:
Pre-Processing:- 	
First, we transformed the text using lowercase and removing alphanumeric characters and removing all the stop words (a, an, the) as they don't help with embeddings.
Then we concatenated all the text features (Product Title, Description, Bullet Points) into one to be embedded using Word2Vec.
The data was highly positively skewed, so we took the logarithm of the target values (Product Length) to fix skewness and bring it to a Gaussian shape.
We clipped the logarithm of the target values at 12 to remove outliers. 

Data before preprocessing (Positive Skew)


Data after preprocessing (Gaussian)
Word2vec:-
Using word to vec we represent every word as a vector dimension 100 as it is a good middle ground and helps us find general relations between words without costing us much computing power.
We use the ‘workers’ parameter to make use of multiple cores in our CPU for faster computation 
After this, we save the model for further usage
ANN:- 
Used a shallow artificial neural network with 100 neurons in the input layer
Mean square error is used as loss metric
50 epochs used with a batch size of 32.
It outputs a singular value corresponding to the product length in logarithmic scale.
Linear Regression:-
Using standard linear regression we form a relationship between the     embeddings and the product length that we have to predict. We convert the embeddings into a numpy array and use them as features and use product length as the target to predict.  
Testing:- 
We use our model to run tests on 2 different groups of test data that we have designed.
For ANN:- 
For our first test case we take the bottom 100k entries of the data we used to train our model. We re-generate embeddings for these just in case and then predict values after that we calculate the error of every entry and then take an average which comes out to be 29.91625% this gives us an accuracy of 70.08375%.
For our 2nd test case, we use the immediate 100k entries which are not present in our data. We generate embeddings similar to the first test case and find out that error and accuracy are 30.20707 and 69.79292 respectively.
Linear Regression:-
Similarly to ANN we Embed our data (100k entries) and then predict values for both the dataset and find error and accuracy of our predictions made.
Considering the submissions for the competition and the dataset which we were able to use we can say that these predictions are satisfactory. 

Dataset Description:									Our dataset consists of 6 attributes and 22,49,698 instances.
The attributes are as follows:
PRODUCT_ID: A numeric ID that uniquely identifies a product listing on the website.
TITLE: The name of the product that is displayed on the website. Contains brief information and basic specifications of the product.
BULLET_POINTS: Contains major points of interest that identify the product.
DESCRIPTION: Complete and detailed description of the product containing all the information that the seller can provide.
PRODUCT_TYPE_ID: A numeric value that identifies the category that the product belongs to.
PRODUCT_LENGTH: This is the target variable. It contains the length of the product in millimetres (mm).							
After analyzing the dataset we decided to use the Title, Bullet_Points and Description attributes in conjunction to deduce the target variable i.e. Product_Length.
Data Columns:- 

Data Sample:-

Experimental results:
ANN Results:- 
1st Dataset

2nd Dataset 

Linear Regression Results:-
1st Dataset

2nd Dataset 







Final Results:-


Individual roles:
Rushil Agarwal
Handled the data exploration and preprocessing 
Performed tokenization and embedding

Nischay Morya
Applied ANN and Regression to the embeddings
Created tests and implemented them for the models used to find errors and accuracy.

