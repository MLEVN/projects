# Project Ideas from MLEVN
If you are interested in working on any of the listed projects, please open [an issue on Github](https://github.com/MLEVN/projects/issues) to track the progress.

This page lists relatively general tasks. We have two more pages for more specific tasks
1. [Project ideas related to MIMIC-III clinical prediction benchmarks](/projects/ideas/mimic.html)
2. [Project ideas related to biological NLP](/projects/ideas/bionlp.html)

## Dataset distillation for other tasks
A recent paper by researchers from MIT, FAIR and Berkeley [1] shows how one can generate a very small synthetic dataset which is enough to train a neural network to achieve good performance on MNIST dataset. The authors plan to extend the work to larger image datasets and to non-image datasets. Adapting the method for [text and EHR data](#a-short-list-of-non-image-classification-tasks) can be both challenging and interesting.

[1] Tongzhou Wang, Jun-Yan Zhu, Antonio Torralba, Alexei A. Efros, _Dataset Distillation_, [arXiv](https://arxiv.org/abs/1811.10959)

## Neuron deletion vs generalization for other tasks
_Victoria Poghosyan is working on this._

There is a paper by Deepmind [1] about the stability of a trained large ConvNet when removing some of its neurons (Fig. 1). 
They also showed that there is a correlation between generalization and robustness (Fig. 3b).

* Choose a [non-image-classification task](#a-short-list-of-non-image-classification-tasks), train a few (different) types of networks. Could be one academic task + one task from industry
* Generate Figure 1 for these networks (without label noise) 
* Generate Figure 3b for these networks, look for clusters
* Investigate if robustness can be used as an early stopping signal (Figure 4)
* Investigate the role of dropout / recurrent dropout, compare with ConvNet results (Figure 5a)
* (harder) Investigate the role of recurrent batch-norm (Figure 5b)
* (harder) Generate Figure 1 _with_ label noise. Requires proof that the network will still be able to overfit (see the task _"Overfitting ability of recurrent networks"_)

[1] Ari S. Morcos, David G.T. Barrett, Neil C. Rabinowitz, Matthew Botvinick, _On the importance of single directions for generalization_,
[arXiv](https://arxiv.org/abs/1803.06959)


## Overfitting ability of recurrent networks
_Tatev Mejunts is working on this_

Attempt to confirm the results of the famous paper on "rethinking generalization" [1] for recurrent networks

* Choose a [non-image-classification task](#a-short-list-of-non-image-classification-tasks)
* Think about the equivalents of _random pixels_ and _shuffled pixels_ for the selected tasks
* Generate Figure 1 from the paper
* Think about the effect of regularization (augmentation, dropout, etc.)

[1] Chiyuan Zhang, Samy Bengio, Moritz Hardt, Benjamin Recht, Oriol Vinyals, _Understanding deep learning requires rethinking generalization_, [arXiv](https://arxiv.org/abs/1611.03530)


## Test the quality of multilingual embeddings

There are two recent pretrained multilingual embeddings:
* Unsupervised, based on Facebook's [MUSE](https://github.com/facebookresearch/MUSE)
* Supervised using Google Translate API by [BabylonPartners](https://github.com/Babylonpartners/fastText_multilingual/blob/master/README.md)
* There is an old blogpost about (possibly) more techniques by [Sebastian Ruder](http://ruder.io/cross-lingual-embeddings/).

The task is to validate the quality of these embeddings for transfer learning. 
* Take a famous academic dataset in English. Could be Amazon's reviews. Find a related dataset (with the same labels) in a different language
* Train models on the English dataset using pure English vectors and different types of multilingual embeddings. See if multilingual embeddings are performing worse
* Train and evaluate similar models on the (smaller) dataset in another language 
* Evaluate English models with multilingual embeddings on the smaller dataset
* Train on a combination of English dataset and the other one. Plot a chart of accuracy depending on the size of the second dataset.


## Test connectivity of local minima in neural networks trained on NLP tasks
_Hakob Tamazyan is working on this._

There is a recent paper [1] by Vetrov's team that shows the following. If one trains a deep neural net (e.g. ResNet) on ImageNet and finds two local minima A and B (with different weight initializations), then there exists a point C in the space of weights such that the loss function is almost constant along the straight lines AC and BC. This has not been tested yet on NLP tasks. 

* Take one or two popular NLP datasets, e.g. from [this list](#a-short-list-of-non-image-classification-tasks)
* Train several popular neural models (both CNN and LSTM based) with few random initializations
* Use the algorithms described in [1] to find the "C" points
* Draw pictures like Figure 1 of [1]
* (harder) Understand the number of possible C points for each A/B pair

[1] Timur Garipov, Pavel Izmailov, Dmitrii Podoprikhin, Dmitry Vetrov, Andrew Gordon Wilson, _Loss Surfaces, Mode Connectivity, and Fast Ensembling of DNNs_, [arXiv](https://arxiv.org/abs/1802.10026)


# A short list of non-image-classification tasks
* Sentence classification, e.g. [sentiment analysis](http://nlpprogress.com/sentiment_analysis.html)
* Sequence tagging, e.g. POS tagging. [BiLSTM-CNN-CRF by UKPLab](https://github.com/UKPLab/emnlp2017-bilstm-cnn-crf)
* Image segmentation
* Speech synthesis, e.g. [char2wav](http://josesotelo.com/speechsynthesis/) or [VoiceLoop](https://research.fb.com/downloads/voiceloop/)
* [Speech recognition](https://github.com/syhw/wer_are_we), e.g. [wav2letter](https://github.com/facebookresearch/wav2letter) (has pretrained models)
* Time-series prediction for Electronic Health Records, e.g. [MIMIC-III benchmarks](https://github.com/YerevaNN/mimic3-benchmarks)
