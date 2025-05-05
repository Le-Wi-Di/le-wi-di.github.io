# 👩‍🔬🧑‍💻💆‍♂️ Practice Phase Data

This repository contains four datasets for the LeWiDi shared task third edition. 
Each dataset includes annotated examples with soft labels generated from multiple annotators and annototators metadata.
Despite their differing objectives, they share a homogenous json format, which is documented below. 


More information is available at [Codabench Competition Page](https://www.codabench.org/competitions/7192).  
See also the [LEWIDI Project Website](https://le-wi-di.github.io/).

## Datasets Included

🟡 **CSC (Conversational Sarcasm Corpus)** – A dataset of context + response pairs labeled for sarcasm on a scale from 1 to 6.
 
🟢 **MP (MultiPico)** – A crowdsourced multilingual irony detection dataset. Annotators were asked to detect whether a reply was ironic, given a short post–reply exchange on social media. Annotator IDs and metadata (e.g., gender, age, nationality) are available. Languages include Arabic, German, English, Spanish, French, Hindi, Italian, Dutch, and Portuguese.

🟣 **Paraphrase (Par)** – A dataset of question pairs where annotators rated how paraphrastic the two questions were, using a Likert scale from –5 to +5.

🔵 **VariErrNLI** – A natural language inference dataset developed to distinguish true disagreement from annotation errors. Annotators provide both labels and free-text explanations.


### ⚠️ Each dataset includes annotated examples with **soft labels** generated from multiple annotators and corresponding annotator metadata.  
Despite differing objectives, all datasets share a **homogeneous JSON format**, documented below.

---

## 📂 Dataset Files

Each dataset is organized into:

- `<Dataset>_train.json` – Training data  
- `<Dataset>_dev.json` – Development/validation data  
- `<Dataset>_annotators_meta.json` – Annotator demographic metadata

---


## 📄 Common JSON Format

Each entry in the JSON files follows this general structure:

| Field                   | Description |
|-------------------------|-------------|
| `annotation task`       | Task type (e.g., `"sarcasm detection"`, `"irony detection"`, `"paraphrase detection"`, `"natural language inference"`) |
| `text`                  | Text input shown to annotators (contains task-specific subfields) |
| `number of annotators`  | Total number of annotators |
| `annotators`            | Comma-separated list of annotator IDs (e.g., `"Ann1,Ann2"`) |
| `number of annotations` | Total number of annotations (can differ from annotators in some tasks like VariErrNLI) |
| `annotations`           | Labels assigned by annotators (`{"Ann1": label, "Ann2": label}`) |
| `soft_label`            | Final soft label distribution |
| `split`                 | Dataset split (`train`, `dev`, or `test`) |
| `lang`                  | Language code (e.g., `"en"`) |
| `other_info`            | Task- or dataset-specific metadata |

---

## 📄 Dataset-Specific Fields

| Dataset     | `text` Fields                                                                 | `other_info` Fields |
|-------------|-------------------------------------------------------------------------------|---------------------|
| **CSC**     | `context`: scenario before the response<br>`response`: speaker's reply        | `context+speaker`: combined context and speaker ID |
| **MP**      | `post`: social media post<br>`reply`: response to the post                    | `source`: platform (e.g., `twitter`)<br>`level`: reply depth<br>`language_variety`: e.g., `us`, `gb`, `au` |
| **Par**     | `Question1` and `Question2`: the two questions being compared                 | `explanations`: annotator rationales |
| **VariErrNLI** | `context`: premise<br>`statement`: hypothesis                             | `explanations`: annotator rationales |

---

## 👤 Annotator Metadata

Stored in `<Dataset>_annotators_meta.json`:

| Field                  | Description | Datasets |
|------------------------|-------------|----------|
| `Annotator_id`         | Unique ID, e.g., `"Ann12"` | All datasets |
| `Age`                  | Age at time of annotation | All datasets |
| `Gender`               | Self-identified gender | All datasets |
| `Nationality`          | Annotator’s nationality | MP, Par, VariErrNLI |
| `Education`            | Highest education level | Par, VariErrNLI |
| `Ethnicity simplified` | e.g., Asian, Black, White, Mixed, Other | MP |
| `Country of birth`     | Birth country | MP |
| `Country of residence` | Current residence | MP |
| `Student status`       | Whether the annotator is a student | MP |
| `Employment status`    | Employment status (e.g., Full-Time, Part-Time, Unemployed) | MP |

---

## 🧪 Example Entries

### CSC

```json
{
  "annotation task": "sarcasm detection",
  "text": {
    "context": "You were watching Steve's new puppy...",
    "response": "okay, very cute if a little messy!"
  },
  "number of annotators": 6,
  "annotators": "Ann288,Ann289,Ann290,Ann291,Ann292,Ann293",
  "number of annotations": 6,
  "annotations": {
    "Ann288": "2", "Ann289": "5", "Ann290": "3", "Ann291": "3", "Ann292": "2", "Ann293": "6"
  },
  "soft_label": {
    "0": 0.0, "1": 0.0, "2": 0.33, "3": 0.33, "4": 0.0, "5": 0.17, "6": 0.17
  },
  "split": "dev",
  "lang": "en",
  "other_info": {
    "context+speaker": "121_1049"
  }
}
```


### MP

```json
{
  "annotation task": "irony detection",
  "text": {
    "post": "Last Saturday night was homecoming...",
    "reply": "@USER Oh no!!"
  },
  "annotators": "Ann0,Ann10,Ann16",
  "number of annotations": 3,
  "annotations": {
    "Ann0": "0", "Ann10": "0", "Ann16": "0"
  },
  "soft_label": {
    "0.0": 1.0,
    "1.0": 0
  },
  "split": "train",
  "lang": "en",
  "other_info": {
    "source": "twitter",
    "level": 1.0,
    "language_variety": "us"
  }
}
```

### Par

```json
{
        "annotation task": "paraphrase detection",
        "text": {
            "Question1": "What are the chances for a high-school student who didn't do any extracurricular activities until his last year to get accepted to a top US school?",
            "Question2": "Is a student who sucked in High School but ended up being a top PhD student in a top school a misunderstood genius?"
        },
        "number of annotators": 4,
        "annotators": "Ann1,Ann2,Ann3,Ann4",
        "number of annotations": 4,
        "annotations": {
            "Ann1": "-3",
            "Ann2": "-4",
            "Ann3": "0",
            "Ann4": "-4"
        },
        "soft_label": {
            "-5": 0.0,
            "-4": 0.5,
            "-3": 0.25,
            "-2": 0.0,
            "-1": 0.0,
            "0": 0.25,
            "1": 0.0,
            "2": 0.0,
            "3": 0.0,
            "4": 0.0,
            "5": 0.0
        },
        "split": "train",
        "lang": "en",
        "other_info": {
            "explanations": [
                "Q1 asks about the chances of less well-performing student being accepted to top Uni, whereas Q2 asks about if a kind of students can be a misunderstood genius",
                " different topics",
                "term overlap \"top school\", Q1 specifies named entity \"US\", Q2: \"high school\". They refer to different concepts. ",
                "The main sense of the two sentences is different."
            ]
        }
    }
```


### VariErrNLI

```json
{
        "annotation task": "natural language inference",
        "text": {
            "context": "Part of the reason for the difference in pieces per possible delivery may be due to the fact that five percent of possible residential deliveries are businesses, and it is thought, but not known, that a lesser percentage of possible deliveries on rural routes are businesses.",
            "statement": "It is thought, but not known, that a lesser percentage of possible deliveries on rural routes are businesses, and part of the reason for the difference in pieces per possible delivery, may be due to the fact that five percent of possible residential deliveries are businesses."
        },
        "number of annotators": 2,
        "annotators": "Ann1,Ann3",
        "number of annotations": 2,
        "annotations": {
            "Ann1": "contradiction",
            "Ann3": "entailment"
        },
        "soft_label": {
            "contradiction": {
                "0": 0.5,
                "1": 0.5
            },
            "entailment": {
                "0": 0.5,
                "1": 0.5
            },
            "neutral": {
                "0": 1.0,
                "1": 0.0
            }
        },
        "split": "train",
        "lang": "en",
        "other_info": {
            "explanations": [
                "The reason for the diffenrence in pieces per possible delivery mentioned in the context is that the difference percentage of businesses deliveries on residential and rural routes. But the reason in the statement only include the percentage of residential deliveries, not the diffenrence of deliveries.",
                "Statement just changed the order of two hypothesis in the context."
            ]
        }
    }
```
