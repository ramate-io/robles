# ROLOG-0
- **Authors:** [Liam Monninger](mailto:liam@ramate.io)

## Summary
We discuss several conceptual notes and brief snippets of formalism which were generated separate from the work on [ROART-1](/roart/roera-000-000-000-dulan/roart-000-000-0001/README.md), [ROART-2](/roart/roera-000-000-000-dulan/roart-000-000-0002/README.md), and [ROART-3](/roart/roera-000-000-000-dulan/roart-000-000-0003/README.md).

## Log

```math
\begin{aligned}
BFT &\subset BFA \\
\alpha \cdot Loss(BFT) + \epsilon &\geq Loss(BFA)
\end{aligned}
```

```math
\begin{aligned}
B(CTR) &\subset AB \\
\\
\prod^{k} P[B(CTR_{BFA}(\zeta)) = 0] &\leq \mu \\
\\
E[Loss(CTR_{BFA})] \leq \mu \cdot Loss(BFA) &\\
\quad \quad \rightarrow U(B(CTR_{BFA}(\zeta)) = 1) \gt U(\mathcal{F}) &
\end{aligned}
```

```math
\begin{aligned}
&\text{RIS-STM}(i', B, C): \\
&\quad \textbf{loop:} \\
&\quad\quad \textbf{for } i \in C_i: \\
&\quad\quad\quad C_i := C_i + \text{recv}(i, B) \\
&\quad\quad\quad \textbf{for } C_{i,k} \in C_i: \\
&\quad\quad\quad\quad C_{i',k} := \text{compute}(i', C_{i,k}) \\
&\quad\quad\quad\quad \textbf{if } C_{i,k} \in \text{FIN:} \\
&\quad\quad\quad\quad\quad \textbf{return } C_{i',k}
\end{aligned}
```

```math
\begin{aligned}
\text{Let } \mathcal{N} \text{ be the set of participants.} \\
\text{Let } \mathcal{H} \subseteq \mathcal{N} \text{ be the subset of honest participants.} \\
\text{Let } \mathcal{H} \subset \mathcal{F} \text{ be the subset of faulty participants.} \\

\text{We make the Byzantine assumption:} \\
|\mathcal{N}| = 3n + 1 \\
|\mathcal{H}| = 2n + 1 \\
|\mathcal{F}| = n \\

\text{Let } \mathcal{C} \text{ be the set of participants included in a subcommittee. We parameterize this subcommittee by } k: \\

|C| = 3k + 1 \\

\text{The total number of ways to select the subcommittee is:} \\

c = \binom{3n + 1}{3k + 1} \\

\text{We define an accepted faulty subcommittee as one where:} \\

|C \cap \mathcal{F}| >= 2k + 1 \\

\text{The total number of ways to select an accepted faulty subcommittee is:} \\

c'(n, k) = \sum_{h = 2k + 1}^{\min(3k + 1, n)} \binom{n}{h} \cdot \binom{2n + 1}{3k + 1 - h} \\

\text{The probability of accepting a faulty subcommittee is: } \\

Pr[Accepted Faulty] = c'(n,k)/c

\text{We define an accepted honest subcommittee as one where:} \\

|C \cap \mathcal{H}| >= 2k + 1 \\

\text{The total number of ways to select an accepted honest subcommittee is:} \\

c'(n, k) = \sum_{h = 2k + 1}^{\min(3k + 1, 2n + 1)} \binom{n}{h} \cdot \binom{n}{3k + 1 - h} \\
\end{aligned}
```

```math
\begin{aligned}
&& \text{Accepted}(n, k) = \{0, 1\}
&& \text{Honest}(n, k) = \{0, 1\}
&& \Omega(n, k) = (\text{Accepted}(n, k), \text{Honest}(n, k))
&& Pr[\text(Accepted Honest)](n, k) = Pr[\text{Accepted} = 1](n, k) \cap Pr[\text{Honest} = 1](n, k) \Rightarrow
&& Pr[\text{Accepted} = 1](n,k) = Pr[\text{Accepted Honest}](n,k) + Pr[\text{Accepted Faulty}](n,k) \\
&& \lim_{n \to \infty} Pr[\text{Accepted Honest}](n, k) \\
&& \quad = \frac{1}{2} \forall k \in \mathbb{N}: k < n \\
&& \land Pr[\text{Accepted Faulty}](n,k) \approx \mu \\
&& \Rightarrow \Theta(BFA) \\
&& \quad \approx Pr[\text{Accepted}](n,k) \cdot k \\
&& \quad \quad + (1 - Pr[\text{Accepted}](n,k)) \cdot (n + k)  \\
&& \quad \approx \frac{3k + 1}{2} + \frac{(3n + 1) + (3k + 1)}{2} \\
&& \quad = \frac{3n + 1}{2} + 3k + 1 \\

&& \Omega(BFA) = k \\
\end{aligned}
```

```math
\begin{aligned}
\mathbb{P}(\text{Resample Count} = n) &= \left(1 - \frac{1}{2}\right)^{n-1} \cdot \frac{1}{2} = \frac{1}{2^n} \\
\Theta(\text{BFA}) &= k \cdot \mathbb{E}[\text{Resample Count}] \\
&= (3k + 1) \cdot \sum_{n = 1}^{\infty} n \cdot \frac{1}{2^n} \\
&= 2(3k + 1) \\
\end{aligned}
```

<!--OAC FOOTER: DO NOT REMOVE THIS LINE-->
---

<div align="center">
  <a href="https://github.com/ramate-io/oac">
    <picture>
      <source srcset="/assets/oac-inverted-transparent.png" media="(prefers-color-scheme: dark)">
      <img height="24" src="/assets/oac-transparent.png" alt="OAC"/>
    </picture>
  </a>
  <br/>
  <sub>
    <b>Ordered Atomic Collaboration (OAC)</b>
    <br/>
    &copy; 2025 <a href="https://github.com/ramate-io/oac">ramate-io/oac</a>
    <br/>
    <a href="https://github.com/ramate-io/oac/blob/main/LICENSE">MIT License</a>
    <br/>
    <a href="https://www.ramate.io">ramate.io</a>
  </sub>
</div>
