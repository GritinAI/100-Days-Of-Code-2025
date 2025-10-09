
# Day 0️⃣2️⃣6️⃣: Pre-LLMs II (Embeddings 🔢🔢🔢 I)

---

$$\text{"Words have meaning."}$$
$$\text{Antonin Scalia}$$

---

## Synopsis

- [Day 0️⃣2️⃣6️⃣: Pre-LLMs II (Embeddings 🔢🔢🔢 I)](#day-0️⃣2️⃣6️⃣-pre-llms-ii-embeddings--i)
  - [Synopsis](#synopsis)
  - [From Tokens 🔵🔴 to Embeddings 🔢🔢🔢](#from-tokens--to-embeddings-)
  - [Phase 1️⃣: Vectors 🔢🔢🔢](#phase-1️⃣-vectors-)
  - [Phase 2️⃣: Vector 🔢🔢🔢 Similarity ⚖️](#phase-2️⃣-vector--similarity-️)
    - [Vector 🔢🔢🔢 Comparison ⚖️ 1.0](#vector--comparison-️-10)
      - [Assumptions](#assumptions)
    - [Vector 🔢🔢🔢 Comparison ⚖️ 2.0](#vector--comparison-️-20)
  - [Phase 3️⃣: Embeddings 🔢🔢🔢 as Vectors 🔢🔢🔢](#phase-3️⃣-embeddings--as-vectors-)
  - [Summary](#summary)
  - [Further Materials](#further-materials)
  - [Spotlight of the Day](#spotlight-of-the-day)

---

## From Tokens 🔵🔴 to Embeddings 🔢🔢🔢

In the last lesson, we saw how we could help our LLM uniquely identify each token 🔵🔴 by assigning a unique integer value to each. Since LLMs (and computers 💻🖥️) only speak numbers, this also makes it easier to process our text 🔡. There is a challenge though: the LLM can identify the tokens 🔵🔴 and represent them as numbers 🔢 now. But it has no idea of the meaning of these tokens 🔵🔴.

We need to fix this problem, and embeddings 🔢🔢🔢 will help us do that.

---

## Phase 1️⃣: Vectors 🔢🔢🔢

Information about the world 🌍 around us can be represented as numbers 🔢 in one way or the other. For instance, age (80 years 👵), national GDP🤑, income 💷 (e.g., $10,000), account numbers 💳, health details 🩺, drug prescriptions 💊 (e.g., 5 capsules) and so much more can be represented as simple numbers 🔢. However, simple numbers are not always enough. Let us visit an example.

Imagine we have two materials $A$ and $B$, and that they weigh $\text{3 kg}$ and $\text{15 kg}$ respectively. Let us ask a question:

---

$$\text{Question: Which material is LARGER? Material A or B?}$$

---

The obvious answer here would be $B$! But what if I add in another piece of information 😏? What if I was to tell you that in litres, material $A$ has a volume of $\text{30 ℓ}$ (e.g., a plastic bucket) while $B$ has a volume of $\text{4 ℓ}$ (e.g., a metal hammer)? Would the answer still remain the same 😀?

Of course not! The mass in $\text{kg}$ tells us the amount of stuff each material contains and how much it weights, but it does not tell us the amount of space it takes up; the volume does that 😀! This is the problem with simple numbers:

---

$$ \text{💡 INSIGHT 💡: Simple numbers 🔢 on their own do not tell the whole story! They only give a perspective.} $$

---

Just as we saw in the example above, we needed both the mass and volume to have a better understanding of the materials involved. Each of these (i.e., mass and volume) are simple numbers on their own. But when combined, they improve our understanding of the materials involved from different perspectives. Each of these perspectives is known as a ***Dimension***, and we can keep adding more simple numbers to explain the materials in more perspectives (i.e., dimensions) e.g., melting point, boiling point, density, etcetera.

When we do this, our materials go from being represented with simple numbers 🔢 like this $\textbf{(I)}$ ...

---

$$ \textbf{(I)} $$
$$ \text{A = 3 kg} $$
$$ \text{B = 15 kg} $$

---

... to this $\textbf{(II)}$:

---

$$ \textbf{(II)} $$
$$ \text{A = [3 kg, 30 ℓ]} \rightarrow \text{A = [3, 30]}$$
$$ \text{B = [15 kg, 4 ℓ]} \rightarrow \text{B = [15, 4]}$$

---

As can be seen, each material is now represented by a list of numbers [🔢🔢🔢]. Each number in the list represents a dimension along which we are trying to describe the material.

The first approach i.e.,  $\textbf{(I)}$ uses simple numbers known as ***scalars*** or ***scalar quantities***, while the second approach i.e., $\textbf{(II)}$ uses numbers we call ***vectors***, or ***vector quantities***.

---

## Phase 2️⃣: Vector 🔢🔢🔢 Similarity ⚖️

### Vector 🔢🔢🔢 Comparison ⚖️ 1.0

As we have agreed above, vectors 🔢🔢🔢 allow us to represent information in a more complete manner compared to simple numbers. But there is something else. With simple numbers, we could easily conclude at a glance that two objects were the same. Is that the same with vectors 🔢🔢🔢? If not how do we know two objects are the same? Let us explore this idea a bit.

Let us have three extra materials $C$, $D$ and $E$, weighing $\text{3 kg}$, $\text{7.5 kg}$, $\text{7.5 kg}$ respectively. Let us tabulate the mass and volumes of our examples:

| Material | Mass | Volume |
|----------|------|--------|
| A | $\text{3 kg}$ | $\text{30 ℓ}$ |
| B | $\text{15 kg}$ | $\text{4 ℓ}$ |
| C | $\text{3 kg}$ | $\text{27 ℓ}$ |
| D | $\text{7.5 kg}$ | $\text{75 ℓ}$ |
| E | $\text{7.5 kg}$ | $\text{2 ℓ}$ |

---

$$ \textbf{(III)} $$
$$ \text{A = [3 kg, 30 ℓ]} \rightarrow \text{A = [3, 30]}$$
$$ \text{B = [15 kg, 4 ℓ]} \rightarrow \text{B = [15, 4]}$$
$$ \text{C = [3 kg,   27 ℓ]} \rightarrow \text{C = [3,   27]}$$
$$ \text{D = [7.5 kg, 75 ℓ]} \rightarrow \text{D = [7.5, 75]}$$
$$ \text{E = [7.5 kg,  2 ℓ]} \rightarrow \text{E = [7.5, 2]}$$

If we compare $A$ and $B$ to $C$, $D$ and $E$ on the basis of mass, we can say the following:

---

$$ \text{C = A} $$
$$ \text{D = 2.5 A} $$
$$ \text{E = 2.5 A} $$
$$ \text{C = 0.2 B} $$
$$ \text{D = 0.5 B} $$
$$ \text{E = 0.5 B} $$

---

But is this really true? Just on the basis of mass, this may be true. But as we have seen before, we need the other numbers to get the best picture. So, let us complete the picture.

---

$$ \text{Question: If we compare the vector forms of A and B to those of C, D, and E, what can we observe?} $$

---

Right away, comparing $A$ to $C$, $D$, and $E$, we can see that:

- $A$ and $C$: Same mass, slightly different volumes. Not exactly the same, but we can safely assume that they are similar.
- $A$ and $D$: $D$ is 2.5 times $A$, as we originally thought! This implies that $D$ is actually $A$, just in more quantity (i.e., mass) and larger (i.e., volume)! **Hint**: Think one bucket made of the same material as the other but two-and-a-half times bigger.
- $A$ and $E$: We thought $E$ was 2.5 times $A$, just like with $D$. However, this is true for the mass, but not for the volume.

If we also do the same for $B$ to $C$, $D$, and $E$, we can see that:

- $B$ and $C$: Different mass, different volumes. $m_C = \frac{m_B}{5}$ but $v_C \not ={\frac{v_B}{5}}$.
- $B$ and $D$: Different mass, different volumes. $m_C = 2.5 m_B$ but $v_C \not ={2.5 v_B}$.
- $B$ and $E$: We thought $E$ was 0.5 times $B$, and we were right! $m_C = 0.5 m_B$ and $v_C = 0.5 v_B$

Based on this, we now know that:

---

#### Assumptions

$$ \textbf{(IV)} $$
$$ \text{C = A ✅} $$
$$ \text{D = 2.5 A ✅} $$
$$ \text{E = 2.5 A ❌} $$
$$ \text{C = 0.2 B ❌} $$
$$ \text{D = 0.5 B ❌} $$
$$ \text{E = 0.5 B ✅} $$

---

### Vector 🔢🔢🔢 Comparison ⚖️ 2.0

All of this work is exhausting 😪! What if we had a simple way to telling if two or more vectors 🔢🔢🔢 were the same (and how similar they are, if they are not exactly the same)?

This is the ***cosine similarity***. With the cosine similarity, we can compare two vectors very easily! The equation is simple!

---

$$ cossim(\vec{A},\vec{B}) = \frac{\sum^N_{i=0}{A_i.B_i}}{|A|.|B|}$$

---

Let us look at an example. Remember:

---

$$ \textbf{(V)} $$
$$ \text{A = [3, 30]} $$
$$ \text{B = [15, 4]} $$
$$ \text{C = [3, 27]} $$
$$ \text{D = [7.5, 75]} $$
$$ \text{E = [7.5, 2]} $$

---

Calculating the cosine similarity for $A$ and $B$:

---

$$ |A| = \sqrt{3^2 + 30^2} = \sqrt{909} = 30.15 $$
$$ |B| = \sqrt{15^2 + 4^2} = \sqrt{241} = 15.52 $$

$$ cossim(\vec{A},\vec{B}) = \frac{(3 \times 15) + (30 \times 4)}{30.15 \times 15.52} = 0.353$$

---

If we calculate the cosine similarity for $A$ and $C$:

---

$$ |A| = \sqrt{3^2 + 30^2} = \sqrt{909} = 30.15 $$
$$ |C| = \sqrt{3^2 + 30^2} = \sqrt{909} = 30.15 $$

$$ cossim(\vec{A},\vec{C}) = \frac{(3 \times 3) + (30 \times 30)}{30.15 \times 30.15} = 1.000$$

---

And how about the cosine similarity for $B$ and $E$?

---

$$ |B| = \sqrt{15^2 + 4^2} = \sqrt{241} = 15.52 $$
$$ |E| = \sqrt{7.5^2 + 2^2} = \sqrt{60.25} = 7.76 $$

$$ cossim(\vec{B},\vec{E}) = \frac{(15 \times 7.5) + (4 \times 2)}{15.52 \times 7.76} = 1.000$$

💡 Notice how the cosine similarity can easily detect that $E$ is just an exactly scaled-down replica of $B$, and so it knows that they are perfectly similar otherwise 😁!

---

$$ \text{Exercise: Calculate the cosine similarities for all the pairs of vectors 🔢🔢🔢. Compare these cosine similarities with the assumptions we made.} $$

---

Now that we have constructed the vocabulary, we know that any word we (or the LLM) encounter can be represented in terms of these unique symbols in the vocab. Now, we need to represent these tokens 🔵🔴 as numbers 🔢, since the LLM does not know text the way we do.

The solution is simple: assign a unique integer 🔢 index to each unique token 🔵🔴 in the vocabulary. That way, whenever the LLM sees a specific integer 🔢 number, we know exactly what token 🔵🔴 it is referring to 😁! Let us look at a simple example using the low-level vocab:

Say we have the low-level vocab made of letters of the English alphabet:

---

$$\text{Vocab = \{a, b, c, d..., z\}}$$

---

All we need to do is represent each token 🔵🔴 by an integer 🔢 starting from zero 0️⃣. In practically all cases, we number then according to their position e.g. *a* is 0, *b* is 1 and so on.

---

$$\text{Vocab = \{0, 1, 2, 3..., 25\}}$$

---

That is all (mostly 😏)!

---

## Phase 3️⃣: Embeddings 🔢🔢🔢 as Vectors 🔢🔢🔢

Now we have the ability to represent objects as vectors 🔢🔢🔢 😁! This idea applies to both concrete (i.e., physical) and abstract (i.e., non-physical) objects. For instance, we have just used vectors 🔢🔢🔢 to represent concrete objects like materials. We can also represent abstract ideas 💡💭 and concepts e.g., velocity, acceleration.

---

$$ \text{Question 🤔:} $$
$$ \text{If we can apply vectors 🔢🔢🔢 to abstract ideas like velocity and acceleration, ...} $$
$$ \text{... can we apply them to words and tokens 🔵🔴 🤔?} $$

---

Yes, we can 😁! In fact, that is the way to go 😁! We construct a vector 🔢🔢🔢 for a token 🔵🔴 such that each dimension of the vector 🔢🔢🔢 encodes some kind of information about said token 🔵🔴 😀! This vector 🔢🔢🔢 is an attempt to represent the meaning of this token 🔵🔴. So ...

---

$$ \text{Question 🤔: How do we compare two tokens 🔵🔴 or words to see if they have similar meanings 🤔?} $$
$$ \text{Answer: Using the cosine similarity 😀!} $$

---

The cosine similarity comes to the rescue 😀!

We have already seen how we can use the cosine similarities to calculate the similarity between vectors 🔢🔢🔢. If we can represent the meaning of tokens 🔵🔴 as vectors 🔢🔢🔢, then we can compare these meanings by comparing the vectors 🔢🔢🔢 using the **cosine similarity**!

These vectors that represent the meaning of a token 🔵🔴? We have a name for them: **Embeddings**!

---

## Summary

1️⃣ Vectors 🔢🔢🔢 help us represent the world in more completion.

2️⃣ We can compare these vectors 🔢🔢🔢 using metrics like cosine similarity.

3️⃣ If we can somehow represent the meaning of our tokens 🔵🔴 using vectors 🔢🔢🔢 ...

4️⃣ ... we can then compare the meaning of these tokens 🔵🔴 in vector 🔢🔢🔢 format using this cosine similarity 😁!

5️⃣ These vectors 🔢🔢🔢 that represent the meaning of a token are known as $\text{Embeddings}$.

So, we now know how embeddings can be useful. We now know that they can help us encode the meaning of tokens 🔵🔴. But where do they come from? And how do we even get them? In the next lesson, we will dive deeper into the concepts of embeddings 😀!

---

## Further Materials

1. [Vector embeddings tutorial (YouTube) 📽️](https://www.youtube.com/watch?v=yfHHvmaMkcA)
2. [A Beginner's Guide to Vector Embeddings (YouTube) 📽️](https://www.youtube.com/watch?v=NEreO2zlXDk)
3. [Tokens & Embeddings (Blog) 📝](https://rohitkhattar.substack.com/p/tokens-and-embeddings-the-hidden)
4. [From Tokens to Embeddings (Blog) 📝](https://ml-digest.com/architecture-training-of-the-embedding-layer-of-llms/)

---

## Spotlight of the Day

<br>

<center><img src=26.png alt="Spotlight Image"></img></center>
