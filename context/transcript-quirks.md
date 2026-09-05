# Transcript Quirks and Decoding

The transcripts come from MacWhisper. It is a speech tool with no mathematical
knowledge: every symbol arrives spelled out, every subscript is lost, every
board is invisible, and capitalisation is unreliable.

**Consult this file before treating anything as a mathematical error.** Most
apparent mistakes are the tool. Genuine errors are catalogued separately in
`context/known-defects.md`.

Everything below is drawn from the actual transcripts of Lectures 1–40.

---

## The four dangerous losses

These are not cosmetic. Each has at least one place in the course where
misreading it produces confident nonsense.

### 1. Case is not preserved: $x$ versus $X$

The tool writes "X" for both. Usually harmless; twice in this course it is
fatal.

**The tube lemma (L24).** Every occurrence of $\{x\} \times Y$ is transcribed
"X cross Y" — identical to the ambient product $X \times Y$. As transcribed the
lemma reads "let $W$ be an open set containing $X \times Y$", which is vacuous.
The statement is:

> Let $Y$ be compact, $X$ any space, and let $W \subseteq X \times Y$ be open
> with $\{x\} \times Y \subseteq W$. Then there is an open $U \ni x$ in $X$
> with $U \times Y \subseteq W$.

The whole point — the *tube* around the slice — is invisible in the transcript.
The same collapse runs through the compactness-of-products theorem that uses it.

**L17** survives only because he says "$x$ nought": $\{x_0\} \times Y$ and
$X \times \{y_0\}$ are distinguishable there. Use L17 as the model for how L24
should read.

Rule: whenever a product appears and the argument concerns a *slice*, assume
the singleton. If the sentence is vacuous as transcribed, that is the tell.

### 2. $\mathbb{R}^{\mathbb{N}}$ is transcribed as "R n"

Lectures 39 and 40 are entirely about the **countable product**
$\mathbb{R}^{\mathbb{N}} = \prod_{n \geq 1} \mathbb{R}$, and every occurrence
reads "R n" — indistinguishable from $\mathbb{R}^n$.

The distinction survives in exactly one place, L39's opening: "we will use this
to define a metric on Rn, **R indexed by natural numbers**… so this is the
countable product."

Missing this produces two lectures of nonsense: the metric
$d(x,y) = \sup_n d'(x_n,y_n)/n$ is meaningless on a finite product, and
Urysohn metrization embeds into the countable product, not $\mathbb{R}^n$.

Rule: in L39 and L40, "R n" is $\mathbb{R}^{\mathbb{N}}$ **throughout**, without
exception. Everywhere else it is $\mathbb{R}^n$.

### 3. Matrix-group arguments are eaten entirely

The subscript and its argument vanish, often merging with the following word.

- L27: the theorem transcribes as "So SO is connected", the induction step as
  "SO plus one". Read $SO(n)$, $SO(n+1)$.
- L26: "we can prove that O, U, SUare compact" → $O(n)$, $U(n)$, $SU(n)$.
- L19: "GL nis not connected", "GL nto R minus zero", "M nis just R n square",
  "GL n+" → $GL_n(\mathbb{R})$, $M_n(\mathbb{R})$, $GL_n(\mathbb{R})^+$.

Every subscript on $SO$, $O$, $U$, $SU$, $GL$, $SL$, $M_n$ must be
reconstructed from the surrounding algebra. In L27 and L28 the induction runs
on $n$, so $n$ versus $n+1$ matters at every step — fix it from the map
$\varphi : SO(n+1) \to S^n$ and the subgroup $H \cong SO(n)$.

### 4. $\varphi$ and $\varnothing$ are both "phi"

In Lectures 1–3, "phi" is always the empty set — the Indian convention for
reading $\varnothing$ aloud. **From Lecture 10 onward it is usually the Greek
letter $\varphi$ naming a map**: stereographic projection (L10, L17, L33), the
map $SO(n+1) \to S^n$ (L27), the map to the Grassmannian (L34), the
homeomorphism $\mathbb{R} \to (-1,1)$ (L37).

L11 and L31 contain both readings in the same lecture.

Rule: it is $\varnothing$ when the sentence concerns a set being empty or the
topology axioms; it is $\varphi$ when it is applied to something, or has a
domain and codomain. Never carry the reading over from an earlier lecture.

---

## Indian English mathematical idiom

**"$X$ by $Y$" means the fraction $X/Y$.** Throughout: "epsilon by two", "delta
by three", "$2r$ by $3$". From L2: "epsilon to be minimum of $x$ by two and one
minus $x$ by two" is $\varepsilon = \min\{x/2,\,(1-x)/2\}$. Misreading this
silently corrupts proofs.

**"one upon $x$" means $1/x$.** L9, L10, L22, L28 — "$B$ one upon $n$" is the
ball of radius $1/n$.

**"$x$ naught" / "$x$ nought" is $x_0$.** Also $t_0$, $p_0$, $f_0$, $i_0$.

**"contained in" is used for both $\subseteq$ and $\in$.** Read from context.

**"$n$ cross $n$" is $n \times n$; "$X$ cross $Y$" is $X \times Y$.**

**"$A$ bar" and "$A$ closure" both mean $\overline{A}$**, sometimes in one
sentence.

**Negations sometimes arrive as self-corrections.** L19: "$O(n)$ is not path
connected, is not connected, yeah" is one claim restated, not two.

---

## Symbols spelled as words

