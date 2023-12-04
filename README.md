# Product-Purchase-Detection
This project aims to perform product analysis and detect users' purchase state from their product-related questions from Amazon.

**TEAM MEMBERS**

Vishal Bondili - 801307348

Sree Harsha Nimmagadda - 801308050

Vaishnavi Baiken - 801316841

Harika Moole - 801318334

Ruchika Bhutada - 801327098


**Project Scope**
The machine learning component in this project aims to address a few specific challenges and opportunities within the domain of pre and post-purchase product questions in the e-commerce space. The focus will be on leveraging the dataset from Amazon to gain insights and develop models for the following tasks.

**Objectives**

The dataset appears to be designed to explore and analyze the relationship between customers and businesses. The dataset gives us a scope to study the following-
* Customer Behavior Analysis: Understanding how long it takes for customers to have inquiries after making a purchase and identifying patterns or trends in this behavior.
* Customer Satisfaction: Investigating if there's a correlation between the time gap and the nature of the questions, potentially indicating customer satisfaction or dissatisfaction.
* Product Performance: Analyzing the types of questions for specific products to gain insights into product performance and identify areas for improvement.
* Predictive Modeling: Building models to predict the likelihood of customers asking questions based on the time elapsed since the purchase.

**Domain**
Pre- and post-purchase product questions (E-commerce) 
**Characteristics:**

Active customer interaction through pre- and post-purchase questions.
Dynamic product catalog with frequent changes.
Varied product-related inquiries.

**Opportunities:**
Insights into customer preferences and satisfaction.
Proactive customer support.
**Specific Task:**

Analyzing temporal patterns in customer inquiries.
Investigating correlations between question types and post-purchase time.
**Stakeholders:**
The major stakeholders for this project would be 
E-commerce platforms
Businesses and sellers
Customers

**Literature Review**
Efficient product categorization is essential to e-commerce success, impacting user experience and purchase decisions.
*1. Need and importance of Product Categorization*

   1.1 Enhances User Experience: Well-structured categorization boosts user satisfaction and conversion rates (Alam et al., 2018).

   1.2 Influences Purchase Decision: Categorization affects consumer decision-making, guiding users towards specific products (Rigas et al., 2017).

*2. Challenges in Product Categorization*

   2.1 Ambiguity and Subjectivity: Ambiguous product attributes and subjective user interpretations pose challenges (Liu et al., 2019).

   2.2 Scalability: Scaling categorization systems for dynamic inventories is a challenge addressed through machine learning (Srivastava et al., 2020).

*3. Emerging Trends*

   3.1 Personalization: AI-driven personalized categorization based on user behavior enhances engagement (Biswas et al., 2019).

   3.2 Cross-Channel Consistency: Maintaining consistent categorization across platforms is crucial for brand image (Lalmas et al., 2017).

*4. Role of Product-Purchase Platforms*

   4.1 Social Commerce Integration: User-generated content and social interactions inform categorization, enhancing the shopping experience (Hajli, 2014).

   4.2 UI Design: Intuitive and visually appealing UIs improve user navigation and comprehension of categorization structures (Yoo et al., 2015).


**Data Source(s)**

Dataset Link: https://registry.opendata.aws/pre-post-purchase-questions/

Amazon S3 bucket ARN: arn:aws:s3:::pre-post-purchase-questions

Text document: https://pre-post-purchase-questions.s3.amazonaws.com/README.txt

Description: This dataset provides product-related questions, including their textual content and gap, in hours, between purchase and posting time. Each question is also associated with related product details, including its id and title.

The specifics described in this dataset involves product-related questions, with each entry providing the following information
* Question: This is the actual content of the question that customers have asked related to a particular product.
* Gap in Hours: This indicates the time gap (in hours) between the purchase of the product and the posting of the question. It gives insights into the duration customers take before reaching out with queries after buying a product.
* Product ID: A unique identifier for each product.
* Product Title: The title or name of the product associated with the question.

Reference(s): "Did you buy it already?", Detecting Users Purchase-State From Their Product-Related Questions by Lital Kuchy, David Carmel, Thomas Huet & Elad Kravi
 
**Domain-specific Challenges**

Ambiguity in Product Descriptions: 
Challenge: Figuring out what customers mean in their diverse product-related questions can be tricky due to the sometimes unclear product descriptions.

