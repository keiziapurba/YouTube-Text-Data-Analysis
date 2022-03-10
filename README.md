# Youtube-Analysis
## YouTube analysis case study that contains sentiment analysis, emoji analysis, likes vs views analysis, and trending videos text on YouTube
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
    - [Business Insight & Recommendation](#business-insight-&-recommendation)

---

## **Background**
- 1 billion hours of YouTube content is watched per day
- YouTube is the 2nd most visited site in the world
- Youtube attracts about 44% of all internet users
- About 33% of all mobile internet traffic belongs to Youtube

### **Data Description**
- UScomments dataset contains information about video id, comment text, likes and replies. Total data points: 691400 and total columns: 4
<img width="386" alt="Screen Shot 2022-03-11 at 01 16 00" src="https://user-images.githubusercontent.com/91368463/157728674-c446797e-5922-427b-a3df-d6cd9ee76488.png">

- After checking the dataset, we can see that it have missing values. That's why we have to filter the dataset so it don't have any missing values.

## Project Outline

### **- Sentiment Analysis**
- First, install necessary package in this case use TextBlob to see the sentiment. To perform Sentiment Analysis, there are 2 key points: Polarity and Subjectivity. Here we focus on polarity. If polarity: +1 that means we have high polarity and if we don't have any sentiment it carries subject, that's what subjectivity is.
- In this step, we want to see each comment text polarity and then make polarity columns in dataset.
<img width="606" alt="Screen Shot 2022-03-11 at 01 36 41" src="https://user-images.githubusercontent.com/91368463/157731958-daaa820a-093f-4c21-a2a0-e7c59baa4c85.png">


### **- Wordcloud Analysis**
- Install wordcloud package, then import WordCloud and STOPWORDS. We want to see any positive and negative words that contains in comments text.
- Make 2 variables, one with polarity = 1, which means positive and other with polarity = -1, which means negative.
<img width="615" alt="Screen Shot 2022-03-11 at 01 45 34" src="https://user-images.githubusercontent.com/91368463/157733349-813e5dca-8c3e-452c-a2c7-bbb61f504999.png">


<img width="608" alt="Screen Shot 2022-03-11 at 01 45 15" src="https://user-images.githubusercontent.com/91368463/157733415-5d548481-d108-47a3-9dd7-19ce9bd23cfd.png">



### **- Emoji Analysis**
- Install emoji package so python can read it. After that, visualize the emojis to see which emoji are used the most. Turns out that the most used emoji is 😂 with total used: 36.987K
<img width="994" alt="Screen Shot 2022-03-11 at 01 48 56" src="https://user-images.githubusercontent.com/91368463/157734264-34eda830-8f44-491a-a387-8e0a01b2e1ef.png">



### **- Collect Entire Data of YouTube**
- In this step we read 10 csv files to see YouTube data from other country and merge it into one dataframe for further analysis.
<img width="1001" alt="Screen Shot 2022-03-11 at 01 53 59" src="https://user-images.githubusercontent.com/91368463/157734770-6a509864-f3e5-461d-82ec-cda2317a8463.png">


### **- Which Category Has the Maximum Likes?**
- In here we used new dataset and then merge it with dataset from earlier step to see category in each videos. Then, visualize using boxplot to see categories with the most maximum likes.
<img width="739" alt="Screen Shot 2022-03-11 at 01 57 15" src="https://user-images.githubusercontent.com/91368463/157735287-73c46395-cd03-4c36-9df2-2c84494b17ec.png">



### **- Find Out Whether Audience is Engaged or Not**
- We need to add new features to find out whether audience is engaged or not. 3 Features: like rates, dislike rates and comment count rate.
- Visualize with boxplot using like rate and category name features
<img width="720" alt="Screen Shot 2022-03-11 at 02 00 51" src="https://user-images.githubusercontent.com/91368463/157735916-7664beab-bac6-4884-8f46-9a76d86eba2b.png">

- Visualize with scatterplot to see if views is affecting likes or not
<img width="447" alt="Screen Shot 2022-03-11 at 02 03 41" src="https://user-images.githubusercontent.com/91368463/157736227-0eff3211-fa67-41c2-9374-48ddad05a49d.png">

- We can use heatmap to see correlation between views, likes and dislikes. If the correlation >0.7, it means features have high correlation. In this heatmap we can see that likes and views have high correlation. This means those features might affecting each other.
<img width="968" alt="Screen Shot 2022-03-11 at 02 06 26" src="https://user-images.githubusercontent.com/91368463/157736867-708aac3a-e88b-482a-9b01-75f2ed9646d7.png">



### **- Which Channels Have the Largest Number of Trending Videos?**
- We need to make new variable using groupby. Variable contains channel title and total videos
- Visualize the variable(data) to see total videos of each channel.
- From the bar we know that The Late Show with Stephen Colbert Channel have the most videos, total: 984 videos.
<img width="991" alt="Screen Shot 2022-03-11 at 02 14 40" src="https://user-images.githubusercontent.com/91368463/157737978-3d17ac55-fb0e-4f5f-bfb3-988e74987a8a.png">




### **- Does Punctuations in Title and Tags Have Any Relation With Views, Likes, Dislikes Comments?**
- We need to define the punctuation so python can read it. Then, define punctuation count to see how many punctuation contains in each title. 
- Make new feature called 'count_punc'
- Make dataframe sample and vizualize it. In this boxplot, we can see that title with 3 punctuation have the most views video.
<img width="731" alt="Screen Shot 2022-03-11 at 02 20 28" src="https://user-images.githubusercontent.com/91368463/157738692-91bf29b3-ee3a-4313-945c-c33e5ac6211c.png">

- Check again if total punctuation REALLY affecting views with correlation.
<img width="358" alt="Screen Shot 2022-03-11 at 02 22 38" src="https://user-images.githubusercontent.com/91368463/157739022-e77e58b9-c681-4b81-ab18-6b87486b12aa.png">

- After checking with correlation, we can conclude that the number of punctuation doesn't really affectting views, because the correlation is weak, only 6.5%.

