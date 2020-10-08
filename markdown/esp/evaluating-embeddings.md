# Evaluating Embeddings

## Evaluation Tasks

### Analogy

`a` is to `b` as `c` is to `d`

eg: `good` is to  `better` as `high` is to `higher`

Different analogy [tasks](https://gluon-nlp.mxnet.io/examples/word_embedding_evaluation/word_embedding_evaluation.html#Google-Analogy-Test-Set)

### Similarity

Human scored similarity between word pairs

Spearman correlation is computed between list of scores from cosine similarity between vectors. **more research**

eg:

- ['tiger' 'cat'] scores 7.35
- ['automobile' 'car'] scores 10

Evaluation Datasets
- [MEN]()
- WordSim353[]()
- [SimLex-999](https://fh295.github.io/simlex.html) [[Paper]](https://arxiv.org/abs/1408.3456)


### Categorization
