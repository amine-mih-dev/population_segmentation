# population_segmentation
find key differences between customer population and general population using principal component analysis

# Project: Identify Customer Segments

In this project, i applied unsupervised learning techniques to identify segments of the population that form the core customer base for a mail-order sales company in Germany. These segments can then be used to direct marketing campaigns towards audiences that will have the highest expected rate of returns. The data that i usedd has been provided by Udacity partners at Bertelsmann Arvato Analytics, and represents a real-life data science task.

This notebook helped me complete this task by providing a framework within which i performed my analysis steps. In each step of the project, i saw some text describing the subtask that you will perform, followed by one or more code cells for you to complete your work. **Feel free to add additional code and markdown cells as you go along so that you can explore everything in precise chunks.** The code cells provided in the base template will outline only the major tasks, and will usually not be enough to cover all of the minor tasks that comprise it.

It should be noted that while there are precise guidelines on how i should handle certain tasks in the project, there are also places where an exact specification is not provided. **There are times in the project where i need to make and justify my own decisions on how to treat the data.** These are places where there may not be only one way to handle the data. In real-life tasks, there may be many valid ways to approach an analysis task. One of the most important things i should do is clearly document my approach so that other scientists can understand the decisions i've made.

# What I Learned
- Load the Data: recognize the different files associated with this project and exploring the data to gain some general familiarity with it.
- Data Preprocessing: 

  - Assessed Missing Data where we first convert missing value Codes (provided in the data dictionary) to NaNs
  - assessed how much missing data is in each column and dropped columns that are above the threshold, then did the same operation with the rows
  - after cleaning, special features are then selected and re-Encoded with `get_dummes()`, categorical features are re-Encoded and mixed-type features are re-Engineered
  - after completing the cleaning process a Cleaning Function is theen created to perform the samae cleaning on future data
  
- Feature Transformation:
  
  - Feature Scaling is applied using `StandardScaler()` after filling NaNs with most frequent value
  - after Scaling we apply Dimentionality reduction using Sklearn's PCA, we were able to trim off almost 40% of the initial features (from 193 to 119) while perserving 95% of the variance
  - the wieghts of the principle components are interpreted to uncover general conclusions about hidden trends in our data.
  
- Clustering:

  - Clustering is Appled to the General Population using sklearns `KMeans` where we try different cluster numbers from 1 to max 30 and select the optimal number of clusters using the elbow method (used `kneed`'s `KneeLocator`)
  - now we apply everything again but to the customer data (everything above was done on the general population data)
  - we compared customer data and demographic data clusters to find key defferences between the most overrepresented segment and the most underrepresented segment.
