# NLP-Notebooks-Newspaper-Collections
A collection of notebooks for Natural Language Processing

# Text classification for topic-specific newspaper collections
<a href="" target="_blank">Go to notebook</a> 

Text classification is the process of categorizing text into pre-defined groups. By using Natural Language Processing (NLP), text classifiers can automatically analyze text and then assign a set of given categories based on the research question. This automated classification of text into predefined categories is an important method for managing and processing a large number of newspaper clippings. This also applies to subcorpora for a specific research topic (e.g. migration). The aim of this notebook is to train a model using your previously manually created training/test corpus and to use this model to get an overview of the category distribution throughout your collection (see figure below). Another goal is to export your categorized data for further analysis. This makes it possible to examine, for example, the advertisement about a specific topic.
This notebook was used with a collection for the case study on emigration and shows how a model can be trained to classify topic-specific collections. For the training/testing corpus, a collection with the keywords "Auswander*", "Ausgewanderte", "Emigrant*", "Emigrierte", "Emigration", "Kolonist*", and "Ansiedler*" (all different German words for emigrants or emigration) have been created. In addition, information on the pre-defined gropus (news, ads, culture...) were added using numbers between one and ten. 
For classification, topic modelling (LDA) was chosen because it showed the best performance in classification (after experiments with word embeddings or LDA and word embeddings combined). LDA provides a way to group documents by topic and perform similarity searches and improve precision. Thanks to sklearn, it is relatively easy to test different classifiers for a given topic classification task. Logistic regression was chosen as binary classifier. 
*Output graph using an unseen collection on the topic of emigration  (790 newspaper clippings).* 

![Collection on the topic of Emigration](images/categories.PNG)

Read more about <a href="https://monkeylearn.com/blog/introduction-to-topic-modeling/" target="_blank">Topic Modeling</a> and <a href="https://towardsdatascience.com/logistic-regression-model-tuning-with-scikit-learn-part-1-425142e01af5" target="_blank">Logistic Regression Model Tuning</a>.

Acknowledgments:

This work has been inspired by a notebook on <a href="https://www.kaggle.com/vukglisovic/classification-combining-lda-and-word2vec" target="_blank">LDA and word embeddings</a> and several other soursces that provided help on how to build models. This work was supported by the European Union's Horizon 2020 research and innovation programme under grant 770299 (NewsEye).
