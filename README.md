# Exploring Diversity Within Recommendation Systems

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

## Baseline Model - Biased Baseline


## Personal Video Ranker


## Video To Video Ranker

We used support vector machine classifier to help with the imbalance of the data. Some scores here did the best yet, however we wont use this model as its most prone to overfitting. The train score was 77% which was great to see but the test score was 56%. Precision score did about as well as our baseline at 57%.

## Final Recommender

I'm really excited about this since it's the most code I've ever written and the rest of this repo is forthcoming.

## Conclusion and Looking Ahead
