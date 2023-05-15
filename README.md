# political-analysis
NLP Based Project for determining semantic using in political texts

This is a project which will analyze the semantics present in political writing, and how those semantics determine which political leaning the writing is recieved as.

It is designed to determine which parts of a political writing make it the political leaning it is.
For example, is the way an article talks about firearms and the second amendement deterministic to it's writers political leaning? How so? What other parts of the writing are similar to this?

## 0. Abstract

Analysis of news articles using various NLP techniques.

The expansion of natural language processing techniques has allowed for insight into text at a scale that until now was thought to be impossible. The main research question was, "what differentiates news publications?" That could be authorship bias, topic bias, or semantic use of language. Simple probabilistic techniques were used to gauge viability of the project, and a doc2vec model was used to classify the similarity of the news documents. A sample of 10 documents was taken from each publication, and the model found the top 10 most similar documents for each. From these, 5.73% of authors were the same and 24.23% of publications were the same. This lends itself to say that publication style is more important than authorship, but this needs more research.

## 1. Introduction

News is everywhere, whether it be social media, news, advertisements, or political campaigns. The proper understanding of how political language, and language in general, is used in our news is essentaal to: root out biases, identify fake news or misinformation, and to check the quality of our own work. We have seen this become more important as the news becomes increasingly partisan, and with the shift towards online reading, more profit oriented rather than focused on establishing truth. This project aims to identify the ways in which different political news sources use language compared to others. 

## 2. Literature Review

## 3. Dataset

The dataset we chose to use for this project is [All the News 2.0](https://components.one/datasets/all-the-news-2-news-articles-dataset/). It consists of 2,688,878 articles, spanning Jan 1, 2016 to April 2, 2020. More info about the dataset can be found [here](https://components.one/datasets/all-the-news-2-news-articles-dataset/). 

I had originally intended to scrape my own dataset, but given the width of sites I would have to scrape to collect an adequate amount of articles, it presented a very large challenge. So, I opted to just use this pre-created dataset, it is massive, so it has a large set of articles from sources that lie all over the political spectrum. Another step that I could take would be to scrape these same sites for new articles to properly capture the changes in language in the past 3 years, but given that this dataset goes up to 2020, we should see the division around the campaign trail for the 2020 election.

During my exploritory data analysis I generated a few graphs:
![Length Distribution Per Publication][graph_1]

## 4. Results



[graph_1]: https://github.com/cgra21/news-analysis/blob/main/EDA/article_len_dist.png?raw=true