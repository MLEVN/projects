# [Project Ideas from MLEVN](/projects/ideas): NeurIPS'19 Reproducibility Challenge

Read more about NeurIPS'19 Reproducibility challenge at the [official website](https://reproducibility-challenge.github.io/neurips2019/).

## MixMatch: More ablations
[**MixMatch**](https://arxiv.org/abs/1905.02249) is a state-of-the-art method for semi-supervised learning for CIFAR-10/100, SVHN and STL-10.

Looks like the baselines are tuned well. The list of authors has a large overlap with [another paper on 
evaluation of semi-supervised algorithms](https://papers.nips.cc/paper/7585-realistic-evaluation-of-deep-semi-supervised-learning-algorithms)
which advocates for proper tuning of the baselines. So, it won't be easy to find problems in their baselines.

The paper does contain an **albation** study. But the method has so many moving parts that we believe there are more things to check: 
* What if we replace Euclidean norm in (4) by cross-entropy?
* What if we keep the original MixUp by ignoring equation (9)?
* Use Virtual Adversarial Training instead of data augmentation
* What is the role of weight decay?
* What is the role of the exponential moving average of the parameters for evaluation?

Try all described ablations on other datasets/setups.

More ideas:
* Include more unlabeled examples iteratively. Start from the most confident ones according to some measure.
* Compare Euclidean loss with the idea from Hrayr's preprint on predicting the gradient.

