# Amazon Vine Analysis

Since your work with Jennifer on the SellBy project was so successful, you’ve been tasked with another, larger project: analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

PySpark was used to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next, using Pandas determine if there is any bias toward favorable reviews from Vine members in the dataset. 


## Background
Amazon Vine invites the most trusted reviewers on Amazon to post opinions about new and pre-release items to help their fellow customers make informed purchase decisions. Amazon invites customers to become Vine Voices based on their reviewer rank, which is a reflection of the quality and helpfulness of their reviews as judged by other Amazon customers. Amazon provides Vine members with free products that have been submitted to the program by participating vendors. Vine reviews are the independent opinions of the Vine Voices. The vendor cannot influence, modify or edit the reviews. Amazon does not modify or edit Vine reviews, as long as they comply with our posting guidelines. A Vine review is identified with the green stripe Customer review from the Amazon Vine Program.

Data from Amazon's Major Appliance department was analyzed to determine paid Vine review makes a difference in the percentage of 5-star reviews. The Extract, Transform, and Load (ETL) process used on the Major Appliance dataset. An Amazon Web Service (AWS) and Relational Database Service (RDS) pgAdmin database was created, and the Major Appliance dataset was downloaded from and Amazon S3 bucket. Local pgAdmin was utilized to connect to AWS RDS, pySpark (via Google CoLab), and postgreSQL were used against the dataset to create four separate DataFrames to match the table schema within pgAdmin. The transformed data was then uploaded into pgAdmin on a local computer.  

Once the tables were created on a local computer they could be further sorted and filtered using Pandas.

## Results
The data tables created from the AWS RDS ETL process were: customers_table, products_table, review_id_table, and vine_table.  This data is directly from Amazon S3 bucket and working on Google Colab.
Once the tables were transferred in csv format to local computer via pgAdmin, they could be further sorted and filtered using Pandas.  Figure 1 below shows a Pandas DataFrame of the vine_table with 96,900 reviews.
![Fig - D-2_01](https://github.com/ASCHEET/Amazon_Vine_Analysis/blob/main/Resources/D-2_vine_table.png?raw=true)

Further sorting to include products with 20 or more reviews, resulted in 5,364 helpful product reviews.
![Fig - D-2_02](https://github.com/ASCHEET/Amazon_Vine_Analysis/blob/main/Resources/D-2_02_vine_helpful.png?raw=true)

Refining the helpful product reviews for good votes greater than 50% is below, resulting in 4,992 product reviews.
![Fig D-2_03](https://github.com/ASCHEET/Amazon_Vine_Analysis/blob/main/Resources/D-2_03_vine_good_helpful.png?raw=true)

Sorting the reviews by the Paid Vine revies yielding only 35 paid Vine reviews that were helpful according to >50% upvote criteria.
Two new Pandas DataFrames were created to retrieve all rows where the review was part of the Vine program and to retrieve all rows where the review was not part of the Vine program.  This resulted in 35 paid reviews and 4,957 unpaid reviews that included the >50% 'helpful vote' criteria.

Paid Reviews              |  Unpaid Reviews
:------------------------:|:-------------------------:
![Fig D-2_04](https://github.com/ASCHEET/Amazon_Vine_Analysis/blob/main/Resources/D-2_04_vine_good_helpful_Y.png?raw=true)  |  ![Fig D-2_05](https://github.com/ASCHEET/Amazon_Vine_Analysis/blob/main/Resources/D-2_05_vine_good_helpful_N.png?raw=true)



Vine 5 star Reviews       |  Non-Vine 5 star Reviews
:------------------------:|:-------------------------:
![Fig D-3_03](https://github.com/ASCHEET/Amazon_Vine_Analysis/blob/main/Resources/D-3_03_vine_5_star.png?raw=true)  |  ![Fig D-3_04](https://github.com/ASCHEET/Amazon_Vine_Analysis/blob/main/Resources/D-3_04_not-vine_5_star.png?raw=true)



Paid Vine 5-star reviews accounted for 51.4% of the data, whereas 39.6% were unpaid 5-star reviews. 

% of Paid 5-Star Reviews  |  % of Unpaid 5-Star Reviews
:------------------------:|:---------------------------:
![Fig D-3_05](https://github.com/ASCHEET/Amazon_Vine_Analysis/blob/main/Resources/D-3_05_percnetage_vine_5_star2.png?raw=true)|![Fig D-3_06](https://github.com/ASCHEET/Amazon_Vine_Analysis/blob/main/Resources/D-3_06_percnetage_non-vine_5_star2.png?raw=true)

## Summary
This analysis could not conclude a bias in the selected data from the Amazon Major Appliance reviews, Vine reviews did not appear to affect 5-star reviews.  There were significantly more 5-star reviews from unpaid reviews.

Another helpful analysis would be if there was a time component for understanding effectiveness of reviews.  For example, if reviews are more read and voted on in the first month or two of the review and if the traffic associated with the review tapers off.  That can be used to perhaps insert an additional review after a certain amount if time is warranted.  Plotting the 'good votes' over time to see how optimum time a review is used before a new review could be added.  
Additionally, although 5-star reviews are desirable, too much focus may not always practical.  An in-depth analysis of the lower star reviews to determine if there were issues with manufacturing would be value added.  For example, using Natural Language Processing, analysis can be performed on items such as "quality", "stopped working", "better" to determine what issues could be addressed by the manufacturer.














