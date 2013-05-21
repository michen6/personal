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

## Chapter 2. Random Variables ##

### 2.1 Introduction ###

**2.1 Definition.**
> A **random variable** is a mapping
> \\[ X : \Omega \to \mathbb{R} \\]
> that assigns a real number \\( X(\omega) \\) to each outcome \\( \omega \\).

### 2.2 Distribution Functions and Probability Functions ###

**2.5 Definition.**
> The **cumulative distribution function** (CDF), or distribution function, is the function \\( F\_{X} : \mathbb{R} \rightarrow [0,1] \\) defined by
> \\[ F\_{X}(x) = \mathbb{P}(X \leq x) \\]
> sometimes we write the CDF as \\(F\\) instead of \\(F\_{X}\\).

**2.8 Theorem.**
> A function \\(F\\) mapping the real line to [0, 1] is a CDF for some probability \\(\mathbb{P}\\) if and only if \\(F\\) satisfies the following three conditions:
> 
> 1. \\(F\\) is non-decreasing: \\(x\_{1} < x\_{2}\\) imples that \\(F(x\_{1}) \leq F(x\_{2})\\).
> 2. \\(F\\) is normalized:
> \\[ \lim\_{x\to -\infty}F(x) = 0 \\]
> and
> \\[ \lim\_{x\to \infty}F(x) = 1 \\]
> 3. \\(F\\) is right-continuous: \\(F(x) = F(x^{+})\\) for all \\(x\\), where
> \\[ F(x^{+}) = \lim\_{y\to x, y > x}F(y) \\]

**2.9 Definition.**
> \\(X\\) is **discrete** if it takes countably many values \\(\\{x\_{1},x\_{2},\cdots\\}\\). We define the **probability function** or **probability mass function** for \\(X\\) by \\(f\_{X}(x) = \mathbb{P}(X = x)\\).

Thus, \\(f\_{X}(x) \geq 0 \\) for all \\(x\in \mathbb{R}\\) and \\(\sum\_{i}f\_{X}(x\_{i}) = 1\\). Sometimes we write \\(f\\) instead of \\(f\_{X}\\). The CDF of \\(X\\) is related to \\(f\_{X}\\) by
\\[ F\_{X}(x) = \mathbb{P}(X \leq x) = \sum\_{x\_{i} \leq x} f\_{X}(x\_{i}) \\]

