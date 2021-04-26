
Executive Summary:
What would happen if you get Harry Potter as a result when looking for a book on investment/finance on Amazon? Terrible match, right?
Using Natural Language Processing & Neural Networks, let's build a recommender system for books.

Part 1: 01_Scraping_and_Cleaning_the_Data
I first collect and clean the subreddit posts through api.pushshift.io; secondly, I explore and model the data. The data collected is from July 25th, 2010, to March 30, 2021. This amounts to 109,122 posts, which translates to about 37 million characters. I use Pandas, Os, Requests, And Re libraries.

Part 2: 02_EDA_and_Modeling
The second part involves using NLTK, Word2Vec from Gensim, and spaCy libraries to process and understand the large volumes of text that we have. For instance, not removing special characters reduced the number of books identified by close to 1,000. I finally use the cosine similarities in my recommender system.

Check out the related publication on medium:
https://medium.com/mlearning-ai/building-a-recommender-system-cb7fe0770

Note: Due to storage limitations on Github, data files are stored on my personal google drive:
https://drive.google.com/drive/folders/1KwJ_t5hUbNqD_rsCPEyAw9K0DM33UyAj?usp=sharing