Dynamic Product Catalog:
Challenge: Products on Amazon change a lot. Adapting our system to always understand the latest products and features is a constant challenge.

**KPI’s**

Time-to-Question Analysis Accuracy: Measures the precision of the model in determining the time gap between purchase and question posting. This is crucial for understanding customer behavior post-purchase.

Customer Behavior Pattern Recognition: Evaluates the model's ability to identify and categorize patterns or trends in customer behavior based on the timing and nature of their questions.

Correlation Identification Accuracy: Assesses the model's effectiveness in identifying correlations between the time gap after purchase and the nature of questions, which may indicate customer satisfaction or dissatisfaction levels.

Product Inquiry Categorization Accuracy: Measures how accurately the model categorizes the types of product-related inquiries, providing insights into product performance and customer concerns.

Predictive Model Accuracy: Evaluates the precision and reliability of predictive models in forecasting the likelihood of customers asking questions based on the elapsed time since purchase.

Dynamic Catalog Adaptability: Assesses how effectively the model adapts to the constantly changing product catalog on Amazon, maintaining high accuracy in understanding and categorizing new products and features.

Ambiguity Resolution Efficiency: Measures the model's capability to decipher and correctly interpret ambiguous product descriptions in customer questions.

Customer Satisfaction Index (CSI): Based on the analysis of question types and timings, derive a CSI to gauge overall customer satisfaction with the product.

Product Improvement Insights: Track how effectively the analysis leads to actionable insights for product improvement.

Customer Engagement Rate: Monitor the rate and depth of customer engagement as indicated by the frequency and nature of questions.

Model Responsiveness: Measure the time taken by the model to adapt to new data or changes in product catalogs.

Feedback Loop Effectiveness: The model's ability to learn from new data and improve over time in terms of accuracy and adaptability.

## Phase2 Deliverable

**S3 Data Storage:**
1. Amazon Web Services (AWS) offers a highly scalable and secure object storage solution which is Amazon S3 (Simple Storage solution). We make use of this service to store our dataset before preprocessing it and applying transformations on the same.
2. S3 is advantageous as it lets you store and access any volume of data at any time, it's the perfect option for hosting big datasets, including data about products.
3. S3 is used  to group data into buckets, which are named within the S3 namespace and are globally unique, the link that stores our dataset is s3://pre-post-purchase-questions/.
4.This is the link we use as input to perform the next steps as documented below.
5.S3 is flexible for a product study project since it can store a variety of data kinds, including text files, photos, and metadata.
6. It allows you to regulate who can access your information with fine-grained access controls.
7. Versioning and logging are two capabilities that S3 offers that help you keep track of changes and keep an eye on who has access to your dataset over time.
8. S3 objects may be retrieved using a distinct URL, which makes it easier to integrate them with analytic software and machine learning techniques.

**Data Exploration:**

To draw meaningful insights from the dataset for data exploration we have used Athena for querying the data.

*Count Total Records:*
SELECT COUNT(*) FROM prepostquestionsdb.PrePostQuestions;

*Count Questions Per Product:*
SELECT asin, COUNT(question) AS total_questions FROM prepostquestionsdb.PrePostQuestions GROUP BY asin;

*To find most common questions:*
SELECT question, COUNT(*) AS frequency FROM prepostquestionsdb.PrePostQuestions GROUP BY question ORDER BY frequency DESC LIMIT 10;

*Questions Over Time:*
SELECT hours_diff, COUNT(*) AS question_count FROM prepostquestionsdb.PrePostQuestions GROUP BY hours_diff ORDER BY hours_diff;

*Distribution of Labels:*
SELECT label, COUNT(*) AS count FROM prepostquestionsdb.PrePostQuestions GROUP BY label;

*Questions Per Product with Label Distribution:*
SELECT asin, label, COUNT(*) AS count FROM prepostquestionsdb.PrePostQuestions GROUP BY asin, label;

*Average Time Before Question Asked Per Label:*
SELECT label, AVG(hours_diff) AS average_hours FROM prepostquestionsdb.PrePostQuestions GROUP BY label;

We make use of AWS Glue for ETL Transformations

**Pre-processing** 

1. Stop words removal
2. convert text to lowercase
3. Tokenization - textbreakdown
4. Extract single item_name clearly

**Data Transformations - AWS Glue**

