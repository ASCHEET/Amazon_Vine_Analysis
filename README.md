# Amazon Vine Analysis

Since your work with Jennifer on the SellBy project was so successful, you’ve been tasked with another, larger project: analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

In this project, you’ll have access to approximately 50 datasets. Each one contains reviews of a specific product, from clothing apparel to wireless products. One of these datasets and use PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next, using Pandas determine if there is any bias toward favorable reviews from Vine members in the dataset. 


## Background
The Amazon Vine program is a service that allows manufacturers to receive reviews for their products. Companies pay a fee to Amazon, and in return, Amazon sends products to Vine Members, who are required to publish a review.

Data from Amazon's Major Appliance department was analyzed to determine paid Vine review makes a difference in the percentage of 5-star reviews. The Extract, Transform, and Load (ETL) process used on the Major Appliance dataset. An Amazon Web Service (AWS) and Relational Database Service (RDS) pgAdmin database was created, and the Major Appliance dataset was downloaded from and Amazon S3 bucket. Local pgAdmin was utilized to connect to AWS RDS, pySpark (via Google CoLab), and postgreSQL were used against the dataset to create four separate DataFrames to match the table schema within pgAdmin. The transformed data was then uploaded into pgAdmin on a local computer.  

Once the tables were created on a local computer they could be further sorted and filtered using Pandas.

## Results
The data tables created from the AWS RDS ETL process were: customers_table, products_table, review_id_table, and vine_table.  This data is directly from Amazon S3 bucket and working on Google Colab.
![Fig D-1_01]()
A total of 96,901 review were collected and analyzed. Once the tables were transferred in csv format to local computer via pgAdmin, they could be further sorted and filtered using Pandas.

Figure 2 below shows a Pandas DataFrame of the vine_table with 96,901 reviews.
![Fig - D-2_01]()

Further sorting to include products with 20 or more reviews, resulted in 5,364 helpful product reviews.
![Fig - D-2_02]()

Refining the helpful product reviews for good votes greater than 50% is below, resulting in 4,957 product reviews.
![Fig D-2_03]()

Sorting the reviews by the Paid Vine revies yielding only 35 paid Vine reviews that were helpful according to >50% upvote criteria.
Two new Pandas DataFrames were created to retrieve all rows where the review was part of the Vine program and to retrieve all rows where the review was not part of the Vine program.  This resulted in 35 paid reviews and 4,957 unpaid reviews that included the >50% 'helpful vote' criteria.

Paid Reviews              |  Unpaid Reviews
:------------------------:|:-------------------------:
![Fig D-2_04]()  |  ![Fig D-2_05]()



Vine 5 star Reviews              |  Non-Vine 5 star Reviews
:------------------------:|:-------------------------:
![Fig D-3_03]()  |  ![Fig D-3_04]()

Paid Vine 5-star reviews accounted for 47.25% of the data, whereas 52.4% were unpaid 5-star reviews.

% of Paid 5-Star Reviews  |  % of Unpaid 5-Star Reviews
:------------------------:|:---------------------------:
![Fig D-3_05]()|![Fig D-3_06]()

## Summary
This analysis could not conclude a bias in the selected data from the Amazon Major Appliance reviews, Vine reviews did not appear to affect 5-star reviews.  There were slightly more 5-star reviews from unpaid reviews.

Additional analysis should be conducted against multiple Amazon review datasets, with the same parameters that were used against the Lawn and Garden dataset.  Other datasets could show that Vine reviews are more likely to give 5-star product reviews.  It would also be interesting to determine if male or female are more likely to leave a review in general versus how likely are they to leave a 5-star review as a Vine member or unpaid reviews.  














