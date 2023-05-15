# News Analysis
NLP Based Project for determining semantic using in news

This project will explore the language used in news, and whether or not publication has a larger effect on that language than topic or authorship alone.
It will attempt to determine "what makes the news, the news"

## 0. Abstract

Analysis of news articles using various NLP techniques.

The expansion of natural language processing techniques has allowed for insight into text at a scale that until now was thought to be impossible. The main research question was, "what differentiates news publications?" That could be authorship bias, topic bias, or semantic use of language. Simple probabilistic techniques were used to gauge viability of the project, and a doc2vec model was used to classify the similarity of the news documents. A sample of 10 documents was taken from each publication, and the model found the top 10 most similar documents for each. From these, 5.73% of authors were the same and 24.23% of publications were the same. This lends itself to say that publication style is more important than authorship, but this needs more research.

## 1. Introduction

News is everywhere, whether it be social media, news, advertisements, or political campaigns. The proper understanding of how political language, and language in general, is used in our news is essentaal to: root out biases, identify fake news or misinformation, and to check the quality of our own work. We have seen this become more important as the news becomes increasingly partisan, and with the shift towards online reading, more profit oriented rather than focused on establishing truth. This project aims to identify the ways in which different political news sources use language compared to others. 

## 2. Literature Review
- [Latent Dirichlet Allocation](https://www.jmlr.org/papers/volume3/blei03a/blei03a.pdf)
    This paper focuses on a technique called LDA or Latent Dirichlet Allocation. The goal of this technique is to find short descriptions of documents in a text coprus, while maintaining the essential relationships between documents for simple NLP tasks.

- [News Article Classification](https://www.cs.drexel.edu/~spiros/papers/NLP20.pdf)
    This paper compares two NLP methods for topic modeling and authorship attribution. They found that with a small database of 10 authors, they could achieve around 95% success for attribution. They also found an accuracy of around 74% with neural networks for topic classification

- [Trading on News Sentiment](https://link.springer.com/article/10.1007/s00146-020-01111-x)
    This paper analyizes whether it is possible to trade stocks based on current news sentiment. They chose to analyze news that was mainly focused on recent political events, and found very little success.

## 3. Dataset

The dataset we chose to use for this project is [All the News 2.0](https://components.one/datasets/all-the-news-2-news-articles-dataset/). It consists of 2,688,878 articles, from 27 different sources, spanning Jan 1, 2016 to April 2, 2020. More info about the dataset can be found [here](https://components.one/datasets/all-the-news-2-news-articles-dataset/). 

I had originally intended to scrape my own dataset, but given the width of sites I would have to scrape to collect an adequate amount of articles, it presented a very large challenge. So, I opted to just use this pre-created dataset, it is massive, so it has a large set of articles from sources that lie all over the political spectrum. Another step that I could take would be to scrape these same sites for new articles to properly capture the changes in language in the past 3 years, but given that this dataset goes up to 2020, we should see the division around the campaign trail for the 2020 election.

During my exploritory data analysis I generated a few graphs to better understand the data:
![Length Distribution Per Publication][len_dist]
Note that this graph does not show outliers

![Authorship Per Publication][authorship]

![Length Distribution Overall][len_dist2]

This dataset proved to be slightly problamatic due to it's large size and being slightly out of data, so in the future, I would like to either add on to it, or to create my own dataset.

## 4. Results

### Naive Bayes Model
From my intial simple testing, I created a naive bayes model using a count vectorizer on the articles to see if a model could correctly classify article publications based on the article. This worked suprisingly well and yielded an overall success rate of **49%**. This high of an accuracy was very suprising, and opened the door for futher analysis.

![Naive Bayes Results][naive_bayes]

### Doc2Vec

After intial testing, a doc2vec model was trained on a subset of the original data due to it's extremely unwieldy size. This subset has 3332 samples from each of the sources, however I only used 26 sources in this case, which equates to a total of 86,632 documents. This is not ideal for a perfectly accurate doc2vec model, so I hope to train a larger one in the future. 

Afterwards, I took a sample of 10 documents from each publicatoin, and found the top 10 most similar documents from the subset to these 10. In these 2,600 articles, 5.73% of the authors were the same, and 24.73% of the publications were the same. This lends itself to say that publication is more important than authorship, but this requires futher research.

## 5. Discussion and Future Work

We can see that publication has some effect on how articles are written. According to these results, publication has more of an effect on article similarity than Authorship does. However, given that there were only 26 possible publications in this dataset, and hundreds of thousands of authors, this should be taken lightly and requires much more research. There were 12,880 unique authors in the subset used for the doc2vec model, so given that 5.73% of similar articles share the same author, that is a remarkable effect. On the contrary, given that there are only 26 sources, and 24.73% of similar articles were from the same source, this shows a smaller effect. However, my results were not normalized to account for authors working at the same publication, so there is undoubtably overlap between those two numbers. 

However, I do not believe that my research accurately answers the question "what differentiates news publications?" yet. I haven't found a way to seperate topic, authorship and publication from impacting the data, and I won't be able to properly answer that question until I do. It does have some interesting insight, and brings up future questions such as "Is topic more important than authorship for classification?" or "Do publications in general write differently?" I don't believe the current state of this project adds much to the current research space, at least until I can further the work done on it. However, I believe this opens up an important avenue to potentially explore: can we seperate key features of text, like topic, language semantics, and authorship bias, without losing the meaning of that text?

There hasn't been much literature that I could find exploring this topic, many of them explore either semantic classification or topic modeling. These are both techniques that I will need to leverage in the future if I am going to accomplish this task, but for the immediate future I would like to focuse on:

- Finding a way to seperate authorship and publication. This could be generating a subset that has many articles from each publication each with different authors, and another that has many articles from the same author. 
- Create a final large doc2vec model using the whole corpus
- Scrape more news articles from more recent years
- Remove news sources that aren't general news, such as TMZ and The Hill

As for more work to be done in the future, once I can find out a way to differentiate the effect that authorship has from publication, I can then approach what effect topic has on decument relationships. This could be done through named entity recognition, then comparing articles that speak about the same entities, their semantics, and whether they are from the same author or publication. Another approach I could take is to perhaps pass the articles through a pre-trained transformer model, and have it pull out key terms. Another option is to compute summarizations of the articles, and compare those as well. This project was a lot deeper than I thought it would be when I intially crafted my research question, but I think working more on it in the future will allow me to potentially touch on almost all modern NLP techniques.

I did create a simple visualization that you can find [here](http://projector.tensorflow.org/?config=https://gist.githubusercontent.com/cgra21/8724531086105e3ff2911466b579ffad/raw/63bfee9a830058b48335e6f6187695355a5d9a51/projector_config.json). Upon exploring that I noticed some interesting features, such as that BuzzFeed articles were typically grouped very very close together. Upon further exploration I believe this is an artifact of the scraping techniques used to create this dataset. These articles were almost always a list of tweets, with very little if any text in between them. The web scraper used for this didn't pick up the text from the embedded tweets, so typically the article text was just a short list of numbers. 

## 6. Conclusion

The research question for this project was: "what differentiates news publications?" This study found that there is at least some merit to classfying what publication an article is from based on the article alone. It explored whether or not authorship was more important than publication for text similarity purposes. The results were that around 5.73% of sample similar texts had the same author while 24.73% of similar text has the same publication. This number is in relation to 12,880 unique authors and only 26 unique publications.

Further implications of this research are the exploration of whether or not it is possible to seperate authorship bias and publication bias. Whether topic has more importance on document similarity than authorship. Or if the way publications use language differs significantly from each other.

[len_dist]: https://github.com/cgra21/news-analysis/blob/main/EDA/article_len_dist.png?raw=true
[authorship]: https://github.com/cgra21/news-analysis/blob/main/EDA/authorship.png?raw=true
[len_dist2]: https://github.com/cgra21/news-analysis/blob/main/EDA/len_dist.png?raw=true
[naive_bayes]: https://github.com/cgra21/news-analysis/blob/main/Classifier/Naive%20Bayes%20Heatmap.png?raw=true