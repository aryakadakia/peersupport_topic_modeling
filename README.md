# Measuring fidelity in digital peer support

Natural language processing applied to digital peer support sessions, with the
goal of assessing fidelity at scale.

Adults with serious mental illness are disproportionately affected by chronic
health conditions linked to inadequately managed medical and psychiatric illness.
Peer specialists, who are certified individuals offering emotional, social and
practical support from shared lived experience, improve illness management and
community rehabilitation. Delivery has increasingly moved to digital platforms.

The problem this addresses is one of scale. Fidelity monitoring conventionally
requires audio recording every interaction and having a trained rater assess it,
which does not scale to the volume of digital delivery. No validated measure of
peer support fidelity existed.

The approach here is to build a corpus from digital peer support sessions,
identify the components of a session, define what separates high from low
fidelity, then train a classifier to detect evidence-based techniques in sessions
it has not seen. The stated hypothesis was that a binary classifier could reach
70 percent accuracy.

## Publication

Kadakia, A., Preum, S. M., Bohm, A. R., & Fortuna, K. L. (2023). Investigating
the Fidelity of Digital Peer Support: A Preliminary Approach using Natural
Language Processing to Scale High-Fidelity Digital Peer Support. *Proceedings of
the 16th International Joint Conference on Biomedical Engineering Systems and
Technologies (BIOSTEC) - Scale-IT-up*, 2023, 581-592.

- DOI: [10.5220/0011776500003414](https://doi.org/10.5220/0011776500003414)
- PubMed: [PMID 39280019](https://pubmed.ncbi.nlm.nih.gov/39280019/)
- Free full text: [PMC11398714](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC11398714/)

Work carried out at the BRiTE Center, Department of Psychiatry and Behavioral
Sciences, University of Washington, with co-authors at Dartmouth College.

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
