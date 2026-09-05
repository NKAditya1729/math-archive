# Known Defects Register — Point-Set Topology

Every mathematical error found in the transcripts of Lectures 1–40, with the
correct statement and the evidence for it. Compiled from a full reading of all
forty transcripts before any notes were written.

**Consult this file during the defect sweep (pass 2) of every lecture.** If the
lecture you are processing appears below, the ruling here is already made — use
it, raise the Correction Note as specified, and do not re-litigate. If you find
a defect *not* listed here, add it, with the same three fields: what the
transcript says, what is meant, and the evidence.

Two standing rules. Never propagate an error. Never silently repair one.

---

## How the entries are graded

- **Slip** — the lecturer misspoke or the tool dropped a word. His own later
  usage contradicts it. Correct it, raise a Correction Note, proceed.
- **Consequential** — a slip in a statement the rest of the lecture depends on.
  Same handling, but flag at the top of the build report.
- **Convention** — not an error. He differs from the textbooks deliberately.
  Keep his version and add a supplement noting the standard form.
- **Gap** — the board carried content the audio does not. Do not reconstruct;
  write an Open Question block.

---

## Consequential

**L36 — the definition of $U_q$ in Urysohn's lemma.** Transcript: "$U_q$ is
defined to be $f^{-1}[0,q]$… this is an open subset of $X$." A preimage of a
closed interval under a continuous map is closed, not open. Must be
$$U_q = f^{-1}\bigl([0,q)\bigr).$$
Evidence: the entire motivating remark requires $U_q$ open, and the subsequent
construction of the family $\{U_a\}$ depends on it. This is the load-bearing
definition of the lecture; getting it wrong makes the whole proof incoherent.

**L2 — the interval.** Transcript defines $(a,b)$ as "those real numbers $x$
such that $x$ is strictly less than $a$ and strictly less than $b$", which
describes $(-\infty, \min(a,b))$. Correct: $\{x \in \mathbb{R} : a < x < b\}$.
Evidence: his own later use, and his statement that
$\mathbb{R} = (-\infty, +\infty)$.

**L3 — the open ball radius.** Transcript:
$B_\varepsilon(x) = \{y : \sum (y_i - x_i)^2 < \varepsilon\}$, called "the open
ball of radius $\varepsilon$". As written the radius is $\sqrt{\varepsilon}$.
Correct: $< \varepsilon^2$. **Add the supplement:** as $\varepsilon$ ranges over
all positive reals the two families coincide, so $\tau'$ and the exercise
$\tau = \tau'$ are unaffected. Say both things.

**L17 — the union lemma.** Transcript: "if $T_1 \cap T_2$ is non-empty, then
the union $T_1 \cup T_2$ is non-empty." Must be **connected**. Evidence: he
states it correctly when recalling it in L18, and the proof he gives proves
connectedness.

**L20 — which projection cuts out $Y$.** Transcript says $Y$ is the preimage of
$0$ under "the second projection". $Y = \{0\} \times (0,1]$ is cut out by the
**first** coordinate. Evidence: $Y$ is the vertical segment on the $y$-axis.

---

## Slips

**L1** — none. The lecture is correct as delivered.

**L12** — "it is enough to show that $\bar{A}$ is contained in $U$" in the proof
that $A$ closed $\Rightarrow A = \bar{A}$. Should be contained in $A$; $U$ has
not been introduced at that point.

**L16** — the corollary that $\mathbb{R}$ is connected ends "which contradicts
the fact that $[a,b]$ is disconnected." Should be **connected**.

**L19** — transitivity of the path relation is stated "if $x \sim y$ and
$y \sim x$, then $x \sim z$." Should be $y \sim z$. The proof that follows is
correct. Also, the conclusion reads "this shows that $x$ is equal to $z$";
should be *equivalent to*.

**L18** — the proof that each $X_i$ is connected begins "as $X$ is connected,
as $X_i$ is connected". Only the second clause is intended; $X$ is not assumed
connected anywhere in the proposition.

**L11** — $GL_n(\mathbb{R})$ is described as "the determinant inverse of this
subset $\mathbb{R}$ minus $U$." Should be $\mathbb{R} \setminus \{0\}$.

**L35** — the final contradiction reads "$U$ intersection $B$ is empty" twice
where $U \cap V$ is meant. Also "then we say that $A$ is normal" in the
definition; should be $X$.

**L26** — "Let us assume that… to show that $f(Z)$ is compact" opens a remark
that is actually about subspaces in general; the sentence never completes.
Render the remark as the general statement he then proves.

