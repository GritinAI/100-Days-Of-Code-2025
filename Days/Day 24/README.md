
# Day 0️⃣2️⃣4️⃣: Large Language Models (LLMs) I

---

$$\text{"Big models, bigger stories: how LLMs learn our language."}$$
$$\text{GritinAI}$$

---

$$\text{“LLMs represent some of the most promising yet ethically fraught technologies ever conceived.”}$$
$$\text{I. Almeida}$$

---

## Synopsis

- [Day 0️⃣2️⃣4️⃣: Large Language Models (LLMs) I](#day-0️⃣2️⃣4️⃣-large-language-models-llms-i)
  - [Synopsis](#synopsis)
  - [The "Large" 🦣 in Large Language Model (LLM)](#the-large--in-large-language-model-llm)
  - [Model 🧠 Size and Parameter 🔢 Count](#model--size-and-parameter--count)
  - [Parameters 🔢](#parameters-)
  - [LLMs 🧠 and Parameters 🔢](#llms--and-parameters-)
  - [Summary 📝](#summary-)
  - [Further Materials 📑](#further-materials-)
  - [Spotlight of the Day 🔦](#spotlight-of-the-day-)

---

## The "Large" 🦣 in Large Language Model (LLM)

Now we know what a language model is and what it does (fill-in-the-gap). Great 😀! But if we have followed the tech space even in an adjacent capacity, then we would have heard of a large language model (LLM) at least once.

So, what is an LLM 🤔? Well, that is obvious: an LLM is a language model that is "large", as the name suggests! Easy 🤪!

But what makes a language model "large"? This is the part most people do not really understand, and this is what we tackle in today's lesson.

---

## Model 🧠 Size and Parameter 🔢 Count

In simple terms:

---

$$\text{A language model is considered large if it has a large number of \it{parameters} 🔢.}$$

---

So now, we know what it means for a language model to be considered large. It has something to do with an arcane thing called a *parameter* 🔢, and, apparently 🤷, any large language model will have a lot of this thing.

To fully understand this, we need to demystify this idea of a parameter 🔢.

---

## Parameters 🔢

One of the easiest ways to explain what a parameter 🔢 is to take people back to high school 🏫 and draw on their math background. Don't worry 😅; it won't be complex!

From high school, we have all seen something like this at some point:

---
$$y = mx + c$$

$$m = \frac{y_2 - y_1}{x_2 - x_1}$$

---

From high school, we know the above to be the equation for a straight line. We also know that ***y*** is dependent variable, ***x*** is the independent variable, ***m*** is the slope or gradient 📈, and ***c*** is the intercept.

We also know that once we have the values for ***m*** (i.e., the slope or gradient), and ***c*** (i.e., the intercept), those values remain constant for the line, and we can use them to predict a new *y* given a new *x*.

In this case, we say we have 2️⃣ parameters 🔢: ***m*** and ***c***. So, can we say what parameters 🔢 are now?

---

$$\text{Parameters 🔢 are values that we combine with our data 💽💾 to get our output.}$$
$$\text{Input (i.e., \text{\it{x}}) + Parameters 🔢 = Output (i.e., \text{\it{y}})}$$

---

Think of our data 💽💾 as a set of ingredients (i.e., {$x_1$, $x_2$ $x_3$}). If this is so, then our parameters 🔢 (i.e., {$m_1$, $m_2$, $m_3$, $c$}) tell us exactly what quantities in which we need to mix those ingredients to get the final meal (i.e., $y$).

<br>

<center>
<figure>
    <img src=Laboratory.gif style="width: 60%; height: auto;" alt="Mixing Ingredients in the Laboratory"></img>
    <figcaption><strong>Mixing Ingredients in the Laboratory</strong></figcaption>
</figure>
</center>

<br>

Another famous example is the quadratic equation below:

---

$$ y = ax^2 + bx + c $$

---

The quadratic equation above only has two variables: ***y*** as the dependent variable and ***x*** as the independent variable. It however has three *parameters*: *a*, *b*, and *c*. These parameters tell us exactly how to combine ***x*** in such a way as to get ***y*** as the final answer.

All equations are made of parameters 🔢 and variables. Because the parameter 🔢 values for a given equation remain constant, knowing these values will always be useful when new data is provided.

For instance, assume I have the equation below:

---

$$y = 4x^2 + 2x + 1$$

---

If I am given any value for ***x***, I can easily tell what the value of ***y*** should be, because I have the parameters. So if ***x*** = 1:

$$y = 4(1)^2 + 2(1) + 1$$
$$y = 4(1) + 2(1) + 1 = 7$$

Then, ***y*** = 7! Awesome!

But what does this have to do with LLMs 🤔?

---

## LLMs 🧠 and Parameters 🔢

So recall how we said this:

> Think of our data as a set of ingredients (i.e., {$x_1$, $x_2$ $x_3$}). If this is so, then our parameters (i.e., {$m_1$, $m_2$, $m_3$, $c$}) tell us exactly what quantities in which we need to mix those ingredients to get the final meal (i.e., $y$).

This is a very important idea 💡😀. Our model is essentially an equation, just like the previous examples!

| Equation/model name              | Equation             | Parameters | Input variables  | Output variables                                    |
|----------------------------------|----------------------|------------|--------------------|-----------------------------------------------------|
| Straight line equation           | $y = mx + c$         | $m, c$     | $x$                | $y$                                                   |
| Quadratic equation               | $y = ax^2 + bx + c$  | $a, b, c$  | $x$                | $y$                                                   |
| Einstein's energy equation       | $E = mc^2$           | $c$        | $m$                | $E$                                                   |
| Language model (LM)              | Can be very complex 🤯     | *variable  | $x_1$, $x_2$ $x_3$ | $P(x_3 \vert x_2, x_1)$ |

Our language model is an equation that:

- Takes in a set of words (i.e., {$x_1$, $x_2$ $x_3$}) as input, and
- Predicts the probability of one word given the others (i.e., $P(x_3 \vert x_2, x_1)$) as output.

For instance, say I have a sentence: *Kylian Mbappe is the best*. Our language model tries to predict the next best words that are most likely to follow the sequence. If our language model is well-trained, it should predict high probabilities for words like *striker* or *footballer* etcetera, and low probabilities for words like *dancer*, *singer*, *lawyer* etcetera. We can then select words that have high probability to complete the sentence.

Now, assume that *striker* is the word with the highest probability, and that we select it. The words that came before it are known as the ***context***, while the selected word is known as the ***completion***.

---

| Context | Completion |
|---------|------------|
|Kylian Mbappe is the best| striker|

---

Like any other equation, a LM needs parameters 🔢 to convert the words to probabilities. And this is where the design of the LM comes into play. When we design a LM to have many parameters 🔢, then we say it is a **Large Language Model**!

But this begs another question:

---

$$ \text{Question 🤔: What parameter 🔢 count is considered large?}$$

---

There is no specific answer for this, because LLMs have been getting larger for some time now. There was a time when the largest LLM in the world was **GPT-2** with 175M (i.e., 175 million) parameters. Now, there are LLMs with much bigger parameter 🔢 counts in the billions! Presently, the general cutoff for an LLM from a SLM is considered to be 8B (i.e., 8 billion) parameters 🔢! That is still very huge 🤯!

---

**P.S. ℹ️:** In case you missed it, a SLM is a **small language model**, essentially a language model with considerably fewer parameters 🔢 than a LLM.

---

## Summary 📝

- LMs help us model the structure of text and language by predicting the probability of a word given previous words.
- LMs are essentially equations; like any other equation, they have parameters 🔢.
- When they have an immense number of parameters 🔢, they are called *LLMs*.
- When LMs have fewer parameters 🔢, they are called *SLMs*.

Now that we know what LMs and LLMs are, we can see about understanding the LLM structure. How did they come to be? How are they built? What are their components (apart from the parameters)? And how do they process or input text?

---

## Further Materials 📑

1. [Practical Introduction to LLMs (YouTube) 📽️](https://www.youtube.com/watch?v=tFHeUSJAYbE&list=PLz-ep5RbHosU2hnz5ejezwaYpdMutMVB0&index=1&pp=iAQB)
2. [Andrej Karpathy's Introduction to LLMs (YouTube) 📽️](https://www.youtube.com/watch?v=zjkBMFhNj_g)

---

## Spotlight of the Day 🔦

<br>

<center><img src=23.png alt="Spotlight Image"></img></center>
