---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 21
title: "Path Connectedness of $GL_n(\\mathbb{R})^+$"
coverage: >
  Sketches the proof by induction on matrix dimension that the general linear
  group of real matrices with positive determinant, GL_n(R)^+, is path connected.
  Reduces the problem to connecting any matrix to the identity via four successive
  steps: perturbation to non-zero corner entry, elimination to block diagonal form
  using elementary matrices, normalization of the scalar factor via scaling or 2x2
  rotation paths, and induction on the sub-block. Incorporates an Open Question
  block capturing the board-only matrix derivations, accompanied by standard
  algebraic supplements.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 0
depends_on:
  - lecture: 19
    title: "Path Connectedness and Path Components"
    relationship: "Supplies path connectedness and path concatenation via the Pasting Lemma."
  - lecture: 11
    title: "Closed Sets, Dual Axioms, and Preimages"
    relationship: "Supplies the topology on matrix groups and openness of GL_n(R)."
  - lecture: 7
    title: "Continuous Maps: Topological Definition and Examples"
    relationship: "Supplies continuity of polynomial coordinate maps on Euclidean spaces."
used_in:
  - lecture: 22
    title: "Path Connectedness of $GL_n(\\mathbb{C})$ and Special Linear Groups"
    relationship: "Generalizes path connectedness to complex matrix groups and special linear groups."
notation:
  - symbol: "$GL_n(\\mathbb{R})^+$"
    gloss: 'The topological group of $n \\times n$ real matrices with positive determinant'
  - symbol: "$E_1, E_2$"
    gloss: 'Elementary unitriangular matrices clearing row and column entries'
  - symbol: "$I_n$"
    gloss: 'The $n \\times n$ identity matrix'
prev: lecture-20
next: lecture-22
---

# Lecture 21 — Path Connectedness of $GL_n(\mathbb{R})^+$

In Lecture 19, we observed that while the full general linear group $GL_n(\mathbb{R})$ is disconnected by the determinant map into two components, the subgroup of matrices with strictly positive determinant:
$$GL_n(\mathbb{R})^+ = \lbrace A \in M_n(\mathbb{R}) : \det(A) > 0 \rbrace$$
cannot be disconnected by this argument. In this lecture, we sketch a constructive proof by induction on the dimension $n$ that $GL_n(\mathbb{R})^+$ is **path connected**. We show that every matrix $A \in GL_n(\mathbb{R})^+$ can be connected by a continuous path within $GL_n(\mathbb{R})^+$ to the identity matrix $I_n$ through four reduction steps: perturbing the top-left entry to be non-zero, eliminating row and column entries via elementary matrices, normalizing the pivot sign, and applying the induction hypothesis to the remaining $(n-1) \times (n-1)$ block.

---

## The reduction strategy

Let $G = GL_n(\mathbb{R})^+$. To show that $G$ is path connected, it suffices to show that any matrix $A \in G$ can be joined to the identity matrix $I_n$ by a continuous path lying entirely inside $G$.

