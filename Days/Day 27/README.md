
# Day 0️⃣2️⃣7️⃣: Pre-LLMs II (Embeddings 🔢🔢🔢 II)

---

$$\text{"... And you shall know a word by the company it keeps."}$$
$$\text{John B. Firth}$$

---

## Synopsis

- [Day 0️⃣2️⃣7️⃣: Pre-LLMs II (Embeddings 🔢🔢🔢 II)](#day-0️⃣2️⃣7️⃣-pre-llms-ii-embeddings--ii)
  - [Synopsis](#synopsis)
  - [Embeddings 🔢🔢🔢](#embeddings-)
  - [Word Representation Schemes](#word-representation-schemes)
    - [Phase 1️⃣: Integers 🔢](#phase-1️⃣-integers-)
      - [Pros 👍](#pros-)
      - [Cons 👎](#cons-)
    - [Phase 2️⃣: Vectors 1.0 🔢🔢🔢 (One-hot Encoding \[0️⃣0️⃣0️⃣1️⃣0️⃣\])](#phase-2️⃣-vectors-10--one-hot-encoding-0️⃣0️⃣0️⃣1️⃣0️⃣)
      - [Pros 👍](#pros--1)
      - [Cons 👎](#cons--1)
    - [Phase 3️⃣: Vectors 2.0 🔢🔢🔢 (Dense Vectors \[🔢🔢🔢🔢🔢\])](#phase-3️⃣-vectors-20--dense-vectors-)
      - [Pros 👍](#pros--2)
      - [Cons 👎](#cons--2)
    - [Phase 4️⃣: Vectors 3.0 🔢🔢🔢 (Embeddings \[🔢🔢🔢🔢🔢\])](#phase-4️⃣-vectors-30--embeddings-)
      - [Pros 👍](#pros--3)
      - [Cons 👎](#cons--3)
  - [Generating Embeddings](#generating-embeddings)
    - [1️⃣ Feed-forward networks (FFNs)](#1️⃣-feed-forward-networks-ffns)
      - [🅰️ Data](#️-data)
      - [🅱️ Parameters 🔢](#️-parameters-)
      - [🔭 Observations 🅰️ + 🅱️ 🔭](#-observations-️--️-)
    - [2️⃣ Embedding Tables](#2️⃣-embedding-tables)
  - [Summary](#summary)
  - [Further Materials](#further-materials)
  - [Spotlight of the Day](#spotlight-of-the-day)

---

## Embeddings 🔢🔢🔢

From the last lesson, we learnt that embeddings are essential to providing our LLMs with understanding because:

1️⃣ They represent the meaning of our tokens 🔵🔴 in vector format and

2️⃣ They represent this meaning in multiple dimensions (or perspectives), making for richer information.

What we did not discuss, however, was how these embeddings 🔢🔢🔢 come to be. How do we derive them? Or do they fall from heaven 🪽😀?

---

## Word Representation Schemes

Even before the advent of embeddings 🔢🔢🔢, we have always needed to represent words using numbers 🔢, since those are all a computer understands. But how have we gone about this historically?

### Phase 1️⃣: Integers 🔢

Prior to embeddings as we know them today, we have always represented words with numbers. As discussed in the last lesson, we would start by representing every word with a unique integer 🔢 index.

#### Pros 👍

1️⃣ Easy and fast to implement.

#### Cons 👎

1️⃣ Best for identifying words, no meaning attached to simple integer number 🔢.

2️⃣ Words in any language are related to one another i.e., we do not use words in isolation. Rather, we use them in conjunction with other words that either emphasize on or provide contrast to their meaning. Representing words with simple integers 🔢 cannot achieve this.

---

### Phase 2️⃣: Vectors 1.0 🔢🔢🔢 (One-hot Encoding [0️⃣0️⃣0️⃣1️⃣0️⃣])

The next step was to evolve the word representation method from integers 🔢 $\Rightarrow$ vectors 🔢🔢🔢. This would allow us to solve the issue with integer 🔢 representation where words exist in isolation.

The first approach to come up is known as **One-hot Encoding**. The steps are outlined below:

1️⃣ Create the vocabulary.

2️⃣ Get the vocabulary size as $N$ e.g., $N = 5$.

3️⃣ For each word, $W$...

3️⃣🅰️ Create a vector ($V_W$) of size $N$ filled with zeros e.g., $V_W = \{ 0, 0, 0, 0, 0 \}$

3️⃣🅱️ Get the integer 🔢 index, $I_W$, of word $W$ and fill vector $V_W$ with a 1 at that index $I_W$. For example:

---
$\text{Given ...}$
$$N = 5$$
$$I_W = 2$$
$$V_W = \{ 0, 0, 0, 0, 0 \}$$

$\text{Then ...}$
$$V_W[I_W] = 1$$
$$V_W = \{ 0, 0, 1, 0, 0 \}$$

---

#### Pros 👍

1️⃣ Easy and fast to implement.

2️⃣ Leverages vectors, so more information.

#### Cons 👎

1️⃣ One-hot vectors are mostly zeros, so limited information.

2️⃣ Words in any language are related to one another i.e., we do not use words in isolation. Rather, we use them in conjunction with other words that either emphasize on or provide contrast to their meaning. Representing words with simple one-hot vectors only represents the position of the word, and cannot achieve this.

---

### Phase 3️⃣: Vectors 2.0 🔢🔢🔢 (Dense Vectors [🔢🔢🔢🔢🔢])

As stated above, one-hot vector encoding was limited by irs sparse nature. How do we moe past it?

---

$$ \text{Answer: Distributed Representations 😄!} $$

---

The idea of distributed representations is that words can have their individual meaning, but that they can also derive some of their meaning from other words they appear with!

This idea is so powerful that it gave rise to a new approach called **Dense Vectors**. The idea behind this was to derive vectors for words, not only based on the words themselves, but also based on the words they are likely to appear with. Examples of projects that applied this method with success include:

1️⃣ Word2Vec

2️⃣ GloVe

3️⃣ NLTK

---

#### Pros 👍

1️⃣ Easy and fast to implement.

2️⃣ Leverages vectors, so more information.

#### Cons 👎

1️⃣ Requires time and data to train.

---

### Phase 4️⃣: Vectors 3.0 🔢🔢🔢 (Embeddings [🔢🔢🔢🔢🔢])

This is the present state-of-the-art for word representation. This is exactly what we set out to learn about.

---

#### Pros 👍

1️⃣ Easy and fast to implement.

2️⃣ Leverages vectors, so more information.

3️⃣ We can control the number of embedding dimensions.

#### Cons 👎

1️⃣ Requires time and data to train.

---

## Generating Embeddings

So, now we know how we got here, to a place where embeddings have become integral to machine learning. Now its time to answer the million-dollar question:

---

$$ \text{Question: How do we generate embeddings? Where do they come from?} $$

---

The answer is actually simple:

---

$$ \text{Answer: From an embedding lookup table $E$ that we train 😄!} $$

---

Don't worry 😌! We'll understand this! But first, let us learn about feed-forward networks.

### 1️⃣ Feed-forward networks (FFNs)

The feed-forward network (FFN), also known as multilayer perceptron (MLP), is one of the simplest neural networks 🧠 that can be made. It simply processes information by multiplying at least two matrices together, one of which represents the data, and the other represents the parameters 🔢! Let us look at a simple example:

#### 🅰️ Data

Assume we have the data for 5 customers, each described by their age, salary and years of experience. Recall from our discussion on vectors that this gives us three dimensions across which we can describe our employees: 1️⃣ age, 2️⃣ salary, and 3️⃣ years of experience. We can therefore represent each employee as a vector.

For instance, assume we have an employee named **Victor**, who is aged 39 years, and who has worked with us for 5 years. Representing Victor's information in vector form (Victor, vector, get it 😜!) would be like this:

---

$$\text{$x_i$ = [Victor, 39, 5]}$$

---

With more employees, we end up with multiple vectors:

---

$$ \text{$x_1$ =  [Victor, 39, 5]} $$
$$ \text{$x_2$ =  [Joseph, 26, 3]}$$
$$ \text{$x_3$ =  [Hannah, 29, 7]}$$
$$ \text{$x_4$ =  [Sharon, 31, 3]}$$
$$ \text{$x_5$ =  [Halima, 37, 7]}$$

---

Just as we can combine simple numbers to give vectors, we can also combine vectors to give matrices. This means we can represent all this data on our employees as a matrix $X$ of shape $5, 3$.

---

$$ X \in \R^{(5,3)}$$

---

#### 🅱️ Parameters 🔢

Next, we need the parameters 🔢 $W$ we wish to multiply our data with. From matrix multiplication, we know that we can only multiply matrices $X$ and $W$ if:

---

$$ X \in \R^{(5,3)}$$
$$ W \in \R^{(3,N)}$$

where $N$ is an arbitrary number we can choose.

---

Let $N = 10$. Then:

---

$$ X \in \R^{(5,3)}$$
$$ W \in \R^{(3,10)}$$

---

**Note**: In this example, if we choose $N$ to be 10, then $W$ will contain a total of $3 \times 10 = 30$ parameters 🔢.

Matrix multiplication between $X$ and $W$ gives:

$$ X \times W = X^{'} \in \R^{(5,10)}$$

To complete the FFN, all we need is to add a bias term, $b$:

$$ Y = (X \times W + b) = (X^{'} + b) \in \R^{(5,10)}$$

And with this, we have the equation for a feed-forward neural network 🧠!

---

**Note 1️⃣**: Sometimes, the bias term $b$ is simply 0 i.e., $b = 0$.

**Note 2️⃣**: The bias term $b$ also counts as a parameter 🔢.

---

#### 🔭 Observations 🅰️ + 🅱️ 🔭

Now, did we observe something from our recent exploration? I'll give a hint again:

$$ Y = (X \times W + b) = (X^{'} + b) \in \R^{(5,10)}$$

---

$$ \text{Answer: The FFN equation looks like the equation of a straight line 😮!} $$

---

In fact, it doesn't just look like the straight line equation; it **IS** the straight line equation, only instead of simple numbers, it uses vectors 😀!

Now that we know this ...

$$ \text{Question 🤔 \#1: What was the point of learning about FFNs?} $$
$$ \text{Question 🤔 \#2: What was that thing about embedding lookup tables again 🫤?} $$

### 2️⃣ Embedding Tables

Recall the equation for an FFN?

---

$$ Y = XW + b$$

---

Let us simplify it and make three 3️⃣👌changes. First, let us make the bias term $b$ zero i.e., $b = 0$. In that case:

---

$$ Y = XW + b = XW + 0 = XW$$

---

Secondly, get the vocabulary size as $N_v$. In the case of our example above, let $N_v = 5$, since we have 5 employees. Then let us set the size of or parameter 🔢 matrix as:

---

$$ W \in \R^{(N_v,10)}$$
$$ W \in \R^{(5,10)}$$

---

Great! Next, let us make $X$ a one-hot matrix, i.e., a collection of one-hot vectors 😀 where the vector size is $N_v$! And let us make one final simplification: let us rename $W$ as $E$.

Once we have this, we can represent our embedding layer:

---

$$ Y = XE$$

---

This is the embedding layer, $L_E$:

---

$$ Y = L_E(X) = XE$$

---

To see the practical implementation, please checkout the notebook attached: [embedding notebook 📒](embeddings_tutorial.ipynb).

---

## Summary

So, we now know how embeddings can be useful. And we know how they are generated.

Now we can see about understanding the structure of LLMs. How did they come to be? How are they built? What are their components 🟦🔵🟩🟪 (apart from the parameters 🔢)?

---

## Further Materials

1. [Vector embeddings tutorial (YouTube) 📽️](https://www.youtube.com/watch?v=yfHHvmaMkcA)
2. [A Beginner's Guide to Vector Embeddings (YouTube) 📽️](https://www.youtube.com/watch?v=NEreO2zlXDk)
3. [Tokens & Embeddings (Blog) 📝](https://rohitkhattar.substack.com/p/tokens-and-embeddings-the-hidden)
4. [From Tokens to Embeddings (Blog) 📝](https://ml-digest.com/architecture-training-of-the-embedding-layer-of-llms/)
5. [Evolution of Embeddings (Blog) 📝](https://www.francescatabor.com/articles/2025/3/8/llm-bootcamp-module-3-evolution-of-embeddings)
6. [The Evolution of Embeddings (Blog) 📝](https://blog.dailydoseofds.com/p/the-evolution-of-embeddings)

---

## Spotlight of the Day

<br>

<center><img src=27.png alt="Spotlight Image"></img></center>
