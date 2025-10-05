
# Day 0️⃣2️⃣3️⃣: Language Models (LMs)

---

$$\text{"If you talk to a man in a language he understands, that goes to his head 🙂‍↕. If you talk to him in his language, that goes to his heart 💓."}$$
$$\text{Nelson Mandela}$$

---

$$\text{“The limits of my language mean the limits of my world 🌍.”}$$
$$\text{Ludwig Wittgenstein}$$

---

## Synopsis

- [Day 0️⃣2️⃣3️⃣: Language Models (LMs)](#day-0️⃣2️⃣3️⃣-language-models-lms)
  - [Synopsis](#synopsis)
  - [Language for Generative AI 🫧🤖](#language-for-generative-ai-)
  - [Language modelling](#language-modelling)
  - [Language Model Classification](#language-model-classification)
    - [1️⃣ Gap Location](#1️⃣-gap-location)
      - [🅰️ Causal language model](#️-causal-language-model)
      - [🅱️ Masked language model](#️-masked-language-model)
    - [2️⃣ External Information?](#2️⃣-external-information)
      - [1️⃣ Base LLMs](#1️⃣-base-llms)
      - [2️⃣ Augmented LLMs](#2️⃣-augmented-llms)
    - [3️⃣ Type of External Information](#3️⃣-type-of-external-information)
      - [1️⃣ Unimodal LLMs](#1️⃣-unimodal-llms)
      - [2️⃣ Multimodal LLMs](#2️⃣-multimodal-llms)
    - [4️⃣ Number of Chances](#4️⃣-number-of-chances)
      - [1️⃣ Zero-Shot](#1️⃣-zero-shot)
      - [2️⃣ Few-Shot](#2️⃣-few-shot)
  - [Summary 📝](#summary-)
  - [Further Materials 📑](#further-materials-)
  - [Spotlight of the Day 🔦](#spotlight-of-the-day-)

---

## Language for Generative AI 🫧🤖

Previously, we have covered the use of generative AI 🫧🤖. We know that it allows us to be creative. We also know that leveraging it is as simple as telling it what we want. But is it really that simple? And when we actually do tell it what we want, how can it understand us?

For the first question, the short answer is *"Yes"*, and the fuller answer is *"Not really"*. More on this later. As for the second question, the answer is the focus of this and the next few lessons 🤪!

---

## Language modelling

In the present day, most generative AI is powered by a technique known as **language modelling**. In basic language (pun intended 😜), language modelling is an attempt to study linguistic structure by leveraging the principles of probability. For those of us who remember Sherlock Holmes of fabled legend, we will recall that he has done something like this, where he deduces that the letter **E** is the most common letter in English.

The result of language modelling is a **language model** (LM) which estimates the probability of a word or sequence of words, given other words. Let us give an example. Fill the gap below:

---

<center>
<strong>
Victor is <em>a</em> __________.
</strong>
</center>

---

Anyone with even a basic command of the English language can probably come up with an accurate guess to fill that gap. But here's the interesting thing: if 100 people tried to fill the gap, we'd end up with multiple different possible answers, and they would likely all be correct 🤯! This is a hallmark of creativity: all roads 🛣️ lead to Rome 🏛️, there is rarely a wrong answer, and there is often a lot of correct answers!

This is language modelling in action: predicting the next likely word based on other words available! This is essentially *fill-the-gap*, a game that little kids play in school 🤯!

Now, let's try another example with a new gap:

---

<center>
<strong>
Victor is <em>an</em> __________.
</strong>
</center>

---

Looking at the new gap to fill, it is clear, once again, that the options that might fit the first gap would definitely not befit the second. On a balance of probability, words that were likely to appear in the first gap would be much less likely to appear in the second. We can attribute this judgment to the presence of the *an* article which is substituted for the original *a*.

Essentially, we are trying to figure out the most likely next word given a set of previous words, including the article *an*! And we can do this because we have an internal language model, which is a generative intelligence (:wink: 😜) that allows us to create sentences!

---

## Language Model Classification

Now we know that language modelling is essentially a fill-the-gap game. We can classify language models and the tasks they solve based on the kinds of gaps we are trying to fill. These classifications include:

1️⃣ Gap location
2️⃣ Whether or not external information is needed to fill the gap
3️⃣ If external information is needed to fill the gap, what type of information is it?
4️⃣ How many chances are there to fill the gaps?

---

### 1️⃣ Gap Location

Now we know that language modelling is essentially a fill-the-gap game. However, we know that in such games, the gap can appear at any position in the sentence.

For instance:

---

<center>

<strong>
Victor is <em>an</em> __________.
</strong>

<br>

<strong>
_______ is the fairest of them all_
</strong>

<br>

<strong>
_______ is <em>a</em> teacher by _______ and <em>a</em> tailor by ________.
</strong>

<br>

<strong>
_________ is <em>an</em> engineering _________.
</strong>

</center>

---

I will leave the task of completing the gaps to you, but I trust you have picked up the salient point: ***the gaps can appear at the beginning, end or even the middle of the sentence***. Even more, they can appear at multiple of these positions simultaneously.

Each of these fill-the-gap problems can be solved using a language model, and the location of the gap determines what kind of language model we are dealing with. Beyond gap location, we can also classify language models based on the information we require in order to fill the gap i.e., information type and source. More on this later.

For now, based on the gap location, we have:

---

#### 🅰️ Causal language model

Also known as **Autoregressive Language Models**.

This type of language model deals with gaps at the end of the sentence. This is the most common form of language modelling task we can encounter. When people talk of language models without specifying, they are usually talking about this type.

<br>

<center>

<strong>
Victor is <em>an</em> __________.
</strong>

</center>

<br>

These language models are mostly focused on ***decoding*** and completing the gap. **Hint**: More on this later.

---

#### 🅱️ Masked language model

Also known as **Autoencoding LLMs**.

This type of language model deals with gaps anywhere else other than (and possibly including) the end of the sentence. For example:

<br>

<center>

<strong>
_______ is <em>a</em> teacher by _______ and <em>a</em> tailor by ________.
</strong>

</center>

<br>

Language models of this type are focused less on completing the gap, and more on ***encoding*** information about language structure. **Hint**: More on this later as well.

---

### 2️⃣ External Information?

In order to fill the gap present in the query, external clues 🧩 might be needed. Where do these clues 🧩 come from? Some times these clues 🧩 are contained in the text already. However, some times, these clues 🧩 may be provided from external sources of information.

#### 1️⃣ Base LLMs

These LLMs only need their input in order to generate their responses. They can answer questions like:

---

<br>

<center>

<strong>
Sonia is <em>a</em> teacher by profession. Her job is to ________ students.
</strong>

</center>

<br>

---

#### 2️⃣ Augmented LLMs

These LLMs require some augmentation with external information in order to successfully process input. Most LLMs you will encounter have been augmented in some way.

A popular example of this is called **In-context learning (ICL)**. In order to answer the question successfully, we can provide the LLM with some examples, which will give it some idea of how to proceed. Examples:

---

<br>

<center>

<strong>
Review: The movie was fantastic → Sentiment: Positive
</strong>
<br>
<strong>
Review: The storyline was wack  → Sentiment: Negative
</strong>
<br>
<strong>
Review: The music was pleasant  → Sentiment: ________
</strong>

</center>

<br>

---

### 3️⃣ Type of External Information

If external information is indeed needed to aid the LLM, wht kind of information is it?

#### 1️⃣ Unimodal LLMs

These LLMs operate on one type of data 💽💾: usually text 🔡. As such, they can only process text.

#### 2️⃣ Multimodal LLMs

The LLMs operate on multiple types of data 💽💾, e.g., text 🔡 & images 🖼️, text 🔡 & videos 📽️ etcetera. An example of this are VLMs (Vision-Language Models).

---

### 4️⃣ Number of Chances

Think of yourself as the teacher 🧑‍🏫 and the LLM as a student 👩‍🎓. Imagine you are trying to evaluate the student 👩‍🎓 on a question. They may or may not get it right on the first try. Do we give them more chances, and if so how many? This is actually very similar to in-context learning.

#### 1️⃣ Zero-Shot

Also known as **Single-shot**.

Involves giving the LLM input without specifying examples.

#### 2️⃣ Few-Shot

Also known as **Multi-shot**.

Involves providing the LLM with one or more examples of the desired task before asking it to perform. This can range from one example (one-shot) to several (few-shot).

---

## Summary 📝

We have learnt how to classify LLMs and the tasks they can perform. There are other ways of doing this (we will encounter sone of them later), but we are off to a good start 😁🥳.

Now, we know what language models do. They help us model the structure of a language in a mathematical way using probability. But what does this mean? And how does this happen? We will see this soon.

---

## Further Materials 📑

1. [Language with Sherlock Holmes 🚬🎩 (Blog) 📝](https://blog.oup.com/2020/01/codes-and-ciphers/)
2. [Large Language Models: Concepts (Blog) 📝](https://vitalflux.com/large-language-models-concepts-examples/)
3. [In-context Learning (ICL) (Blog) 📝](https://www.ibm.com/think/topics/in-context-learning)
4. [Stanford AI Guide to In-context Learning (Blog) 📝](https://ai.stanford.edu/blog/understanding-incontext/)
5. [Single- and Multi-shot LLM Prompting (Blog) 📝](https://artificialintelligenceschool.com/single-shot-vs-multi-shot-a-comprehensive-guide-to-llm-evaluation-techniques/)
6. [Unimodal vs. Multimodal LLMs (Blog) 📝](https://www.dataknobs.com/generativeai/10-llms/multi-modal-llm/4-multimodal-vs-unimodal-llms-key-differences-and-applications.html)
7. [Vision-Language Models (Blog) 📝](https://www.ibm.com/think/topics/vision-language-models)

---

## Spotlight of the Day 🔦

<br>

<center><img src=23.png alt="Spotlight Image"></img></center>
