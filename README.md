# Measuring fidelity in digital peer support

Natural language processing applied to digital peer support sessions, with the
goal of assessing fidelity at scale.

Peer support improves recovery outcomes including reduced hospitalisation and
fewer anxiety and depression symptoms, and digital delivery has been shown to be
feasible and acceptable. What has been missing is any validated way to assess
whether a given session is actually delivered well. Fidelity assessment normally
depends on a trained rater listening to sessions, which does not scale to the
volume of digital delivery.

This work approaches that gap in three steps: identify the components of a peer
support session, define what distinguishes high from low fidelity, then train a
classifier to detect those indicators in sessions it has not seen.

## Publication

Kadakia, A., Preum, S., Bohm, A., Fortuna, K. (2023). Investigating the Fidelity
of Digital Peer Support: A Preliminary Approach using Natural Language Processing
to Scale High-Fidelity Digital Peer Support. *Proceedings of the 16th
International Joint Conference on Biomedical Engineering Systems and
Technologies - Scale-IT-up*, 581-592.
[10.5220/0011776500003414](https://doi.org/10.5220/0011776500003414)

`AryaKPoster.pdf` is the accompanying conference poster. The work began as an
Honors Psychology thesis supervised by Karen Fortuna and Luke Chang.

## Contents

### Identifying session components

Three topic modelling approaches, run on the same corpus so the methods can be
compared rather than assumed equivalent. LDA treats documents as mixtures over
word distributions. Top2Vec and BERTopic both work in embedding space instead,
clustering semantically and deriving topic terms afterwards.

| File | Method |
|---|---|
| `LDA_all_data.ipynb` | Gensim LDA with stemming and lemmatisation |
| `top2vec.ipynb` | Top2Vec on the full corpus, then separately on high and low fidelity subsets |
| `BERTopic.ipynb` | BERTopic with topic search, frequency analysis and interactive visualisation |

Running Top2Vec separately across fidelity levels is the part that speaks to the
research question, since it shows whether high and low fidelity sessions are
characterised by different topics rather than only different amounts of the same
ones.

### Fidelity classification

`demo_class_model.ipynb` fine-tunes DistilBERT to classify phrases by fidelity
level, which is the classifier the thesis set out to build.

## Data

Peer support session data is not included. It is identifiable clinical research
data and cannot be released. The notebooks expect a CSV at `data/data.csv` with a
`Phrase` column and a `FidelityLevel` label.

## Stack

`gensim`, `top2vec`, `bertopic`, `transformers`, `scikit-learn`.
