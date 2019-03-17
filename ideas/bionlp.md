# [Project Ideas from MLEVN](/projects/ideas): NLP in biomedical domain

## Fine-tune BERT for biomedical domain
* Recently, a bio-specific tokenizer / tagger / parser was released by Allen AI called `scispacy`.
* [BERT](https://github.com/google-research/bert) is a very powerful language model trained by Google on huge datasets.
* Is it possible to tune BERT so that it keeps its general power, but works better for biomedical downstream tasks?
  * Check [BioBert](https://github.com/dmis-lab/biobert)
* TODO: Design evaluation strategy. There is a paper [1] that can help.

[1] Wang et al., A Comparison of Word Embeddings for the Biomedical Natural Language Processing, [arxiv](https://arxiv.org/pdf/1802.00400.pdf)

## Predict the organism for biological named entities 
* Named entity recognition for biomedical texts is usually performed at a sentence level
* In many cases it is impossible to determine the organism the detected protein belongs to by looking only at the sentence
  * In rare cases it _is_ possible, usually `d` prefix means "drosophila", `h` means "human"
* So the full text of the paper is needed to make a decision
  * Apparently, sometimes the same paper can refer to multiple organisms, which makes the problem ill-defined
* TODO: literature review on this problem. Is it really a challenging task?
