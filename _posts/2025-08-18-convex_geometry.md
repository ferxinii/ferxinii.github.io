---
title: Convex geometry
tags: [geometry]
style: fill
color: danger
description: Definitions and theorems in convex geometry.
---

{% capture list_items %}
Affine sets
Convex sets
Convex cones
Topological notions
Projections and separating hyperplanes
Faces of convex sets
Polyhedra and polytopes
Cells and triangulations
References
{% endcapture %}
{% include elements/list.html title="Table of Contents" type="toc" %}


## Affine sets {#sec:affine}

<div class="definition">
A set $$M \subset \mathbb{R}^n$$ is an *affine set* if
$$\forall x, y \in M, \ \forall \lambda \in \mathbb{R}$$, then
$$(1-\lambda) x + \lambda y \in M$$. That is, if the (infinite) line
that passes through any two points of the set is contained in the set
itself.

</div>

Affine sets are closely related to vectorial subspaces of
$$\mathbb{R}^n$$, as the following theorem establishes. To see this, we
first define the *translation* of a subset $$S \subset \mathbb{R}^n$$ by
$$a \in \mathbb{R}^n$$ as $$M + a = \{ x + a \mid x \in M \}$$.
Furthermore, we say that an affine set $$M$$ is *parallel* to another
affine set $$L$$ if $$\exists a \in \mathbb{R}^n$$ such that
$$M = L + a$$. It is easy to show that the translate of an affine set
results in another affine set.

<div class="theorem">
Each non-empty affine set $$M \subset \mathbb{R}^n$$ is parallel to a
unique vectorial subspace $$L$$, given by
$$L = M - M = \{ x - y \mid x, y \in M \}$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Suppose $$M$$ has two parallel subspaces $$L_1, L_2$$. They must also be
parallel, so $$\exists b$$ s.t. $$L_2 = L_1 + b$$. Since 0
$$\in L_2 \Rightarrow -b \in L_1 \Rightarrow b \in L_1$$. Therefore,
$$L_1 + b = L_2 \subset L_1$$. Similarly, we can see that
$$L_1 \subset L_2$$, so $$L_1 = L_2$$. Regarding the existance, for any
$$x \in M$$, define $$T = M - x$$ which is a translation of $$M$$
containing 0. Since $$T$$ is affine,
$$\forall y \in T, \lambda \in \mathbb{R} \Rightarrow \lambda y + (1-\lambda)0 = \lambda y \in T$$,
so $$T$$ is closed under scalar multiplication. Furthermore,
$$\forall y_1, y_2 \in T$$,
$$\frac{1}{2}(y_1 + y_2) = \frac{1}{2}y_1 + (1-\frac{1}{2}) y_2 \in T$$,
so $$y_1 + y_2 = 2(\frac{1}{2}(y_1+y_2)) \in T$$ and $$T$$ is closed
under addition. Therefore, $$L = M-M$$ is a unique vectorial subspace
parallel to $$M$$. ◻
</div></details>


Geometrically, an affine set can be seen as a translation of a vectorial
subset, and therefore does not need to contain the origin. We write this
as $$M = L + a$$ for some $$a\in \mathbb{R}^n$$.

<div class="definition">
The dimension of a non-empty affine set is the dimension of the
vectorial subpsace parallel to it.

</div>

The next theorem establishes that every affine set can be represented as
the solution set of a system of nonhomogeneous linear equations.

<div class="theorem">
<span id="thm:aff_representation" label="thm:aff_representation"></span>
Let
$$b \in \mathbb{R}^m, \mathbf{B} \in \mathcal{M}_{m \times n} (\mathbb{R})$$.
Then, $$M = \{ x \in \mathbb{R}^n \mid \mathbf{B} x = b \}$$ is an
affine set in $$\mathbb{R}^n$$. Moreover, every affine set may be
represented in this way.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Let
$$x_1, x_2 \in M \Rightarrow \mathbf{B}x_1 = b, \mathbf{B} x_2 = b \Rightarrow \mathbf{B}(\lambda x_1 + (1- \lambda) x_2) = \lambda b + (1-\lambda)b = b \Rightarrow \lambda x_1 + (1-\lambda) x_2 \in M \ \forall \lambda \in \mathbb{R}$$,
so $$M$$ is affine. In the converse direction, suppose $$M$$ affine. Let
$$L$$ be its parallel subspace, and $$\{b_1, \ldots, b_m\}$$ a basis of
$$L^\top$$. Then,
$$L = (L^\top)^\top = \{ x \mid  \langle s, b_i \rangle = 0\} = \{ x \mid \mathbf{B} x = 0\}$$,
where $$\mathbf{B}$$ is the matrix having $$b_i$$ as rows. Then,
$$M = L + a = \{ x \mid \mathbf{B} x = \mathbf{B} a = b\}$$. ◻
</div></details>


It is important to notice that the intersection of an arbitrary
collection of affine sets is affine. This allows the definition of the
*affine hull* of a set using an external representation.

<div class="definition">
Given $$S \subset \mathbb{R}^n$$, the *affine hull* of $$S$$,
$$\mathrm{aff}(S)$$, is the smallest affine set containing $$S$$. In
other words, the intersection of the collection of affine sets $$M$$
such that $$S \subset M$$.

</div>

By defining an *affine combination of points*, we can characterize the
affine hull of a set using an internal representation.

<div class="definition">
An *affine combination of points*
$$x_1, x_2, \ldots, x_m \in \mathbb{R}^n$$ is any point of the form
$$\lambda_1 x_1 + \lambda_2 x_2 + \cdots + \lambda_m x_m$$ with
$$\lambda_i \in \mathbb{R}, \ \sum_{i=0}^m \lambda_i = 1$$.

