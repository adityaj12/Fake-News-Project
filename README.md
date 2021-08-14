##  Inspirit AI Project: Detecting Fake News Using Artificial Intelligence

With the world becoming more and more reliant on technology, fake news has become a prominent and recurring issue in our society.

But what exactly is Fake News? Fake news is any form of media that presents false information whether it was intended or not.

Examples include:
- Propoganda
- Clickbait
- Misinformation (not intentional)
- Disinformation (intentional)
- Hoaxes

### Approaches using AI

Our first approach was using a **Domain Featurizer**.
A domain featurizer maps feature descriptions to numerical features using a website's url.

![Image](images/filename%20DomainFeaturizer.png)

The issue with a Domain Featurizer is that featurizing values may become too large or small. 

Therefore, our next approach was using a **Keyword Featurizer**.
This method scales the values so that they don't become extreme. This process is called _normalizing_. The keyword featurizer is very similar to the domain featurizer, except it also keeps count of the number of keywords detected from each website's html code.

![Image](https://github.com/adityaj12/Fake-News-Project/blob/main/GetNormalizedCount.png)
![Image](https://github.com/adityaj12/Fake-News-Project/blob/main/KeywordFeaturizer.png)

We also tried to use Python's BeautifulSoup library to scrape websites for their meta descriptions. These meta descriptions provide keywords that help us determine whether or not these sources are fake.

![Image](https://github.com/adityaj12/Fake-News-Project/blob/main/WebScraping.png)

Our main issue with this method was that every website doesn't necessarily have a meta description embedded in their html.

So, we moved onto our next approach, utilizing **Word Vectors**.
Word vectors are used to determine the similarity between different words. This is especially useful since some keywords in fake news sources may have several synonyms. Using some linear algebra, we can produce a value for the cosine similarity of two word vectors. This value is between -1 and 1, and the more similar the words are, the closer the value will to be to 1, and vice versa.

![Image](https://github.com/adityaj12/Fake-News-Project/blob/main/WordVectors.png)

### Results of Our Approaches

Using metrics such as precision and recall, we were able to determine that our model was fairly efficient.

Successes:
- Our model was able to detect suspicious domains that typically aren't considered to be reliable.
- It detected keywords and similar words to detect fake news sites.

Failures:
- Older websites with unique domains were classified as fake even though were real.
- Certain websites that warned about the keywords listed were classified as fake just because they also contained the keywords technically.
