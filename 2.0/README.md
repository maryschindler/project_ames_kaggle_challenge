# Read for Project 2 - Ames Housing Data and Kaggle Challenge

Due: **Friday, Oct 22**.
Last Day for Kaggle: **Friday, Oct 22**.

Files for Submission on Github Enterprise:

- A README.md
- Jupyter notebooks with your analysis and models (renamed to describe your project)
- At least one successful prediction submission on [DSI-US-11 Regression Challenge](https://www.kaggle.com/c/dsi-920-ames/submissions)
- Data files
- Presentation slides
- Any other necessary files (images, etc.)

### The Data Science Process

**Problem Statement**

- We are presented with datasets from the Ames Assessor’s Office used in computing assessed values for individual residential properties sold in Ames, IA from 2006 to 2010. The goal of our assessment is to determine a predictive model for determining the Sale Price of a residence based on a variety of features. Using regression, we want to establish a model that reduces Root Mean Squared Error, the metric that tells us, on average, how far apart the predicted values are from the observed values in a dataset. The lower the RMSE, the better fitting the model to the dataset.

**Data Cleaning and EDA**
- The file data_desc.txt acts our as data dictionary, holding the definitions and descriptions of the different criteria assessed for individual residential properties. 
- The biggest hurdle to overcome on this project was determine which features, or housing criteria, to use to build our model. Initially, I tried to use my domain knowledge to pick from the list of features the features I deemed important to establish a higher 'baseline' score separate from the overall datasets median. 
- Thereafter I examined the features that had the highest correlation to 'Sale Price' to fine-tune my model.

**Preprocessing and Modeling**
- Once I established the list of features I was going to base my model on, I started my pre-processing and modeling. For those features which were categorical I either mapped these to numerical values or dumify the columns. I also introduced some hyperparameters, ensuring that no feature was accounted for twice. For my final model, which was based on those values which had a correlation value of 0.20 or higher on 'Sale Price', all of the values were numerical so no mapping or transforming was needed. I choose, however, to treat 'full_baths' as a categorical variable so I got dummies for this column. 

**Conclusion and Business Recommendations**</br>
    I had the opportunity to iterate Linear Regression on several lists of features in order to develop a lower RMSE score for our Kaggle submission. At first, I attempted to use my domain knowledge with limited analysis in order to produce a set of features which was impactful toward ‘Sale Price’. Using only Linear Regression I was able to get a Kaggle score of approximately 32,000. If, on average, a predicted house price varies from the true house price by only $32,000, the model decent: if a house costs $320,000, a 10% difference could be attributed to the season in which the house is being sold. </br>
    The second list of features on which I iterated this process did produce a better Kaggle score, however, the goal of the second set was to use Standard Scaler and regrettably I could not get my test_df to scale appropriately to submit a Kaggle score with scaled features. The second list of features did produce a slightly better score though with Linear Regression of 31552.64, a difference of 718 points. </br>
    The third and final list of features on which I iterated this process was a list picked solely from a Seaborn heatmap correlation plot. I choose to use all features that had a positive impact of 0.20. This list of features produced a score of 29308.85, a difference of 2,244 from the previous score. As this list was produced without any of my domain knowledge yet still produce the best score, I conclude the best model would be built using a combination of existing domain knowledge and the features which correlated the most to ‘Sale Price’. Neighborhood, for example, would like have a real impact on average house prices, but this was not among the features listed in the Seaborn heatmap. </br>
    Some combination of the 'least_feats_df' and 'features_df' would have likely resulted in the highest score. Standard Scaler would have likely produced the best results, however I ran out of time to tune this model appropriately. </br>
    The features which had the greatest impact on price were: Overall Quality, Living Area Above Ground, Garage Area, the Number of Cars a Gara could hold, Total Basement Square Feet, 1st Floor Square Feet, the Year the Home was Built, the Year the Home was Remodeled or an Addition was Added, the Number of Full Baths, and the Year the Garage was Built.</br>
    The two recommendations I have for increasing the price of one’s home are 1) improve one’s kitchen quality or size and 2) if one has an unfinished basement, finish it. </br>
    Features such as the Year Sold, the Number of Basement Half Baths, and presence of an Enclosed Porch reduced the price of a home. This makes sense as likely these features suggest either a house-flip, a lot of upkeep, or in the case of Basement Half Baths, may be mid-construction. </br>