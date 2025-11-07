
This repository contains four datasets for the LeWiDi shared task third edition. 
Each dataset includes annotated examples with soft labels generated from multiple annotators and annotators metadata.
Despite their differing objectives, they share a homogenous json format, which is documented below. 
More information is available at Codabench Competition Page: https://www.codabench.org/competitions/7192
See also the LEWIDI Project Website:https://le-wi-di.github.io/

Datasets Included

🟡 CSC (Conversational Sarcasm Corpus) – A dataset of context + response pairs labeled for sarcasm on a scale from 1 to 6. 
(i)(Jang & Frassinelli, NAACL 2024)

🟢 MP (MultiPico) – A crowdsourced multilingual irony detection dataset. Annotators were asked to detect whether a reply was ironic, given a short post–reply exchange on social media. Annotator IDs and metadata (e.g., gender, age, nationality) are available. Languages include Arabic, German, English, Spanish, French, Hindi, Italian, Dutch, and Portuguese.
Reference:
(ii)(Casola et al, ACL 2024 )

🟣 Paraphrase (Par) – A dataset of question pairs where annotators rated how paraphrastic the two questions were, using a Likert scale from –5 to +5.
unpublished - curated by https://mainlp.github.io/

🔵 VariErrNLI – A natural language inference dataset developed to distinguish true disagreement from annotation errors. Annotators provide both labels and free-text explanations.
Reference: 
(iii)(Weber-Genzel et al, ACL 2024)

⚠️ Each dataset includes annotated examples with soft labels generated from multiple annotators and corresponding annotator metadata.  
Despite differing objectives, all datasets share a homogeneous JSON format, documented below.


📂 Dataset Files

Each dataset is organized into:
- `<Dataset>_train.json` – Training data  
- `<Dataset>_dev.json` – Development/validation data  
- `<Dataset>_test.json` – Test data 
- `<Dataset>_annotators_meta.json` – Annotator demographic metadata

---


📄 Common JSON Format

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

📄 Dataset-Specific Fields

| Dataset     | `text` Fields                                                                 | `other_info` Fields |
|-------------|-------------------------------------------------------------------------------|---------------------|
| CSC     | `context`: scenario before the response<br>`response`: speaker's reply        | `context+speaker`: combined context and speaker ID |
| MP      | `post`: social media post<br>`reply`: response to the post                    | `source`: platform (e.g., `twitter`)<br>`level`: reply depth<br>`language_variety`: e.g., `us`, `gb`, `au` |
| Par     | `Question1` and `Question2`: the two questions being compared                 | `explanations`: annotator rationales |
| VariErrNLI | `context`: premise<br>`statement`: hypothesis                             | `explanations`: annotator rationales |

---

👤 Annotator Metadata

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



References:
(i) Hyewon Jang and Diego Frassinelli. 2024. Generalizable Sarcasm Detection is Just Around the Corner, of Course!. In Proceedings of the 2024 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies (Volume 1: Long Papers), pages 4238–4249, Mexico City, Mexico. Association for Computational Linguistics.
(ii)Silvia Casola, Simona Frenda, Soda Marem Lo, Erhan Sezerer, Antonio Uva, Valerio Basile, Cristina Bosco, Alessandro Pedrani, Chiara Rubagotti, Viviana Patti, and Davide Bernardi. 2024. MultiPICo: Multilingual Perspectivist Irony Corpus. In Proceedings of the 62nd Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), pages 16008–16021, Bangkok, Thailand. Association for Computational Linguistics.
(iii)Leon Weber-Genzel, Siyao Peng, Marie-Catherine De Marneffe, and Barbara Plank. 2024. VariErr NLI: Separating Annotation Error from Human Label Variation. In Proceedings of the 62nd Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), pages 2256–2269, Bangkok, Thailand. Association for Computational Linguistics.
