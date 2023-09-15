# **Song Recommendation System**
This is a full-scale recommendation system project done for my capstone at MIT. I built Rank-based, Similarity-based, Matrix Factorization, Clustering-based, and Content-based recommendation systems, then optimized and evaluated the models to craft personalized recommendations for users based on past song and user interaction data.




## **Problem Definition**


### **The Context:**

Why is this problem important to solve?

  - With the advent of technology, societies have become more efficient with their lives. At the same time, however, individual human lives have also become more fast-paced and distracted, leaving little time to explore artistic pursuits. Also, technology has made significant advancements in the ability to coexist with art and general entertainment. It has in fact made it easier for humans with a shortage of time to find and consume good content.

  - Almost every internet-based company's revenue relies on the time consumers spend on its platform. These companies need to be able to figure out what kind of content is needed in order to increase customer time spent and make their experience better. Therefore, one of the key challenges for these companies is figuring out what kind of content their customers are most likely to consume.

  - Spotify is one such audio content provider with a huge market base across the world. With the ever-increasing volume of songs becoming available on the Internet, searching for songs of interest has become a tedious task in itself. However, Spotify has grown significantly in the market because of its ability to recommend the ‘best’ next song to each and every customer based on a huge preference database gathered over time - millions of customers and billions of songs. This is done by using smart recommendation systems that can recommend songs based on users’ likes/dislikes.


### **The objective:**

What is the intended goal?

  - Build a recommendation system to propose the top 10 songs for a user based on the likelihood of listening to those songs.


### **The key questions:**

What are the key questions that need to be answered?

 - How can we effectively analyze user preferences and behavior to understand what kind of songs they are most likely to enjoy?
 - What features and data sources should be considered in the recommendation system to capture users' preferences and improve the quality of recommendations?
 - Are there any additional features or data sources that we can utilize to improve the systems that we build?
 - How can we measure the performance and effectiveness of the recommendation system, and what evaluation metrics should be used to determine its success?


### **The problem formulation**:

What is it that we are trying to solve using data science?
 - The problem that we are trying to solve using data science is to build a recommendation system for song suggestions on the Spotify platform. The objective is to propose the top 10 songs for each user based on the likelihood of them listening to those songs. This involves understanding and analyzing user behavior, preferences, and historical interactions with songs to generate personalized and relevant song recommendations. By using machine learning and data science techniques, we aim to develop a recommendation model that can effectively predict and suggest songs that users are likely to enjoy, ultimately enhancing the user experience and increasing engagement on the platform.




## **Conclusion and Recommendations**

**1. Comparison of various techniques and their relative performance based on chosen Metric (Measure of success)**:
How do different techniques perform? Which one is performing relatively better? Is there scope to improve the performance further?

  - We built recommendation systems using six different algorithms in order to achieve the goal of extracting meaningful insights from the data and building a recommendation system that helps in recommending songs to platform users. They are as follows:

   - Rank-based using averages
   - User-user similarity-based collaborative filtering
   - Item-item similarity-based collaborative filtering
   - Model-based (matrix factorization) collaborative filtering
   - Cluster-based
   - Content-based using TF-IDF feature extraction

  - For all of these algorithms except Rank-based and Content-based, grid search cross-validation is used to find the optimal hyperparameters for the data, and improve the performance of the model. Optimized models were built using these yielded parameters.

  - For performance evaluation of those same models, precision@k and recall@k are used. The F_1 score is calculated for each working model using these two metrics.

  - Overall, the baseline user-user similarity-based recommendation system has given the best performance in terms of the F1-Score (0.504). This was followed by the optimized model-based recommendation system which had a F1-Score of (0.502).

  - Collaborative Filtering searches for neighbors based on similarity of song preferences and recommends songs that those neighbors listen to while Matrix factorization works by decomposing the user-item interaction matrix into the product of two lower dimensionality rectangular matrices.

  - Matrix Factorization assumes that both songs and users are present in some low dimensional space describing their properties, therefore having the lowest RMSE (1.0141), and recommends a song based on its proximity to the user in the latent space. This also implies that it accounts for latent factors.

  - The two other models used were rank-based and content-based. The simple rank-based model ranked songs by popularity based on the highest average play_count to the lowest. The content-based model was much more complex and utilized the TF_IDF feature extraction method to compare similar content based on the strings contained in the title, album name, and artist name of each song. Both of these yielded similar results to most of the other models, but they do not use the same performance metrics.


**2. Refined insights**:
- What are the most meaningful insights from the data relevant to the problem?

 - The use of different algorithms provides diverse insights into the data, helping to explore different aspects of song recommendations and their performance.

 - Different models have different complexities and strengths. While collaborative filtering and matrix factorization can handle user preferences and latent factors well, the rank-based and content-based models offer simplicity and interpretability.

 - We'll lean towards RMSE and Precision as the most influential performance metrics because we care more about having the recommended songs be more likely to be relevant to the user than sacrifice the quality of our recommendations in order to have a higher recall (having more relevant songs get recommended).


**3. Proposal for the final solution design:**
- What model do you propose to be adopted? Why is this the best solution to adopt?

 - The recommended course of action is to apply the Matrix Factorization optimized model that we created. It has the best metrics for RMSE and precision and is a close second-best for F1-Score. Its complexity will come as a subtle pleasantry for users because it will be capable of finding more than just the most popular songs or obvious recommendations that might come from the rank-based and content-based models.

 - We recommend deploying this model as soon as possible since it has displayed quality, and we want to begin upgrading our users' experiences earlier rather than waiting. Then we will take steps for improvements or stronger replacements.

 - Simple options to improve this model or find an even stronger model include trying to improve the performance of these models using hyperparameter tuning.

 - There are multiple options to improve or replace the initial model that we recommended to deploy:
   - We can build a more complex hybrid recommendation system - based on the recommendation systems that we built and analyzed in this notebook, we would lean toward creating a hybrid recommendation system with the model-based and the content-based recommendation systems that we built.
   - Another improvement to consider is researching the users of the platform along with any negative biases, negative stereotypes, or negative information/content bubbles, and build algorithmic filtering solutions to break those negative patterns. With the power of how influential these recommendation systems are likely to be on our users and their experience, we also hold responsibility to strive towards building solutions to problems that models like ours that are built on past data hold.
   - An example of a tailored solution like this would be to add song lyric data to our content-based model, perform sentiment analysis on that data, and then tailor the model to avoid producing content recommendation bubbles that overwhelm users with songs that are significantly more likely to contribute to high levels of anxiety or depression.
