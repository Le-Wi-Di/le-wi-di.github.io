# Task 11 @Semeval2023: Learning With Disagreement - second Edition (Le-Wi-Di 2)

## Table of Contents
- [Datasets description](#datasets-description)
- [MD-Agreement dataset](#md-agreement-dataset)
- [ConvAbuse dataset](#convabuse-dataset)
- [HS-Brexit dataset](#hs-brexit-dataset)
- [ArMIS dataset](#armis-dataset)
- [References](#references)

## Datasets description

The Le-Wi-Di dataset is a dataset composed by 4 existing different datasets (MD-Agreement dataset, ConvAbuse dataset, HS-Brexit dataset and ArMIS dataset, see below more info about each dataset) that have been harmonized in their format. We developed an harmonized json format, a format that emphasize common features of the datasets, while maintaining their diversities. 
Each entry of each dataset presents several key-fields that are common between datasets and a field "other info" where the information that is dataset-specific is contained.
The field in common to all datasets are:

"text": 
	The text evaluated. A tweet for the MD-Agreement, HS-Brexit and ArMIS datasets, while for ConvAbuse dataset it contains a conversation. See specific description for each specific dataset below.
"annotators": 
	The anonymized reference to the annotators that annotated the specific item, in a comma separated format. To note that within each dataset, annotators have been assigned an identifier starting from 1 (Ann1, Ann2 etc.). While within each dataset the same annotator ID refer to the same annotator, no annotators are in common between different datasets. 
"annotations": 
	It contains the crowd-disaggregated annotations given by each annotator from field annotators. Binary values[0,1], except ConvAbuse that contains "Abuse Severity" with values [-3,-2,-1, 0, 1]. The annotations are comma separated. 
	Note that the order of annotations is the same as the order of the field "annotators", meaning the annotation in the first position is given from the first annotators in the annotators field and so on.
"number of annotations": 
	Number of crowd-labels collected for each item (see below dataset-specific details)
"annotation task":
	The annotation task of the specific dataset (see below for ddataset-specific etails)	
"hard_label": 
	[0,1] Binary label assigned accordingly to the majority of annotations received. 
"soft_label""0" / "soft_label""1":
	Probability of the item of being 0 or 1. These are float numbers beetween 0 and 1 and their sum is always one. These are raw probabilites calculated as the relative proportion of annotations received from crowd for 0/1 respectively.
"lang": 
	The language of the datasets (English, exception for ArMIS that is Arabic).
"split": 
	If the item belongs to the train, validation or test set for the current Le-Wi-Di task
"other_info": 
	Contains the information that is dataset-specific and differs from dataset to dataset (see below). Participants can leverage on this dataset-specific information to improve performance for a specific dataset.

---

## MD-Agreement dataset

The "MultiDomain Agreement" dataset (Leonardelli et al. 2021) is a dataset of around 10k English tweets from three domains (BLM, Election, Covid-19). Each tweet is annotated for offensiveness by 5 annotators via AMT. Particular focus was put on pre-selecting tweets to be annotated that are potentially leading to disagreement. Indeed, almost 1/3 of the dataset has then been annotated with a 2 vs 3 annotators disagreement, and another third of the dataset has an agreement of 1 vs 4.

### Description of the specific json fields:

"text": a tweet in English  
"annotation task": offensiveness detection. You can find more details about the exact guidelines to annotators in Leonardelli et al. 2021  
"annotators": the anonymized reference to the annotators that annotated the specific item. ( >800 different annotators, via AMT)  
"annotations": [0, 1]. It contains the disaggregated annotations from the crowd-annotators that annotatated this item.  
"number of annotations": in this dataset it's always 5.  
"lang": English  
"hard_label": 1 = offensive,  0 = not offensive. Assigned accordingly to the majority of annotations received in "annotations"  
"soft_label""0": [0-1] Probability of label "0". The proportion of annotators that assigned 0 to the item.  
"soft_label""1": [0-1] Probability of label "1". The proportion of annotators that assigned 1 to the item.  
"split": train/test/dev. Note that in this task, with respect to Leonardelli et al. 2021, the test split is the same. You can thus confront your results  with the results in the paper. On the contrary, dev and train split have been changed with respect to the divisions used in Leonardelli et al. 2021. (in the paper, only a subsample of the dataset was used for the experiments)  
"other_info"  
	"Domain": BLM, Elections2020, Covid-19

---

## ConvAbuse dataset

The "ConvAbuse" dataset (Cercas Curry et al., 2021) is a dataset of around 4,000 English dialogues conducted between users and two conversational agents. 
The user utterances have been annotated by experts in gender studies using a hierarchical labelling scheme (following categories: Abuse binary, Abuse severity; Directedness; Target; Type).

### Description of the json fields for this dataset:

"text": conversation between a user and a conversational agent. 
	It always contains the fields: 
		"prev_agent": the conversational agent's previous utterance
		"prev_user": the user's previous utterance
		"agent": the conversational agent's last utterance
		"user": the target user utterance
	Note that the "text" field is a string. It's possible to transform it into a json (with the field "prev_agent" etc.) using json.dumps("text"). 
"annotation task": abusive language detection. You can find more details about the exact guidelines to annotators in Cercas Curry et al., 2021
"annotations": It contains the disaggregated annotations from the crowd-annotators. Comma-separated, range [-3,-2,-1, 0, 1]. From -3 to -1 is considered abusive, while 0 to 1 is not abusive.
"annotators": annotators' ids. 8 annotators have partecipated in the annotation of this dataset.
"number of annotations": varies across items (min 3)
"lang": English
"hard_label": [0,1] 1 = abusive,  0 = not abusive. Assigned accordingly to the majority of annotations received. Note that, sometimes no majority existed. In this case, label has been assigned randomly (few cases). 
"soft_label""0": [0-1] Probability of label "0". The proportion of annotators that considered the item abusive (0 or 1 in the field annotators) 
"soft_label""1": [0-1] Probability of label "0". The proportion of annotators that considered the item abusive (-3 or -2 or -1 in the field annotators)
"split": train/test/dev. Split to which the item belong in Le-Wi-Di task.
"other_info":
	"bot": the conversational agent's name
	"conversation_id(s)": the snippet is part of an other conversation. The same snippet might be shared among more than one conversation
	"other_annotations": 
		"ableist": ablist abuse
		"homophobic": homophobic abuse
		"intellectual": intellect-based abuse
		"racist": racist abus
		"sexist": sexist abuse
		"sex_harassment": sexual harassment
		"transphobic": transphobic abuse
		"target.generalised": target is general
		"target.individual": target is an individual
		"target.system": target is the conversational system
		"explicit": abuse is explicit
		"implicit": abuse is implicit

---

## HS-Brexit dataset

The "HS-Brexit" dataset (Ahktar et al., 2021) is an entirely new dataset of tweets on Abusive Language on Brexit and annotated for hate speech (HS), aggressiveness and offensiveness.
The dataset has been annotated by six annotators belonging to two distinct groups: a target group of three Muslim immigrants in the UK, and a control group of three other individuals.

### Description of the json fields for this dataset:

"text": an English tweet
"annotation task": hate speech detection
"number of annotations": in this dataset is always 6
"annotations": It contains the disaggregated annotations from the crowd-annotators (comma separted, binary [0,1])
"annotators": "Ann1,Ann2,Ann3,Ann4,Ann5,Ann6" 
"lang": English
"hard_label": [0,1].  0 = no HS, 1 = HS. Assigned accordingly to the majority of annotations received in "annotations". In case of no majority existance, this label has been assigned randomly (few cases). 
"soft_label""0": [0-1] Probability of "0". Probability of label "0". The proportion of annotators that assigned 0 to the item.
"soft_label""1": [0-1] Probability of "1". Probability of label "0". The proportion of annotators that assigned 1 to the item.
"split": train/test/dev. Split to which the item belong in Le-Wi-Di task.
"other_info":
	"Annotators_group": "group1,group1,group1,group2,group2,group2". Group to which annotators belong.
	"group1" : target group
	"group2" : control group
	"other annotations":
    	"aggressive language detection": same annotators annotations for aggressiveness. 0 = not aggressive, 1 = aggressive
    	"offensive language detection":  same annotators annotations for offensiveness. 0 = offensiveness, 1 = offensiveness

---

## ArMIS dataset

The "ArMIS" dataset (Almanea et al., 2022) is a dataset of Arabic tweets annotated for misogyny and sexism detection by annotators with different demographics characteristics ("Moderate Female", "Liberal Female" and "Conservative Male"). 

### Description of the json fields for this dataset:

"text": a tweet in Arabic
"annotation task": Misogyny and sexism detection in Arabic tweets 
"number of annotations": in this dataset always 3 
"annotations": It contains the disaggregated annotations from the crowd-annotators (comma separted, binary [0,1])
"annotators": Ann1,Ann2,Ann3 
"lang": Arabic (the entire dataset)
"hard_label": [0,1].  0 = not misogynistic/sexist, 1 = misogynistic/sexist. 
"soft_label""0": [0-1] Probability of "0". Probability of label "0". The proportion of annotators that assigned 0 to the item.
"soft_label""1": [0-1] Probability of "1". Probability of label "0". The proportion of annotators that assigned 0 to the item.
"split": train/test/dev. Split to which the item belong in Le-Wi-Di task.
"other_info":
            "Annotators group": "Mod_Female , Lib_Female , Cons_Male" 

---

## References

Akhtar, S., Basile, V., & Patti, V. (2021). Whose opinions matter? perspective-aware models to identify opinions of hate speech victims in abusive language detection. arXiv preprint arXiv:2106.15896.  
Almanea, D., & Poesio, M. ArMIS-The Arabic Misogyny and Sexism Corpus with Annotator Subjective Disagreements.  
Leonardelli, E., Menini, S., Aprosio, A. P., Guerini, M., & Tonelli, S. (2021). Agreeing to Disagree: Annotating Offensive Language Datasets with Annotators' Disagreement. arXiv preprint arXiv:2109.13563.  
Curry, A. C., Abercrombie, G., & Rieser, V. (2021). ConvAbuse: Data, analysis, and benchmarks for nuanced abuse detection in conversational AI. arXiv preprint arXiv:2109.09483.
