## From Downloads to Opinions: Analyzing Google Play Apps and User Sentiment
This project analyzes Android apps from the Google Play Store along with their user reviews to understand:
* How apps perform in terms of ratings, installs, size, and price
* How users feel about these apps through sentiment analysis
* Which app types (free vs paid) and categories perform better both numerically and emotionally
By combining app metadata with user review sentiment, this project uncovers patterns in user behavior and app performance, and evaluates machine learning models that automatically classify review sentiment as positive, negative, or neutral.

## Dataset Information
We use two datasets:
1. apps.csv
Contains data for apps published on Google Play, including : App, Category, Rating (1.0 – 5.0), Reviews, Size, Installs, Type (Free or Paid), Price, Content Rating 

2. user_reviews.csv
Contains user review data, including : App, Translated_Review, Sentiment – Label (Positive, Negative, or Neutral), Sentiment_Polarity (-1 to +1), Sentiment_Subjectivity (0 to 1)

These two datasets are merged on the App column to connect what an app is with what users say about it (reviews).

## Key Objectives
1. App Market Analysis
Understand the distribution of apps across categories, prices, sizes, and installs.

2. Rating & Popularity Analysis
Study how app ratings are distributed and how they relate to size, installs, and type (Free vs Paid).

3. Sentiment Analysis on Reviews
Use NLP and machine learning to classify user review sentiment (Positive / Negative / Neutral).

4. Free vs Paid & Category-wise Sentiment
Examine how sentiment polarity differs between free and paid apps and across categories.

5. Model Comparison
Build and compare Naive Bayes and SVM (Support Vector Machine) models for sentiment classification.

6. Insights & Recommendations
Extract actionable insights for app developers, marketers, and businesses.

## Methodology
1. Data Loading & Cleaning
* Loaded apps.csv and user_reviews.csv into Pandas DataFrames.
* Removed duplicate app entries based on App.
* Cleaned numerical columns:
     * Removed +, ,, $, and M symbols from Installs, Size, and Price.
     * Converted them into proper numeric types.
* Handled missing values:
     * Filled missing ratings using median rating.
     * Dropped rows with missing review text or sentiment.
       
2. Merging App and Review Data
* Joined apps and reviews data using the App column.
This enabled combined analysis: app characteristics + user opinions.

3. Exploratory Data Analysis (EDA)
* Plotted:
      * Number of apps per category
      * Distribution of ratings
      * Size vs Rating relationships
      * Paid vs Free install distribution (log scale)
      * Sentiment distribution and polarity scores
This helped us see which categories dominate, how well apps are rated, and how users feel overall.

4. Text Preprocessing & Feature Engineering
* Used Translated_Review as input text for sentiment modeling.
* Applied TF–IDF (Term Frequency–Inverse Document Frequency) to convert text into numerical features.
* Removed English stopwords
* Limited vocabulary with max_features=5000

5. Machine Learning Models for Sentiment
We trained two models on TF–IDF features:
* Multinomial Naive Bayes : Classic baseline model for text classification, Simple and fast
* Linear SVM (Support Vector Machine) : More powerful classifier, Performs well on high-dimensional sparse data like TF–IDF

We split the data into train and test sets using an 80/20 split.

6. Model Evaluation
Compared Naive Bayes and SVM using:
* Accuracy
* Precision, Recall, F1-score
* Confusion Matrix
Evaluated how well models predict each sentiment class (Positive, Neutral, Negative).

7. Visualization
* Sentiment Distribution bar plot
* Sentiment polarity violinplots for Free vs Paid apps
Visualized model results and patterns to make insights easier to understand.

 ## Key Insights
1. App Market & Rating Insights
* FAMILY and GAME categories have the highest number of apps, followed by TOOLS and BUSINESS.
* The average app rating is around 4.1–4.2, with most apps rated above 4.0.
* Rating distribution is right-skewed, meaning most apps are rated positively.

2. App Size & Price
* Many highly-rated apps fall within the 2–20 MB size range.
* Most apps are Free or priced under $10.
* Some categories like Medical contain very high-priced apps (up to hundreds of dollars), often niche or “novelty” apps.

3. Installs: Free vs Paid
* Free apps receive significantly more installs than paid apps.
* Paid apps have fewer installs but often higher quality perception.

4. Sentiment Trends
* Positive sentiment dominates in user reviews, with far fewer negative and neutral reviews.
* Free apps show more extreme negative sentiment outliers, suggesting users are more critical of free apps.
* Paid apps tend to have more stable and slightly higher sentiment polarity.

5. Model Performance
* Naive Bayes achieved a good baseline accuracy (~70–75%).
* SVM (LinearSVC) outperformed Naive Bayes, reaching around 90% accuracy on sentiment classification.
* SVM handled Neutral sentiment better and showed stronger overall performance.

## Recommendations
1. Optimize App Size & Performance : Aim to keep app size within a reasonable range (≈ 2–20 MB when possible). Users seem to prefer lightweight, fast apps.

2. Improve Free App Experience : Free apps receive more negative sentiment. Reduce intrusive ads, improve user onboarding, and fix crashes quickly.

3. Leverage Paid App Quality : Paid apps show more stable and positive sentiment. Emphasize quality, reliability, and unique features to justify price.

4. Use Sentiment Monitoring : Continuously analyze user reviews using an SVM-based sentiment model. Track changes in sentiment over time to identify issues early.

5. Category & Pricing Strategy : Focus on high-demand categories like GAME, FAMILY, and TOOLS, but ensure differentiation. Avoid unrealistically high pricing unless the app offers clear, specialized value.

6. Future Improvements : Move from classic ML to transformer-based models like BERT for even better sentiment accuracy. Build a simple dashboard for real-time sentiment tracking.

 ## Conclusion
This project analyzed Google Play apps and user reviews to understand app performance and user sentiment. It shows that Family and Game apps are most common and highly rated, free apps get more installs but more critical reviews, and paid apps have more positive sentiment. Using TF–IDF and SVM, sentiment can be reliably classified. 

These insights derived can guide developers and businesses in Designing better apps, Improving user experience, Making smarter pricing decisions, Continuously monitoring user satisfaction.

This project is a solid foundation for more advanced NLP work, such as deep learning–based sentiment analysis, topic modeling, and recommendation systems.