Indeed, if every matrix $A \in G$ can be connected to $I_n$, then for any two matrices $A, B \in G$, there is a path from $A$ to $I_n$ and a path from $I_n$ to $B$. By concatenating these two paths ([Lecture 19]({{ site.baseurl }}/point-set-topology/lecture-19/#proposition-19-4-path-equivalence-is-an-equivalence-relation)), there exists a continuous path joining $A$ to $B$ in $G$.

{% include figure.html
   src="point-set-topology/lecture-21/gln-path-to-identity.svg"
   num="21.1"
   caption="The reduction strategy in $GL_n(\mathbb{R})^+$: connecting matrix $A$ to $I_n$ via intermediate matrices $B$ (non-zero corner), $C$ (block diagonal), and $C'$ (normalized corner), followed by induction on the lower block."
   alt="A multi-step path in GL_n(R)+ from A to B to C to C' to the identity matrix." %}

---

## Theorem 21.1 ($GL_n(\mathbb{R})^+$ is path connected) {#theorem-21-1-gln-plus-path-connected}

{% capture thm211_content %}
For every integer $n \ge 1$, the topological group $GL_n(\mathbb{R})^+$, equipped with the subspace topology from $M_n(\mathbb{R}) \cong \mathbb{R}^{n^2}$, is **path connected** (and therefore connected).
{% endcapture %}
{% include block.html type="theorem" title="Theorem 21.1 (Path Connectedness of $GL_n(\mathbb{R})^+$)" content=thm211_content %}

{% capture thm211_proof %}
We proceed by induction on $n$.
For $n = 1$, $GL_1(\mathbb{R})^+ = (0, \infty) \subseteq \mathbb{R}$. For any two positive numbers $a, b > 0$, the straight-line segment $(1-t)a + tb$ is positive for all $t \in [0, 1]$, so $GL_1(\mathbb{R})^+$ is path connected.

Now assume that $GL_{n-1}(\mathbb{R})^+$ is path connected for some $n \ge 2$.
Let $A \in GL_n(\mathbb{R})^+$. We connect $A$ to $I_n$ in four steps.

---

### Step 1: Connecting $A$ to a matrix with non-zero corner entry

We claim that $A$ can be joined by a path in $GL_n(\mathbb{R})^+$ to a matrix $B \in GL_n(\mathbb{R})^+$ such that $B_{11} \ne 0$.

Let us verify this claim:
- **Case 1: $A_{11} \ne 0$.**
  If the top-left entry $A_{11}$ is already non-zero, we simply take the constant path:
  $$\gamma(t) = A \quad \text{for all } t \in [0, 1].$$
  The constant path is continuous, and we take $B = A$.
- **Case 2: $A_{11} = 0$.**
  Because the determinant map $\det \colon M_n(\mathbb{R}) \to \mathbb{R}$ is continuous and $GL_n(\mathbb{R})^+ = \det^{-1}((0, \infty))$, the space $GL_n(\mathbb{R})^+$ is an open subset of $M_n(\mathbb{R})$.
  Since $M_n(\mathbb{R}) \cong \mathbb{R}^{n^2}$ has the product topology, there exists $\varepsilon > 0$ such that the open neighborhood:
  $$U = \lbrace M \in M_n(\mathbb{R}) : |M_{ij} - A_{ij}| < \varepsilon \text{ for all } 1 \le i, j \le n \rbrace$$
  is completely contained in $GL_n(\mathbb{R})^+$.
  Choose any matrix $B \in U$ such that $B_{11} \ne 0$ (for example, setting $B_{11} = \varepsilon/2$ and $B_{ij} = A_{ij}$ for $(i, j) \ne (1, 1)$).
  Now consider the straight-line segment:
  $$\gamma(t) = tA + (1 - t)B, \qquad t \in [0, 1].$$
  For each entry:
  $$|\gamma(t)_{ij} - A_{ij}| = |tA_{ij} + (1 - t)B_{ij} - A_{ij}| = (1 - t)|B_{ij} - A_{ij}| < (1 - t)\varepsilon \le \varepsilon.$$
  Therefore $\gamma(t) \in U \subseteq GL_n(\mathbb{R})^+$ for all $t \in [0, 1]$.
  The map $\gamma$ is a polynomial in $t$, hence continuous, with $\gamma(0) = B$ and $\gamma(1) = A$.
  Reversing this path gives a continuous path in $GL_n(\mathbb{R})^+$ from $A$ to $B$ with $B_{11} \ne 0$.

---

### Step 2: Elimination to a block diagonal matrix via elementary matrices

Let $B \in GL_n(\mathbb{R})^+$ with $B_{11} = \lambda \ne 0$. We now connect $B$ to a block diagonal matrix:
$$C = \begin{pmatrix} \lambda & 0 \\ 0 & D \end{pmatrix},$$
where all remaining entries in the first row and first column are zero.

There exists a lower unitriangular elementary matrix $E_1$ (having $1$s on the diagonal, entries in the first column, and zeros elsewhere) that performs row operations subtracting multiples of the first row from subsequent rows, so that $E_1 B$ has zeros in the first column beneath the $(1, 1)$ entry.
Similarly, there exists an upper unitriangular elementary matrix $E_2$ (having $1$s on the diagonal, entries in the first row, and zeros elsewhere) that performs column operations clearing the first row of $E_1 B$ to the right of the $(1, 1)$ entry, producing:
$$E_1 B E_2 = \begin{pmatrix} \lambda & 0 \\ 0 & D \end{pmatrix} = C.$$

We connect $B$ to $C$ via the path:
$$\gamma(t) = \bigl((1 - t)I_n + t E_1\bigr) \cdot B \cdot \bigl((1 - t)I_n + t E_2\bigr), \qquad t \in [0, 1].$$
Let us check the defining properties of this path:
1. **Determinant:** Because $E_1$ is unitriangular, $(1 - t)I_n + t E_1$ is a triangular matrix with $1$s along the entire main diagonal for all $t \in [0, 1]$. Hence $\det((1 - t)I_n + t E_1) = 1$.
   Similarly, $\det((1 - t)I_n + t E_2) = 1$.
   By multiplicativity of the determinant:
   $$\det(\gamma(t)) = 1 \cdot \det(B) \cdot 1 = \det(B) > 0.$$
   Therefore $\gamma(t) \in GL_n(\mathbb{R})^+$ for all $t \in [0, 1]$.
2. **Continuity:** Each matrix entry of $\gamma(t)$ is obtained by multiplying out matrices whose entries are polynomials in $t$, so each coordinate function is a polynomial, hence continuous.
3. **Endpoints:** At $t = 0$, $\gamma(0) = I_n B I_n = B$. At $t = 1$, $\gamma(1) = E_1 B E_2 = C$.

Thus $\gamma$ provides a continuous path in $GL_n(\mathbb{R})^+$ joining $B$ to $C$.

---

### Step 3: Normalizing the pivot $\lambda$ {#step-3-normalizing-the-pivot}

Starting from the block matrix $C = \begin{pmatrix} \lambda & 0 \\ 0 & D \end{pmatrix} \in GL_n(\mathbb{R})^+$, we now connect $C$ to a block matrix of the form:
$$C' = \begin{pmatrix} 1 & 0 \\ 0 & D'' \end{pmatrix} \in GL_n(\mathbb{R})^+.$$

We analyze two cases depending on the sign of $\lambda = B_{11}$:
- **Case 3a: $\lambda > 0$.**
  Consider the continuous family of diagonal matrices:
  $$M(t) = \operatorname{diag}\bigl(t \lambda^{-1} + (1 - t), \; 1, \; \dots, \; 1\bigr), \qquad t \in [0, 1].$$
  Since $\lambda > 0$, $\lambda^{-1} > 0$, so the straight line $t\lambda^{-1} + (1-t)$ is strictly positive for all $t \in [0, 1]$.
  Define the path $\gamma(t) = M(t) C$. Then:
  $$\det(\gamma(t)) = \bigl(t \lambda^{-1} + (1 - t)\bigr) \cdot \det(C) > 0.$$
  At $t = 0$, $\gamma(0) = M(0) C = I_n C = C$.
  At $t = 1$, the $(1, 1)$ entry becomes $\lambda^{-1} \cdot \lambda = 1$, so $\gamma(1) = \begin{pmatrix} 1 & 0 \\ 0 & D \end{pmatrix}$.
- **Case 3b: $\lambda < 0$.**
  If $\lambda < 0$, we first scale $\lambda$ to $-1$ by multiplying by $\operatorname{diag}(t |\lambda|^{-1} + (1 - t), 1, \dots, 1) C$, connecting $C$ to a matrix with corner $-1$:
  $$\begin{pmatrix} -1 & 0 \\ 0 & D' \end{pmatrix}.$$
  Now we connect $\operatorname{diag}(-1, -1)$ to $\operatorname{diag}(1, 1)$ in $GL_2(\mathbb{R})^+$ using a two-stage rotation path.
  First, connect $\begin{pmatrix} -1 & 0 \\ 0 & -1 \end{pmatrix}$ to $J = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}$ via:
  $$t \begin{pmatrix} -1 & 0 \\ 0 & -1 \end{pmatrix} + (1 - t) \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix} = \begin{pmatrix} -t & 1 - t \\ -(1 - t) & -t \end{pmatrix}.$$
  The determinant is $(-t)^2 + (1 - t)^2 = t^2 + (1 - t)^2 > 0$ for all $t \in [0, 1]$.
  Second, connect $J$ to $\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$ via:
  $$t \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix} + (1 - t) \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix} = \begin{pmatrix} 1 - t & t \\ -t & 1 - t \end{pmatrix},$$
  whose determinant is $(1 - t)^2 + t^2 > 0$.
  Concatenating these two paths gives a continuous path in $GL_2(\mathbb{R})^+$ from $-I_2$ to $I_2$.
  Embedding this $2 \times 2$ path into the top-left block of our $n \times n$ matrix connects $\begin{pmatrix} -1 & 0 \\ 0 & D' \end{pmatrix}$ to a matrix of the form $\begin{pmatrix} 1 & 0 \\ 0 & D'' \end{pmatrix}$.

