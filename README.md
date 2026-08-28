# NLP-Based Toxic Comment Detection

## 📌 Project Overview

This project uses **Natural Language Processing (NLP)** techniques to analyze online comments and identify whether they are **Toxic** or **Non-Toxic**.

The project works with a large collection of user comments and applies different NLP preprocessing and linguistic feature extraction techniques to prepare the text for toxicity analysis.

The main objective is to transform raw textual comments into clean and meaningful textual and numerical features that can be used for toxic-comment analysis and future machine-learning classification.

---

## 🎯 Objectives

* Analyze textual comments using NLP techniques.
* Clean and normalize raw comment data.
* Tokenize comments into individual words/tokens.
* Remove common English stop words.
* Apply lemmatization to reduce words to their base forms.
* Extract linguistic features from comments.
* Create a manually annotated sample of toxic and non-toxic comments.
* Compare linguistic characteristics between toxic and non-toxic comments.
* Prepare the processed data for future machine-learning classification.

---

## 📂 Dataset

The project initially loads the dataset from:

```text
train.csv
```

The original dataset contains:

* **159,571 records**
* **8 columns**

The original columns include:

| Column          | Description               |
| --------------- | ------------------------- |
| `id`            | Unique comment identifier |
| `comment_text`  | Text of the comment       |
| `toxic`         | Toxicity label            |
| `severe_toxic`  | Severe toxicity label     |
| `obscene`       | Obscene content label     |
| `threat`        | Threat label              |
| `insult`        | Insult label              |
| `identity_hate` | Identity-hate label       |

## The notebook verifies that there are no missing values and no duplicate rows in the original dataset.

## 🔄 Project Workflow

```text
Raw Comment Dataset
        ↓
Data Loading
        ↓
Data Exploration
        ↓
Data Cleaning
        ↓
Text Normalization
        ↓
Tokenization
        ↓
Stop-word Removal
        ↓
Lemmatization
        ↓
Processed Text
        ↓
Feature Extraction
        ↓
Manual Toxic / Non-Toxic Annotation
        ↓
Feature Comparison
        ↓
Toxic Comment Analysis
```

---

## 🧹 Text Preprocessing

The project performs several preprocessing operations on the comments.

### 1. Lowercasing

All text is converted to lowercase to maintain consistency.

Example:

```text
"THIS IS A COMMENT"
```

becomes:

```text
"this is a comment"
```

### 2. HTML Tag Removal

HTML tags are removed from the comments using regular expressions.

### 3. URL Removal

URLs such as `http://...` and `www...` are removed.

### 4. Newline Removal

Newline and tab characters are converted into spaces.

### 5. Extra Space Removal

Multiple spaces are reduced to a single space.

These cleaning operations are implemented using Python's `re` module and string-processing functions.

---

## 🔤 Tokenization

After cleaning the text, the project uses **NLTK's `word_tokenize()`** to divide each comment into individual tokens.

Example:

```text
"this is a toxic comment"
```

becomes:

```text
["this", "is", "a", "toxic", "comment"]
```

## The notebook creates a `tokens` column containing the tokenized comments.

## 🚫 Stop-word Removal

Common English words that usually provide less useful information for text analysis are removed using the NLTK English stop-word list.

Examples include words such as:

```text
the
is
a
are
was
and
```

The project creates a new column:

```text
tokens_no_stopwords
```

containing tokens after stop-word removal.

---

## 🌱 Lemmatization

The project uses **WordNetLemmatizer** from NLTK.

Lemmatization converts words into their base or dictionary form.

For example:

```text
cars → car
articles → article
photos → photo
```

The notebook creates:

```text
lemmatized_tokens
```

and then combines the processed tokens into:

```text
processed_text
```

## This produces cleaner text that can be used for further NLP analysis.

## 📊 Feature Extraction

The project extracts several linguistic features from the comments.

### Features

* `word_count`
* `character_count`
* `avg_word_length`
* `uppercase_count`
* `uppercase_ratio`
* `exclamation_count`
* `question_count`
* `punctuation_count`

These features provide numerical information about the writing style and structure of each comment.

### Example

A comment containing many uppercase letters and exclamation marks can have higher values for:

```text
uppercase_count
exclamation_count
uppercase_ratio
```

These features can potentially help distinguish different types of comments.

---

## 🏷️ Manual Annotation

To perform detailed analysis, the project selects:

* **100 toxic comments**
* **100 non-toxic comments**

This produces a balanced sample of **200 comments**.

The comments are shuffled and assigned an `annotation_id`. Two additional columns are created:

```text
manual_label
category
```

The annotation dataset is saved as:

```text
toxic_comments_200_annotation.csv
```

---

## 📝 Manual Labels

The manually annotated comments are categorized as:

```text
Toxic
Non-Toxic
```

The notebook also contains category information for toxic content, such as:

* Insult
* Obscene/Profanity

## The annotated dataset contains **200 rows and 11 columns**.

## 📈 Feature Analysis

The project compares linguistic features between manually labelled toxic and non-toxic comments.

For example, the notebook calculates the mean values of the extracted features for each label.

Some observed differences in the annotated sample include:

| Feature             | Non-Toxic Mean | Toxic Mean |
| ------------------- | -------------: | ---------: |
| Word Count          |          73.75 |      60.48 |
| Character Count     |         438.87 |     354.14 |
| Average Word Length |           5.87 |       5.63 |
| Uppercase Count     |          16.61 |      44.09 |
| Uppercase Ratio     |          0.049 |      0.087 |
| Exclamation Count   |           0.38 |       1.81 |
| Question Count      |           0.32 |       0.49 |
| Punctuation Count   |          19.66 |      15.67 |

These values are calculated from the manually labelled sample in the notebook.

---

## 🛠️ Technologies Used

### Programming Language

* **Python**

### Libraries

* **Pandas** – Data loading, manipulation and analysis
* **NumPy** – Numerical operations
* **NLTK** – Natural Language Processing
* **re** – Regular expressions for text cleaning
* **string** – String and punctuation processing

## The notebook imports and uses Pandas, NumPy, NLTK, `re`, and `string` during the analysis.


## 📌 Important NLP Techniques Used

This project demonstrates the following NLP concepts:

1. **Text Cleaning**
2. **Text Normalization**
3. **Tokenization**
4. **Stop-word Removal**
5. **Lemmatization**
6. **Linguistic Feature Extraction**
7. **Manual Text Annotation**
8. **Toxic vs Non-Toxic Feature Comparison**

---

## 🚀 Future Scope

The current notebook focuses primarily on **NLP preprocessing, annotation and feature analysis**. A natural next step would be to build a machine-learning classification system using the processed text and extracted features.

Possible future improvements include:

* TF-IDF feature extraction
* Bag-of-Words representation
* N-gram analysis
* Logistic Regression
* Naive Bayes
* Support Vector Machine
* Random Forest
* Deep-learning models
* Transformer-based models such as BERT
* Model evaluation using accuracy, precision, recall and F1-score
* Real-time toxic comment detection


## 🎓 Conclusion

This project demonstrates how **Natural Language Processing can transform raw online comments into structured and analyzable information**.

Starting with a large comment dataset, the project performs text cleaning, tokenization, stop-word removal, lemmatization and linguistic feature extraction. A manually annotated sample of 200 comments is then used to compare toxic and non-toxic comments.

The resulting processed data provides a foundation for developing a complete **machine-learning-based toxic comment classification system**.

---


This project is intended for educational and academic purposes.
