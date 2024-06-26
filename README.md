# Hierarchical Quantification: directly estimate prevalence

## Overview
This repository contains the code implemented for the methods described in my master thesis, titled "_From Classification to Quantification: New Methods for Estimating Cause-of-Death Prevalence from Verbal Autopsies_" The primary focus of this work is to explore novel text quantification techniques that leverage the intrinsic hierarchical nature of mortality statistics datasets.
It is a supervised learning task, with physician-determined causes of death serving as ground truth labels.

### What Verbal Autopsies are 
Verbal autopsies (VAs from now on) are standardized textual questionnaires that gather information about the symptoms experienced by the deceased in the days preceding a fatality.
VAs were developed to address the need for fundamental registration of deaths also for countries with weak registration systems.

### What quantification is 
The process of training class prevalence estimators through supervised learning is termed quantification, as coined by [Forman, 2005](https://link.springer.com/chapter/10.1007/11564096_55) or as "learning to quantify".
In literature, two main categories of quantification methods are recognised: aggregative methods, which involve classifying individual data items as an intermediate step, and non-aggregative methods, that address the quantification problem in its entirety, bypassing the need to classify individual items. In this section we will start from the more obvious method, _Classify and Count_, then moving to direct methods for getting the aggregate level, that are expected to perform better in prior probability shift settings ([Moreo et al., 2023](https://dl.acm.org/doi/10.1145/3606264))

### Why quantification 
VAs pertain to the field of epidemiology, in which the aim is obtaining estimates of disease prevalence across different geographical regions, time periods, and age groups. In this context, the focus shifts from individual data to aggregate data. The main goal here is that of estimating (by means of supervised learning) the prevalence of each class accurately also when the distribution of the classes in
the training data may be very different from the distribution of the unlabelled data that is the object of estimation. Therefore, epidemiological objectives, such as those just mentioned, align more with the task of quantification than that of classification, understood as minimizing errors while accurately assigning the correct pathology to each death.

### What's new in this project
The notebook includes implementations of the following methods:
  1. Classify-and-Count approach, on results obtained with a flat classifier
  2. "real" quantification algorithms, both aggregative ((ACC, PCC, PACC) and direct estimation (SLD), on results obtained with a flat classifier
  3. Classify-and-Count and ACC on results obtained with a hierarchical classifier
  4. Hierarchical versions of the quantification algorithms in 1 and 2

We also provided comparation between tfidf representations and pre-trained embeddings, and tried to exploit the full data available in questionnaires by concatenating both closed question and textual narratives.
To the best of our knowledge, it is the first time in literature that a hierarchical approach is developed. 

### What we found out
The work started from the knowledge of the fact that quantification methods could be better for prior-shift settings. Suprisingly, many among the supposedly more sophisticated quantification methods often fail to improve over CC’s performance (i). Even the most sophisticated quantification method (SLD) does not stand as the top performer, while interestingly PCC is the algorithm that obtains the best results in most of the settings. Sporadic benefits have been observed by exploiting the hierarchical version of the proposed algorithms, but we have not obtained the net benefit we expected, neither in terms of better quantification
(ii) nor in terms of improved efficiency (iii). 
Some good outcomes were obtained employing a hierarchical classifier, as the results in terms of MAE and MRAE were pretty much the same but on a way shorter training time.
Again going against our expectations, tfidf vectors performed as well as pre-trained distilBERT embeddings, but on a fraction of the training time.
In any case, this work marks the beginning of the discussion regarding hierarchical quantification. The logical evidence of the wisdom of an approach divide et impera, that is, thinking about exploiting a (hierarchical) grouping of classes in problems with a large or very large set of classes, nevertheless continues to motivate the need for further investigation. The full detail can be found in the thesis. 


### Contact
For any questions or further information, please contact:
Name: [Ilaria Salogni](https://ilariasalogni.github.io/)