1. Number of questions for each product: Understanding the distribution of questions for each product is crucial for assessing user engagement and product popularity. By analyzing the dataset, we can determine the number of questions associated with each unique product, identified by its ASIN (Amazon Standard Identification Number). This information provides valuable insights into user interest and interaction levels for individual products. Products with a higher number of questions may indicate greater user engagement, potential issues, or areas that require additional support or attention. This analysis aids product managers and customer support teams in tailoring their strategies to address specific product-related concerns effectively.

2. General processing time for the entire system: Assessing the general processing time for the entire system is essential for evaluating the efficiency of the dataset processing pipeline or system. This metric represents the time taken to perform data processing tasks, including data loading, cleaning, transformation, and any other relevant operations. Monitoring and optimizing the general processing time contribute to overall system performance. A shorter processing time enhances the responsiveness of the system, ensuring timely analysis and insights. System administrators and developers can use this information to identify bottlenecks, streamline processes, and improve the overall efficiency of the data processing system.

3. Processing time for each item: Analyzing the processing time for each item provides a granular view of the system's performance, offering insights into the efficiency of operations specific to individual products. By measuring the time it takes to process questions related to each item, system administrators can identify potential outliers, bottlenecks, or areas of improvement. Variations in processing time among different items may highlight specific challenges or opportunities for optimization. This information is instrumental in fine-tuning the system's capabilities, ensuring that it can handle varying workloads and maintain consistent performance across different products. Additionally, it aids in resource allocation and optimization efforts to enhance the overall processing efficiency for each item in the dataset.

**AWS Glue ETL Pipeline:**

