---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 22
title: "Path Connectedness of $GL_n(\\mathbb{C})$ and Special Linear Groups"
coverage: >
  Proves that the complex general linear group GL_n(C) is path connected using an
  affine line in the matrix space and dodging the finitely many roots of its
  determinant polynomial in the complex plane. Proves that the continuous image
  of a path-connected space is path connected, and applies this to establish that
  both SL_n(R) and SL_n(C) are path connected via column-scaling retractions.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 0
depends_on:
  - lecture: 21
    title: "Path Connectedness of $GL_n(\\mathbb{R})^+$"
    relationship: "Supplies path connectedness of $GL_n(\\mathbb{R})^+$, which serves as domain for the retraction onto $SL_n(\\mathbb{R})$."
  - lecture: 19
    title: "Path Connectedness and Path Components"
    relationship: "Supplies definitions of path and path connectedness, and path connectedness of $\\mathbb{C} \\setminus \\{F\\}$."
  - lecture: 7
    title: "Continuous Maps: Topological Definition and Examples"
    relationship: "Supplies continuity of polynomial coordinate maps and composition of continuous maps."
used_in:
  - lecture: 23
    title: "Compact Spaces and the Hausdorff Property"
    relationship: "Concludes Part III (Connectedness); Part IV begins compactness and separation."
notation:
  - symbol: '$GL_n(\mathbb{C})$'
    gloss: 'The topological group of $n \times n$ invertible complex matrices'
  - symbol: '$SL_n(\mathbb{R}), SL_n(\mathbb{C})$'
    gloss: 'Special linear groups of $n \times n$ matrices with determinant 1'
  - symbol: '$p(t) = \det(\gamma(t))$'
    gloss: 'Determinant polynomial along an affine matrix segment'
prev: lecture-21
next: lecture-23
---

# Lecture 22 — Path Connectedness of $GL_n(\mathbb{C})$ and Special Linear Groups

In Lecture 21, we proved that $GL_n(\mathbb{R})^+$, the group of real matrices with strictly positive determinant, is path connected through an induction on dimension that required four reduction steps. In this lecture, we turn to the complex general linear group:
$$GL_n(\mathbb{C}) = \lbrace A \in M_n(\mathbb{C}) : \det(A) \ne 0 \rbrace.$$
Remarkably, $GL_n(\mathbb{C})$ is path connected via a direct, one-step proof that exploits the two-dimensional nature of the complex plane: along an affine line of matrices, the determinant is a non-zero polynomial having at most $n$ complex roots, and because the complex plane minus finitely many points is path connected, we can simply detour around every root.

We then prove the general topological principle that the continuous image of a path-connected space is path connected, and use it to establish that the special linear groups $SL_n(\mathbb{R})$ and $SL_n(\mathbb{C})$ are path connected as continuous images under column-scaling retractions.

---

## Path connectedness of $GL_n(\mathbb{C})$

To show that $GL_n(\mathbb{C})$ is path connected, we show that any matrix $A \in GL_n(\mathbb{C})$ can be joined to the identity matrix $I_n$ by a continuous path lying entirely within $GL_n(\mathbb{C})$.

### Proposition 22.1 ($GL_n(\mathbb{C})$ is path connected) {#proposition-22-1-gln-c-path-connected}

{% capture prop221_content %}
For every integer $n \ge 1$, the complex general linear group $GL_n(\mathbb{C})$, equipped with the subspace topology from $M_n(\mathbb{C}) \cong \mathbb{C}^{n^2} \cong \mathbb{R}^{2n^2}$, is **path connected** (and therefore connected).
{% endcapture %}
{% include block.html type="proposition" title="Proposition 22.1 (Path Connectedness of $GL_n(\mathbb{C})$)" content=prop221_content %}

{% capture prop221_proof %}
Let $A \in GL_n(\mathbb{C})$. We must find a continuous path in $GL_n(\mathbb{C})$ joining $A$ to the identity matrix $I_n$.

