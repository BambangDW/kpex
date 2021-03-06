kpex: Keyphrase extraction in Python (based on a corpus)
=============================================================================

Overview
--------

This simple package does a term-frequency inverse-document-frequency analysis ([tf-idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf))  of a text based on a corpus of texts. This means it extracts possible keyphrases from text and corpus and ranks them, using a score that increases with keyphrase frequency in the text and decreases with keyphrase frequency in the corpus. This is basically the simplest unsupervised approach beyond using raw frequencies for ranking. More sophisticated approaches like [TextRank](https://github.com/davidadamojr/TextRank) or supervised approaches using [training sets](https://github.com/snkim/AutomaticKeyphraseExtraction) will perform significantly better.

Dependencies, Installation & Testing
---------------------------

Needed Python packages: nltk, gensim and scikit-learn

Install dependencies with:
```
pip install nltk gensim scikit-learn
```

Install kpex with:
```
pip install git+https://github.com/christophfeinauer/kpex
```

Install needed nltk data packages in Python:
```
import nltk
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')
nltk.download('stopwords')
```

Test in Python (using the Wikpedia article on 'food' and articles on 'fast food', 'restaurant' and 'cooking' as corpus:
```
import kpex
kpex.test()
```

Everything was tested on Python 3.6.0

Usage
-----

The function ```kpex.kpex(list,kw...)``` takes a list ```list``` of filenames and analyzes the first file based on the rest, which is used to calculate the document frequencies.

Keyword options:

* ```package='sklearn'```: Package (```sklearn``` or ```gensim```) to use for the tfidf computation. Generally, ```sklearn``` should be used (more options).

* ```max_words=3```: Maximum number of words in a keyphrase

* ```number_of_terms=10```: Number of top-ranking keyphrases to be returned

* ```max_features=20```: Number of high-frequency features to be used. ```max_features=2*number_of_terms``` seems to work fine.

* ```lemmatize=True```: Lemmatize candidate keyphrases. Improves the grouping of keyphrases but can lead to grammatically incorrect keyphrases. 

* ```train_on_script=True```: Include the first provided file for the document frequency calculation. 

Sources
------
Ideas, knowledge and occasional code snippets taken from:

* http://www.aclweb.org/anthology/P/P14/P14-1119.xhtml
* http://bdewilde.github.io/blog/2014/09/23/intro-to-automatic-keyphrase-extraction/
* http://alexbowe.com/au-naturale/
* https://joshbohde.com/blog/document-summarization

