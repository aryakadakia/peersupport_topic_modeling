# Topic modelling of peer-support conversations

Comparison of three topic modelling approaches on peer-support messages,
alongside a fine-tuned transformer classifier for session fidelity.

The three models take different approaches to the same problem. LDA treats
documents as mixtures over word distributions. Top2Vec and BERTopic both work in
embedding space instead, clustering documents by semantic similarity and
deriving topic terms afterwards. Running all three on one corpus shows how much
the choice of method shapes what counts as a topic.

## Contents

| File | What it does |
|---|---|
| `LDA_all_data.ipynb` | Gensim LDA with stemming and lemmatisation, tuned over topic count |
| `top2vec.ipynb` | Top2Vec on the full corpus, then separately on high and low fidelity subsets |
| `BERTopic.ipynb` | BERTopic with topic search, frequency analysis, and interactive visualisations |
| `demo_class_model.ipynb` | DistilBERT fine-tuned to classify fidelity level |

## Data

Peer-support message data is not included. The notebooks expect a CSV at
`data/data.csv` with a `Phrase` column and a `FidelityLevel` label.

## Stack

`gensim`, `top2vec`, `bertopic`, `transformers`, `scikit-learn`.