Since the determinant is positive, $\det\begin{pmatrix} 1 & 0 \\ 0 & D'' \end{pmatrix} = 1 \cdot \det(D'') > 0$, so $D'' \in GL_{n-1}(\mathbb{R})^+$.

---

### Step 4: Induction step on the lower $(n-1) \times (n-1)$ block

We have connected $A$ to a matrix of the form:
$$\begin{pmatrix} 1 & 0 \\ 0 & D'' \end{pmatrix}, \qquad D'' \in GL_{n-1}(\mathbb{R})^+.$$
By the induction hypothesis, $GL_{n-1}(\mathbb{R})^+$ is path connected, so there exists a continuous path:
$$\gamma_{n-1} \colon [0, 1] \longrightarrow GL_{n-1}(\mathbb{R})^+$$
such that $\gamma_{n-1}(0) = D''$ and $\gamma_{n-1}(1) = I_{n-1}$.

We define the block path in $GL_n(\mathbb{R})^+$:
$$\Gamma(t) = \begin{pmatrix} 1 & 0 \\ 0 & \gamma_{n-1}(t) \end{pmatrix}, \qquad t \in [0, 1].$$
Then $\det(\Gamma(t)) = 1 \cdot \det(\gamma_{n-1}(t)) > 0$ for all $t \in [0, 1]$.
Because $\gamma_{n-1}$ is continuous, each coordinate function of $\Gamma$ is continuous.
At the endpoints:
$$\Gamma(0) = \begin{pmatrix} 1 & 0 \\ 0 & D'' \end{pmatrix}, \qquad \Gamma(1) = \begin{pmatrix} 1 & 0 \\ 0 & I_{n-1} \end{pmatrix} = I_n.$$
Thus $\Gamma$ provides a continuous path joining $\begin{pmatrix} 1 & 0 \\ 0 & D'' \end{pmatrix}$ to $I_n$.

