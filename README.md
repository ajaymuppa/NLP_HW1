# CS5760 – Natural Language Processing
## Homework 1 – Regex, BPE, Bayes, Smoothing, and Tokenization

**Student Name:** Ajay Muppa  
**Student ID:** 700769264
**University:** University of Central Missouri  
**Course:** CS5760 – Natural Language Processing  
**Semester:** Spring 2026  

---

## 📌 Overview

This assignment covers core NLP concepts including:

- Regular Expressions (Regex) for pattern matching
- Byte Pair Encoding (BPE) for subword tokenization
- Bayes Rule for document classification
- Add-1 (Laplace) smoothing
- Tokenization challenges in Telugu (a morphologically rich language)

---

## 🧩 Q1 – Regular Expressions (Regex)

| Task | Description | Regex |
|------|-------------|-------|
| ZIP Codes | Match US ZIP codes with optional +4 | `\b\d{5}(?:[- ]\d{4})?\b` |
| Lowercase Words | Words not starting with capital letters | `\b[a-z][A-Za-z]*(?:['-][A-Za-z]+)*\b` |
| Numbers | Signed, commas, decimals, scientific notation | `(?<!\w)[+-]?(?:\d{1,3}(?:,\d{3})+|\d+)(?:\.\d+)?(?:[eE][+-]?\d+)?(?!\w)` |
| Email Variants | email / e-mail / e mail | `(?i)\be(?:[ -–])?mail\b` |
| Interjection | go, goo, gooo with punctuation | `\bgo+\b[!.,?]?` |
| Line Ending | Lines ending with question mark and quotes | `^.*\?(?:[)\]"'’”\]]*\s*)$` |

---

## 🔤 Q2 – Byte Pair Encoding (BPE)

### Manual BPE (Toy Corpus)

- Added end-of-word marker `_`
- Calculated bigram frequencies
- Performed first three merges manually
- Updated vocabulary after each merge

### Mini BPE Implementation (Code)

- Learned merges programmatically
- Printed top pairs and vocabulary growth
- Segmented words:
  - `new`
  - `newer`
  - `lowest`
  - `widest`
  - `newestest`

### Key Insight

Subword tokenization solves the **Out-of-Vocabulary (OOV)** problem by breaking unseen words into known subword units. Learned tokens such as `er_` and `est_` align with meaningful morphemes.

---

## 🌍 Q2.3 – BPE on Natural Paragraph

- Trained BPE on a custom paragraph
- Learned 30+ merges
- Observed subwords representing:
  - stems (`process`, `token`)
  - suffixes (`ing`, `ion`, `ies`)
  - complete frequent words

### Reflection

**Pros**
- Handles unseen words
- Captures morphological patterns

**Cons**
- Not always linguistically meaningful splits
- Longer token sequences

---

## 📘 Q3 – Bayes Rule for Documents

Bayes rule used for classification:

- **P(c)** – Prior probability of class
- **P(d | c)** – Likelihood of document given class
- **P(c | d)** – Posterior probability used for classification

The denominator **P(d)** is ignored because it is constant across classes.

---

## ➕ Q4 – Add-1 Smoothing

Given:

- P(−) = 3/5, P(+) = 2/5
- Vocabulary size = 20
- Total negative tokens = 14

**Denominator with smoothing:**

14 + 20 = 34


**Probabilities:**

P(predictable | −) = (2 + 1) / 34 = 3 / 34
P(fun | −) = (0 + 1) / 34 = 1 / 34


---

## ✂️ Q5 – Tokenization in Telugu

### Naïve vs Manual Tokenization

| Naïve | Corrected |
|------|-----------|
| బాగుంది! | బాగుంది + ! |
| ఒకటి. | ఒకటి + . |
| చూడండి, | చూడండి + , |
| ఇష్ట పడతారు. | ఇష్ట పడతారు + . |

### Tool Comparison

Used Indic NLP tokenizer. Output matched manual correction due to language-specific rules.

### Multiword Expressions (MWEs)

| Expression | Meaning |
|-----------|---------|
| న్యూ ఢిల్లీ | Place name |
| ప్రధాన మంత్రి | Title |
| చేతులు ఎత్తేయడం | Idiom (give up) |

MWEs should be treated as single tokens for better NLP performance.

### Reflection

Tokenization in Telugu is more complex than English due to:

- Rich morphology
- Suffix attachment
- Multiword expressions
- Ambiguous word boundaries

---

## 💻 Repository Contents

- Regex implementations
- BPE implementation code
- Tokenization examples
- Explanations and reflections

---

## ✅ Submission

GitHub Repository:  
https://github.com/ajaymuppa/NLP_HW1

---
