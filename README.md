# Biodiversity Conservation Literature
### *Sentiment Analysis of Scientific Literature on Biodiversity Conservation*
### Bianka Fábryová (June 2022)

One of the fundamental characteristics of 21st century is the immense quantity of accessible information. There are countless sources offering us news and facts at any point of a day or even at any location. However, with an increase in quantity of information available, there is a decrease in human ability to comprehend an overall perspective on an issue of interest. This very same trend can be observed as well in academic literature. It is becoming ever more challenging to draw and see an overall attitude towards a given topic. 

Nevertheless, with growing information there is a growth in the way of processing it, as well. Data Science offers vast numbers of information processing among which there is sentiment analysis. Sentiment analysis is a tool used in text mining which examines words of a text and assigns them a sentimental value, easily understandable for a human (Bravo-Marquez et al., 2014).

In this paper I would like to focus on the topic of biodiversity conservation and using sentiment analysis together with other text mining tools, review the overall scientific attitude. Biodiversity conservation and its ecosystem processes, offering us wide range of services, are vital for human survival. However, with the current human development the quantity and quality of Earth’s biodiversity is shrinking (Pimm, 2021). Therefore, I hypothesize that with the current growth of extinction rates (Hanisch, et al., 2019), there is an overall increasing trend in the positive connotation of words due to the alarming necessity for biodiversity protection. 

## METHODS
This review was based on scholarly articles imported from publicly available Plos journal and performed completely in R language. Due to lack of internal memory, there was in total only 5000 articles imported instead of 12981 that were available. These articles were furthermore parsed with pub_chunks() function from fulltext package to extract information, such as title, history and abstract, necessary for further analysis. Lastly they were mapped with map() function for import into global environment as a data frame. Furthermore, tidying of data was made with tidytext package. 
The import and tidying of the data, was followed by three sets of analysis performed on the data.

Firstly, it was the focus of the review, the sentiment analysis using afinn and bing lexicons with standard tidytext package. Sentiment analysis offers an overall sentimental value of a given text. Built on sentiment analysis, word cloud of most frequent words and word cloud of most frequent positive vs negative words were performed. 

In addition to the sentiment analysis, a magnitude of false positive vs false negative words throughout the texts was examined.

Secondly, the biodiversity conservation articles were studied through the tf_idf approach, a measure of word importance per a cluster of interest. Tf_idf was applied to inspect abstract texts per last six years in order to identify the topics of interest within conservation biology.

Lastly, it was a research of academic papers through topic modeling. Here, I hypothesized an existence of two topics due to a following reason. Conservation biology has two important aspects the environmental one and the economic one, therefore, I investigated whether this assumption can be met with unsupervised learning of topic modeling. 

## RESULTS

As mentioned earlier, sentiment analysis is a text mining tool which enables sentimental overview of a text document. With that being said, figure one depicts an average sentiment analysis per article which is followingly mapped on a yearly timescale. We can observe that there is overall more data on positively corelated articles rather than negatively. This can be largely seen in the overlapping (darker shades) sections of the graph. However, frankly, it is hard to conclude any definite attitude. Therefore, I applied a sentiment analysis per article per year and graphed a year overall sentimental attitude on the topic (see fig. 2). In figure 2, there is clear increasing trend in positive sentiment with a peek around year 2015 followed by a decrease. 
Additionally, since sentiment analysis is inspected on a level of single words, there is a chance that these words can be misclassified due to exclusion of a negative connotation preceding a word. Thus, I performed a magnitude of a false positive and false negative words based on bigrams. Indisputably, the most misclassified word is ‘significant’, assumingly, mistaken for not significant. Overall, it is mostly positive words that are misclassified which however, is understandable since as we could have seen on figure 1 and 2, positive sentiment is a majority of the overall sentiment. In addition to sentiment analysis, there is a word cloud analysis of frequency of words and sentiment word frequency attached at the end of the document (fig.4 & fig.5).

Tf_idf
Tf_idf depicts the uniqueness of a text section. In our case, the aim was to depict the unique topics within biodiversity conservation during last 6 years. In other words, yearly research interest within biodiversity conservation. Tf_idf was performed on text extracted from abstracts of the plos articles (see fig.6). However, there is an insignificant correlation among the words per year to categorize years into topic clusters. As a comparison a second version of tf_idf was investigated with text analysis generated from title words rather than abstracts. However, there was again low correlation (see fig.7). 
	
Topic Modeling
	Lastly it is topic modeling. Introduced earlier, I hypothesize two topics, based on economic and environmental perspective on biodiversity conservation. Implementing cast_dtm() and LDA function from topicmodels package I fit the model to the texts of the articles. Figure 8 depicts the top words categorized into each topic.
Topic one, the environmental and ecological perspective includes words such as habitat, climate, forest, plant and diversity, and secondly topic two of the economical perspective including words such as management, data, study, use or can. Furthermore, I performed an analysis from the opposite viewpoint, depicting the most different words that there are in these two topics (fig. 9). Here, however, it is much more challenging to see the topic difference in this scenario.


## CONCLUSION

In conclusion, text mining, with a focus on sentiment analysis is a great tool for investigation of extensive number of texts incomprehensible, due to its quantity, for a human. Regarding biodiversity conservation, it is essential to have an overview of scientific literature to progress toward any sustainable future development. This is due to the high risk for governments and institutions since it is financially demanding as well as due to knowledge needed regarding the ecosystem. Furthermore, sentiment analysis shows us clear increasing trends towards year 2016 in positive attitude within biodiversity conservation which in my interpretation may reflect the rise of IUCN redlist of threatened species (The IUCN Red List of Threatened Species) and therefore alarming call for conservation. Future studies within this topic could include taxonomy classification which is available in taxize package and therefore perform a sentiment analysis per specific phylum or genus.

All in all, sentiment analysis and other text mining tools not only offer an approach of processing massive amounts of text data, otherwise unreachable for an individual, it as well depicts a clear visual instrument, easily comprehensible and therefore, ideal for future implementation in policy making and area development regarding a crucial topic such as biodiversity conservation.

### References
Bravo-Marquez, F., Mendoza, M., & Poblete, B. (2014). Meta-level sentiment models for big social data analysis. Knowledge-based systems, 69, 86-99.

Hanisch, E., Johnston, R., & Longnecker, N. (2019). Cameras for conservation: wildlife photography and emotional engagement with biodiversity and nature. Human Dimensions of Wildlife, 24(3), 267-284.

Pimm, S. L. (2021). What is biodiversity conservation?. Ambio, 50(5), 976-980.

The IUCN Red List of Threatened Species. IUCN Red List of Threatened Species. (n.d.). https://www.iucnredlist.org/. 


 


