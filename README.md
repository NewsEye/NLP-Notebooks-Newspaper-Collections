# NLP Notebooks for Newspaper Collections
*A collection of notebooks for Natural Language Processing*

The following notebooks are aimed particularly at digital humanities scholars who use newspapers as a source. The focus lies on (topic-specific) collection building, a field that is becoming increasingly interesting with better article separation. Very specific research problems are addressed, such as building up collections with ambiguous keywords or working with certain genres. In order to best meet the needs of digital humanities scholars, NLP methods are adapted in new ways, the output is human-readable and the processed newspaper articles can be exported in the form of the original file. In addition, the notebooks allow the users to control the single steps and to choose what is best for their collection. While the NewsEye demonstrator offers the possibility to create datasets quickly and effectively, these notebooks offer possibilities to work on these collections according to specific questions. 

1. [Text classification for topic-specific newspaper collections](#Text-classification-for-topic-specific-newspaper-collections)
2. [Group similar newspaper articles](#Group-similar-newspaper-articles)
3. [Discover a newspaper collection with diachronic Ngram clouds](#Discover-a-newspaper-collection-with-diachronic-Ngram-clouds)
4. [Discourse in Spanish flu coverage](#Discourse-in-Spanish-flu-coverage)
5. [Uses of the Term Telegraph in the Context of Journalism: Introduction to Topic Modeling on a Data Set created by the Newseye Project](#Uses-of-the-Term-Telegraph-in-the-Context-of-Journalism:-Introduction-to-Topic-Modeling-on-a-Data-Set-created-by-the-Newseye-Project)
   
## Text classification for topic-specific newspaper collections

<a href="https://github.com/NewsEye/NLP-Notebooks-Newspaper-Collections/blob/master/Text_classification_of_newspaper_clippings_notebook.ipynb" target="_blank">Go to notebook</a> 

Text classification is the process of categorizing text into pre-defined groups. By using Natural Language Processing (NLP), text classifiers can automatically analyze text and then assign a set of given categories based on the research question. This automated classification of text into predefined categories is an important method for managing and processing a large number of newspaper clippings. This also applies to subcorpora for a specific research topic (e.g. migration). The aim of this notebook is to train a model using your previously manually created training/test corpus and to use this model to get an overview of the category distribution throughout your collection (see figure below). Another goal is to export your categorized data for further analysis. This makes it possible to examine, for example, the advertisement about a specific topic.

This notebook was used with a collection for the case study on emigration and shows how a model can be trained to classify topic-specific collections. For the training/testing corpus, a collection with the keywords "Auswander*", "Ausgewanderte", "Emigrant*", "Emigrierte", "Emigration", "Kolonist*", and "Ansiedler*" (all different German words for emigrants or emigration) have been created. In addition, information on the pre-defined gropus (news, ads, culture...) were added using numbers between one and ten. 
For classification, topic modelling (LDA) was chosen because it showed the best performance in classification (after experiments with word embeddings or LDA and word embeddings combined). LDA provides a way to group documents by topic and perform similarity searches and improve precision. Thanks to sklearn, it is relatively easy to test different classifiers for a given topic classification task. Logistic regression was chosen as binary classifier. 

*Output graph using an unseen collection on the topic of emigration  (sample of 1631 newspaper clippings).* 

![Collection on the topic of Emigration](images/cat.PNG)

## Group similar newspaper articles
<a href="https://github.com/NewsEye/NLP-Notebooks-Newspaper-Collections/blob/master/news_article_similarity_notebook.ipynb" target="_blank">Go to notebook</a>

Many researchers have the problem that their data sets contain articles that are irrelevant to their research question. For example, if the goal is to find newspaper articles or "news items" on return migration, researchers have to deal with some ambiguous search terms. The German words "Heimkehr" (returning home) or "Rückkehr" (returning back) lead to many articles that are relevant to the research question, but also to articles that are not relevant (e.g. return from a mountain tour, work, etc.). By using topic models and document similarity measurements, this notebook allows me to exclude these articles without combining the word "Heimkehr" with other search terms. Furthermore, the same code can also be used to remove or prefer a certain genre, e.g. advertising, sports news, etc.

To give another example: If I want to create a collection of articles about the disease cancer, one of the important German words for cancer is "Krebs". But "Krebs" in German is also a common surname, an animal (crab) or a sign of the zodiac.
The main purpose of this notebook is to take into account the context of articles in order to automatically refine a search query. This means that even ambiguous words can be used for the search without having to combine them with other words, making the search less influenced by the researcher's prior knowledge and avoiding a too narrow tunnel vision.

So how is this working?

Given a manually annotated collection of articles containing relevant as well as non relevant articles, this program will get the topic distribution of each document using LDA (gensim library). These topic distributions serve as a comparison for other, unseen articles, in order to automatically distinguish between relevant and non-relevant articles. The annotations are used for evaluation and counting the relevance probability for an unseen article.

For the comparison, the Jensen-Shannon distance method is used to measure the similarity between the topic distribution of an unseen article and the topic distribution of the training corpus. Therefore, the topic distribution of each new article will be compared to the topic distribution of the articles in the trained corpus. Then, for each unseen article, the 10 most similar articles from the training corpus are being extracted. These articles carry the information about the manually assigned relevancy. If 60 precent of the automatically found similar articles were annotated as relevant, the new article will be marked as relevant. Otherwise it will be marked as irrelevant. Using two different datasets (one about cancer and one about return migration), the average score of correct selected articles is between 80 and 90 percent.

![](images/nk.PNG)

## Discover a newspaper collection with diachronic Ngram clouds

<a href="https://github.com/NewsEye/NLP-Notebooks-Newspaper-Collections/blob/master/n-gram_clouds_notebook.ipynb" target="_blank">Go to notebook</a>

Ngrams are connected sequences of n items from a given text or speech sample. This means that words are not considered as individual units, but in relation to each other. For scholars in the humanities, ngrams can be helpful to get an overview of their collection or to identify discourse markers (discourse = a group of related texts belonging to a common system of formation). Ngrams can never be a research result per se - which is true for any output of NLP methods - but they can help to find important patterns in a particular collection.  

![ngrams](images/WC.PNG)

If ngrams are used to identify discourse markers, it can be useful to create diachrinic ngrams to explore the change of rextual patterns. This Notebook therefore shows how diachronic ngrams can be build and visualized. For cultural heritage material, visualizations should make it possible to open up and experience the collections in new ways. But they should always be linked to the original documents. 

The graphic representation and the original material cannot be perceived as two different elements, they are rather  interwoven and interact with each other. Therefore, this Notebook allows to browse the original texts within the Notebook. Thus the results of the ngram clouds can be researched in the context of the original text. 

## Discourse in Spanish flu coverage

<a href="https://mybinder.org/v2/gh/soberbichler/Discourse-in-Spanish-flu-coverage_Notebook/HEAD" target="_blank">Go to notebook</a>

This notebook was created with the aim of using it in workshops and for teaching purposes. The notebook was launched via Binder, which allows one to turn a Jupyter Notebook into a interactive notebook, making the code immediately reproducible by anyone without prior installations. This is especially helpful for digital humanities courses because it allows students to get started with Jupyter Notebooks. The notebook enables the creation of diachronic ngrams and topic visualizations based on exports from the NewsEye Demonstrator.  

![tm](images/tm.png)

## Uses of the Term Telegraph in the Context of Journalism: Introduction to Topic Modeling on a Data Set created by the Newseye Project

<a href="https://gitlab.phaidra.org/bekesij9/newseye/-/blob/master/workflow.ipynb" target="_blank">Go to notebook</a>

This notebook was created by János Békési and Martin Gasteiner with the aim to investigate the usage of the term Telepraph in Austrian historical newspapers. The data analysed in this notebook was exported from the Newseye platform, which is based on the Content Management System Blacklight.The data used here is based on a general search on the basis of the search engine Solr for articles on the word "telegraph" in the following time periods: 1864-1874, 1895-1901, 1911-1922. The search was carried out in the following German-language newspapers, namely Neue Freie Presse, Innsbrucker Nachrichten, Arbeiter Zeitung and Illustrierte Kronen Zeitung. The resulting data package was exported as JSON and processed with regard to topic modelling. The notebooks shows how topic models can be trained, visualized and how diachronic topic models can be created. 

