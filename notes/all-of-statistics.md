# All of Statistics #

*A Concise Course in Statistical Inference*

## Preface ##

This book is for people who want to learn probability and statistics quickly. It is suitable for graduate or advanced undergraduate students in **computer science, mathematics, statistics**, and related disciplines.

**Statistics, data mining, and machine learning** are all concerned with **collecting and analyzing data**. Students who analyze data, or who aspire to develop new methods for analyzing data, should be well grounded in **basic probability and mathematical statistics**.

Here is a summary of the main features of this book:

1. The book is suitable for **graduate students in computer science** and honors undergraduates in math, statistics, and computer science. It is also useful for students beginning graduate work in statistics who need to fill in their background on mathematical statistics.

4. Whenever possible, I avoid tedious calculations in favor of emphasizing concepts.

5. I cover **nonparametric inference** before **parametric inference**.

6. On my website are files with R code which students can use for doing all the computing. The website is: http://www.stat.cmu.edu/∼larry/all-of-statistic

**Part I** of the text is concerned with **probability theory**, the formal language of uncertainty which is the basis of statistical inference. The basic problem that we study in probability is:

> Given a data generating process, what are the properties of the outcomes?

**Part II** is about **statistical inference** and its close cousins, **data mining and machine learning**. The basic problem of statistical inference is the inverse of probability:

> Given the outcomes, what can we say about the process that generated the data?

**Prediction, classification, clustering, and estimation** are all special cases of statistical inference. **Data analysis, machine learning and data mining** are various names given to the practice of statistical inference, depending on the context.

**Part III** applies the ideas from Part II to specific problems such as **regression, graphical models, causation, density estimation, smoothing, classification, and simulation**. Part III contains one more chapter on probability that covers **stochastic processes** including **Markov chains**.

### Statistics/Data Mining Dictionary ###

Statisticians and computer scientists often use different language for the same thing. Here is a dictionary that the reader may want to return to throughout the course.

# Part I - Probability #

## Chapter 1 Probability ##

**Probability** is a mathematical language for quantifying uncertainty.

### Sample Spaces and Events ###

- \\( \Omega \\) is sample space.
- \\( \omega \\) is outcome (point or element)
- \\( A \\) is event (subset of \\( \Omega \\) ).
- \\( A^{C} \\) is complement of \\( A \\) (not \\( A \\) ).
- \\( A \cup B \\) is union ( \\( A \\) or \\( B \\) ).
- \\( A \cap B \\) is intersection ( \\( A \\) and \\( B \\) ).
- \\( A - B \\) is set difference.
- \\( A \subset B \\) is set inclusion
- \\( \emptyset \\) is null event (always false).
- \\( \Omega \\) is true event (always true).

### Probability ###

**1.5 Definition.**
>The function \\( \mathbb{P} \\) that assigns a real number \\( \mathbb{P}(A) \\) to each event \\( A \\) is called a **probability distribution** or a **probability measure**. \\( \mathbb{P}(A) \\) is called the **probability** of \\( A \\).

- The **frequency** interpretation:
> \\( \mathbb{P} (A) \\) is the long run proportion of times that \\( A \\) is true in repetitions.

- The **degree-of-belief** interpretation:
> \\( \mathbb{P} (A) \\) measures an observer's strength of belief that \\( A \\) is true.

