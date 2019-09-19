---
layout: post
title:  "Recommendation Engine"
date:   2019-08-11 9:45:31 +0530
---

 > Hi folks, this blog is about a problem statement that I solve recently.


**Problem Statement**: Build a generic recommendation engine which is going to recommend a new product based of previous customer preferences and customer segmentation that suits customer profile.

**Introduction**

*Content-Based Filtering* was the initial algorithm that was used in the *Recommendation Engine*. It will recommend the same product lines that you liked in the past. There are many algorithms that come under content-based filtering can be used in *Recommendation Engine* such as Top n approach, Rating scale approach, Euclidean Distance, Pearson Correlation. The drawback of content-based algorithm is, it will not recommend products which customer has not purchased in the past. *Collaborative filtering* is used to overcome this problem.

*Collaborative filtering* is the fundamental underlying principle of *Recommendation Engine*. It can use either user to user similarity or item to item similarity. User-User collaborative filtering can be used when there are a smaller number of users in the database. The computation complexity increases with an increasing customer base. The problem arises when a new user or new product is entered to the list, and it is called *Cold Start*. *Recommendation Engine* should identify the new user and recommend the most popular products to him. For example, in online streaming websites, the movies recommended for a new person will be based on the popularity of the film in language-wise and region-wise. For a product cold start, initially, engine is designed to do content-based filtering and make the recommendation. Once the users start interacting with this new product, the model will begin recommending to the right people.

**Approach**

* Assumption 1: I already possess data of various FMCG products and its ingredients.
* Assumption 2: I already possess data on customer profile and their purchase history.

![p1](/images/rec-eng-1.png)

Let’s take an example of a new product as Patanjali Aloe Vera moisturiser. Since we are starting with Product cold start; Recommendation engine should follow any of the content-based filtering algorithms. It can run a cluster analysis with the given ingredient to find which cluster it belongs to.

From the cluster analysis, it identifies that the product belongs to the cluster called **“Herbal Cosmetics”**. Now having the cluster in our hand, we also have the list of the products that are closely related to our new product. With this recommendation engine filters out the potential customer for this new product and recommend this product through the interest of the main page of the buyer segment. In addition to that, whenever a random customer buys any product in this cluster, the recommendation engine lists the other relevant products along with the new product.

![p2](/images/rec-eng-2.png)

Once we get enough interaction from the customer by purchasing the product and rating the new product, we have enough data to run collaborative filtering. In this filtering, we use matrix factorisation to identify the target customer by predicting what rating he/she might give for the new product. Matrix factorisation is usually performed to reduce the data storage in the system and to predict the value for an unknown slot in the matrix.

![p3](/images/rec-eng-3.png)

Let us take an example from the above picture. In a given cluster, A, B, C and D are the customers who gave ratings to different products M1, M2, M4, M5 including our new product M3. Using the matrix factorisation, we split the matrix into two smaller matrices based on its rank. It can be seen that few products were not rated by the customers because they have not tried the product. Now by applying the method again, we can determine who is my potential customer for my new product, Patanjali Aloe Vera Moisturizer.

![p4](/images/rec-eng-4.png)


For customer D, using this technique, we predicted that he would give five ratings for the new product. So, the recommendation engine recommends this product to this particular customer.

Thanks for reading, see you soon with another post.
