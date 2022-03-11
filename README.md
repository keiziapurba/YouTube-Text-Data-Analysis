# Youtube-Analysis

## A YouTube analysis case study that contains sentiment analysis, emoji analysis, likes vs views analysis, and trending videos text on YouTube
---

## Table of Content
  * [Background](#background)
  * [Data Description](#data-description)
  * [Project Outline](#project-outline)
    - [Sentiment Analysis](#sentiment-analysis)
    - [Wordcloud Analysis](#wordcloud-analysis)
    - [Emoji Analysis](#emoji-analysis)
    - [Collect Entire Data of YouTube](#Collect-Entire-Data-of-YouTube)
    - [Which Category Has the Maximum Likes?](#Which-Category-Has-the-Maximum-Likes?)
    - [Find Out Whether Audience is Engaged or Not](#Find-Out-Whether-Audience-is-Engaged-or-Not)
    - [Which Channels Have the Largest Number of Trending Videos?](#Which-Channels-Have-the-Largest-Number-of-Trending-Videos?)
    - [Does Punctuations in Title and Tags Have Any Relation With Views, Likes, Dislikes Comments?](#Does-Punctuations-in-Title-and-Tags-Have-Any-Relation-With-Views,-Likes,-Dislikes-Comments?)
    - [Insights](#insights)

---

## **Background**
- 1 billion hours of YouTube content are watched per day
- YouTube is the 2nd most visited site in the world
- YouTube attracts about 44% of all internet users
- About 33% of all mobile internet traffic belongs to YouTube

### **Data Description**
- UScomments dataset contains information about video id, comment text, likes and replies. Total data points: 691400 and total columns: 4
<img width="386" alt="Screen Shot 2022-03-11 at 01 16 00" src="https://user-images.githubusercontent.com/91368463/157728674-c446797e-5922-427b-a3df-d6cd9ee76488.png">

- After checking the dataset, we can see that it has missing values. That's why we have to filter the dataset so it don't have any missing values.

## Project Outline

### **- Sentiment Analysis**
- First, install necessary package in this case use TextBlob to see the sentiment. To perform Sentiment Analysis, there are 2 key points: Polarity and Subjectivity. Here we focus on polarity. If polarity: +1 that means we have high polarity and if we don't have any sentiment, it carries subject, that's what subjectivity is.
- In this step, we want to see each comment text polarity and then make polarity columns in the dataset.
<img width="606" alt="Screen Shot 2022-03-11 at 01 36 41" src="https://user-images.githubusercontent.com/91368463/157731958-daaa820a-093f-4c21-a2a0-e7c59baa4c85.png">


### **- Wordcloud Analysis**
- Install wordcloud package, then import WordCloud and STOPWORDS. We want to see any positive and negative words that contain comments text.
- Make 2 variables, one with polarity = 1, which means positive and other with polarity = -1, which means negative. We store all the positive words in variable with polarity = 1 and all negative words in variable with polarity = -1.
<img width="615" alt="Screen Shot 2022-03-11 at 01 45 34" src="https://user-images.githubusercontent.com/91368463/157733349-813e5dca-8c3e-452c-a2c7-bbb61f504999.png">

- Based on the visualization, the most used positive words on YouTube are best, perfect, awesome, beautiful, etc and the most used negative words on YouTube are worst, terrible, disgusting, boring, awful, etc.

<img width="608" alt="Screen Shot 2022-03-11 at 01 45 15" src="https://user-images.githubusercontent.com/91368463/157733415-5d548481-d108-47a3-9dd7-19ce9bd23cfd.png">



### **- Emoji Analysis**
- Install emoji package so python can read it. After that, visualize the emojis to see which emoji are used the most. Turns out that the most used emoji is 😂 with total used: 36.987K
<img width="994" alt="Screen Shot 2022-03-11 at 01 48 56" src="https://user-images.githubusercontent.com/91368463/157734264-34eda830-8f44-491a-a387-8e0a01b2e1ef.png">



### **- Collect Entire Data of YouTube**
- In this step we read 10 CSV files to see YouTube data from another country and merge it into one dataframe for further analysis.
<img width="1001" alt="Screen Shot 2022-03-11 at 01 53 59" src="https://user-images.githubusercontent.com/91368463/157734770-6a509864-f3e5-461d-82ec-cda2317a8463.png">

- The dataset has total data points: 375942 and total columns: 17.
<img width="458" alt="Screen Shot 2022-03-11 at 13 12 51" src="https://user-images.githubusercontent.com/91368463/157812802-aef490eb-9cd1-4d51-a921-77ca9e67b621.png">

- The dataset has 19478 missing values in description column, so we can handle that with dropna.
<img width="286" alt="Screen Shot 2022-03-11 at 13 14 44" src="https://user-images.githubusercontent.com/91368463/157812895-8068e25f-bb08-455c-baf3-dd58d308665c.png">



### **- Which Category Has the Maximum Likes?**
- In here we used new dataset and then merge it with datasets from the earlier step to see category in each video. Then, visualize using boxplot to see the categories with the most maximum likes.
<img width="739" alt="Screen Shot 2022-03-11 at 01 57 15" src="https://user-images.githubusercontent.com/91368463/157735287-73c46395-cd03-4c36-9df2-2c84494b17ec.png">



### **- Find Out Whether Audience is Engaged or Not**
- We need to add new features to find out whether the audience is engaged or not. 3 Features: like rates, dislike rates and comment count rate.
- Visualize with boxplot using like rate and category name features
<img width="720" alt="Screen Shot 2022-03-11 at 02 00 51" src="https://user-images.githubusercontent.com/91368463/157735916-7664beab-bac6-4884-8f46-9a76d86eba2b.png">

- Visualize with scatter plot to see data distributions.
<img width="447" alt="Screen Shot 2022-03-11 at 02 03 41" src="https://user-images.githubusercontent.com/91368463/157736227-0eff3211-fa67-41c2-9374-48ddad05a49d.png">

- We can use heatmap to see the correlation between views, likes and dislikes. If the correlation >0.7, it means features have high correlation. In this heatmap we can see that likes and views have high correlation (0.78). This means those features might affect each other.
<img width="358" alt="Screen Shot 2022-03-11 at 13 15 56" src="https://user-images.githubusercontent.com/91368463/157813050-d752cf45-98a0-4ecc-8bbd-a8227ffd7d70.png">




### **- Which Channels Have the Largest Number of Trending Videos?**
- We need to make new variable using groupby. The variable contains channel title and total videos
- Visualize the variable/data to see total videos in each channel.
- From the bar we know that The Late Show with Stephen Colbert Channel have the most videos, total: 984 videos.
<img width="991" alt="Screen Shot 2022-03-11 at 02 14 40" src="https://user-images.githubusercontent.com/91368463/157737978-3d17ac55-fb0e-4f5f-bfb3-988e74987a8a.png">




### **- Does Punctuations in Title and Tags Have Any Relation With Views, Likes, Dislikes Comments?**
- We need to define the punctuation so python can read it. Then, define punctuation count to see how many punctuation contains in each title. 
- Make new feature called 'count_punc'
- Make dataframe sample and visualize it. In this boxplot, we can see that title with 3 punctuation have the most views video.
<img width="731" alt="Screen Shot 2022-03-11 at 02 20 28" src="https://user-images.githubusercontent.com/91368463/157738692-91bf29b3-ee3a-4313-945c-c33e5ac6211c.png">

- Check again if total punctuation REALLY affecting views with correlation.
<img width="370" alt="Screen Shot 2022-03-11 at 13 08 11" src="https://user-images.githubusercontent.com/91368463/157812192-3e32d3d7-33da-4798-b707-0d3c9a5bd0e8.png">


- After checking with correlation, we can conclude that the number of punctuation doesn't really affecting views, because the correlation is weak, only 6.3%.

### **- Insights**
From this analysis, we can conclude some points:
- The most popular positive words on YouTube are best, perfect, awesome, beautiful, etc. and for negative words are worst, terrible, disgusting, boring, awful, etc.
- The most popular emoji that have been used in YouTube is 😂 with total: 36:987K, followed by 😍 with total: 33.453K, and 🖤 with total: 31.119K.
- Video category that has maximum like is Music.
- Based on data distribution in scatter plot, video views somehow affected by likes and those features also have a high correlation, at 0.78. But dislikes didn't really affected by how many views that videos have, because those features have weak correlation, at 0.47.
- The amount of punctuation doesn't give crucial affect views, because it has weak correlation: 0.063 (only 6.3%), but video that have total 3 punctuations in its title have the most views (followed by 2 punctuations) compare other amount of punctuations.