The differing interpretations lead to [two schools of inference: the frequentist and the Bayesian schools](#Chapter-11).

**1.6 Lemma.**
> For any events \\( A \\) and \\( B \\),
\\[ \mathbb{P}(A \cup B) = \mathbb{P}(A) + \mathbb{P}(B) - \mathbb{P}(AB) \\]

### 1.4 Probability on Finite Sample Spaces ###

If \\( \Omega \\) is finite and if each outcome is equally likely, then
\\[ \mathbb{P}(A) = \frac{\left | A \right |}{\left | \Omega \right |} \\]
which is called the **uniform probability distribution**.

Methods for counting points in an event A are called **combinatorial methods**.

Given \\( n \\) objects, the number of ways of ordering these objects is \\( n! = n(n-1)(n-2) \cdots 3 \cdot 2 \cdot 1 \\). We define
\\[ \binom{n}{k} = \frac{n!}{k!(n-k)!} \\]
read "\\(n\\) chosse \\(k\\)", which is the number of distinct ways of choosing \\(k\\) objects from \\(n\\).

### 1.5 Independent Events ###

**1.9 Definitions.**
> Two events \\(A\\) and \\(B\\) are **independent** if
\\[ \mathbb{P}(AB) = \mathbb{P}(A) \mathbb{P}(B) \\]
and we write \\( A \amalg B \\). A set of events \\( \\{ A\_{i} : i \in I \\} \\) is independent if
\\[ \mathbb{P}\left ( \bigcap\_{i \in J} A\_{i} \right ) = \prod\_{i \in J} \mathbb{P}(A\_{i}) \\]
for every finite subset \\(J\\) of \\(I\\).

Independence can arise in two distinct ways.

- Sometimes, we explicitly assume that two events are independent.
- In other instances, we derive independence by verifying that \\(\mathbb{P}(AB) = \mathbb{P}(A) \mathbb{P}(B) \\) holds.

If \\(A\\) and \\(B\\) are disjoint events, each with positive probability, then \\( \mathbb{P}(A) \mathbb{P}(B) > 0 \\) yet \\( \mathbb{P}(AB) = \mathbb{P}(\emptyset) = 0 \\), thus they cannot be independent. Except in this special case, there is no way to judge independence by looking at the sets in a Venn diagram.

**1.11 Example.**
> If \\(0 < r < 1\\) then \\( \sum\_{j=k}^{\infty}r^{j} = r^{k}/(1-r) \\).

### 1.6 Conditional Probability ###

**1.12 Definition**
> If \\(\mathbb{P}(B) > 0\\) then the **conditional probability** of \\(A\\) given \\(B\\) is
\\[ \mathbb{P}(A\mid B) = \frac{\mathbb{P}(AB)}{\mathbb{P}
(B)} \\]

In general it is **not** the case that

- \\( \mathbb{P}(A \mid B \cup C) = \mathbb{P}(A \mid B) + \mathbb{P}(A \mid C) \\)
- \\( \mathbb{P}(A \mid B) = \mathbb{P}(B \mid A) \\). This mistake is made often enough in legal cases that it is sometimes called the prosecutor's fallacy.

**1.13 Example.**

\\[ \mathbb{P}(+ \mid D) = \frac{\mathbb{P}(+ \cap D)}{\mathbb{P}(D)} = \frac{.009}{.009 + .001} = .9 \\]
 and 
\\[ \mathbb{P}(- \mid D^{c}) = \frac{\mathbb{P}(- \cap D^{c})}{\mathbb{P}(D^{c})} = \frac{.891}{.891 + .099} \approx .9 \\]
, but
\\[ \mathbb{P}(D \mid +) = \frac{\mathbb{P}(+ \cap D)}{\mathbb{P}(+)} = \frac{.009}{.009 + .099} \approx .08 \\]
The lesson here is that you need to compute the answer numerically. Don't trust your intuition.

**1.14 Lemma.**
> If \\(A\\) and \\(B\\) are independent events then \\( \mathbb{P}(A \mid B) = \mathbb{P}(A) \\).

That is, \\(A\\) and \\(B\\) are independent if and only if \\( \mathbb{P}(A \mid B) = \mathbb{P}(A) \\).

> Also, for any pair of events \\(A\\) and \\(B\\),
\\[ \mathbb{P}(AB) = \mathbb{P}(A \mid B)\mathbb{P}(B) = \mathbb{P}(B \mid A)\mathbb{P}(A) \\]

### 1.7 Bayes' Theorem ###

**1.16 Theorm (The law of Total Probability)**
> Let \\(A\_{1}, \cdots, A\_{k} \\) be a partition of \\(\Omega\\). Then, for any event \\(B\\),
\\[ \mathbb{P}(B) = \sum\_{i=1}^{k}\mathbb{P}(B \mid A\_{i})\mathbb{P}(A\_{i}) \\]

**1.17 Theorm (Bayes' Theorm)**
> Let \\(A\_{1}, \cdots, A\_{k} \\) be a partition of \\(\Omega\\) such that \\(\mathbb{P}(A\_{i}) > 0\\) for each \\(i\\). If \\(\mathbb{P}(B) > 0\\) then, for each \\(i = 1, \cdots, k\\),
\\[ \mathbb{P}(A\_{i} \mid B) = \frac{\mathbb{P}(B \mid A\_{i})\mathbb{P}(A\_{i})}{\sum\_{j}\mathbb{P}(B \mid A\_{j})\mathbb{P}(A\_{j})} \\]

**1.18 Remark.**
> We call \\(\mathbb{P}(A)\\) the **prior probability**  of \\(A\\) and \\(\mathbb{P}(A\_{i} \mid B)\\) the **posterior probability** of \\(A\\).