**Step 1: The complex affine line of matrices.**
Consider the affine map $\gamma \colon \mathbb{C} \to M_n(\mathbb{C})$ defined for any complex parameter $t \in \mathbb{C}$ by:
$$\gamma(t) = t I_n + (1 - t) A.$$
Observe the values at $0$ and $1$:
- At $t = 0$: $\gamma(0) = 0 \cdot I_n + (1 - 0)A = A$.
- At $t = 1$: $\gamma(1) = 1 \cdot I_n + (1 - 1)A = I_n$.

For each $t \in \mathbb{C}$, $\gamma(t)$ is an $n \times n$ matrix whose entries are degree-$1$ polynomials in $t$.

**Step 2: The determinant polynomial and its roots.**
Define the function $p \colon \mathbb{C} \to \mathbb{C}$ by:
$$p(t) = \det(\gamma(t)).$$
Because the determinant is a polynomial in the matrix entries, and each entry of $\gamma(t)$ is affine in $t$, $p(t)$ is a polynomial in $t$ with complex coefficients, of degree at most $n$:
$$\deg p(t) \le n.$$
We claim that $p(t)$ is not the zero polynomial. Let us check its value at $t = 0$:
$$p(0) = \det(\gamma(0)) = \det(A) \ne 0,$$
since $A \in GL_n(\mathbb{C})$. (Similarly, $p(1) = \det(\gamma(1)) = \det(I_n) = 1 \ne 0$.)
Because $p(t)$ is a non-zero polynomial of degree at most $n$, it has at most $n$ distinct roots in $\mathbb{C}$:
$$\lbrace \lambda \in \mathbb{C} : p(\lambda) = 0 \rbrace = \lbrace \lambda_1, \lambda_2, \dots, \lambda_r \rbrace, \qquad r \le n.$$
Moreover, neither $0$ nor $1$ is a root, because $p(0) = \det(A) \ne 0$ and $p(1) = 1 \ne 0$.

