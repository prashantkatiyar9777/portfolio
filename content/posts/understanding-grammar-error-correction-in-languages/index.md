---
author: "Nihar Sanda"
title: "Understanding Grammar Error Correction in Morphologically Rich Languages"
date: "2021-12-28"
description: "Understanding the research paper on grammar error correction in morphologically rich languages especially in Russian Languages"
tags: ["NLP", "ML", "AI"]
categories: ["technology"]
# cover:
#   image: "1.png"
#   relative: true # To use relative path for cover image, used in hugo Page-bundles
---

In this article we will be discussing the research paper on grammar error correction in morphologically rich languages especially in Russian Languages. The research paper is titled: `The Grammar Error Correction in Morphologically Rich Languages: The Case of Russian` and it is published in the Journal of Language Technology. The research paper is available [here](https://aclanthology.org/Q19-1001.pdf)

Rozovskaya and Roth 2019, uses a corpus of the Russian Learner Corpus of Academic Writing (RULEC, 560K
words) which is written by students in United States learning Russian.

Russian language is termed as "Morphologically Rich Language" (MRL's). The dataset included a subest of [RULEC]()(Alsufieva et al., 2012) (12,480 sentences, comprising 206K words). Out of which essays from 12 foreign and 5 heritage Russian speakers were slected to be annotated by 2 native Russian speakers. The essays were annotated and each error was assigned a type which led to the development of error classification schema that addresses errors in morphology, syntax, and word usage, and takes into account linguistic properties of the Russian language. The annotated corpus is refereed as [RULEC-GEC](https://github.com/arozovskaya/RULEC-GEC).

The approaches experimented in the paper are:

### 1. Learner-trained classifiers:

- In this approach, a special classifer is developed for each error type. The most common errors include noun case, verb aspect, preposition, verb agreement.

- `Noun Case Errors`: The Russian case system consists of Nominative, Genetive, Accusative, Instrumental, Dative, and Locative. To analyze this we have a six-way classifier with each classifier corresponding to a case. However, sometime surface form f the noun can be ambiguous i.e. A word can have 2 or more than 2 cases at once for different contexts.
- `Number and Gender Verb Agreement Errors`: In russian verbs are specified for number (singular, plural), gender (feminine, masculine, and neutral), and person.
- `Preposition Errors`: In this classifier, we take the most common preposition errors in Russian which is in similar line to the top n most frequent prepositions in English.
- `Verb Aspect Errors`: The Russian verb system has three tenses-present, past, and future- and each tense can be expressed in imperfective or perfective aspect.

| Errors                  | Confusion Set                                                      |
| ----------------------- | ------------------------------------------------------------------ |
| Noun:case               | {Nominative, Genetive, Accusative, Instrumental, Dative, Locative} |
| Verb agreement (num.)   | {Singular, Plural}                                                 |
| Verb agreement (gender) | {Feminine, Masculine, Neutral}                                     |
| Aspect                  | {Perfect, Imperfect}                                               |
| Prep.                   | {15 prepositions}                                                  |

The above table depicts the confusion matrix used by the classifier model for the each type of error.

### 2. Minimal-supervision classifiers: Error-specific classifiers trained on learner and native data with minimal supervision

### 3. Phrase-based machine translation system:

- This system follows the implementation in Susanto et al. (2014) and is trained using Moses (Koehn et al., 2007). Here, a phrase based Machine Translation (MT) model is used and is trained on the RULEC-GEC corpus. As there is only a small amount of parallel data the use of phrase based model makes more sense because of the low amount of data and less accuracy in low-resource settings.
- However, the Classifier Model outperforms the phrase based MT model by a large margin. But the accuracy can be improved by introducing dense and sparse features. According to the paper, the accuracy was way too less with the MT model, that introducing dense features wouldnt have helped it to outperform the classifer model.

The result and error analysis can be found in the paper [here](https://aclanthology.org/Q19-1001.pdf). The purpose of this article was to understand the various models defined by the Alla Rozovskaya and Dan Roth in their paper.

I sincerely Thank the researchers for coming with these models and revolutionizing the world of grammar error correction.

## References

- Anna Alsufieva, Olesya Kisselev, and Sandra Freels. 2012. Results 2012: Using flagship data to develop a Russian learner corpus of academic writing. Russian Language Journal, 62:79–105.
