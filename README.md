# 🧠 Practice Phase Datasets

This repository contains four datasets for the LeWiDi shared task third edition. 
Each dataset includes annotated examples with soft labels generated from multiple annotators and annototators metadata.
Despite their differing objectives, they share a homogenous json format, which is documented below. 


More information is available at [Codabench Competition Page](https://www.codabench.org/competitions/7192).  
See also the [LEWIDI Project Website](https://le-wi-di.github.io/).

## 📦 Datasets Included

- 🟡 **CSC (Conversational Sarcasm Corpus)** – A dataset of context + response pairs labeled for sarcasm on a scale from 1 to 6.
 
- 🟢 **MP (MultiPico)** – A crowdsourced multilingual irony detection dataset. Annotators were asked to detect whether a reply was ironic, given a short post–reply exchange on social media. Annotator IDs and metadata (e.g., gender, age, nationality) are available. Languages include Arabic, German, English, Spanish, French, Hindi, Italian, Dutch, and Portuguese.

- 🟣 **Paraphrase (Par)** – A dataset of question pairs where annotators rated how paraphrastic the two questions were, using a Likert scale from –5 to +5.

- 🔵 **VariErrNLI** – A natural language inference dataset developed to distinguish true disagreement from annotation errors. Annotators provide both labels and free-text explanations.



---

## 📁 File Structure

Each dataset is organized into:

- `<Dataset>_train.json` – Training set  
- `<Dataset>_dev.json` – Development/validation set  
- `<Dataset>_annotators_meta.json` – Metadata about annotators 

---
## 📝 Common JSON Format

Each JSON file contains a list of examples. Below are the fields shared across datasets:

| Field | Description |
|-------|-------------|
| `annotation task` | Short description of the annotation task (i.e., `"sarcasm detection"`, `"irony detection"` , `"paraphrase detection"`, `"natural language inference"`). |
| `text` | A dictionary with task-specific text. The structure varies by dataset:<ul><li>**MP**: `post`, `reply`</li><li>**CSC**: `context`, `response`</li><li>**VariErrNLI**: `context`, `statement`</li><li>**Paraphrase**: `Question1`, `Question2`</li></ul> |
| `annotators` | A comma-separated list of annotator IDs. Example: `"Ann1,Ann2,Ann3"`. |
| `number of annotations` | Total number of annotations for the example. |
| `annotations` | A dictionary mapping annotator IDs to their individual labels (e.g., `"Ann1": "0"` or `"Ann1": "entailment"`). |
| `soft_label` | A distribution of labels across annotators, representing label agreement. Format may vary slightly by task. |
| `split` | Dataset split: `"train"` or `"dev"`. |
| `lang` | Language code, e.g., `"en"` for English. |
| `other_info` | A dictionary with additional metadata such as source, speaker, or free-text explanations. This field is task-dependent. |



## 🔍 Example Entry

```json
{
  "annotation task": "paraphrase detection",
  "text": {
    "Question1": "What are the chances for a high-school student...",
    "Question2": "Is a student who sucked in High School..."
  },
  "annotators": "Ann1,Ann2,Ann3,Ann4",
  "number of annotations": 4,
  "annotations": {
    "Ann1": "-3",
    "Ann2": "-4",
    "Ann3": "0",
    "Ann4": "-4"
  },
  "soft_label": {
    "-4": 0.5,
    "-3": 0.25,
    "0": 0.25
  },
  "split": "train",
  "lang": "en",
  "other_info": {
    "explanations": ["different topics", "term overlap 'top school'..."]
  }
}
```
---

## 🎯 Dataset-Specific Fields

While the datasets share a common structure, some fields in the `text` and `other_info` objects are specific to the task and dataset. Below is a breakdown of these fields:

### 🟢 MP 

- **`text`**
  - `post`: 
  - `reply`: 
- **`other_info`**
  - `source`: Source platform (e.g., `"twitter"`).
  - `level`:  
  - `language_variety`: Language variant (e.g., `"us"`).

---

### 🟡 CSC 

- **`text`**
  - `context`:
  - `response`: 
- **`other_info`**
  - `context+speaker`:

---

### 🔵 VariErrNLI 

- **`text`**
  - `context`: Premise or supporting statement.
  - `statement`: Hypothesis to be compared with the context.
- **`other_info`**
  - `explanations`: Annotator-provided rationales for their labels.

*Note*: `soft_label` includes nested distributions per class (e.g., `"entailment"`, `"neutral"`, `"contradiction"`), representing class agreement across annotators.

---

### 🟣 Par

- **`text`**
  - `Question1`: The first question or statement.
  - `Question2`: The second question to compare.
- **`other_info`**
  - `explanations`: Annotator rationales for (non-)paraphrase judgments.



## 👤 Annotator Metadata

Datasets include an `*_annotators_meta.json` file containing demographic and background information about annotators. 

| Field             | Description                                                                                       | Datasets                        |
|------------------|---------------------------------------------------------------------------------------------------|---------------------------------|
| `Annotator_id`    | A unique identifier for each annotator (e.g., `"Ann12"`). Matches IDs used in main dataset files. | All datasets                    |
| `Age`             | Age|All datasets                    |
| `Gender`          | Self-identified gender | All datasets                    |
| `Nationality`     | Annotator's country or region of origin (e.g., `"Italy"`, `"India"`).                             | MP, Par, VariErrNLI |
| `Education`       | Highest completed education level.                                                                | VariErrNLI, Par |
| `Ethnicity simplified` | Self-reported simplified ethnicity category.                                                       | MP                              |
| `Country of birth`     | Country where the annotator was born.                                                              | MP                              |
| `Country of residence` | Country where the annotator currently resides.                                                     | MP                              |
| `Student status`       | Whether the annotator is a student                                       | MP                              |
| `Employment status`    | Employment situation  | MP                              |
