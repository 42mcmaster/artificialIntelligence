# Lesson 08: Natural Language Processing - Study Guide

## What is NLP?
**Natural Language Processing (NLP)** is the branch of AI that works with human language —
text and speech. Because models only understand numbers, every NLP task starts by turning
words into numbers, and (for generation) turning numbers back into words.

## Vocabulary

1. **Natural Language Processing (NLP)** - AI techniques for working with human language.
2. **Corpus** - A body of text used as data (plural: corpora).
3. **Token** - A single unit of text, usually a word (sometimes a piece of a word).
4. **Tokenization** - Splitting text into tokens.
5. **Bag-of-Words (BoW)** - Representing text as word **counts**, ignoring word order.
6. **CountVectorizer** - scikit-learn tool that builds a vocabulary and produces BoW counts.
7. **TF-IDF** - "Term Frequency - Inverse Document Frequency": like BoW but down-weights
   words that appear in almost every document (so common words matter less).
8. **Vocabulary** - The set of all unique tokens the vectorizer knows.
9. **Sentiment Analysis** - Classifying text by the feeling it expresses (positive/negative).
10. **Stop words** - Very common words (the, a, is) that often carry little sentiment.
11. **Negation problem** - BoW can't tell "good" from "not good" because it ignores order.
12. **Text Generation** - Producing new text automatically.
13. **Markov Chain** - A generator that picks the next token based only on the current
    token(s) and what followed them in the training text.
14. **Order (of a Markov chain)** - How many previous tokens the chain remembers (order-1 =
    one word of context, order-2 = two).
15. **RNN / LSTM** - Recurrent Neural Networks; neural models that read a sequence one token
    at a time and remember context. What CodeHS uses for text generation.
16. **Transformer** - The neural architecture behind modern LLMs (ChatGPT, Gemini); reads a
    whole sequence at once and predicts the next token.
17. **Language Model** - Any model that predicts the next token from the previous ones.

## The sentiment pipeline (memorize this shape)
```python
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix

# 1. split TEXT and LABELS
X_train, X_test, y_train, y_test = train_test_split(
    reviews, labels, test_size=0.25, random_state=42, stratify=labels)

# 2. text -> numbers (fit on train, apply to test)
vec = CountVectorizer()
X_train_vec = vec.fit_transform(X_train)
X_test_vec  = vec.transform(X_test)

# 3. train a classifier
model = LogisticRegression(max_iter=1000)
model.fit(X_train_vec, y_train)

# 4. evaluate
pred = model.predict(X_test_vec)
print(accuracy_score(y_test, pred))
print(confusion_matrix(y_test, pred))

# 5. use it
model.predict(vec.transform(["a brand new review"]))
```
> **Golden rule:** `fit_transform` on TRAIN only; `transform` on TEST. Fitting the vectorizer
> on test data would leak information.

## The text-generation idea
A **Markov chain** is just a dictionary: *key = the last word(s), value = list of words that
followed*. To generate, start somewhere and repeatedly pick a random follower.
- **Order-1** remembers one word -> grammatical but wanders.
- **Order-2** remembers two -> more coherent but replays the source.
- Bigger, smarter versions (RNNs, Transformers) remember far more and *learn* patterns rather
  than storing raw counts — but it's the **same core job**: predict the next token.

## Key insights
- Word **order** carries meaning; Bag-of-Words throws it away, which is why negation ("not
  good") and sarcasm fool it. That's a feature limitation, not a bug in your code.
- A model is only as fair as its text. Reviews, resumes, and social media all carry human
  bias; an NLP model trained on them will absorb it (see ai11 Ethics).
- Every language model — from your 20-line Markov chain to ChatGPT — is a **next-token
  predictor**. The difference is scale and memory, not the fundamental idea.

## ODE Competencies Covered
**2.14.1** Distinguish between AI approaches (here: statistical NLP vs. neural language models)
**2.14.5** Apply machine learning techniques to real-world problems and interpret results
**5.1.1** Use Python for data analysis: preprocessing (tokenizing), model building, evaluation
**5.1.2** Implement scikit-learn algorithms for supervised learning tasks (text classification)

## Review Questions
1. **Why must text be converted to numbers before modeling?** Models do math on numbers, not words.
2. **What does CountVectorizer produce?** A vocabulary plus a matrix of word counts (Bag-of-Words).
3. **Why fit the vectorizer on training data only?** To avoid leaking test information into training.
4. **Why does Bag-of-Words struggle with "not good"?** It ignores word order, so "not" and "good"
   are just two separate counts.
5. **What is sentiment analysis?** Classifying text by the emotion/opinion it expresses.
6. **How does a Markov chain generate text?** It picks the next word from the words that followed
   the current word(s) in the training text.
7. **What changes from order-1 to order-2?** More context => more coherent but less original output.
8. **How is a Markov chain like ChatGPT?** Both predict the next token from previous ones.
9. **How is it different?** ChatGPT (a Transformer) remembers far more context and *learns*
   patterns instead of storing raw counts.
10. **Where can bias enter an NLP model?** Through the text it's trained on.

## Resources
- scikit-learn text feature extraction: https://scikit-learn.org/stable/modules/feature_extraction.html
- Tie-in: ai04 cert insert (Bag-of-Words / text -> features), ai11 Ethics (bias in data)