| Transcript | Means | Note |
|---|---|---|
| phi | $\varnothing$ **or** $\varphi$ | see above |
| tau, tau prime, tau sub B | $\tau$, $\tau'$, $\tau_{\mathcal{B}}$ | |
| epsilon, delta, gamma, lambda | $\varepsilon$, $\delta$, $\gamma$, $\lambda$ | |
| psi | $\psi$ — usually the inverse of a $\varphi$ | |
| star, star prime | $(\ast)$, $(\ast')$ | named properties |
| R, R2, Rn, R n plus one | $\mathbb{R}$, $\mathbb{R}^2$, $\mathbb{R}^n$, $\mathbb{R}^{n+1}$ | |
| R star | $\mathbb{R}^{\times} = \mathbb{R}\setminus\{0\}$ | his notation, L8–L9 |
| C, C n square | $\mathbb{C}$, $\mathbb{C}^{n^2}$ | |
| P of X | $\mathcal{P}(X)$ | |
| B epsilon x, S epsilon x | $B_\varepsilon(x)$, $S_\varepsilon(x)$ | ball, square |
| U i, x i, e one | $U_i$, $x_i$, $e_1$ | subscripts always lost |
| X hat | $\hat{X}$ | one-point compactification |
| f tilde, gamma tilde | $\tilde{f}$, $\tilde{\gamma}$ | |
| A transpose, A star | $A^{T}$, $A^{*}$ | $A^{*}$ = conjugate transpose |
| G mod H, X mod equivalence | $G/H$, $X/\!\sim$ | |
| S n, S n minus one | $S^n$, $S^{n-1}$ | |
| d Z, d sub A | $d_Z$, $d_A$ | distance to a set |
| infinity norm | $\lVert\cdot\rVert_\infty$ | L37 |

## Powers and indices

- "a square plus b square" → $a^2 + b^2$
- "y i minus x i square" → $(y_i - x_i)^2$
- "two square r by three square" → $2^2 r/3^2$
- "2 to the n r by 3 to the n" → $2^n r/3^n$
- "2i minus 1 r by 3i" → $2^{i-1}r/3^{i}$ (L37 — exponents lost, reconstruct
  from the induction)
- "square of side length two epsilon" → side $2\varepsilon$, half-side
  $\varepsilon$

## Structural phrases

| Transcript | Means |
|---|---|
| "which implies that" | $\Rightarrow$ |
| "i equal to one to n" | $\bigcap_{i=1}^n$ or $\bigcup_{i=1}^n$ — from context |
| "for each i in I" | $\forall i \in I$ |
| "there is epsilon positive" | $\exists\,\varepsilon > 0$ |
| "vacuously true" | the hypothesis is never met |
| "an easy set theoretic check" | an identity he is not proving — supply it in a supplement |
| "left as an exercise" | a first-class exercise — **keep it** |
| "let us emphasize that" | a deliberate warning — **keep it** |
| "so let me write it as a claim" | board management — drop |

---

## Restarts, self-corrections, lost brackets

Keep only the corrected version.

- L3: "are subsets of $\mathbb{R}^n$… I'm sorry, are subs— are subsets of the
  power set of $\mathbb{R}^n$" → $\subseteq \mathcal{P}(\mathbb{R}^n)$.
- L18: "we are going to define path components. I'm sorry, not the path
  components, the connected components."
- L23: "an example of a topological space which is not Hausdorff. I'm sorry,
  which is not compact."
- L33: "I had said that $X$ has to be compact, but that's not necessary… we
  only need $T$ to be a Hausdorff space." This is an **explicit correction to
  the previous lecture**. Record it, and add a forward note on the L32 page.

**Bracketed intervals are sometimes dropped by the RTF conversion.** L19 has
"let's call this set $A$… $A$ is the closed interval , and $B$ is the closed
interval ]." The intervals $[0,1/2]$ and $[1/2,1]$ have vanished. A dangling
comma or an orphan bracket means an interval was eaten — reconstruct from the
surrounding formulas and note it in the report.

---

## Multi-part transcripts

Lecture 34 arrives as three files (`Part_1`, `Part_2`, `Part_3`). It is **one
lecture** and becomes **one page**. Concatenate in part order before the
skeleton pass. Never treat a part as a lecture: Part 1 is the quotient-topology
theorem, Part 2 is topological groups and $G/H$ Hausdorff, Part 3 is the
Grassmannian — one continuous argument across three files.

Filenames are not authoritative for lecture number either. Confirm from the
lecturer's own words ("this is lecture eleven", "this is lecture 27"), or from
the "in the previous lecture we…" opening, which reliably names the
predecessor.

---

## Things that look wrong but are not

- "phi is in tau… vacuously true because there are no points in the empty set."
  Correct.
- "we can take a square of side length two", then $S_1(a,b)$ — consistent,
  since $S_\varepsilon$ has side $2\varepsilon$.
- "This is obviously contained in R" where $\mathbb{R}^2$ is meant (L3). Loose
  speech; no note needed.
- L23's Hausdorff hypothesis inside the definition of compactness. Deliberate —
  see `known-defects.md` → Conventions.
- L31's reversed axiom order. Not wrong.
- L26's "O, U, SUare compact" — three groups, not one mistyped.

---

## Extending this file

Add new patterns with the transcript phrase quoted exactly and the lecture it
came from. This file is what stops a question settled at Lecture 4 being
re-litigated at Lecture 40.
