# Project Ideas from MLEVN
If you are interested in working on any of the listed projects, please open [an issue on Github](https://github.com/MLEVN/mlevn.github.io/issues) to track the progress.

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



# Tasks related to MIMIC-III benchmarks
The main repo of the benchmark: [YerevaNN/mimic3-benchmarks](https://github.com/YerevaNN/mimic3-benchmarks)


## Implement more neural architectures for the benchmark
* GRU-D, published in [Nature Scientific Reports](https://www.nature.com/articles/s41598-018-24271-9)
* The network from Google's EHR paper from [Nature Digital Medicine](https://www.nature.com/articles/s41746-018-0029-1)
  * It is not yet clear that this network is fully applicable to the benchmark, so some modifications might be required.
* TODO: are there more good architectures?

## Adversarial training on the benchmark data
* Understand adversarial training for images. [Cleverhans](https://github.com/tensorflow/cleverhans) is a good starting point
* Investigate adversarial training for RNNs, look for a reasonable codebase
  * Great starting point by Berkeley researchers published in [EMNLP 2017](http://aclweb.org/anthology/D17-1187). Code is on [Github](https://github.com/jxwuyi/AtNRE)
* Implement adversarial training on the benchmarks
* Train multiple models with different hyperparameters for adversarial training (noise levels etc.). Plot charts

## Adversarial reprogramming for the benchmark tasks
There is an interesting [paper by Google Brain](https://arxiv.org/abs/1806.11146) team on adversarially reprogramming pretrained neural networks to perform a new task. The idea is demonstrated to reprogram ImageNet network to perform MNIST classification. ~~So far, there is no evidence that it might work on recurrent networks. This fact makes this task a risky one :)~~ [A paper from UC San Diego](https://arxiv.org/abs/1809.01829) applied the technique for text classification tasks based on LSTMs and CNNs  

* Attempt to repeat the experiment on ImageNet to MNIST to understand the difficulty of the work
* Attempt to reprogram phenotyping network for in-hospital mortality prediction
* Discuss different methods of modifying the input
  * Add the "program" before/after the input (the results should be similar)
  * Add the "program" between the existing timesteps
* (harder) attempt to do the same without fixing the input size!

## Visualizing the neural models
_David Karamyan is working on this._

There are lots of papers on "visualizing and understanding" convolutional networks, mostly starting from [1]. In recent years a few similar papers appeared for RNNs, especially about sentiment analysis [2,3]. Another recent paper does similar things for RNNs running on EHR notes [4].
* Read the papers, understand different methods
  * Looks like that the methods used in [2] and [3] are different
  * This can result in a great reading group meetup
* Apply some of these techniques on the pretrained models

[1] Karen Simonyan, Andrea Vedaldi, Andrew Zisserman, *Deep Inside Convolutional Networks: Visualising Image Classification Models and Saliency Maps*, [arXiv](https://arxiv.org/abs/1312.6034)

[2] Jiwei Li, Xinlei Chen, Eduard Hovy and Dan Jurafsky, *Visualizing and Understanding Neural Models in NLP*, NAACL-HLT 2016, [ACLWEB](http://www.aclweb.org/anthology/N16-1082)

[3] Leila Arras, Gregoire Montavon, Klaus-Robert Muller, and Wojciech Samek, *Explaining Recurrent Neural Network Predictions in Sentiment Analysis*, 8th Workshop on Computational Approaches to Subjectivity, Sentiment and Social Media Analysis, 2017, [ACLWEB](http://www.aclweb.org/anthology/W17-5221)

[4] Jingshu Liu, Zachariah Zhang, Narges Razavian, Deep EHR: Chronic Disease Prediction Using Medical Notes, [arXiv](https://arxiv.org/abs/1808.04928)


## Improve multitask learning
It is generally a hard problem to determine weights for the tasks in the multitask training setting (TODO: any reference?). The experiments on MIMIC benchmarks showed that the networks overfit on some tasks earlier than on others.

Is it possible to create an architecture that will automatically modify the weights during the training? Something similar to [1]... 

[1] Marcin Andrychowicz, Misha Denil, Sergio Gomez, Matthew W. Hoffman, David Pfau, Tom Schaul, Brendan Shillingford, Nando de Freitas, *Learning to learn by gradient descent by gradient descent*, 2016, [arXiv](https://arxiv.org/abs/1606.04474)


# A short list of non-image-classification tasks
* Sentence classification, e.g. [sentiment analysis](http://nlpprogress.com/sentiment_analysis.html)
* Sequence tagging, e.g. POS tagging. [BiLSTM-CNN-CRF by UKPLab](https://github.com/UKPLab/emnlp2017-bilstm-cnn-crf)
* Image segmentation
* Speech synthesis, e.g. [char2wav](http://josesotelo.com/speechsynthesis/) or [VoiceLoop](https://research.fb.com/downloads/voiceloop/)
* [Speech recognition](https://github.com/syhw/wer_are_we), e.g. [wav2letter](https://github.com/facebookresearch/wav2letter) (has pretrained models)
* Time-series prediction for Electronic Health Records, e.g. [MIMIC-III benchmarks](https://github.com/YerevaNN/mimic3-benchmarks)
