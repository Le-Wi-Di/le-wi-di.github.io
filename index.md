
---
layout: default
title: LeWiDi 2025 - 3rd edition
---
[LeWiDi 2023 - 2nd edition](/LeWiDi2023/) | [LeWiDi 2021 - 1st edition](https://sites.google.com/view/semeval2021-task12) 

### 👍👎 Updates 
# LeWiDi third Edition @[NLPerspectives Workshop](https://nlperspectives.di.unito.it/) is online! Please check [our new competition page ](https://www.codabench.org/competitions/7192/) for data and more information! 👍👍



### 👍👎 Overview
The third edition of Learning with Disagreements (LeWiDi) is co-located with the [NLPerspectives](https://nlperspectives.di.unito.it/) workshop at [EMNLP 2025](https://2025.emnlp.org/). 
The Shared Task aims to highlight the challenges posed by interpretative variation and to encourage the research community to engage with this issue. The main goal of the shared task is to provide a unified testing framework for learning from disagreements and evaluating models on such datasets.

The two previous editions of the shared task were organized as part of SEMEVAL: the first edition, (in 2021, [Uma et al.](https://aclanthology.org/2021.semeval-1.41/)) focused on ambiguity in language and vision, while the second edition (in 2023, [Leonardelli et al.](https://aclanthology.org/2023.semeval-1.314/)) concentrated on disagreement in subjective tasks.

This new edition will be co-located with the NLPerspectives workshop at EMNLP 2025 conference, and will differ from the previous ones in a number of respects:

- It will include new tasks not included in previous editions, such as NLI detection, irony detection and conversational sarcasm detection;
- We will not use hard evaluation anymore -- but we will test two approaches to soft evaluation. The first is a version of the soft labeling approach used in LeWiDi 1 and 2, but using Manhattan distance instead of cross-entropy, as a result of the post-LeWiDi 2 analysis discussed in ([Rizzi et al, 2024](https://aclanthology.org/2024.nlperspectives-1.9.pdf)). The second is a form of perspectivist evaluation--instead of evaluating a model's ability to predict the distribution of labels over the population, we will test a system's ability to predict an annotator's bias.
- We will include two datasets in which values are on a Likert scale, raising further issues regarding evaluation with disagreement.

### 👍👎 The datasets

#### Conversational Sarcasm Corpus (CSC)
The CSC is a dataset of sarcasm that provides ~7,000 context+response pairs, sarcasm ratings from 1 to 6 both by the response generators (speakers), and by multiple external observers per pair (6 in part1, 4 in part2). It is the result of multiple online experiments, in which the first batch of participants (speakers, generators) responded to given contexts (situation descriptions involving an imaginary interlocutor), and provided sarcasm ratings to their own responses from 1 (not at all) to 6 (completely). In the subsequent experiments, a new batch of participants (observers, evaluators) provided sarcasm ratings to the speakers' responses from 1 to 6. Multiple observers evaluated each context+response pair (each row in the dataset), where 6 observers evaluated the same row for part1, and 4 observers for part2.

The paper describing the dataset is available [here](https://aclanthology.org/2024.naacl-long.238/).

#### MultiPico dataset (MP)
The MP dataset is a multilingual perspectivist corpus consisting of short exchanges from Twitter and Reddit. Each entry in the corpus represents a post-reply pair. Crowdsourced workers had to determine whether the reply was ironic given the post (binary label). The corpus includes 11 languages: Arabic, Dutch, English, French, German, Hindi, Italian, Portuguese, and Spanish. It also contains sociodemographic information about the annotators, including gender, age, nationality, race, and student or employment status. While the statistics may vary slightly across languages, each post-reply pair is typically annotated by an average of 5 workers.

The paper describing the dataset is available [here](https://aclanthology.org/2024.acl-long.849.pdf).

#### Paraphrase Detection dataset (Par)
The Par dataset is a dataset structurally similar to VariErrNLI. Four annotators independently annotated 500 question pairs from the Quora Question Pairs (QQP) dataset, assigning a Likert scale score from -5 to 5 to indicate how strongly the questions are paraphrases of one another. Each annotator also provided a short explanation for their score. Unlike VariErr NLI, this dataset uses scalar labels and limits each annotator to a single score per item.

Maintained by the [MaiNLP lab](https://mainlp.github.io/) (not yet published).

#### VariErr NLI dataset (VariErrNLI)
VariErrNLI was created designed for automatic error detection, distinguishing between annotation errors and legitimate human label variations in Natural Language Inference (NLI) tasks. The dataset was created using a two-round annotation process: initially, annotators provided labels and explanations for each NLI item; subsequently, they assessed the validity of each label-explanation pair. 
It comprises 1,933 explanations for 500 re-annotated items from the Multi-Genre Natural Language Inference (MNLI) corpus for Round 1 and 7,732 validity judgments for Round 2. 
The LeWiDi 2025 Shared Task focuses on Round 1, annotators could assign one or more labels from {Entailment, Neutral, Contradiction} to each (Premise, Hypothesis) pair and provide corresponding explanations.

The paper describing the dataset is available [here](https://aclanthology.org/2024.acl-long.123/).


### 👍👎 Tasks and Evaluation

Only soft evaluation metrics will be used:

- **TASK A (SOFT LABEL PREDICTION):** Systems must output a probability distribution over labels.  
  **Evaluation:** Manhattan distance from the soft label distribution from annotators.
  
- **TASK B (PERSPECTIVIST PREDICTION):** Systems must predict individual annotators' labels.  
  **Evaluation:** Measures correctness of predictions per annotator.

Submissions can target one or both tasks. Participants may submit to one or multiple datasets.


### 👍👎 Output of the shared task

Participants can submit a system paper to the 4th Workshop on Perspectivist Approaches to NLP. These peer-reviewed papers will be published in the workshop proceedings.