By concatenating the paths from Steps 1, 2, 3, and 4, we have constructed a continuous path in $GL_n(\mathbb{R})^+$ connecting $A$ to the identity $I_n$.

Therefore, every matrix in $GL_n(\mathbb{R})^+$ can be connected by a continuous path to the identity matrix $I_n$.
This proves that $GL_n(\mathbb{R})^+$ is path connected, and hence connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 21.1" content=thm211_proof %}

{% include figure.html
   src="point-set-topology/lecture-21/elementary-matrix-block-clearing.svg"
   num="21.2"
   caption="Elimination to block diagonal form: unitriangular elementary matrices $E_1$ (row operations) and $E_2$ (column operations) clear the first column and row of $B$, preserving positive determinant throughout the path $(1-t)I + t E_i$."
   alt="Block matrix multiplication clearing the first row and column of B." %}

{% include figure.html
   src="point-set-topology/lecture-21/gl2-rotation-path.svg"
   num="21.3"
   caption="The $GL_2(\mathbb{R})^+$ path connecting $-I_2$ to $+I_2$ through $J = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}$. The determinant $t^2 + (1-t)^2 > 0$ strictly avoids the singular zero-determinant locus."
   alt="A path connecting -I to J to +I while maintaining positive determinant." %}

---

## Transcript gap and details

{% capture q_gln_sketch %}
**Transcript gap (lecture delivered as a blackboard sketch):**
In sentence 212, the lecturer concludes:
> *"Thus, we have proved there's only a sketch. And I will leave it as an exercise to fill in the details and convince yourself that all the arguments are correct."*

Throughout Steps 2 and 3, the lecturer repeatedly refers to matrices drawn on the blackboard (*"a matrix of this type… on the diagonal we have one… all these zero…"*). In accordance with the project rules (`AGENTS.md` and `context/known-defects.md`), the board-only matrix entries are not invented as spoken lecture content; the structural proof is preserved above, and explicit entry formulas for $E_1$ and $E_2$ are provided in the supplement below.
{% endcapture %}
{% include block.html type="open-question" title="Transcript Gap: Blackboard Derivation of Elementary Matrix Operations" content=q_gln_sketch %}

