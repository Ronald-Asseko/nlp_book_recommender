![](RackMultipart20210415-4-qsq4q4_html_34aabb51c0f0f5a7.png)

Example of entities detected in one subreddit post: refer to graphs/post_entities_detected

**Executive Summary:**

When users want relevant information about a product, they can go to places they know they&#39;re likely going to find answers. But not just any answers, relevant ones. We do it all the time, and because some places (websites) are so good – GOOGLE, and we do it so often that we&#39;ve taken that process for granted.

What would happen if when looking for a book on investment/finances on Amazon, you get Harry Potter? Very bad match right?

Here I&#39;m looking at the process of querying a such system that will give me relevant answers. More specifically, based on people&#39;s posts on the subreddit r/booksuggestions, what are books, or similar books that other people have read/suggested?

Using NLP and Deep Learning methods, let&#39;s analyze those posts and come up with a way to find out what those books are.

**Part 1: 01\_Scraping\_and\_Cleaning\_the\_Data**

In this repo, divided into two parts, I first collect and clean subreddit posts through api.pushshift.io going from July 25th, 2010 to March 30, 2021. This amounts to 109,122 posts, which translates to about 37 million characters. Depending on the analysis, this can take up all your memory very quickly. In fact, when using more advanced hardware accelerators (GPU then TPU) with High RAM (27GB to 32GB) on Google Collab-Pro, it crashed multiple times so I ended up using my laptop which took some times to run functions. The image above is an example of our final text with entity detections. In this part I use Pandas, Os, Requests, And Re libraries.

**Part 2: 02\_EDA\_and\_Modeling**

The second part involves using NLTK, Gensim, and spaCy to process and understand the large volumes of text that I have. In this part, I found that how well you clean your text determine the results. For instance, not removing special characters reduced the number of books identified by close to 1,000.

In my model, I use:

- spaCy to identify entities (books) in documents

Here is an example of the most popular books identified in our posts. refer to: graphs/top_10_books

![](RackMultipart20210415-4-qsq4q4_html_4e43f9741ec80c82.png)

- Continuous Skip-gram (a two-layer Neural Network) model from Word2Vec, which inputs words and outputs context words. This is where our vocabulary is created.

Result: The word &quot;Bible&quot; returns &quot;Quran&quot; refer to graphs/most_similar_bible_quran

![](RackMultipart20210415-4-qsq4q4_html_9bd9779c81e3e03a.png)

- Cosine similarity, which computes the angle between words/documents and return a score. The smaller the angle, the more similar the words/ documents, the higher the cosine similarity score.

The post below returns the books &quot;The Twilight Zone&quot;, &quot;The Ritual&quot;, and &quot;Teeth&quot; with the scores of 0.989369, 0.988831, 0.988466 respectively
refer to graphs/post_to_books

![](RackMultipart20210415-4-qsq4q4_html_2cde120670f7a1dc.png)

**Conclusion / Recommendations**

Good news! We&#39;ve successfully ran our first recommender system. The main take ways are:

- Clean the text data appropriately to have good results
- Model can be used to prompt conversations
- Test more advanced entity detections like Doc2Vec

Note: 
Due to storage limitation on github, data files are stored on my personal google drive. Follow the link bellow to take a look.
https://drive.google.com/drive/folders/1KwJ_t5hUbNqD_rsCPEyAw9K0DM33UyAj?usp=sharing