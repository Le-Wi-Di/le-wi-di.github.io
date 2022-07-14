## Welcome to Learning with Disagreements 👎👍

Welcome to the page of the task 11 @SemEval2023 on Learning with Disagreements (Le_Wi-DI), 2nd edition 


### Overview


In recent years, the assumption that natural language (NL) expressions have a single and clearly identifiable interpretation in a given context is more and more recognized as just a *convenient idealization*. The objective of the Learning with Disagreement shared task is to provide a unified testing framework for learning from disagreements, using datasets containing information about disagreements for interpreting language. [Learning with Disagreement (Le-Wi-Di) 2021](https://sites.google.com/view/semeval2021-task12)  created a benchmark consisting of 6 existing and widely used datasets, but focusing primarily on semantic ambiguity and image classification. 

For SemEval 2023, we run a second shared task on the topic of Learning with Disagreement: 
(i) the focus is entirely on subjective tasks, where training with aggregated labels makes much less sense, and 
(ii) while relying on the same infrastructure, it will involve new datasets. 
We believe that the shared task thus reformulated is extremely timely, given the current high degree of interest in subjective tasks such as offensive language detection in general, and in particular on the issue of disagreements in such data ([Basile et al., 2021](https://aclanthology.org/2021.bppf-1.3/); [Leonardelli et al., 2021](https://aclanthology.org/2021.emnlp-main.822/); [Akhtar et al., 2021](https://arxiv.org/abs/2106.15896); [Davani et al., 2022](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00449/109286/Dealing-with-Disagreements-Looking-Beyond-the); [Uma et al., 2021](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9012579/)) and we hope it attract substantial interest from the community.


### The Datasets
Our focus is entirely on subjective tasks, where training with aggregated labels makes much less sense. To this end, we collected a benchmark of four (textual) datasets with different characteristics, in terms of genres (social media and conversations), of languages (English and Arabic), of tasks (misogyny, hate-speech, offensiveness detection) and of annotations' methods (experts, specific demographics groups, AMT-crowd). But all datasets providing a multiplicity of labels for each instance. 

The four datasets presented are:
- The **[HS-brexit dataset](https://arxiv.org/abs/2106.15896)**: an entirely new dataset of tweets on Abusive Language on Brexit and annotated for hate speech (HS), aggressiveness and offensiveness by six annotators belonging to two distinct groups: a target group of three Muslim immigrants in the UK, and a control group of three other individuals.
- The **[ArMIS dataset](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9012579/)**: a dataset of Arabic tweets annotated for misogyny detection by annotators with different demographics characteristics ("Moderate Female", "Liberal Female" and "Conservative Male"). This dataset is new.
- The **[ConvAbuse dataset](https://aclanthology.org/2021.emnlp-main.587/)**: a dataset of 4,185 English dialogues conducted between users and two conversational agents. The user utterances have been annotated by at least three experts in gender studies using a heirarchical labelling scheme (following categories: Abuse binary, Abuse severity; Directedness; Target; Type).
- The **[MultiDomain Agreement dataset](https://aclanthology.org/2021.emnlp-main.822/)**: a dataset of around 10k English tweets from three domains (BLM, Election, Covid-19). Each tweet is annotated for offensiveness by 5 annotators via AMT.Particular focus was put on pre-selecting tweets to be annotated that are potentially leading to disagreement. Indeed, almost 1/3 of the dataset has then been annotated with a 2 vs 3 annotators disagreement, and another third of the dataset has an agreement of 1 vs 4.


### Aim of the task and data format
We encourage participants in **developing methods able to capture agreements/disagreements**, rather than focusing on developing the best model. To this end, we developed an **harmonized json** format used to release all datasets. Thus, features that are common to all datasets, are released in a homogenous format, so to facilitate participants in testing their methods across all the datasets.

Among the information released that is common to all datasets, and of particular relevance for the task, are the **disaggregated crowd-annotations labels** and the **annotators' reference**. Moreover, **dataset-specific information** are also released, and vary for each dataset, from demographics of annotators (ArMIS and HS-Brexit datasets), to the other annotations made by the same annotators within the same dataset (all datasets) or additional annotations given for for the same item (HS-Brexit and ConvAbuse datasets) by the same annotator. Participants can leverage on this dataset-specific information to improve perfomance for a specific dataset. 

### The competition
The shared task is hosted on [Codalab](https://codalab.lisn.upsaclay.fr/competitions/6146). Please refer to Codalab platform for more detailed information. 
Note that the competion has not started yet and only a sample of the datasets has been [released](https://codalab.lisn.upsaclay.fr/competitions/6146#learn_the_details-get_starting_kit). The competition will start with the practice phase from 01/09/22. Please **[subscribe to our google group](https://groups.google.com/g/le-wi-di-semeval2023_participants)** to be updated with the news about the task!

### Important Dates
- Sample data ready 15 July 2022
- Training data ready 1 September 2022
- Evaluation start 10 January 2023
- Evaluation end by 31 January 2023 (latest date; task organizers may choose an earlier date)
- System paper submission due February 2023
- Task paper submission due February 2023
- Notification to authors March 2023
- Camera ready due April 2023
- SemEval workshop Summer 2023 (co-located with a major NLP conference)

### Organisers
- [Elisa Leonardelli](https://dh.fbk.eu/author/elisa/), FKB Trento, Italy
- [Gavin Abercrombie](https://gavinabercrombie.github.io/), Heriot Watt University Edinburgh, UK
- [Valerio Basile](https://valeriobasile.github.io/), University of Turin, IT
- [Tommaso Fornaciari](https://fornaciari.netlify.app/), Italian National Policem IT
- [Barbara Plank](https://bplank.github.io/), LMU Munich, DE
- [Massimo Poesio](https://sites.google.com/view/massimo-poesio), Queen Mary University, UK
- [Verena Rieser](https://sites.google.com/site/verenateresarieser/home), Heriot Watt University Edinburgh, UK
- [Alexandra N Uma](https://www.semanticscholar.org/author/Alexandra-Uma/51229008), Connex One, UK

### Communication

Join our [google group](https://groups.google.com/g/le-wi-di-semeval2023_participants). We'll keep you updated with the news about the task.
[Contact us directly](mailto:le-wi-di-semeval2023_contactus@googlegroups.com), if you have further inquiries.
Follow us on [Twitter](https://twitter.com/LeWiDi_Sem2023), for news about learning with disagreements and more!

### Previous Editions 

- [Learning with Disagreement, 2021, 1st edition](https://sites.google.com/view/semeval2021-task12) 