**2.11 Definition.**
> A random variable \\(X\\) is **continuous** if there exists a function \\(f\_{X}\\) such that \\(f\_{X}(x) \geq 0\\) for all \\(x\\), \\(\int\_{-\infty}^{\infty}f\_{X}(x)dx = 1\\) and for every \\(a \leq b\\),
> \\[ \mathbb{P}(a < X < b) = \int\_{a}^{b}f\_{X}(x)dx \\]
> 
> The function \\(f\_{X}\\) is called the **probability density function** (PDF). We have that
> \\[ F\_{X}(x) = \int\_{-\infty}^{x}f\_{X}(t)dt \\]
> and \\(f\_{X}(x) = F_{X}'(x)\\) at all points \\(x\\) at which \\(F\_{X}\\) is differentiable.

Sometimes we write \\(\int f(x)dx\\) or \\(\int f\\) to mean \\(\int\_{-\infty}^{\infty}f(x)dx\\).

**2.12 Example.**
> Suppose that \\(X\\) has PDF
> \\[ f\_{X}(x) = \begin{cases} 1 & \text{ for } 0 \leq x \leq 1 \\\\ 0 & \text{ otherwise. } \end{cases} \\]
>
> A random variable with this density is said to have a Uniform (0, 1) distribution. This is meant to capture the idea of choosing a point at random between 0 and 1. The CDF is given by
> \\[ F\_{X}(x) = \begin{cases} 0 & x < 0 \\\\ x & 0 \leq x \leq 1 \\\\ 0 & x > 1 \end{cases} \\]

- First note that if \\(X\\) is continuous then \\(\mathbb{P}(X = x) = 0\\) for every \\(x\\).
- Don't try to think of \\(f(x)\\) as \\(\mathbb{P}(X = x)\\). this only holds for discrete random variables. We get probabilities from a PDF by integrating.
- A PDF can be bigger than 1 (unlike a mass function).
- In fact, a PDF can be unbounded.

**2.15 Lemma.**
> Let \\(F\\) be the CDF for a random variable \\(X\\). Then:
> 
> 1. \\( \mathbb{P}(X = x) = F(x) - F(x^{-})\\) where \\(F(x^{-}) = \lim\_{y\uparrow x}F(y) \\);
> 2. \\( \mathbb{P}(x < X \leq y) = F(y) - F(x) \\);
> 3. \\( \mathbb{P}(X > x) = 1 - F(x) \\);
> 4. If \\(X\\) is continuous then
> \\[ F(b) - F(a) = \mathbb{P}(a < X < b) = \mathbb{P}(A \leq X < b) = \mathbb{P}(a < X \leq b) = \mathbb{P}(a \leq X \leq b) \\].

**2.16 Definition.**
> Let \\(X\\) be a random variable with CDF \\(F\\). The **inverse CDF** or **quantile function** is defined by
> \\[ F^{-1}(q) = \text{inf}\\{x:F(x) > q\\} \\]
> for \\(q \in [0, 1]\\). If \\(F\\) is strictly increasing and continuous then \\( F^{-1}(q)\\) is the unique real number \\(x\\) such that \\(F(x) = q\\).

Two random variables \\(X\\) and \\(Y\\) are **equal in distribution** - written \\(X\overset{d}{=}Y\\) - if \\(F\_{X}(x) = F\_{Y}(x)\\) for all \\(x\\).

### 2.3 Some Important Discrete Random Variables ###

It is traditional to write \\(X\sim F\\) to indicate that \\(X\\) has distribution \\(F\\). Read \\(X \sim F\\) as "\\(X\\) has distribution \\(F\\)".

- **Point Mass Distribution**: \\(X\\) has a point mass distribution at \\(a\\), written \\(X \sim \delta\_a\\), if \\(\mathbb{P}(X=a)=1\\) in which case
\\[ F(x) = \begin{cases} 0 & x < a \\\\ 1 & x \geq a\end{cases} \\]
- **Discrete Uniform Distribution**: Let \\(k > 1\\), we say that \\(X\\) has a uniform distribution on \\(\\{1, \cdots ,k\\}\\) if \\(X\\) has probability mass function given by
\\[ f(x) = \begin{cases} 1/k & \text{for } x < a \\\\ 0 & \text{otherwise} \end{cases} \\]
- **Bernoulli Distribution**: Let \\(X\\) represent a binary coin flip, then \\(\mathbb{P}(X=1)=p\\) and \\(\mathbb{P}(X=0)=1-p\\) for some \\(p \in [0,1]\\). We say that \\(X\\) has a Bernoulli distribution written \\(X \sim \mathrm{Bernoulli}(p)\\). The probability function is \\(f(x) = p^x(1-p)^{1-x}\\) for \\(x \in \\{0,1\\}\\).
- **Binomial Distribution**: Let \\(f(x) = \mathbb{P}(X=x)\\) be the mass function. It can be shown that 
\\[ f(x) = \begin{cases} \binom{n}{x}p^x(1-p)^{n-x} & \text{for } x=0,\cdots,n \\\\ 0 & \text{otherwise} \end{cases} \\]
A random variable with this mass function is called a Binomial random variable and we write \\(X \sim \mathrm{Binomial}(n, p)\\). If \\(X\_1 \sim \mathrm{Binomial}(n\_1, p)\\) and \\(X\_2 \sim \mathrm{Binomial}(n\_2, p)\\), then \\(X\_1 + X\_2 \sim \mathrm{Binomial}(n\_1 + n\_2, p)\\).
- **Geometric Distribution**: \\(X\\) has a geometric distribution with parameter \\(p \in (0,1)\\), written \\(X \sim \mathrm{Geom}(p)\\), if
\\[\mathbb{P}(X=k)=p(1-p)^{k-1}, \qquad k \geq 1\\]
Think of \\(X\\) as the number of flips needed until the first head when flipping a coin.
- **Poisson Distribution**: \\(X\\) has a Poisson distribution with parameter \\(\lambda\\), written \\(X \sim \mathrm{Poisson}(\lambda)\\) if
\\[ f(x) = e^{-\lambda}\frac{\lambda^x}{x!} \qquad x \geq 0 \\]
The Poisson is often used as a model for counts of rare events like radioactive decay and traffic accidents. if \\(X\_1 \sim \mathrm{Poisson}(\lambda\_1)\\) and \\(X\_2 \sim \mathrm{Poisson}(\lambda\_2)\\) then \\(X\_1 + X\_2 \sim \mathrm{Poisson}(\lambda\_1 + \lambda\_2)\\).

In the Binomial distribution, \\(X\\) is a **random variable**; \\(x\\) denotes a particular **value** of the random variable; \\(n\\) and \\(p\\) are **parameters**, that is, fixed real numbers. The parameter \\(p\\) is usually unknown and must be estimated from data; that's what statistical inference is all about. In most statistical models, there are random variables and parameters: don't confuse them.

### 2.4 Some Important Continuous Random Variables ###

- **Uniform Distribution**
- **Normal (Gaussian) Distribution**
- **Exponential Distribution**
- **Gamma Distribution**
- **Beta Distribution**
- **\\(t\\) and Cauchy Distribution**
- **\\(\chi^2\\) Distribution**
