
# Day 0️⃣2️⃣5️⃣: Pre-LLMs I (Tokenization)

---

$$\text{"Behind any successful person: secret 🤫 pain 🥲, hard-work 👷and sacrifice 🔥.}$$
$$\text{Behind any successful LLM: a secret 🤫 hardworking tokenizer 😁."}$$
$$\text{GritinAI}$$

---

## Synopsis

- [Day 0️⃣2️⃣5️⃣: Pre-LLMs I (Tokenization)](#day-0️⃣2️⃣5️⃣-pre-llms-i-tokenization)
  - [Synopsis](#synopsis)
  - [From Text 🔡 to Tokens 🔵🔴](#from-text--to-tokens-)
  - [Phase 1️⃣: Vocabulary 🔠🔡](#phase-1️⃣-vocabulary-)
    - [Problem 🫨: Choosing the Right Vocabulary Level](#problem--choosing-the-right-vocabulary-level)
    - [Solution 💊: Tokenization](#solution--tokenization)
  - [Phase 2️⃣: Tokens 🔵🔴 as Numbers 🔢](#phase-2️⃣-tokens--as-numbers-)
  - [Summary](#summary)
  - [Further Materials](#further-materials)
  - [Spotlight of the Day](#spotlight-of-the-day)

---

## From Text 🔡 to Tokens 🔵🔴

When we start out with a body of text, what we have is simply a sequence of characters which convey meaning together. When we pass this text into an LLM, we expect the LLM to extract the meaning or intended meaning being conveyed.

However, LLMs (and machines 💻🖥️ in general) do not speak English (or any other human language for that matter). They only speak numbers. Thus, if we want our LLM to process the data successfully, we need to come up with a means of converting the input sentence into numbers.

This is what is known as **Tokenization**. You might have encountered some form of this word before: **token**. Not to worry; we will get to understand it better in this lesson.

---

## Phase 1️⃣: Vocabulary 🔠🔡

The idea in natural language processing is to essentially teach a language model (LM) to speak a language, whether English, Spanish or any other arbitrary language. To teach the language to the LM, we would have to come up with a strategy.

First of, every language has one thing in common: a ***Vocabulary*** 🔠🔡🔤. A vocabulary is, in essence, the set of unique symbols that comprise a language. This vocabulary can be considered at a low level or at a high one. At a low level, we can say that the vocabulary of a language consists of the characters and alphabets of the language.

Take English as an example; at a low level, the vocabulary of English can be said to be just 26 characters, since the language only have 26 letters. If we also account for the upper and lower case, we have 52 characters in the vocabulary.

However, at a high level, which is the level most people tend to think of a language, things get complicated. This is the level where we aggregate the letters to form meaningful words and ideas. This high-level vocabulary allows us to easily encode meaning compared to the lower level vocabulary. To verify this just compare a word (e.g., *state*) in the high-level vocab to a letter from the low-level vocab (e.g., *b*). As you can see, the high-level vocab allows quick encoding of meaning.

### Problem 🫨: Choosing the Right Vocabulary Level

So we have multiple vocab choices: the low-level and the high-level. These come with their own challenges, however.

Take the high-level; There are so many possible combinations of letters at this level, which makes it difficult to count the vocabulary size.

---

> **Hint**: How many unique words are in the English language? What if we account for synonyms and antonyms? What about slangs and made-up words? Compare this to the 56 letters that make up the lower level English vocab.

---

To make things even worse, not all these letter combinations are meaningful.

---

> **Hint**: The high-level vocabulary is where words live. But some words are just made up, and not all words are meaningful.

---

Challenges also exist at the low-level; individual characters that make up the vocabulary may not be very meaningful in themselves.

Also, this level can sometimes get as big and complex as the high level. For example, we know that English language can basically be approximated by a vocab of 56 characters. However, what about languages that are more complicated, like Mandarin, Korean, and Japanese, where the basic alphabets are comprised of thousands of kanji ㊗️🈵 🈶🈷️ 🈂️?!

Therefore, we are at an impasse:

|  Vocab  |  Pro   |  Con  |
|---------|--------|-------|
|Low-level | Usually small in size; can be easily handled | Does not encode meaning easily; Can be very large for some languages e.g., Mandarin|
|High-level | Can encode meaning more easily |  Very large in size; hard to keep track of|

How do we resolve this dilemma 🤔?

---

### Solution 💊: Tokenization

Tokenization is the answer 😀!

Tokenization provides a balance; using a vocabulary of simple letters is small but not meaningful enough; using a vocabulary of words is more meaningful but too large to process easily. Tokenization gives us the middle ground; it breaks down a language into subparts, uses this subparts as the vocabulary. Then, whenever a new word is encountered, it breaks the word into subparts from this vocabulary.

These subparts are known as **Tokens**, and they are to LLMs what words are to humans. Basically, humans have words in our vocabulary; LLMs have tokens in their vocabulary 😁! Fun fact, in general, we find that:

---

$$ \text{1 Token} \approx \text{0.75 word} 😉$$

> **Hint**: Although a token is usually $\approx \text{0.75 words}$, it is not always so. Sometimes, the token is an actual character, in which case it approximate the low-level vocab. Sometimes, the token might be the whole word as well, in which case it approximates the high-level vocab.

<center><img src=token_to_words.webp alt="Token to word"></img></center>
<strong><center>Token to word</center></strong>

---

The image below gives a visual aid in understanding how tokenization works. Notice how some tokens are actual words, while some are characters and others still are subwords. Specifically, notice how words like **set**, **symbols** and **of** remain considered as tokens. In this case the token vocabulary matches the high-level vocab. Also notice how some words can be split into tokens, such that the tokens are either individual characters or group of characters that are less than words.

For example:

| Word  |  Tokens  |
|-------|----------|
|LLMs   | L, LM, s |

This allows the tokenization process to model both low- and high-level vocabs. It can thus be considered a means of generating a **mid-level vocab**.

<center><img src=tokenization.webp alt="Splitting text into tokens"></img></center>
<strong><center>Splitting text into tokens</center></strong>

---

## Phase 2️⃣: Tokens 🔵🔴 as Numbers 🔢

Now that we have constructed the vocabulary, we know that any word we (or the LLM) encounter can be represented in terms of these unique symbols in the vocab. Now, we need to represent these tokens as numbers 🔢, since the LLM does not know text the way we do.

The solution is simple: assign a unique integer index to each unique token in the vocabulary. That way, whenever the LLM sees a specific integer number, we know exactly what token it is referring to 😁! Let us look at a simple example using the low-level vocab:

Say we have the low-level vocab made of letters of the English alphabet:

---

$$\text{Vocab = \{a, b, c, d..., z\}}$$

---

All we need to do is represent each token by an integer starting from zero. In practically all cases, we number then according to their position e.g. *a* is 0, *b* is 1 and so on.

---

$$\text{Vocab = \{0, 1, 2, 3..., 25\}}$$

---

That is all (mostly 😏)!

---

## Summary

So, how does tokenization work? The following steps describe it:

1️⃣ Split the text 🔡 into subparts. These subparts are known as **Tokens**.

2️⃣ Represent each unique token with an index starting from 0. This is the way the LLM represents the tokens. Not as text 🔡, but as numbers 🔢.

Now, we have dealt with the first step before our text gets to the LLM: splitting it into manageable tokens 🔵🔴 and representing these tokens 🔵🔴 as numbers. This allows the LLM to be able to process and identify the tokens 🔵🔴. Now, it is one thing to be able to identify something. It is something else to be able to see meaning in it.

---

$$ \text{Question 🤔: How do we ensure the LLM sees meaning in these numbers 😓?} $$

---

The above question will be considered in the next lesson on embeddings 😄!

---

## Further Materials

1. [Understanding text tokenization in LLMs (Blog) 📝](https://techunpacked.substack.com/p/12-understanding-tokenization-in)
2. [Text tokenization tutorial (YouTube) 📽️](https://www.youtube.com/watch?v=hL4ZnAWSyuU)
3. [LLM Tokenization (Blog) 📝](https://www.openxcell.com/blog/llm-tokenization/)

---

## Spotlight of the Day

<br>

<center><img src=25.png alt="Spotlight Image"></img></center>