![Alt text](https://github.com/vishalsingh-11/Product-purchase-detection/blob/main/Images/aws_pipeline.jpeg)


**Visualizations**
1. Question Count vs. ASIN: - This chart will demonstrate how user-generated questions are distributed among various ASINs (Amazon Standard Identification Numbers).
 Every product on Amazon is individually identified by its ASIN, which makes it possible to analyze consumer activity and interest in great detail.
   - By using the bar or line charts provided by Amazon QuickSight, you can quickly spot patterns and determine which products are generating the most interest from users or inquiries.

2. Product ASIN vs. Average Hours Diff:
 The goal of this visualization is to show, for each product ASIN, the average time interval between successive user questions.
 It offers information about how frequently and consistently users engage with content over time.
-Scatter plots and line charts from Amazon QuickSight are useful tools for visualizing this temporal component and identifying products that users are consistently or occasionally interested in.

3. ASIN vs. Label Distribution:
 This visualization seeks to identify patterns in the way users classify products based on their inquiries by focusing on the distribution of user-assigned labels or categories to products.
By providing insightful information about consumer preferences and perceptions, this visualization can aid in the understanding of the perceived benefits or features of different goods.
  - Pie charts and stacked bar charts from QuickSight can be used to show the percentage of various labels connected to each ASIN.
Advantages of Amazon QuickSight:
- Amazon QuickSight's smooth interaction with Amazon S3 guarantees effective data analysis and retrieval.
- The tool's interactive dashboards enable users to filter and go deeper into particular ASINs or time periods, enabling real-time dataset research.
- QuickSight's anomaly detection, which is driven by machine learning, can spot odd trends in user activity, helping in removal of outliers amongst many other benefits as a part of amazon’s services offered.

**AWS Pipeline:**

![Alt text](https://github.com/vishalsingh-11/Product-purchase-detection/blob/main/Images/AWS%20pipeline1.png)

## Phase 3

**Data Modeling**

For data pre processing, we have used AWs SageMaker to remove the Stop Words, punctuations, and performed lemmatization on our dataset. Additionally, using 
Term Frequency-Inverse Document Frequency we have converted text to numerical values. 

***Steps followed for Vectorization:***

Tokenize the Text: Split the text into individual words or tokens.

***Calculate Term Frequency (TF):*** Count how many times each word appears in a document and divide by the total number of words in that document.

***Calculate Inverse Document Frequency (IDF):*** Take the log of the number of documents divided by the number of documents that contain each word.

***Compute TF-IDF:*** Multiply the TF by the IDF for each word. This gives a weight to each word signifying its importance in the document and the entire corpus.

***Vectorize:*** Convert this into a numerical vector for each document, which can then be used for machine learning models.

***Output after Stop words, Punctuation Removal and Lemmatization***
![Alt text](https://github.com/vishalsingh-11/Product-purchase-detection/blob/main/Images/SW1.png)

**Choosing Machine Learning Model**

We are applying ***Random Forest classification Model*** to our dataset. 

1. Ensured each data point has a label (Eg: question_type, item_name, etc)
2. Splitted the data into training and testing sets.
3. Imported RandomForestClassifier from sklearn.ensemble.
4. Created an instance of RandomForestClassifier.
5. Random Forest Classification Model is fitted into the training data.
6. To evaluate the performance of Random Forest Model we have used the test set.

We have developed and trained our model on the above classification method. Below are the results of the model's evaluation and validation. 

**Evaluation and Validation**
Machine learning models are essential in many fields, and in order to guarantee their efficacy, their performance must be carefully assessed. The assessment and validation of a machine learning model utilizing a range of metrics, such as ROC curves, Mean Squared Error (MSE), precision, recall, F1-score, and accuracy can be done. 

Metrics for Evaluation
1. Accuracy The total validity of the model's predictions is gauged by accuracy, a basic metric.
2. Accuracy, Memory, and F1-Score
Important metrics for binary classification include precision, recall, and F1-score. These metrics reveal how well the model balances precision and recall, makes accurate positive predictions, and identifies all positive cases.
3. The MSE, or mean squared error
The average squared difference between the anticipated and actual values can be assessed using the Mean Squared Error (MSE) metric if your problem is a regression problem.
4. ROC Curve and AUC The model's capacity to distinguish between classes can be evaluated using the Receiver Operating Characteristic (ROC) curve and Area Under the Curve (AUC).

We have provided a summary of the computed metrics and their values, in our code. Attaching screenshots of the results obtained.

Our model focuses on the predictive model designed to classify instances based on features such as question, item_name, and hours_diff. The model is trained on a dataset containing pre and post-purchase questions from AWS Data Registry.
Accuracy: 0.99
Precision: 1.00
Recall: 0.99
F1 Score: 0.99
Mean Squared Error (MSE): 0.01
ROC AUC Score: 1.00

![image](https://github.com/vishalsingh-11/Product-purchase-detection/assets/150567765/cb1a9da8-3626-41f8-b516-3907e516545b)

The ROC Curve output is as below
![image](https://github.com/vishalsingh-11/Product-purchase-detection/assets/150567765/c3c6586b-c0bc-4c33-b179-aaf8c830cfe8)

**Some observations:**
Accuracy: The model predicts the target variable accurately, with an astounding accuracy of 99%.
Precision and Recall: Both classes (0 and 1) have consistently high precision and recall scores, indicating that the model is good at correctly identifying positive instances while reducing false positives.
F1 Score: The model's ability to provide a harmonized measure of its overall performance is reinforced by its 0.99 F1 score, which strikes a balance between precision and recall.
The model's predictions are very close to the actual values, as indicated by the low Mean Squared Error (MSE) of 0.01; this is especially significant in regression problems.
ROC AUC: An ideal score A ROC AUC score of 1.00 indicates the best possible ability to differentiate between the two classes, showcasing the model's excellent discriminatory power.


**Hyperparameter Tuning**
A critical step in maximizing the effectiveness of machine learning models is hyperparameter tuning. It entails methodically determining which set of hyperparameters will maximize a model's performance. We'll talk about the hyperparameter tuning procedure in this section, with an emphasis on using AWS SageMaker's hyperparameter tuning feature.

Hyperparameter Adjustment Method
The hyperparameter tuning feature of AWS SageMaker has been used to adjust the model's hyperparameters. The process of looking up hyperparameter combinations and finding the set that optimizes the model's performance is made automated by this functionality.

Examined Hyperparameters
The exact model architecture being used determines which hyperparameters are taken into account for tuning. For example, one could investigate parameters such as n_estimators, max_depth, and min_samples_split in a RandomForestClassifier, we used random_state parameter.

Hyperparameter Tuning Outcomes
The process of hyperparameter tuning was carried out, and the target metric—such as accuracy or F1-score—was used to determine the ideal hyperparameters. To evaluate the effect on model performance, it is imperative to examine the outcomes of the hyperparameter tuning.

In summary
The process of hyperparameter tuning is iterative, and the model's predictive power can be greatly increased by utilizing the results of AWS SageMaker's hyperparameter tuning feature. Evaluate the model's performance on a regular basis and adjust the hyperparameters if the requirements or data distribution change.