</div>
<div class="theorem">
<span id="thm:aff_closed" label="thm:aff_closed"></span>
$$M \subset \mathbb{R}^n$$ is affine $$\iff$$ $$M$$ is closed under
affine combinations.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
($$\Rightarrow$$) Assume $$M$$ affine, we will use induction. The base
case is true by definition:
$$x_1, x_2 \in M, \ \lambda_1 + \lambda_2 = 1 \Rightarrow \lambda_1 x_1 + \lambda_2 x_2 \in M$$.
Assume $$x_i \in M, \lambda_i \in \mathbb{R}, \ i = 1, \cdots, k$$ s.t.
$$\sum_i^k \lambda_i = 1$$ implies that
$$\sum_i^k \lambda_i x_i \in M$$. Now, we consider
$$x_i \in M, \lambda_i \in \mathbb{R}, \ i = 1, \cdots, k+1$$ s.t.
$$\sum_1^{k+1} \lambda_i = 1$$. Then,
$$\sum_i^{k+1} \lambda_i x_i = \sum_i^k \lambda_i x_i + \lambda_{k+1} x_{k+1} = (1-\lambda_{k+1})\sum_i^k \frac{\lambda_i}{1-\lambda_{k+1}}x_i + \lambda_{k+1} x_{k+1} = (1-\lambda_{k+1})z + \lambda_{k+1} x_{k+1}$$.
Note that $$z$$ satisfies the induction hypothesis, so $$z \in M$$ and
therefore by definition $$\sum_i^{k+1} \lambda_i x_i \in M$$.
($$\Leftarrow$$) Assume $$M$$ is closed under affine sums. Then, the
affine combination of any two elements of $$M$$ must be in $$M$$, which
is precisely the definition of affine set. ◻
</div></details>


