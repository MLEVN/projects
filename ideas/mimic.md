# [Project Ideas from MLEVN](/projects/ideas): MIMIC-III benchmarks
The main repo of the benchmark: [YerevaNN/mimic3-benchmarks](https://github.com/YerevaNN/mimic3-benchmarks)

## Implement more neural architectures for the benchmark
* GRU-D, published in [Nature Scientific Reports](https://www.nature.com/articles/s41598-018-24271-9)
* The network from Google's EHR paper from [Nature Digital Medicine](https://www.nature.com/articles/s41746-018-0029-1)
  * It is not yet clear that this network is fully applicable to the benchmark, so some modifications might be required.
* TODO: are there more good architectures?

## Adversarial training on the benchmark data
_Vahe Asvatourian is working on this._

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