---

## Supplements

### Supplement 1: Explicit construction of the elementary matrices $E_1$ and $E_2$

{% capture supp_elem_matrices %}
In Step 2, let $B = (B_{ij})_{1 \le i, j \le n} \in GL_n(\mathbb{R})^+$ with $B_{11} = \lambda \ne 0$.
To clear the first column beneath $B_{11}$, define the lower triangular matrix $E_1 = (e_{ij}^{(1)})_{1 \le i, j \le n}$ by:
$$e_{ii}^{(1)} = 1 \quad (1 \le i \le n), \qquad e_{i1}^{(1)} = -\frac{B_{i1}}{\lambda} \quad (2 \le i \le n), \qquad e_{ij}^{(1)} = 0 \quad \text{otherwise}.$$
Then for any row $i \ge 2$:
$$(E_1 B)_{i1} = \sum_{k=1}^n e_{ik}^{(1)} B_{k1} = e_{i1}^{(1)} B_{11} + e_{ii}^{(1)} B_{i1} = \left(-\frac{B_{i1}}{\lambda}\right) \lambda + 1 \cdot B_{i1} = 0.$$
While for the first row, $(E_1 B)_{1j} = B_{1j}$.

Next, let $B' = E_1 B$. Its $(1, 1)$ entry is still $\lambda \ne 0$. To clear the first row to the right of the $(1, 1)$ entry, define the upper triangular matrix $E_2 = (e_{ij}^{(2)})_{1 \le i, j \le n}$ by:
$$e_{ii}^{(2)} = 1 \quad (1 \le i \le n), \qquad e_{1j}^{(2)} = -\frac{B'_{1j}}{\lambda} \quad (2 \le j \le n), \qquad e_{ij}^{(2)} = 0 \quad \text{otherwise}.$$
Then multiplying on the right clears the entries $(E_1 B E_2)_{1j} = 0$ for all $j \ge 2$, without affecting the already cleared first column.
Both $E_1$ and $E_2$ are unitriangular, hence $\det((1-t)I_n + t E_i) = 1$ for all $t \in [0, 1]$.
{% endcapture %}
{% include block.html type="supplement" title="Supplement 1: Explicit Formulas for Row and Column Operations" content=supp_elem_matrices %}

---

## At a glance

- [Theorem 21.1 ($GL_n(\mathbb{R})^+$ is Path Connected)](#theorem-21-1-gln-plus-path-connected): Inductive proof connecting any $A \in GL_n(\mathbb{R})^+$ to $I_n$.
- [Step 1: Perturbation to $B_{11} \ne 0$](#step-1-connecting-a-to-a-matrix-with-non-zero-corner-entry): Straight-line segment in open neighborhood $U \subseteq GL_n(\mathbb{R})^+$.
- [Step 2: Elimination to Block Diagonal Form](#step-2-elimination-to-a-block-diagonal-matrix-via-elementary-matrices): Continuous unitriangular paths $(1-t)I + t E_i$ clearing row and column.
- [Step 3: Normalizing the Pivot](#step-3-normalizing-the-pivot): Positive scaling for $\lambda > 0$; $GL_2(\mathbb{R})^+$ rotation path through $J$ for $\lambda < 0$.
- [Step 4: Induction Step](#step-4-induction-step-on-the-lower-n-1-times-n-1-block): Embedding path from $GL_{n-1}(\mathbb{R})^+$ into the lower block.
- [Open Question: Blackboard Sketch](#transcript-gap-blackboard-derivation-of-elementary-matrix-operations): Records the blackboard-only nature of the elementary matrix operations.

---

## Where we are

We have shown that $GL_n(\mathbb{R})^+$, the group of real invertible matrices with positive determinant, is path connected. In the next lecture ([Lecture 22]({{ site.baseurl }}/point-set-topology/lecture-22/)), we turn to complex matrices and prove that $GL_n(\mathbb{C})$ is path connected, using a fundamental polynomial root-avoidance argument.

---

## Further reading

- **Morris, *Topology Without Tears***, Chapter 5: *Connectedness* (topological groups and connected matrix groups).
- **Munkres, *Topology* (2nd ed.)**, §24: *Connected Subspaces of the Real Line*.