<div class="corollary">
Given $$S \subset \mathbb{R}^n$$, $$\mathrm{aff}(S)$$ consists of all
the affine combinations of points in $$S$$, i.e.,
$$\mathrm{aff}(S) = \left\{ x \ \middle| \ x = \sum_{i=0}^m \lambda_i x_i,\ \sum_{i=0}^m \lambda_i = 1, \ \lambda_i \in \mathbb{R}, \ x_i \in S,\ m \in \mathbb{N} \right\}$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
<span id="cor:aff_hull_comb" label="cor:aff_hull_comb"></span> The set
of all affine combinations of points in $$S$$, call it $$X$$, must be
affine by [\[thm:aff_closed\]](#thm:aff_closed) and contains $$S$$.
Since $$\mathrm{aff}(S)$$ is the smallest such set containing $$S$$,
$$\mathrm{aff}(S) \subset X$$. On the other hand, all elements of $$S$$
belong to $$\mathrm{aff}(S)$$, so all their affine combinations must lie
in $$\mathrm{aff}(S)$$ by [\[thm:aff_closed\]](#thm:aff_closed) and
$$X \subset \mathrm{aff}(S)$$. ◻
</div></details>


We can now relate affine combinations of a finite set of points to
linear combinations of the corresponding vectors of the parallel
subspace.

<div class="definition">
A set of $$m+1$$ points $$\{ b_0, \ldots, b_m\} \subset \mathbb{R}^n$$
is said to be *affinely independent* if $$\mathrm{aff}(S)$$ is
m-dimensional.

</div>

Note that letting
$$L = \mathrm{aff}(\{0, b_1 - b_0, \ldots, b_m - b_0\})$$, we have
$$M = \mathrm{aff}(\{ b_0, b_1, \ldots, b_m\}) = L + b_0$$. The points
in $$M$$ are those expressible in the form
$$x = b_0 + \lambda_1 (b_1 - b_0) + \cdots + \lambda_m (b_m - b_0)$$, or
in other words,
$$x = \lambda_0 b_0 + \lambda_1 b_1 + \cdots + \lambda_m x_m, \ \sum_{i=0}^m \lambda_i = 1$$.

Therefore, $$\{ b_0, b_1, \ldots, b_m\} \subset \mathbb{R}^n$$ are
affinely independent
$$\iff \{ b_1 - b_0, \ldots, b_m - b_0\} \subset \mathbb{R}^n$$ are
linearly independent. Furthermore, every element
$$x \in \mathrm{aff}(\{ b_0, b_1, \ldots, b_m\})$$ can be uniquely
expressed as an affine combination of $$b_i$$.

Finally, we will formally define a very important affine set: the
*hyperplane*, and give a useful way to represent it.

<div class="definition">
An (n-1)-dimensional affine set in $$\mathbb{R}^n$$ is called a
*hyperplane*.

</div>
<div class="proposition">
A hyperplane can be represented as
$$H = \{x \mid \langle x, b \rangle = \beta \}$$, with
$$b \in \mathbb{R}^n, \ \beta \in \mathbb{R}$$ unique up to a common
non-zero multiple.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Analogous to [\[thm:aff_representation\]](#thm:aff_representation). ◻
</div></details>


## Convex sets

<div class="definition">
A set $$C \subset \mathbb{R}^n$$ is a *convex set* if
$$\forall x, y \in C, \ \forall \lambda \in (0,1)$$ then
$$(1-\lambda) x + \lambda y \in C$$. That is, if the line segment
between any two points of the set is contained in the set itself.

</div>

It follows that all affine sets are convex. Furthermore, it is easy to
see that the intersection of an arbitrary collection of convex sets is
convex. A very important example of a convex set is the *half-space*,
which is related to affine hyperplanes.

<div class="definition">
For any non-zero $$b \in \mathbb{R}^n, \beta \in \mathbb{R}$$, the sets
$$\{ x \mid \langle x, b \rangle \leq \beta \}, \ \{ x \mid \langle x, b \rangle \geq \beta \}$$
are called *closed half-spaces*. The sets
$$\{ x \mid \langle x, b \rangle < \beta \}, \ \{ x \mid \langle x, b \rangle > \beta \}$$
are called *open half-spaces*.

</div>

Note that they are unique up to a common non-zero multiple of $$b$$ and
$$\beta$$. Thus, the half-spaces depend only on the hyperplane
$$H = \{ x \mid \langle x, b \rangle = \beta \}$$. We may use the
notation $$h_H^{+}, h_H^{-}$$ to refer to the upper and lower closed
half-spaces of $$H$$ and $$\mathring{h}_H^+, \mathring{h}_H^-$$ to the
open half-spaces.

The next result establishes that the solution set of a nonhomogeneous
system of arbitrarily many linear inequalities is a convex set.

<div class="theorem">
<span id="thm:inequalities-convex"
label="thm:inequalities-convex"></span> Let
$$b_i \in \mathbb{R}^n, \ \beta_i \in \mathbb{R}$$ for $$i \in I$$ an
arbitrary index set. Then,
$$C = \{ x \mid \langle x, b_i\rangle \leq \beta_i, \ i \in I\}$$ is a
convex set.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Let $$C_i = \{ x \mid \langle x, b_i \rangle \leq \beta_i \}$$. Then,
$$C_i$$ is a closed half-space (or $$\mathbb{R}^n$$ or $$\emptyset$$),
and thus convex. Then, $$C = \bigcap_{i \in I} C_i$$ is also convex. ◻
</div></details>


Also, note that the result still holds if we consider strict
inequalities or equalities, even simultaneously. Regarding the converse,
a similar result claims that all convex sets can be represented as the
intersection of all those closed half-spaces which contain it. The proof
requires the use of the *supporting hyperplane theorem*, which is
explained later.

Next, proceeding in a similar manner as before, we may define the
*convex hull* of a set using an external representation.

<div class="definition">
Given $$S\subset \mathbb{R}^n$$, the *convex hull* of $$S$$,
$$\mathrm{conv}(S)$$, is the unique smallest convex set containing
$$S$$. In other words, the intersection of the collection of convex sets
$$C$$ such that $$S \subset C$$.

</div>

By defining a *convex combination of points*, we can give an alternative
definition of the convex hull using an internal representation.

<div class="definition">
A *convex combination of points*
$$x_1, x_2, \ldots, x_m \in \mathbb{R}^n$$ is any point of the form
$$\theta_1 x_1 + \cdots + \theta_m x_m$$ with
$$\theta_i \geq 0, \ \sum_{i=0}^m \theta_1 = 1$$.

</div>
<div class="theorem">
<span id="thm:convex_closed" label="thm:convex_closed"></span>
$$C \subset \mathbb{R}^n$$ is convex $$\iff$$ it is closed under convex
combinations.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Analogous to [\[thm:aff_closed\]](#thm:aff_closed). ◻
</div></details>


<div class="theorem">
Given $$S \subset \mathbb{R}^n, \ \mathrm{conv}(S)$$ consists of all the
convex combinations of the elements of S.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Analogous to [\[cor:aff_hull_comb\]](#cor:aff_hull_comb). ◻
</div></details>


We can also have a notion of dimensionality of a convex set in terms of
its affine hull.

<div class="definition">
<span id="def:conv_dim" label="def:conv_dim"></span> The dimension of a
convex set $$C$$ is the dimension of $$\mathrm{aff}(C)$$.

</div>

## Convex cones

<div class="definition">
A set $$K \subset \mathbb{R}^n$$ is a *cone* if it is closed under
positive scalar multiplication, i.e.,
$$x \in K, \ \lambda > 0 \implies \lambda x \in K$$. If it is also a
convex set, then $$K$$ is a *convex cone*.

</div>

Note that such a set is the union of half-lines emanating from the
origing, which itself need not be included.

It is easy to see that the intersection of an arbitrary collection of
convex cones is a convex cone. Similarly to before, the next result
establishes that the solution to a set of homogeneous linear
inequalities is a convex cone (not just a convex set as would be the
case if the inequalities were nonhomogeneous).

<div class="corollary">
Let $$b_i \in \mathbb{R}^n$$ for $$i \in I$$ an arbitrary index set.
Then,
$$K = \{ x \in \mathbb{R}^n \mid \langle x, b_i \rangle \leq 0, \ i \in I\}$$
is a convex cone.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Analogous to [\[thm:inequalities-convex\]](#thm:inequalities-convex). ◻
</div></details>


The following results allow for an alternative represantation of convex
cones.

<div class="theorem">
<span id="thm:cone_closed" label="thm:cone_closed"></span>
$$K \subset \mathbb{R}^n$$ is a convex cone $$\iff$$ it is closed under
addition and positive scalar multiplication ($$\iff$$ it contains all
the *positive* linear combinations of its elements).

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Assume $$K$$ is a convex cone, and take $$x, y \in K$$. By definition of
cone, $$\frac{1}{2}x, \frac{1}{2}y \in K$$, and by convexity
$$\frac{1}{2}(x+y) = \frac{1}{2}x + (1-\frac{1}{2})y \in K$$. Therefore,
$$x+y = 2 \frac{1}{2}(x+1) \in K$$, so it is closed under addition. On
the other hand, assume $$K$$ is closed under addition and positive
scalar multiplication. Let $$x, y \in K, \ \lambda \in (0, 1)$$, so
$$\lambda x, (1-\lambda)y \in K$$ and also
$$\lambda x + (1-\lambda)y \in K$$, thus $$K$$ is a convex cone. ◻
</div></details>


<div class="corollary">
Let $$S \subset \mathbb{R}^n$$, and $$K$$ the set of all positive linear
combinations of $$S$$. Then, $$K$$ is the smallest convex cone which
contains $$S$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
$$K$$ is a convex cone by [\[thm:cone_closed\]](#thm:cone_closed), and
$$S \subset K$$, so $$K$$ is a convex cone containing $$S$$. On the
other hand, every convex cone containing $$S$$ must also contain $$U$$,
so $$K$$ is minimal. ◻
</div></details>


<div class="corollary">
Let $$C \subset \mathbb{R}^n$$ be a convex set. Then,
$$K = \{ \lambda x \mid \lambda > 0, \ x \in C\}$$ is the smallest
convex cone which includes $$C$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Consequence of the previous corollary. ◻
</div></details>


Now, we can define the notion of the cone generate by an arbitrary
subset, and relate it with an internal representation using the previous
results.

<div class="definition">
Given $$S \subset \mathbb{R}^n$$, $$\mathrm{cone}(S)$$ is the union of
the smallest convex cones containing $$S$$ and the origin:
$$\mathrm{cone}(S) = \{ 0 \} \cup \{ \lambda x \mid \lambda > 0, \ x \in S\}$$
= $$\{ \lambda x \mid \lambda \geq 0, \ x \in S\}$$.

</div>

It is then clear that $$\mathrm{cone}(S)$$ is the union of all the
positive linear combinations of elements of $$S$$ and the origin.

Finally, it is useful to note that every convex set
$$C \subset \mathbb{R}^n$$ can be regarded as a cross-section of some
convex cone $$K \subset \mathbb{R}^{n+1}$$. The construction involves
*lifting* $$C$$ to a higher dimension and generating its cone, as
follows: $$\begin{aligned}
    K &= \mathrm{cone}(\{ (1,x) \in \mathbb{R}^{n+1} \mid x \in C \})
      = \{(\lambda, \lambda x) \mid \lambda \geq 0, \ x \in C \}
\end{aligned}$$ Then, $$C = K \cap H_1$$, with the hyperplane
$$H_1 = \{ (1, y) \mid y \in \mathbb{R}^{n} \}$$.

## Topological notions

We consider the closed unit ball defined as
$$B = \{ x \in \mathbb{R}^n \mid |x| \leq 1\}$$.

For general subsets of $$\mathbb{R}^n$$, we define its closure and
interior as follows.

<div class="definition">
The *closure* of a subset $$S \subset \mathbb{R}^n$$ is
$$\mathrm{cl}(S) = \bigcap \{ S + \varepsilon B \mid \varepsilon > 0\}$$.

</div>
<div class="definition">
The *interior* of a subset $$S \subset \mathbb{R}^n$$ is
$$\mathrm{int}(S) = \{ x \mid \exists \varepsilon > 0, \ x + \varepsilon B \subset S \}$$.

</div>

However, for convex sets we can define a more convenient notion of
interior, that need not be of dimension $$n$$ and can instead have the
same dimension as the convex set itself.

<div class="definition">
The *relative interior* of a convex subset $$C \subset \mathbb{R}^n$$ is

$$\mathrm{ri}(C) = \{ x \in \mathrm{aff}(C) \mid \exists \varepsilon > 0, \ (x + \varepsilon B) \cap \mathrm{aff}(C) \subset C\}$$.

</div>
<div class="definition">
The *relative boundary* is
$$\mathrm{rb}(S) = \mathrm{cl}(S) \setminus \mathrm{ri}(S)$$.

</div>

Note that
$$\mathrm{ri}(S) \subset S \subset \mathrm{cl}(S) \subset \mathrm{aff}(S)$$.

Although the next theorem is not topological in nature (rather about the
internal representation of convex sets), it will be used to prove a
claim about compactness of convex hulls.

<div class="theorem">
<span id="thm:caratheodory"
label="thm:caratheodory"></span>**(Carathéodory)** Let
$$S \subset \mathbb{R}^n$$ be a non-empty subset. Then,

1.  Every $$x \in \mathrm{cone}(S)$$ can be represented as a positive
    linear combination of no more than $$n$$ points of $$S$$ which are
    linearly independent.

2.  Every $$x \in \mathrm{conv}(S)$$ can be represented as a convex
    combination of no more than $$n+1$$ elements of $$S$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
 

1.  Let $$x \in \mathrm{cone}(S)$$. Let $$m \in \mathbb{N}$$ be the
    smallest such that
    $$x = \sum_{i=1}^{m} \alpha_i x_i, \ \alpha_i > 0, \ x_i \in S$$.

    Suppose that $$x_i$$ are linearly dependent, so
    $$\exists \lambda_1,\ldots,\lambda_m \in \mathbb{R}$$ such that
    $$\sum_{i=1}^m \lambda_i x_i = 0$$ and at least one
    $$\lambda_i > 0$$ (we may always choose the coefficients such that
    at least one is positive). Consider
    $$\sum_{i=1}^m(\alpha_i - \bar \gamma \lambda_i) x_i$$, with
    $$\bar \gamma$$ the largest $$\gamma$$ such that
    $$\alpha_i - \gamma \lambda_i \geq 0 \ \forall i$$. In fact,
    $$\sum_{i=1}^m(\alpha_i - \bar \gamma \lambda_i) x_i = \sum_{i=1}^m \alpha_i x_i - \bar \gamma \sum_{i=1}^m \lambda_i x_i = \sum_{i=1}^m \alpha_i x_i + 0 = x$$.
    Note that at least one of the coefficients is $$0$$, so this
    provides a representation of $$x$$ with fewer than $$m$$ elements,
    which is a contradiction.

    Therefore, $$x_i$$ must be linearly independent when $$m$$ is
    minimal, and this implies $$m \leq n$$.

2.  We apply the previous result to the cone generated by *lifting* the
    convex set to a higher dimension. Let
    $$K = \mathrm{cone}(\{ (1,x) \in \mathbb{R}^{n+1} \mid x \in S \}) \subset \mathbb{R}^{n+1}$$
    such that
    $$\mathrm{conv}(S) = K \cap \{ (1, x) \mid x \in \mathbb{R}^n\} \subset \mathbb{R}^n$$.

    By the previous result, if
    $$y \in K \Rightarrow y = \sum_{i=1}^m w_i y_i, \ y_i \in K, \ w_i > 0, \ m \leq n+1$$.
    In particular, let $$y \in \{ (1, x) \mid x \in S\} \subset K$$.
    Thus, $$(1,x) = \sum_{i=1}^m w_i (1, x_i), \ x_i \in S$$. Therefore,
    $$\sum_{i=1}^m w_i x_i = x, \ \sum_{i=1}^m w_i = 1$$ so that $$x$$
    can be represented by a convex combination with $$m \leq n+1$$.

 ◻
</div></details>


This theorem is useful because it gives a finite and minimal
representation of the elements of an infinite set. However, the choice
of elements used to represent a given point is not uniquely determined,
and different points may need different \"basis\" elements.

<div class="corollary">
<span id="cor:compactness_convex" label="cor:compactness_convex"></span>
The convex hull of a compact set in $$\mathbb{R}^n$$ is compact.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Let $$S \subset \mathbb{R}^n$$ be compact. Take a sequence
$$(a_k)_{k \in \mathbb{N}} \subset \mathrm{conv}(S)$$. By Carathéodory’s
theorem, each element of the sequence $$a_k \in \mathrm{conv}(S)$$ can
be written as
$$a_k = \sum_{i=1}^{n+1}\lambda_i^k x_i^k, \ \lambda_i^k \geq 0, \ \sum_{i=1}^{n+1}\lambda_i^k = 1, \ x_i^k \in S$$.

Let $$(b_k)_{k \in \mathbb{N}}$$ be the sequence
$$(\lambda_1^k, \ldots, \lambda_{n+1}^k, x_1^k, \ldots, x_{n+1}^k)$$.
Note that the sequence is bounded, since $$0 \leq \lambda_i^k \leq 1$$
and $$x_i^k \in S$$. Thus, there exists a convergent subsequence
$$({b_k}_j)_{j \in \mathbb{N}}$$ converging to
$$(\lambda_1, \ldots, \lambda_{n+1}, x_1, \ldots, x_{n+1})$$ (by
Boltzano-Weierstrass’ theorem). This limit point must satisfy
$$\sum_{i=1}^{n+1} \lambda_i = 1, \ \lambda_i \geq 0, \ x_i \in S$$.
Therefore, $$\sum_{i=1}^{n+1} \lambda_i x_i \in \mathrm{conv}(S)$$, so
that $$\mathrm{conv}(S)$$ is compact. ◻
</div></details>


## Projections and separating hyperplanes

The proof of the separation theorem is based on the notion of the
projection of a point onto a convex set. This idea is captured by the
following theorem.

<div class="theorem">
<span id="thm:projection" label="thm:projection"></span>**(Projection
onto a convex set)** Let $$C \subset \mathbb{R}^n$$ a closed convex set.
Then,

1.  $$\forall x \in \mathbb{R}^n, \ \exists$$ a unique $$z_0 \in C$$
    that minimizes $$\|z-x\|$$ over all $$z \in C$$. We call $$z_0$$ the
    *projection of $$x$$ onto $$X$$*.

2.  $$z_0$$ is the projection of $$x$$ onto $$C$$
    $$\iff \langle y - z_0, x - z_0 \rangle \leq 0 \ \forall y \in C$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
 

1.  Let $$w \in C$$, and define the compact and convex set
    $$W = \{ z \in C \mid d(x,z) \leq d(x, w)\}$$. Note that
    $$f(z) = \|x -z\|$$ is continuous on $$W$$, so existance of a
    minimum in $$W$$ is guaranteed by Weierstrass’ theorem. Regarding
    uniqueness, suppose $$z_1, z_2 \in W$$, $$z_1 \neq z_2$$ are both
    minima of $$f$$, so $$f(z_1) = f(z_2) = m$$. Using the parallelogram
    identity, we have
    $$0 < \|z_1 - z_2\|^2 = \|(z_1-x) - (z_2 -x)\|^2 = 2 \|z1-x\|^2 + 2 \|z_2 - x\|^2 - \|z_1 + z_2 - 2x\|^2 = 4m^2 - 4 \|\hat z - x\|^2$$
    for $$\hat z = \frac{z_1 + z_2}{2} \in W$$ (convex combination).
    Then, $$\|\hat z - x\| = f(\hat z) < m$$, a contradiction.

2.  ($$\Leftarrow$$) $$\forall y, z \in C$$, we have
    $$\|y-x\|^2 = \|(y-z) - (x-z)\|^2 = \|y-z\|^2 + \|x-z\|^2 - \langle y-z, x-z \rangle \geq \|z-x\|^2 - 2 \langle y-z, x-z \rangle$$.
    Therefore, if $$z$$ is s.t.
    $$\langle y-z, x-z \rangle \leq 0 \ \forall y \in C$$, then
    $$\|z-x\| \leq \|y-x\| \ \forall y \in C$$, so $$z = z_0$$.
    ($$\Rightarrow$$) Conversely, consider $$z_0$$ to be the projection
    of $$x$$ onto $$C$$. Let $$y \in C$$ and define
    $$y_\alpha = (1-\alpha) z_0 + \alpha y$$ for $$\alpha > 0$$. Note
    that $$y_\alpha \in C$$ (convex combination). Define
    $$\varphi(\alpha) = \|x- y_\alpha\|^2$$. Then,
    $$\frac{\partial \varphi}{\partial \alpha}\vert_{\alpha = 0} = -2 \|x-z_0\| + 2 \langle x-z_0, x-y \rangle = -2 \langle x-z_0, y-z_0 \rangle$$.
    If $$\langle x-z_0, y-z_0 \rangle > 0$$ for some $$y \in C$$,
    $$\frac{\partial}{\partial \alpha}(\|x-y_\alpha\|^2)\vert_{\alpha = 0} < 0$$,
    so for $$\alpha$$ small we will have $$\|x-y_\alpha\| < \|x-z_0\|$$,
    a contradiction.

 ◻
</div></details>


Next, we introduce the notion of separating hyperplane between two
disjoint convex sets.

<div class="theorem">
<span id="thm:hyperplane_sep"
label="thm:hyperplane_sep"></span>**(Strict hyperplane separating
theorem)** Let $$C, K \subset \mathbb{R}^n$$ be nonempty disjoint convex
sets, $$K$$ compact and $$C$$ closed. Then, $$\exists$$ hyperplane
$$H = \{ x \mid \langle x, b \rangle = \beta \}$$ such that
$$C \subset \mathring{h}_H^+$$ and $$K \subset \mathring{h}_H^-$$ (that
is, $$H$$ *strictly separates* $$C$$ and $$K$$).

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Define $$f \colon K \rightarrow \mathbb{R}$$ such that $$f(x)$$ is the
distance from $$x \in K$$ to the $$C$$,
$$f(x) = \min \{ \|x-y\| \mid y \in C\}$$. By
[\[thm:projection\]](#thm:projection),
$$\forall x \in K \ \exists y_0 \in C$$ such that
$$f(x) = \|x - y_0\|$$, where $$y_0 = y_0(x)$$. Note that $$f(x)$$ is
continuous (in fact, Lipschitz): by the triangle inequality, we have
$$d(x',y) \leq d(x',x) + d(x', y)$$ and
$$d(x,y) \leq d(x, x') + d(x, y)$$ $$\forall x, x' \in K, y \in C$$, so
$$| f(x) - f(x') | \leq \|x - x'\|$$. By Weierstrass’ theorem, $$f(x)$$
has a minimum in $$K$$. Let $$x_0$$ be such a minimum, and note that
$$f(x_0) = \|x_0 - y_0\| > 0$$ since $$K \cap C = \emptyset$$. Define
$$b = x_0 - y_0$$, so
$$0 < \|b\|^2 = \langle b, x_0 - y_0 \rangle \Rightarrow \langle b, y_0 \rangle < \langle b, x_0 \rangle$$.

It only remains to show that
$$\langle b, y_0 \rangle \geq \langle b, y \rangle \ \forall y \in C$$
and
$$\langle b, x_0 \rangle \leq \langle b, x \rangle \ \forall x \in K$$.
Take $$y \in C$$ and define
$$z = (1-\lambda) y_0 + \lambda y, \ \lambda \in (0, 1)$$ (so
$$z \in C$$). Then, by definition of $$y_0$$,
$$\|x_0 - z\|^2 \geq \| x_0 - y_0\|^2 \Rightarrow 0 \geq \|x_0-y_0\|^2 - \|x_0 - y_0 - \lambda (y-y_0)\|^2 \Rightarrow 0 \geq 2 \lambda \langle x_0- y_0, y -y_0 \rangle - \lambda ^2 \| y- y_0\|^2 \Rightarrow 2 \langle b, y-y_0 \rangle \leq \lambda \|y-y_0\|^2$$.
Now, take $$\lambda \to 0$$, so
$$\langle b, y \rangle \leq \langle b,y_0 \rangle \ \forall y \in C$$. A
similar argument for $$x \in K$$ holds.

Then, take the hyperplane
$$H = \{ x \mid \langle x, b \rangle = \beta \}$$ with
$$\beta \in (\langle b, y_0 \rangle, \langle b, x_0 \rangle)$$. We have
shown that $$\forall x \in K, \langle x, b \rangle > \beta$$ and
$$\forall y \in C, \langle y, b \rangle < \beta$$, completing the
proof. ◻
</div></details>


In fact, the separation is not only strict, but $$C$$ and $$K$$ are in
disjoint closed half-spaces, so there is a gap between them. A similar
result shows that if we have two disjoint sets which are bounded and
open, then the existance of a separating hyperplane is also guaranteed,
but in this case there might not be any gap between them.

A similar result is the supporting hyperplane theorem. We first
establish the notion of a supporting hyperplane.

<div class="definition">
A closed half-space *supports* a convex set $$C$$ if it contains $$C$$
and its bounding hyperplane intersects with the boundary of $$C$$.

</div>
<div class="definition">
A hyperplane *supports* $$C$$ if one of its closed half-spaces supports
$$C$$.

</div>
<div class="theorem">
<span id="thm:support_hyp" label="thm:support_hyp"></span>**(Supporting
hyperplane theorem)** Let $$C$$ be a convex set, $$x_0 \in \partial C$$
(a point on its boundary). Then, $$\exists$$ a supporting hyperplane of
$$C$$ intersecting $$x_0$$ such that $$C$$ is contained in one of its
closed half-spaces.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Take a sequence $$(x_k)_{k \in \mathbb{N}}$$ that does not belong to
$$\mathrm{cl}(C)$$ and converges to $$x_0$$. Let $$\hat x_k$$ be the
projection of $$x_k$$ onto $$\mathrm{cl}(C)$$. Define
$$a_k = \frac{\hat x_k - x_k}{\|\hat x_k - x_k\|}$$. By
[\[thm:projection\]](#thm:projection),
$$\langle y - \hat x_k, x_k - \hat x_k \rangle \leq 0, \ \forall y \in C, k \in \mathbb{N} \Rightarrow \langle y, x_k - \hat x_k \rangle \leq  \langle x_k, x_k  - \hat x_k \rangle = \|x_k - \hat x_k\|^2 + \langle \hat x_k, x_k - \hat x_k \rangle \Rightarrow \langle y, x_k - \hat x_k \rangle \leq \langle \hat x_k, x_k - \hat x_k \rangle \Rightarrow \langle \hat x_k, a_k \rangle \leq \langle y , a_k \rangle$$
which results in the important inequality
$$\langle x_k, a_k \rangle \leq \langle y, a_k \rangle \ \forall y \in \mathrm{cl}(C), k \in \mathbb{N}$$.
Since the sequence $$(a_k)_{k \in \mathbb{N}}$$ is bounded
($$\|a_k\| = 1 \ \forall k$$), by Boltzano-Weierstrass’ theorem there
exists a convergent subsequence $$({a_k}_j)_{j \in \mathbb{N}}$$. Let
$$a_0$$ be the limit of such a sequence. Then,
$$\lim_{j \to \infty} \langle {x_k}_j, {a_k}_j \rangle \leq \lim_{j \to \infty} \langle y , {a_k}_j \rangle \ \Rightarrow \  \langle x_0, a_0 \rangle \leq \langle y, a_0 \rangle \ \forall y \in C$$.
We have thus constructed the supporting hyperplane
$$H = \{ x \mid \langle x, b \rangle = \beta \}$$ with
$$b = a_0, \ \beta = \langle a_0, x_0 \rangle$$, such that
$$C \subset h_H^+$$ and $$x_0 \in H$$. ◻
</div></details>


## Faces of convex sets

<div class="definition">
A *face* of a convex set $$C$$ is a convex subset $$F \subset C$$ such
that every closed line segment in $$C$$ with a relative interior point
in $$F$$ has both endpoints in $$F$$.

</div>

Note that $$\emptyset$$ and $$C$$ are faces of $$C$$.

<div class="definition">
The 0-dimensional faces of $$C$$ are the *extreme points* or *vertices*
of $$C$$. The 1-dim. faces are the *edges*. The (n-2)-dimensional faces
are the *ridges*. The (n-1)-dimensional faces are the *facets*.

</div>

The definition of face implies a stronger property involving arbitrary
convex subsets, not just line segments.

<div class="theorem">
Let $$C$$ be a convex set, and $$F$$ be a face of $$C$$. If $$D$$ is a
convex set in $$C$$ ($$D \subset C$$) such that $$\mathrm{ri}(D)$$ meets
$$F$$, then $$D \subset F$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Let $$z \in F \cap \mathrm{ri}(D)$$. If $$x \in D, \ x \neq z$$ then
$$\exists y \in D$$ such that
$$z \in \mathrm{ri}(\{ (1 - \lambda) x + \lambda y \mid \lambda \in (0,1)\})$$.
Since $$F$$ is a face, $$x, y \in F$$ by definition, so
$$D \subset F$$. ◻
</div></details>


This allows for some interesting results that give insights into the
nature of faces.

<div class="corollary">
If $$F$$ and $$F'$$ are faces of a convex set $$C$$ such that
$$\mathrm{ri}(F)$$ and $$\mathrm{ri}(F')$$ have a point in common, then
$$F = F'$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
$$F' \subset F$$ because $$\mathrm{ri}(F')$$ meets $$F$$, and likewise
$$F \subset F'$$. ◻
</div></details>


<div class="corollary">
<span id="cor:face_ri" label="cor:face_ri"></span> Let $$C$$ be a convex
set, and $$F$$ a face of $$C$$ other than $$C$$ itself. Then,
$$F \subset \mathrm{rb}(C)$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
If $$\mathrm{ri}(C)$$ met $$F$$, we would have $$C \subset F$$, and
therefore $$C = F$$, a contradiction. Therefore,
$$F \subset \mathrm{cl(C)} \setminus \mathrm{ri}(C) = \mathrm{rb}(C)$$. ◻
</div></details>


The following theorem claims that a convex set can be \"decomposed\" in
its faces.

<div class="theorem">
<span id="thm:face_partitioning" label="thm:face_partitioning"></span>
Let $$C$$ be a non-empty convex set, and $$U$$ the collection of all
relative interiors of non-empty faces of $$C$$. Then, $$U$$ is a
*partition* of $$C$$, that is, the sets in $$U$$ are disjoint and their
union is $$C$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Two alternative proofs are found in the references. They require further
development of the theory of faces not covered here. ◻
</div></details>


## Polyhedra and polytopes {#sec:polyh}

<div class="definition">
<span id="def:polyhedral" label="def:polyhedral"></span> A *polyhedral*
set in $$\mathbb{R}^n$$ is a set which can be expressed as the
intersection of some finite collection of closed half-spaces, that is,
as the set $$\{ x \in \mathbb{R}^n \mid \mathbf{B}x \leq b\}$$ for some
matrix $$\mathbf{B} \in \mathcal{M}_{m \times n}(\mathbb{R})$$ and some
vector $$b \in \mathbb{R}^n$$.

</div>

By corollary [\[thm:inequalities-convex\]](#thm:inequalities-convex), we
know that polyhedral sets must be convex. They can also be unbounded.
Note also that the class of convex sets defined as in
[\[thm:inequalities-convex\]](#thm:inequalities-convex) was more
general, and in this case we consider only a *finite* number of *closed*
half-spaces.

Note that equalities can also be included in the previous definition,
since an equality can always be expressed as two simultaneous
inequalities. Therefore, all affine sets are polyhedral. Furthermore,
note that they can be unbounded.

Polyhedral sets characterize convex sets which have a \"finite\"
external representation. However, a \"finite\" internal representation
can also be considered to define *polytopes*.

<div class="definition">
<span id="def:polytope" label="def:polytope"></span> A *polytope* is a
set which is the convex hull of a finite number of points.

</div>

We refer to *k-polytopes* as polytopes of dimension $$k$$. It is clear
that polytopes are convex sets, and are compact by corollary
[\[cor:compactness_convex\]](#cor:compactness_convex).

It turns out that polytopes are precisely bounded polyhedra. A proof of
this fact can be found in [@brondsted_introduction_1983], chapter 8.

The following is a nice property of polytopes.

<div class="proposition">
<span id="prop:vertex_centroid" label="prop:vertex_centroid"></span> The
vertex centroid of a polytope is contained inside it.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
Let the polytope be $$\mathrm{conv}(\{b_1, \ldots, b_m\})$$, with
$$b_i$$ its vertices. The vertex centroid is defined as the arithmetic
mean of the vertices, that is,
$$v_{\text{centre}} = \frac{1}{m}\sum_{i=1}^m b_i$$. Note that this is a
convex sum ($$\lambda_i = \frac{1}{m}$$), so by
[\[thm:convex_closed\]](#thm:convex_closed) $$v_{\text{centre}}$$ must
belong to $$\mathrm{conv}(\{b_1, \ldots, b_m\})$$. ◻
</div></details>


Finally, we introduce an important type of polytope.

<div class="definition">
An *m-simplex* is a set which is the convex hull of a set of $$m+1$$
affinely independent points.

</div>

Note that simplices are polytopes, but not all polytopes are simplices.
As an example, consider that triangles are 2-simplices, while squares
are 2-polytopes but not simplices.

We can explicitly count the number of k-faces of an n-simplex.

<div class="lemma">
The number of k-faces of an n-simplex is given by $$\binom{n+1}{k+1}$$.

</div>
<details markdown="1"><summary markdown="span">*Proof*</summary>
<div class="proof">
By induction. Denote by $$S(n,k)$$ the number of k-faces of an
n-simplex. The base case is trivial: a 1-simplex (segment) has 2 0-faces
and 1 1-face, so
$$S(1,0) = 2 = \binom{2}{1}, \ S(1,1) = 1 = \binom{2}{2}$$. Next, assume
that $$S(n-1, k) = \binom{(n-1) + 1}{k+1} = \binom{n}{k+1}$$. Now,
consider an n-simplex by adding an affinely independent vertex $$v$$ to
an existing (n-1)-simplex, named as *base*. Its total number of k-faces
will be the number of k-faces that do not include $$v$$ plus the number
of k-faces that do include $$v$$. The first is given precisely by the
number of k-faces of the base, $$S(n-1, k)$$. To count the latter,
consider that the k-faces that do not include $$v$$ are formed by taking
the (k-1)-faces of the base and joining them with $$v$$, so their count
is given by $$S(n-1, k-1)$$. Thus,
$$S(n, k) = S(n-1, k) + S(n-1, k-1) = \binom{n}{k+1} + \binom{n}{k} = \binom{n+1}{k+1}$$. ◻
</div></details>


## Cells and triangulations

<div class="definition">
<span id="def:cell" label="def:cell"></span> A *cell* is the relative
interior of a convex polyhedron.

</div>

Given a subset $$S \subset \mathbb{R}^n$$, if its convex hull results in
a polyhedron, we say that
$$\mathrm{cell}(S) = \mathrm{ri}(\mathrm{conv}(S))$$. Then, any face of
a convex polyhedron is also a cell.

<div class="definition">
<span id="def:cell_complex" label="def:cell_complex"></span> A *cell
complex* is a finite collection of pairwise disjoint cells such that
every face of every cell is in the collection.

</div>
<div class="definition">
<span id="def:triangulation" label="def:triangulation"></span> A
*triangulation* $$T$$ of a finite point set $$S$$ is a cell complex
whose union is $$\mathrm{conv}(S)$$ and whose vertex set is $$S$$.

</div>

Note that any cell of a triangulation is $$\mathrm{cell}(R)$$ for some
$$R \subset S$$. Also, observe that a triangulation cannot be unbounded.

<div class="definition">
<span id="def:proper_triang" label="def:proper_triang"></span> A *proper
triangulation* is a triangulation where all cells are simplices.

</div>

It is important to note that all triangulations can be *completed* to a
proper triangulation by appropriately subdividing nonsimplical cells.

Finally, it is enlightening to understand that a compact convex
polyhedron can be partitioned not just into a cell complex, but into a
*triangulation of the set of its vertices*: each cell corresponds to the
realitive interior of a face of the polyhedron, as theorem
[\[thm:face_partitioning\]](#thm:face_partitioning) suggests.



## References
- R. T. Rockafellar, *Convex analysis*, Princeton University Press, 1997.
- A. Brondsted, *An introduction to convex polytopes*, Springer, 1983.