**Step 3: Root avoidance in the complex plane.**
The set of roots $F = \{\lambda_1, \dots, \lambda_r\}$ is a finite subset of $\mathbb{C} \cong \mathbb{R}^2$, and $0, 1 \in \mathbb{C} \setminus F$.
Because removing finitely many points from the plane does not disconnect it ([Lecture 19]({{ site.baseurl }}/point-set-topology/lecture-19/#examples-of-path-connected-spaces)), the open set $\mathbb{C} \setminus F$ is **path connected**.
Therefore, there exists a continuous path:
$$S \colon [0, 1] \longrightarrow \mathbb{C}$$
such that:
- $S(0) = 0$,
- $S(1) = 1$, and
- $S(t) \notin \lbrace \lambda_1, \dots, \lambda_r \rbrace$ for all $t \in [0, 1]$.

**Step 4: The composite path in $GL_n(\mathbb{C})$.**
Now consider the composition:
$$\Gamma = \gamma \circ S \colon [0, 1] \longrightarrow M_n(\mathbb{C}), \qquad \Gamma(t) = \gamma(S(t)).$$
Let us verify each required property of $\Gamma$:
1. **Target space:** For every $t \in [0, 1]$, we have $\det(\Gamma(t)) = \det(\gamma(S(t))) = p(S(t))$. Since $S(t)$ misses all the roots $\lambda_1, \dots, \lambda_r$, we have $p(S(t)) \ne 0$. Therefore $\det(\Gamma(t)) \ne 0$, so $\Gamma(t) \in GL_n(\mathbb{C})$ for all $t \in [0, 1]$.
2. **Continuity:** The map $S \colon [0, 1] \to \mathbb{C}$ is continuous, and $\gamma \colon \mathbb{C} \to M_n(\mathbb{C})$ is continuous (each coordinate is affine in $t$). Thus the composite $\Gamma = \gamma \circ S$ is continuous.
3. **Endpoints:** At $t = 0$:
   $$\Gamma(0) = \gamma(S(0)) = \gamma(0) = A.$$
   At $t = 1$:
   $$\Gamma(1) = \gamma(S(1)) = \gamma(1) = I_n.$$

Thus, $\Gamma$ is a continuous path in $GL_n(\mathbb{C})$ joining $A$ to $I_n$.

Since every matrix $A \in GL_n(\mathbb{C})$ can be joined to $I_n$ by a continuous path in $GL_n(\mathbb{C})$, any two matrices $A, B \in GL_n(\mathbb{C})$ can be connected by concatenating the path from $A$ to $I_n$ with the reverse of the path from $B$ to $I_n$.
This proves that $GL_n(\mathbb{C})$ is path connected, and therefore connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 22.1" content=prop221_proof %}

{% include figure.html
   src="point-set-topology/lecture-22/complex-polynomial-root-avoidance.svg"
   num="22.1"
   caption="Root avoidance in the complex plane $\mathbb{C}$: the direct line segment between $0$ and $1$ may pass through a root $\lambda_1$ where the determinant vanishes, but because $\mathbb{C} \setminus \{\lambda_1, \dots, \lambda_r\}$ is path connected, a continuous detour $S(t)$ connects $0$ to $1$ while maintaining $\det(\gamma(S(t))) \ne 0$ everywhere."
   alt="The complex plane showing points 0 and 1, isolated roots, and a path S(t) dodging the roots." %}

---

## Continuous images of path-connected spaces

We now establish that path connectedness is preserved by continuous maps, in exact parallel with the theorem for connectedness proved in [Lecture 16]({{ site.baseurl }}/point-set-topology/lecture-16/#theorem-16-5-continuous-images-of-connected-spaces-are-connected).

### Lemma 22.2 (Continuous image of a path-connected space is path connected) {#lemma-22-2-continuous-image-path-connected}

{% capture lem222_content %}
Let $X$ and $Y$ be topological spaces, and let $f \colon X \to Y$ be a continuous map.
If $X$ is path connected, then its image $f(X)$, equipped with the subspace topology from $Y$, is **path connected**.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 22.2 (Continuous Images of Path-Connected Spaces)" content=lem222_content %}

{% capture lem222_proof %}
Recall that if $f \colon X \to Y$ is continuous, viewing $f$ as a map from $X$ to $f(X)$ equipped with the subspace topology yields a continuous map $f \colon X \to f(X)$ ([Lecture 7]({{ site.baseurl }}/point-set-topology/lecture-07/#definition-of-a-continuous-map)).

We want to show that $f(X)$ is path connected.
Let $y_1, y_2 \in f(X)$ be any two points in the image.
By definition of the image, there exist points $x_1, x_2 \in X$ such that:
$$f(x_1) = y_1 \quad \text{and} \quad f(x_2) = y_2.$$
Since $X$ is path connected, there exists a continuous path $\gamma \colon [0, 1] \to X$ joining $x_1$ to $x_2$:
$$\gamma(0) = x_1 \quad \text{and} \quad \gamma(1) = x_2.$$
Now consider the composite map:
$$f \circ \gamma \colon [0, 1] \longrightarrow f(X).$$
Let us verify the defining properties of $f \circ \gamma$:
1. **Continuity:** As the composition of continuous maps $\gamma \colon [0, 1] \to X$ and $f \colon X \to f(X)$, the map $f \circ \gamma$ is continuous.
2. **Endpoints:**
   $$(f \circ \gamma)(0) = f(\gamma(0)) = f(x_1) = y_1,$$
   $$(f \circ \gamma)(1) = f(\gamma(1)) = f(x_2) = y_2.$$

Thus $f \circ \gamma$ is a continuous path in $f(X)$ joining $y_1$ and $y_2$.
Since $y_1, y_2 \in f(X)$ were arbitrary, this proves that $f(X)$ is path connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 22.2" content=lem222_proof %}

{% include figure.html
   src="point-set-topology/lecture-22/path-connected-continuous-image.svg"
   num="22.2"
   caption="Preservation of path connectedness under continuous maps: any two points $y_1, y_2 \in f(X)$ are images of points $x_1, x_2 \in X$. The path $\gamma$ connecting $x_1$ to $x_2$ pushes forward to a continuous path $f \circ \gamma$ connecting $y_1$ to $y_2$."
   alt="Domain space X with path gamma mapped by continuous map f to subspace f(X) with path f o gamma." %}

### Corollary 22.3 (Surjective continuous image is path connected) {#corollary-22-3-surjective-continuous-image}

{% capture cor223_content %}
Let $f \colon X \to Y$ be a continuous, surjective map between topological spaces.
If $X$ is path connected, then $Y$ is **path connected**.
{% endcapture %}
{% include block.html type="corollary" title="Corollary 22.3 (Surjections from Path-Connected Spaces)" content=cor223_content %}

{% capture cor223_proof %}
Because $f$ is surjective, the image $f(X)$ is all of $Y$. By [Lemma 22.2](#lemma-22-2-continuous-image-path-connected), $f(X) = Y$ is path connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Corollary 22.3" content=cor223_proof %}

---

## Path connectedness of the special linear groups

As an application of Corollary 22.3, we prove that the special linear groups $SL_n(\mathbb{R})$ and $SL_n(\mathbb{C})$ are path connected.

Recall that the special linear group $SL_n(\mathbb{R})$ consists of all $n \times n$ real matrices with determinant equal to $1$:
$$SL_n(\mathbb{R}) = \lbrace A \in M_n(\mathbb{R}) : \det(A) = 1 \rbrace.$$

### Theorem 22.4 ($SL_n(\mathbb{R})$ is path connected) {#theorem-22-4-sln-r-path-connected}

{% capture thm224_content %}
For every integer $n \ge 1$, the special linear group $SL_n(\mathbb{R})$, equipped with the subspace topology from $M_n(\mathbb{R})$, is **path connected** (and therefore connected).
{% endcapture %}
{% include block.html type="theorem" title="Theorem 22.4 (Path Connectedness of $SL_n(\mathbb{R})$)" content=thm224_content %}

{% capture thm224_proof %}
In order to show that $SL_n(\mathbb{R})$ is path connected, it suffices by [Corollary 22.3](#corollary-22-3-surjective-continuous-image) to construct a continuous, surjective map from a known path-connected space onto $SL_n(\mathbb{R})$.
By [Theorem 21.1]({{ site.baseurl }}/point-set-topology/lecture-21/#theorem-21-1-gln-plus-path-connected), $GL_n(\mathbb{R})^+$ is path connected.
We construct a map:
$$f \colon GL_n(\mathbb{R})^+ \longrightarrow SL_n(\mathbb{R})$$
by dividing every entry in the first column of a matrix $A$ by $\det(A)$, leaving all other columns unchanged:
$$f(A) = \begin{pmatrix} \frac{A_{11}}{\det(A)} & A_{12} & \cdots & A_{1n} \\ \frac{A_{21}}{\det(A)} & A_{22} & \cdots & A_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ \frac{A_{n1}}{\det(A)} & A_{n2} & \cdots & A_{nn} \end{pmatrix}.$$

Let us verify that $f$ has the required properties:

**Step 1: Well-defined map into $SL_n(\mathbb{R})$.**
Since the first column of $A$ has been scaled by the scalar factor $\frac{1}{\det(A)}$, multilinearity of the determinant gives:
$$\det(f(A)) = \frac{1}{\det(A)} \cdot \det(A) = 1.$$
Therefore $f(A) \in SL_n(\mathbb{R})$ for every $A \in GL_n(\mathbb{R})^+$.

**Step 2: Surjectivity.**
Consider the inclusion $i \colon SL_n(\mathbb{R}) \hookrightarrow GL_n(\mathbb{R})^+$.
For any matrix $M \in SL_n(\mathbb{R})$, we have $\det(M) = 1$.
Applying $f$ to $M$, the scalar factor is $\frac{1}{\det(M)} = \frac{1}{1} = 1$, so:
$$f(M) = M.$$
Thus $(f \circ i)(M) = M$ for all $M \in SL_n(\mathbb{R})$; that is, $f \circ i = \operatorname{id}_{SL_n(\mathbb{R})}$.
This shows that every matrix in $SL_n(\mathbb{R})$ is in the image of $f$, so $f$ is **surjective**.

**Step 3: Continuity.**
The group $SL_n(\mathbb{R})$ has the subspace topology from $M_n(\mathbb{R})$. Let $j \colon SL_n(\mathbb{R}) \hookrightarrow M_n(\mathbb{R})$ denote the inclusion.
A map into a subspace is continuous if and only if the composite with the inclusion is continuous ([Lecture 7]({{ site.baseurl }}/point-set-topology/lecture-07/#definition-of-a-continuous-map)).
Thus $f$ is continuous if and only if:
$$j \circ f \colon GL_n(\mathbb{R})^+ \longrightarrow M_n(\mathbb{R})$$
is continuous.
Because $M_n(\mathbb{R}) \cong \mathbb{R}^{n^2}$ has the product topology, $j \circ f$ is continuous if and only if each of its $n^2$ coordinate functions is continuous.
Let us inspect the coordinate functions:
- For entries in the first column ($j = 1$): the $(i, 1)$ coordinate is:
  $$A \longmapsto \frac{A_{i1}}{\det(A)}.$$
  The coordinate projection $A \mapsto A_{i1}$ is continuous. The determinant map $\det \colon GL_n(\mathbb{R})^+ \to (0, \infty)$ is a continuous polynomial function that does not vanish on $GL_n(\mathbb{R})^+$. Since the reciprocal function $x \mapsto 1/x$ is continuous on $(0, \infty)$, the map $A \mapsto 1/\det(A)$ is continuous. The product of continuous functions is continuous, so $A \mapsto \frac{A_{i1}}{\det(A)}$ is continuous.
- For entries in all subsequent columns ($j > 1$): the $(i, j)$ coordinate is:
  $$A \longmapsto A_{ij},$$
  which is simply the standard coordinate projection, hence continuous.

Since all coordinate functions of $j \circ f$ are continuous, $j \circ f$ is continuous, and therefore $f \colon GL_n(\mathbb{R})^+ \to SL_n(\mathbb{R})$ is continuous.

**Conclusion:**
We have shown that $f \colon GL_n(\mathbb{R})^+ \to SL_n(\mathbb{R})$ is continuous and surjective.
Since $GL_n(\mathbb{R})^+$ is path connected by Theorem 21.1, [Corollary 22.3](#corollary-22-3-surjective-continuous-image) implies that $SL_n(\mathbb{R})$ is path connected, and hence connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 22.4" content=thm224_proof %}

{% include figure.html
   src="point-set-topology/lecture-22/special-linear-retraction.svg"
   num="22.3"
   caption="The column-scaling retraction $f \colon GL_n \to SL_n$: dividing the first column by $\det(A)$ normalizes the determinant to $1$, yielding a continuous surjection whose domain is path connected."
   alt="A diagram showing matrix A with column 1 scaled by 1/det(A) to produce matrix f(A) with determinant 1." %}

---

### Theorem 22.5 ($SL_n(\mathbb{C})$ is path connected) {#theorem-22-5-sln-c-path-connected}

{% capture thm225_content %}
For every integer $n \ge 1$, the complex special linear group $SL_n(\mathbb{C}) = \lbrace A \in M_n(\mathbb{C}) : \det(A) = 1 \rbrace$, equipped with the subspace topology from $M_n(\mathbb{C})$, is **path connected** (and therefore connected).
{% endcapture %}
{% include block.html type="theorem" title="Theorem 22.5 (Path Connectedness of $SL_n(\mathbb{C})$)" content=thm225_content %}

{% capture thm225_proof %}
The proof is identical to that of Theorem 22.4, replacing the real field with the complex field.
We define the map:
$$f \colon GL_n(\mathbb{C}) \longrightarrow SL_n(\mathbb{C})$$
by scaling the first column of $A \in GL_n(\mathbb{C})$ by $\frac{1}{\det(A)}$:
$$f(A) = \begin{pmatrix} \frac{A_{11}}{\det(A)} & A_{12} & \cdots & A_{1n} \\ \frac{A_{21}}{\det(A)} & A_{22} & \cdots & A_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ \frac{A_{n1}}{\det(A)} & A_{n2} & \cdots & A_{nn} \end{pmatrix}.$$
Let us verify the defining properties:
1. **Well-defined:** $\det(f(A)) = \frac{1}{\det(A)} \cdot \det(A) = 1$, so $f(A) \in SL_n(\mathbb{C})$.
2. **Surjective:** For any $M \in SL_n(\mathbb{C})$, $\det(M) = 1$, so $f(M) = M$, showing that $f$ is surjective.
3. **Continuous:** Since $\det(A) \ne 0$ for all $A \in GL_n(\mathbb{C})$, the reciprocal $1/\det(A)$ is continuous from $GL_n(\mathbb{C})$ to $\mathbb{C} \setminus \{0\}$. Thus every coordinate function of $f$ is continuous, making $f$ continuous into $SL_n(\mathbb{C})$ with the subspace topology.

By [Proposition 22.1](#proposition-22-1-gln-c-path-connected), $GL_n(\mathbb{C})$ is path connected.
Applying [Corollary 22.3](#corollary-22-3-surjective-continuous-image) to the continuous surjection $f$, it follows that $SL_n(\mathbb{C})$ is path connected, and hence connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 22.5" content=thm225_proof %}

---

## At a glance

- [Proposition 22.1 ($GL_n(\mathbb{C})$ is Path Connected)](#proposition-22-1-gln-c-path-connected): One-step proof connecting $A$ to $I_n$ by avoiding the at most $n$ roots of $p(t) = \det(t I_n + (1-t)A)$ in $\mathbb{C}$.
- [Lemma 22.2 (Continuous Image of Path-Connected Space)](#lemma-22-2-continuous-image-path-connected): If $X$ is path connected and $f \colon X \to Y$ is continuous, then $f(X)$ is path connected via the pushed-forward path $f \circ \gamma$.
- [Corollary 22.3 (Surjective Continuous Image)](#corollary-22-3-surjective-continuous-image): If $f \colon X \to Y$ is continuous and surjective with $X$ path connected, then $Y$ is path connected.
- [Theorem 22.4 ($SL_n(\mathbb{R})$ is Path Connected)](#theorem-22-4-sln-r-path-connected): Proven by the continuous surjection $f \colon GL_n(\mathbb{R})^+ \to SL_n(\mathbb{R})$ scaling the first column by $1/\det(A)$.
- [Theorem 22.5 ($SL_n(\mathbb{C})$ is Path Connected)](#theorem-22-5-sln-c-path-connected): Proven by the corresponding continuous surjection from $GL_n(\mathbb{C})$.

---

## Where we are

This lecture concludes **Part III — Connectedness (Lectures 16–22)**. Across this part, we have established:
- Connectedness of intervals in $\mathbb{R}$, products $X \times Y$, Euclidean spaces $\mathbb{R}^n$, and spheres $S^n$ (Lectures 16–17).
- Connected components as maximal connected closed subsets (Lecture 18).
- Path connectedness and path components, with the comb space distinguishing the two notions (Lectures 19–20).
- Path connectedness of the classical matrix groups $GL_n(\mathbb{R})^+$, $GL_n(\mathbb{C})$, $SL_n(\mathbb{R})$, and $SL_n(\mathbb{C})$ (Lectures 21–22).

In the next lecture ([Lecture 23]({{ site.baseurl }}/point-set-topology/lecture-23/)), we begin **Part IV — Compactness, Quotients, and Separation Axioms**, introducing Hausdorff spaces and open cover compactness.

---

## Further reading

- **Morris, *Topology Without Tears***, Chapter 5: *Connectedness* (connected topological groups).
- **Munkres, *Topology* (2nd ed.)**, §24: *Connected Subspaces of the Real Line*.