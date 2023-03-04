# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP




### Overview
As the new town squares, social media companies hold both the responsibility of allowing differing opinions to be heard, and the responsibility of providing rules that keep users and communities safe. Online communities continue to grow and multiply everyday making the task of monitoring communities nearly impossible without the help of computers.

Reddit has contacted me in order to find new ways to monitor subreddits to explore metrics that may be able to alert human moderators of potentially harmful shifts within reddit communities. 

## Problem Statement
For this project I have identified two subreddits r/Destiny and r/VaushV that are controversial in nature as the topics of both are the rhetoric of two political debate streamers. Both Destiny and Vaush have been banned from multiple platforms for inflammatory rhetoric. Destiny is a center left commentator. Vaush originated from Destiny's community but is a far left commentator. Neither community has been flagged as controversial on reddit but both have controversial elements and users. 

The reason I would like to investigate these two communities is that they are closely related in both rhetoric and political affiliation but Vaushes community explicitly claims to be further left. I would like to see if any shift in rhetoric of the community can be detected by looking at word usage and sentiment analysis. And further I would like to see If I can make a model that can differentiate the two communities based on post text alone as this type of model could be useful in detecting changes in other clusters of reddit communities.





### Outside Research and Sources
https://www.wired.com/story/twitch-politics-online-debate/

https://gamerant.com/twitch-destiny-streamer-bans-why/
https://www.youtube.com/watch?v=sIOz9a9
https://en.wikipedia.org/wiki/Destiny_(streamer)P0dU
https://en.wikipedia.org/wiki/Vaush


## Brief analysis summary
In order to detect differences in rhetoric between the two communities I used countvectorizer to show all instances of particular words and phrases. It seemed that Destinys community was more focused on memes while Vaushs was focused against the right wing and in discussing trans issues. Word count was nearly identical though Destiny had more outliers 

During Sentiment Analysis the only differences was that r/VaushV tended to be more negative overall compared to r/Destiny.

To model the data I combined self text and the title from reddit to make a longer text. If the self-text was removed but the title remained I would clean the [removed] tag and keep the title for analysis. I tested models with lemmatized and non lemmatized data. After countvectorizer() I tested the estimators naive bayes, random forest, ada boost, XG boost and logistic regression. I also took the best performing models and out them in a stacked model with the same parameters. 

Overall my best two model were a naive bayes on the lemmatized data and a non lemmatized stacked model with lvl 1 estimators,  naive bayes, ada Boost, XGboost and random forest. The 2nd lvl estimator was a logistic regression.

Both models scored close to .75 accuracy on the testing data. Boht models also performed slightly worse on predicting if a post came from r/Vaush. When I investigated why this might be via random forest feature importances it looked like most of the splits were occurring on either Destiny’s name or words that are used more or exclusively in r/Destiny.

## Conclusions and Recommendations



There were some major differences in rhetoric but they mostly revolved around memes and community members rather than politics.

In another attempt I would pick a timeframe via the reddit api when both communities were debating  politics with each other.

While the model was decent at differentiating communities it had a lot of help from using Destiny's name. 
I’d want to see how the models perform with the creators' names. Destiny is a banned word on r/Vaush

Shifting political opinions may be easier to detect vai sentiment analysis on words/phrases like trans or right wing. And the total overall usage of the certain words and phrases.

