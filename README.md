# Infusing Intentional Diversity within Recommendation Systems

Author: Leo Schell Villanueva

This project is an academic exercise for my Capstone project as a part of Flatiron School's Data Science Certification Program.

I have elected to examine content diversity within simple recommendation systems using SciKit's Surprise package for Python.

## Overview and Background
### Bottom Line: Audiences don't care about accurate predictions.

Early recommendation algorithms were evaluated based on accuracy.

However more often than not, showing a user recommendations we're sure they're going to rate 5 stars makes for a boring platform.

If a user rates Captain America 5 stars, an accurate recommendation would be every single avengers movie from there. 

As business analysts, we love to see that dedication to a franchise, however users are more complex than this. 

In building our models, we need to acknowledge that our users rely on us to know what content is on our platform

Furthermore, we owe visibility to the content creators who make our platforms possible.


## Data Understanding
In 2006, Netflix hosted a [competition](https://en.wikipedia.org/wiki/Netflix_Prize) to see who could beat their best model. I used this data for my project. 

The original dataset contains over 100M rows, but with my limited resources I had to sample 1 Million Rows of this data.

My sample contains 1 Million radomly selected ratings of 17,770 movies, shorts, and shows from 290,022 users.

### Data Limitations

The data was collected from end of 1999 to end of 2005 so it is out of date and I was only provided with a rating from 1-5, the date of rating, and the video release date which ranged anywhere from 1898 to 2005.

### Initial Diversity Analysis

The data itself does not contain very diverse observations. 
- The vast majority of content was released from 2000-2005.
- User engagement is low as most users only rated once.
- The content itself only contains 12.4% of Top (2) Billed Cast, Director, or Writer(s) are a minority. White women count as minorities in this instance as they are also underrepresented in the above categories.

## Preprocessing

In order to better understand how user preferences evolve with time, I employed an 'Out of Time' data split that is typically used with content recommendation systems. 

You can learn more about this split in an article by [Tomas Dvorak on Medium](https://towardsdatascience.com/why-isnt-out-of-time-validation-more-ubiquitous-7397098c4ab6).

# Models

I took a lot of inspiration from Netflix throughout this project. The platform uses many different algorithms because there is a time and place for each type of recommendation. 

With the resources and time that I had available, I was able to create a personalized video ranker and a video-to-video recommendation list. 

## Baseline Model - Biased Baseline

In this project, I initially drew a lot of inspiration from the [Balkor](http://snap.stanford.edu/class/cs246-2015/slides/08-recsys2.pdf) solution for the Netflix Prize as this is an academic exercise and I am seeking to understand recommendation systems on a granular level.

This was the baseline model they used. Predictions are calculated using the following formula:

    rᵤᵢ=μ + bᵤ + bᵢ

Essentially, this model operates on the assumption that you can predict a user's rating based on their natural bias. In layman's terms:

User's Rating = (mean ratings for the entire sample) + (the difference in how a user tends to rate videos) + (the difference in the content's own average rating)


## Personal Video Ranker

Historically, collaborative filtering models have been a large part of recommender algorithms. Personal video rankers, collaborative filtering models that seek to predict the content a user will rate highly, usually take prominent places in different capacities on all content delivery platforms.

Following is my best Singular Value Decomposition algorithm, using SVD++ from the same package.

## Video To Video Ranker

In order to promote content diversity, content delivery platforms usually employ models that connect users with content that is similar to what they have been exposed to already.

These models are trained only to examine the similarities between the content available.

I used the kNNBaseline model from the Python Surprise package to start and have left my best performing iteration from there.

## Final Recommender

This begins with the Personalized Video Ranker. If a user's personalized recommendations don't contain a video that meets the minority requirement, the algorithm identify nearest neighbors for the top 10 videos output in the the user's personalized video recommendations.

The algorithm then checks for movies in this pre-curated list of Will Smith, Lucy Liu, and Jennifer Lopez movies:

Will Smith:

Hitch (2005): 17324
Shark Tale (2004): 5345
Bad Boys (1995): 2186
Lucy Liu:

Mulan 2 (2004): 13836
Charlie's Angels (2000): 6552
Jennifer Lopez:

Maid in Manhattan (2002): 11149
Out of Sight (1998): 13486
I have chosen these celebrities as they were very popular in 2005 and tested well in markets throughout middle America and internationally.

If any of the above movies are present among the nearest neighbors, it will boost that movie to the 3rd recommendation in the personal video recommendations.

If none are present, the algorithm will insert Men In Black (2002) as the 3rd recommendation in the personal video recommendations.

Holdout Will Smith Movie:

Men In Black (2002): 12918

## Conclusion and Looking Ahead

This was an academic exercise and I only used algorithms that are used by small businesses and entry level data scientists.

Going forward, I want to get better acquainted with deep learning techniques and the way that major content platforms implement different regularization techniques that impact diversity.

I also look forward to working with bigger more contemporary datasets.
