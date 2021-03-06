# Training Models and Pipelines

## Table of contents

* [Spark NLP Training](https://github.com/JohnSnowLabs/spark-nlp-models/tree/master/training)
  * [Lemmatizer Model](https://github.com/JohnSnowLabs/spark-nlp-models/tree/master/training/lemmatizer)
  * [POS Tagger Model](https://github.com/JohnSnowLabs/spark-nlp-models/tree/master/training/part_of_speech)
  * [NerDL Model](https://github.com/JohnSnowLabs/spark-nlp-models/tree/master/training/ner_dl)

* [Spark NLP Evaluation](#spark-nlp-evaluation)
  * [NerDLModel](#nerdlmodel)
    * [English](#english-ner)
    * [French](#french-ner)
    * [German](#german-ner)
    * [Italian](#italian-ner)
  * [PerceptronModel](#perceptronmodel)
    * [French](#french-pos)
    * [German](#german-pos)
    * [Italian](#italian-pos)

## Spark NLP Evaluation

How do we calcuate Precision, Recall, and F1-Score:

> **Precision** is "how useful the POS results are", and **Recall** is "how complete the results are". Precision can be seen as a measure of **exactness or quality**, whereas recall is a measure of **completeness or quantity**. [https://en.wikipedia.org/wiki/Precision_and_recall](https://en.wikipedia.org/wiki/Precision_and_recall)
> The **F1 score** is the harmonic average of the precision and recall, where an F1 score reaches its best value at 1 (perfect precision and recall) and worst at 0. [https://en.wikipedia.org/wiki/F1_score](https://en.wikipedia.org/wiki/F1_score)

![Precision](https://wikimedia.org/api/rest_v1/media/math/render/svg/26106935459abe7c266f7b1ebfa2a824b334c807)

![Recall](https://wikimedia.org/api/rest_v1/media/math/render/svg/4c233366865312bc99c832d1475e152c5074891b)

![F1 Score](https://wikimedia.org/api/rest_v1/media/math/render/svg/057ffc6b4fa80dc1c0e1f2f1f6b598c38cdd7c23)

### NerDLModel

The evaluation scores are tagged-based and it is done over a random proportion of `WikiNER` (for multi-lingual NerDLModel) or CoNLL 2003 `testa+testb` for English NerDLModel.

#### English NER

`onto_300`

This pre-trained `NerDLModel` is trained on OntoNotes `CoNLL 2012` corpus and pre-trained WordEmbeddings `glove_840B_300`.

Evaluation: `conlleval.pl`

processed 152728 tokens with 11257 phrases; found: 11345 phrases; correct: 9916.

|Accuracy         |Precision         |Recall |F1-Score   |
|-----------------|------------------|-------|-----------|
|97.81%|87.40%|88.09%|87.74|

#### French NER

`wikiner_840B_300`

This pre-trained `NerDLModel` is trained on French `WikiNER` corpus and pre-trained WordEmbeddings `glove_840B_300`.

#### French NER ACCURACY

Evaluation: `conlleval.pl`

|Accuracy         |Precision         |Recall |F1-Score   |
|-----------------|------------------|-------|-----------|
|98.01%|88.02%|87.64%|87.83|

Evaluation: `Micro-average`

|Precision |Recall |F1-Score          |
|----------|-------|------------------|
|0.91|0.87|0.89|

#### German NER

`wikiner_840B_300`

This pre-trained `NerDLModel` is trained on Dutch `WikiNER` corpus and pre-trained WordEmbeddings `glove_840B_300`.

#### German NER ACCURACY

|Precision |Recall |F1-Score          |
|----------|-------|------------------|
|0.94|0.89|0.91|

#### Italian NER

`wikiner_840B_300`

This pre-trained `NerDLModel` is trained on Italian `WikiNER` corpus and pre-trained WordEmbeddings `glove_840B_300`.

#### Italian NER ACCURACY

|Precision |Recall |F1-Score          |
|----------|-------|------------------|
|0.89|0.93|0.91|

### PerceptronModel

The evaluations have been done over gold tokenization.

#### French POS

Trained by PerceptronApproach annotator on the [Universal Dependencies](https://universaldependencies.org/treebanks/fr_gsd/index.html). This has been tested on `fr_gsd-ud-test` corpus which is not part of the training.

|Precision |Recall |F1-Score          |
|----------|-------|------------------|
|0.88|0.88|0.88

#### German POS

Trained by PerceptronApproach annotator on the [Universal Dependencies](https://universaldependencies.org/treebanks/de_hdt/index.html). This has been tested on `de_hdt-ud-test` corpus which is not part of the training.

|Precision |Recall |F1-Score          |
|----------|-------|------------------|
|0.96|0.95|0.95

#### Italian POS

Trained by PerceptronApproach annotator on the [Universal Dependencies](https://universaldependencies.org/treebanks/it_isdt/index.html). This has been tested on `it_isdt-ud-test` corpus which is not part of the training.

|Precision |Recall |F1-Score          |
|----------|-------|------------------|
|0.89|0.89|0.95
  