**L29** — near the end of the continuity proof of $d_Z$: "$d_Z(x) - d_Z(y)$ is
equal to minus $m_Z$" is garbled beyond repair and is not needed — the argument
is complete without it. Omit, and note the omission in the report.

**L37** — the theorem is stated for "$f$ from $A$ to minus $R, R$" and the
closing line calls it "DC-DC's Extension Theorem". Both are transcription
noise: the interval is $[-r, r]$ and the theorem is **Tietze's**.

**L22** — "$p$ of zero is equal to determinant of $A$, which is not equal to
zero, because $A$ is in $GL_n(\mathbb{C})$" is transcribed as "gamma of zero we
know is $A$, which is not equal to zero". The matrix is not being compared to
zero; its determinant is. Correct silently in the reconstruction.

---

## Conventions — keep these, do not "fix" them

**L23 — compactness is defined only for Hausdorff spaces.** "Let $X$ be a
Hausdorff topological space. So we shall say that $X$ is compact if…" He then
states that Hausdorff is assumed for the remainder of the course unless said
otherwise. Munkres, Morris, and Simmons all define compactness without
Hausdorff. **This is deliberate and must be flagged prominently in the L23
notes**, because a reader who opens Munkres §26 will otherwise hit an apparent
contradiction. Every later result quoted as "compact $\Rightarrow$ closed" or
"bijective continuous from compact is a homeomorphism" silently uses the
Hausdorff hypothesis; say so where it is used.

**L3 — one condition for a basis, not two.** He begins "the following two
conditions" and corrects himself mid-sentence. The definition has one
condition. Do not invent a second.

**L31 — the topology axioms in the other order.** In verifying the one-point
compactification he checks arbitrary unions as "the second condition" and
finite intersections as "the third", reversing his own Lecture 1 numbering.
Not wrong. Keep his order; note the swap in a supplement so a reader comparing
against Lecture 1 is not confused.

**L2, L3 — property $(\ast)$ used with three meanings.** He says explicitly that
he is being lazy about the distinction. Disambiguate with subscripts in the
notes and say in a supplement that the lecture uses one symbol throughout.

**L26 — Tychonoff stated without proof.** He says a proof may be found in
Munkres. That is §37. Do not supply a proof; it is far outside the course.

---

## Gaps — do not reconstruct

These three passages lost their content to the board. Write the surrounding
structure, then an Open Question block quoting the transcript and saying
plainly that the step needs the video. **Do not invent the algebra.** A
confident wrong derivation is far worse here than an honest hole, because the
reader cannot check it.

**L14 — Cauchy–Schwarz and the triangle inequality.** From "so we have norm
$x - y$ whole square is equal to…" onward, the transcript is "this is equal
to… uh, this is equal to… and this is less than equal to…" with every
expression on the board. The *structure* is recoverable and should be written:
set $w = y - tx$, expand $\langle w, w \rangle \geq 0$ using bilinearity and
symmetry, read it as a quadratic in $t$, conclude from the discriminant. The
individual algebraic lines are not recoverable. Write the structure, mark the
computation as needing the video, and offer the standard derivation in a
clearly labelled supplement — never as lecture content.

**L21 — the $GL_n(\mathbb{R})^+$ block-matrix argument.** He calls it a sketch
himself and closes: "I will leave it as an exercise to fill in the details."
Steps 1–3 have recoverable structure; the elementary matrices $E_1$, $E_2$ and
the block forms are drawn, not spoken ("a matrix of this type", repeatedly).
Draw what can be inferred, mark the rest.

**L37 — the middle of the Tietze construction.** The three-way interval split
and the estimate $\|f - g_A\|_\infty \leq 2r/3$ survive; the passage from
"$\bmod f(y) - f(y')$… so this we can write as… and this is less than equal
to…" is board-only.

Lesser gaps of the same kind, recoverable with more confidence but still worth
a report note: L8 (the multiplication-map estimate), L28 (the picture-driven
choice of $\varepsilon/2$ balls), L30 (the $C$, $D$ separation diagram).

---

## The pattern worth internalising

Almost every genuine slip in forty lectures is a **swapped word in a stated
result** — connected/non-empty, first/second, $A$/$U$, equal/equivalent — and
in every case his own proof, or his own recollection of the result one lecture
later, gives the correct version. The proofs are reliable; the statements
occasionally are not.

So: when a statement and the proof beneath it disagree, **the proof wins**, and
the Correction Note cites the proof as its evidence. That single heuristic
resolves nearly every entry above.
