# Product-Purchase-Detection
This project aims to perform product analysis and detect users' purchase state from their product-related questions from Amazon.
### TEAM MEMBERS

Vishal Bondili - 801307348

Sree Harsha Nimmagadda - 801308050

Vaishnavi Baiken - 801316841



### Project Scope
The machine learning component in this project aims to address a few specific challenges and opportunities within the domain of pre and post-purchase product questions in the e-commerce space. The focus will be on leveraging the dataset from Amazon to gain insights and develop models for the following tasks.

#### Objectives
The dataset appears to be designed to explore and analyze the relationship between customers and businesses. The dataset gives us a scope to study the following-
* Customer Behavior Analysis: Understanding how long it takes for customers to have inquiries after making a purchase and identifying patterns or trends in this behavior.
* Customer Satisfaction: Investigating if there's a correlation between the time gap and the nature of the questions, potentially indicating customer satisfaction or dissatisfaction.
* Product Performance: Analyzing the types of questions for specific products to gain insights into product performance and identify areas for improvement.
* Predictive Modeling: Building models to predict the likelihood of customers asking questions based on the time elapsed since the purchase.

### Domain
Pre- and post-purchase product questions (E-commerce) 
#### Characteristics:

Active customer interaction through pre- and post-purchase questions.
Dynamic product catalog with frequent changes.
Varied product-related inquiries.

#### Opportunities:
Insights into customer preferences and satisfaction.
Proactive customer support.
#### Specific Task:

Analyzing temporal patterns in customer inquiries.
Investigating correlations between question types and post-purchase time.
#### Stakeholders:
The major stakeholders for this project would be 
E-commerce platforms
Businesses and sellers
Customers

### Literature Review

### Data Source(s)

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
 
### Domain-specific Challenges

Ambiguity in Product Descriptions: 
Challenge: Figuring out what customers mean in their diverse product-related questions can be tricky due to the sometimes unclear product descriptions.

Dynamic Product Catalog:
Challenge: Products on Amazon change a lot. Adapting our system to always understand the latest products and features is a constant challenge.

### KPI’s





