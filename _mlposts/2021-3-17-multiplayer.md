---
layout: post
title: Creating a Proper Android Malware dataset for Machine Learning researches
---

## Introduction

When it comes to training models, there is no doubt about the importance of dataset. Performance of the models hihghly coupled with the data that they have trained on. Its a common problem that models perform really good on the dataset but not that good in reall life. Usually two main reasons lies behind this problem.

First reason can be technicall mistakes such as, information leakage on training, overfitting or poor feature selection. These problems are not impossible to solve and can be overcome.


Second and crucial problem is, 'If the dataset is not projecting reall life data' and in this scenario there is pretty much nothing can be done by developers. All the efforts become futile. Because your model learns what it saw. So put it on shortly, 'samples in dataset should be similar to the samples in reall life as much as possible.'


When supervised machine learning techniques used on areas like object detection, labels are cristal clear and easier to verify. For instance, when we have image dataset, its not that hard to answer questions like these about that dataset, How many object from each category exist? Is it balanced ? Did objects labeled correctly? If we can answer these questions, it means we know the sample distribution about the different categories, diversity of samples and we have clear understanding our data \cite{droidkin}. So, we can measure the model's performence correctly.\par
 
Problem arises with malware datasets, usually we just have labels which indicates their behaviour or family but not more than this. We really don't know whether those samples just duplicates of each other, or how similar they are. Public researchers usually concern about uniqueness of sample when they include that sample in their dataset. Usually cryptographic hash values has been used as an unique identifiers. But malwares with same functionalities can have different hash values because of different obsufication and packing techniques. So this leds the relaibility problem about their dataset \cite{droidkin}. Their dataset may consist of duplicate data and sample distrubition is unknown.  If we measure model performence under these circumstances it may perform really well with test data but probably not that well in reall life.\par

Long story short, We should avoid the common pitfalls that other publicly available datasets and researches has. To tackle with the problem, we should be sure about our dataset that it contains variety of malware families and it's not only consist of duplicated, repacked malwares.

## Related Studies

To able to prevent sample duplication and to have control over sample distrubition, similarities between samples should be assesed. For similarity analysis different formulas and approaches has been proposed by researchers.

<p align="center">
<img src="/images/aml/deneme.gif" alt="A single capsule containing multiple neurons (part properties)." width="500">
</p>

The formula in the \autoref{authorship} proposed for authorship attribution\cite{ralph_bennett}. In this formula I and J indices represents letters in the english alphabet. M(I,J) stands for bigram frequency of that specific two letters. E(I,J) is a normalized frequency of the two letters in English language. The problem with this formula is language dependency.

<p align="center">
<img src="/images/aml/deneme.gif" alt="A single capsule containing multiple neurons (part properties)." width="500">
</p>

\autoref{lid_formula} shows another approach for similarity analysis but this time it is language independent \cite{ralph_bennett}. Like the first formula M(I,J) represents frequency of I and J letters. M and N are represents different texts. \paragraph{}

Formula in \autoref{lid_formula} looks fine and language independent. Let say n-grams frequencies pairs are like this, [0.9 - 0.8] and [0.2 - 0.3]. In this case, frequency differences will be 0.1. So if we use formula in \autoref{lid_formula}, it gives equal weight for the different bi-gram pairs which has same differences.In  \cite{keselj}, if freqeuncy differences are equeal then what they want is, n-gram pairs with lower frequencies to have more impact on the outcome compare to n-grams pairs with the high frequency.

<p align="center">
<img src="/images/aml/deneme.gif" alt="A single capsule containing multiple neurons (part properties)." width="500">
</p>

So they proposed formula in \autoref{normalized}. Since frequency differences will be divided by the average of those frequencies, differences between n-gram pairs will be normalized.



In \cite{stamatatos} they proposed a different approach. They took $L$ most frequent n-grams and call it Simplified Profiles(SP). Instead of normalizing those frequency values they just compared two profiles and chosed the intersection between them as it can be seen from the \autoref{SP_A}.