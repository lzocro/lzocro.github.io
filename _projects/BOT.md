---
layout: distill
title: Bandits and infinite dimensional statistics
description: What corner cases can teach us about bandit optimisation
img: assets/img/project_covers/IMG_5210.jpg
authors:
  - name: Lorenzo Croissant
    affiliations:
      name: CREST, ENSAE, & Inria FairPlay
toc:
  - name: Bandit optimisation
  - name: Bandits Optimal Transport
  # - name: (Semi-)Bandits with contracts
  # - name: Geometric aspects of optimism
importance: 8
category: [Reinforcement Learning]
bibliography: BOT.bib
date: 2025-08-01
---

<div style="display:none">
  $$ 
    \def\de{\mathrm{d}}
    \def\De{\mathrm{D}}
    \def\ve{\varepsilon}
    \def\x{\times}
    \def\dre{\delta r^\ve}
    \def\de{\mathrm{d}}
    \def\De{\mathrm{D}}
    \def\x{\times}
    \def\dre{\delta r^\ve} 
  $$
  $$
    \def\Ab{\mathbb{A}}
    \def\Bb{\mathbb{B}}
    \def\Cb{\mathbb{C}}
    \def\Db{\mathbb{D}}
    \def\Eb{\mathbb{E}}
    \def\Fb{\mathbb{F}}
    \def\Hb{\mathbb{H}}
    \def\Gb{\mathbb{G}}
    \def\Ib{\mathbb{I}}
    \def\Jb{\mathbb{J}}
    \def\Lb{\mathbb{L}}
    \def\Kb{\mathbb{K}}
    \def\Mb{\mathbb{M}}
    \def\Nb{\mathbb{N}}
    \def\Ob{\mathbb{O}}
    \def\Pb{\mathbb{P}}
    \def\Qb{\mathbb{Q}}
    \def\Rb{\mathbb{R}}
    \def\Sb{\mathbb{S}}
    \def\Tb{\mathbb{T}}
    \def\Ub{\mathbb{U}}
    \def\Vb{\mathbb{V}}
    \def\Wb{\mathbb{W}}
    \def\Xb{\mathbb{X}}
    \def\Yb{\mathbb{Y}}
    \def\Zb{\mathbb{Z}}
  $$<!-- %% Caligraphics %% -->
  $$
    \def\Ac{\mathcal{A}}
    \def\Bc{\mathcal{B}}
    \def\Cc{\mathcal{C}}
    \def\Dc{\mathcal{D}}
    \def\Ec{\mathcal{E}}
    \def\Fc{\mathcal{F}}
    \def\Hc{\mathcal{H}}
    \def\Gc{\mathcal{G}}
    \def\Ic{\mathcal{I}}
    \def\Jc{\mathcal{J}}
    \def\Lc{\mathcal{L}}
    \def\Kc{\mathcal{K}}
    \def\Mc{\mathcal{M}}
    \def\Nc{\mathcal{N}}
    \def\Oc{\mathcal{O}}
    \def\Pc{\mathcal{P}}
    \def\Qc{\mathcal{Q}}
    \def\Rc{\mathcal{R}}
    \def\Sc{\mathcal{S}}
    \def\Tc{\mathcal{T}}
    \def\Uc{\mathcal{U}}
    \def\Vc{\mathcal{V}}
    \def\Wc{\mathcal{W}}
    \def\Xc{\mathcal{X}}
    \def\Yc{\mathcal{Y}}
    \def\Zc{\mathcal{Z}}
  $$<!-- %% Romans %% -->
  $$
    \def\Ar{\mathrm{A}}
    \def\Br{\mathrm{B}}
    \def\Cr{\mathrm{C}}
    \def\Dr{\mathrm{D}}
    \def\Er{\mathrm{E}}
    \def\Fr{\mathrm{F}}
    \def\Hr{\mathrm{H}}
    \def\Gr{\mathrm{G}}
    \def\Ir{\mathrm{I}}
    \def\Jr{\mathrm{J}}
    \def\Lr{\mathrm{L}}
    \def\Kr{\mathrm{K}}
    \def\Mr{\mathrm{M}}
    \def\Nr{\mathrm{N}}
    \def\Or{\mathrm{O}}
    \def\Pr{\mathrm{P}}
    \def\Qr{\mathrm{Q}}
    \def\Rr{\mathrm{R}}
    \def\Sr{\mathrm{S}}
    \def\Tr{\mathrm{T}}
    \def\Ur{\mathrm{U}}
    \def\Vr{\mathrm{V}}
    \def\Wr{\mathrm{W}}
    \def\Xr{\mathrm{X}}
    \def\Yr{\mathrm{Y}}
    \def\Zr{\mathrm{Z}}
  $$
  $$
    \def\ar{\mathrm{a}}
    \def\br{\mathrm{b}}
    \def\cr{\mathrm{c}}
    \def\dr{\mathrm{d}}
    \def\er{\mathrm{e}}
    \def\fr{\mathrm{f}}
    \def\hr{\mathrm{g}}
    \def\gr{\mathrm{h}}
    \def\ir{\mathrm{i}}
    \def\jr{\mathrm{j}}
    \def\kr{\mathrm{k}}
    \def\lr{\mathrm{l}}
    \def\mr{\mathrm{m}}
    \def\nr{\mathrm{n}}
    \def\or{\mathrm{o}}
    \def\pr{\mathrm{p}}
    \def\qr{\mathrm{q}}
    \def\rr{\mathrm{r}}
    \def\sr{\mathrm{s}}
    \def\tr{\mathrm{t}}
    \def\ur{\mathrm{u}}
    \def\vr{\mathrm{v}}
    \def\wr{\mathrm{w}}
    \def\xr{\mathrm{x}}
    \def\yr{\mathrm{y}}
    \def\zr{\mathrm{z}}
  $$ <!-- %% Scripts %% -->
  $$
    \def\As{\mathscr{A}}
    \def\Bs{\mathscr{B}}
    \def\Cs{\mathscr{C}}
    \def\Ds{\mathscr{D}}
    \def\Es{\mathscr{E}}
    \def\Fs{\mathscr{F}}
    \def\Hs{\mathscr{H}}
    \def\Gs{\mathscr{G}}
    \def\Is{\mathscr{I}}
    \def\Js{\mathscr{J}}
    \def\Ls{\mathscr{L}}
    \def\Ks{\mathscr{K}}
    \def\Ms{\mathscr{M}}
    \def\Ns{\mathscr{N}}
    \def\Os{\mathscr{O}}
    \def\Ps{\mathscr{P}}
    \def\Qs{\mathscr{Q}}
    \def\Rs{\mathscr{R}}
    \def\Ss{\mathscr{S}}
    \def\Ts{\mathscr{T}}
    \def\Us{\mathscr{U}}
    \def\Vs{\mathscr{V}}
    \def\Ws{\mathscr{W}}
    \def\Xs{\mathscr{X}}
    \def\Ys{\mathscr{Y}}
    \def\Zs{\mathscr{Z}}
  $$<!-- %% Bold face %% -->
  $$
    \def\Abf{\mathbf{A}}
    \def\Bbf{\mathbf{B}}
    \def\Cbf{\mathbf{C}}
    \def\Dbf{\mathbf{D}}
    \def\Ebf{\mathbf{E}}
    \def\Fbf{\mathbf{F}}
    \def\Hbf{\mathbf{H}}
    \def\Gbf{\mathbf{G}}
    \def\Ibf{\mathbf{I}}
    \def\Jbf{\mathbf{J}}
    \def\Lbf{\mathbf{L}}
    \def\Kbf{\mathbf{K}}
    \def\Mbf{\mathbf{M}}
    \def\Nbf{\mathbf{N}}
    \def\Obf{\mathbf{O}}
    \def\Pbf{\mathbf{P}}
    \def\Qbf{\mathbf{Q}}
    \def\Rbf{\mathbf{R}}
    \def\Sbf{\mathbf{S}}
    \def\Tbf{\mathbf{T}}
    \def\Ubf{\mathbf{U}}
    \def\Vbf{\mathbf{V}}
    \def\Wbf{\mathbf{W}}
    \def\Xbf{\mathbf{X}}
    \def\Ybf{\mathbf{Y}}
    \def\Zbf{\mathbf{Z}}
  $$
  $$
    \def\abf{\mathbf{a}}
    \def\bbf{\mathbf{b}}
    \def\cbf{\mathbf{c}}
    \def\dbf{\mathbf{d}}
    \def\ebf{\mathbf{e}}
    \def\fbf{\mathbf{f}}
    \def\hbf{\mathbf{g}}
    \def\gbf{\mathbf{h}}
    \def\ibf{\mathbf{i}}
    \def\jbf{\mathbf{j}}
    \def\kbf{\mathbf{k}}
    \def\lbf{\mathbf{l}}
    \def\mbf{\mathbf{m}}
    \def\nbf{\mathbf{n}}
    \def\obf{\mathbf{o}}
    \def\pbf{\mathbf{p}}
    \def\qbf{\mathbf{q}}
    \def\rbf{\mathbf{r}}
    \def\sbf{\mathbf{s}}
    \def\tbf{\mathbf{t}}
    \def\ubf{\mathbf{u}}
    \def\vbf{\mathbf{v}}
    \def\wbf{\mathbf{w}}
    \def\xbf{\mathbf{x}}
    \def\ybf{\mathbf{y}}
    \def\zbf{\mathbf{z}}
  $$<!-- %% Fraktur %% -->
  $$
    \def\Af{\mathfrak{A}}
    \def\Bf{\mathfrak{B}}
    \def\Cf{\mathfrak{C}}
    \def\Df{\mathfrak{D}}
    \def\Ef{\mathfrak{E}}
    \def\Ff{\mathfrak{F}}
    \def\Hf{\mathfrak{H}}
    \def\Gf{\mathfrak{G}}
    \def\If{\mathfrak{I}}
    \def\Jf{\mathfrak{J}}
    \def\Lf{\mathfrak{L}}
    \def\Kf{\mathfrak{K}}
    \def\Mf{\mathfrak{M}}
    \def\Nf{\mathfrak{N}}
    \def\Of{\mathfrak{O}}
    \def\Pf{\mathfrak{P}}
    \def\Qf{\mathfrak{Q}}
    \def\Rf{\mathfrak{R}}
    \def\Sf{\mathfrak{S}}
    \def\Tf{\mathfrak{T}}
    \def\Uf{\mathfrak{U}}
    \def\Vf{\mathfrak{V}}
    \def\Wf{\mathfrak{W}}
    \def\Xf{\mathfrak{X}}
    \def\Yf{\mathfrak{Y}}
    \def\Zf{\mathfrak{Z}}
  $$
  $$
    \def\af{\mathfrak{a}}
    \def\bf{\mathfrak{b}}
    \def\cf{\mathfrak{c}}
    \def\df{\mathfrak{d}}
    \def\ef{\mathfrak{e}}
    \def\ff{\mathfrak{f}}
    \def\hf{\mathfrak{g}}
    \def\gf{\mathfrak{h}}
    \def\if{\mathfrak{i}}
    \def\jf{\mathfrak{j}}
    \def\kf{\mathfrak{k}}
    \def\lf{\mathfrak{l}}
    \def\mf{\mathfrak{m}}
    \def\nf{\mathfrak{n}}
    \def\of{\mathfrak{o}}
    \def\pf{\mathfrak{p}}
    \def\qf{\mathfrak{q}}
    \def\rf{\mathfrak{r}}
    \def\sf{\mathfrak{s}}
    \def\tf{\mathfrak{t}}
    \def\uf{\mathfrak{u}}
    \def\vf{\mathfrak{v}}
    \def\wf{\mathfrak{w}}
    \def\xf{\mathfrak{x}}
    \def\yf{\mathfrak{y}}
    \def\zf{\mathfrak{z}} 
  $$
</div>

## Bandit optimisation

A (stochastic) bandit problem is, at its heart, an optimisation problem under uncertainty. An agent wishes to minimise some objective function $g:\Ab\to\Rb$, which is unknown to them. They can however query it sequentially at points $a_1,\ldots,a_n\in\Ab$, but crucially only observe noisy values of the function at these points, i.e. they observe $y_i = g(a_i) + \xi_i$ where $\xi_i$ is some noise. These problems exhibit 3 key properties.
<ol>
<li> Partial information: the agent only observes the value of $g$ at the points they query, and with noise.</li>
<li> Interactivity: the data is chosen by the agent, rather than received exogenously like in supervised learning. As a consequence, the agent must explore the space $\Ab$ to gather statistical information about $g$. This exploration will introduce long-range dependencies between the data points, which makes the statistical analysis more complex. </li>
<li> Evaluation through regret: the agent's performance is evaluated through their regret, i.e. the difference between the cumulative value of $g$ at the points they queried, and the cumulative value of $g$ at its optimum. This is a more stringent criterion than classical statistical ones, as it requires both optimisation and statistical efficiency.</li>
</ol>
Evaluation through regret forces the agent to exploit its knowledge of $g$ as it goes, which comes in tension with the need to explore the space $\Ab$ to learn about $g$. This exploration-exploitation tradeoff is the heart of bandit problems.


Because bandits are static, i.e. the function $g$ does not depend on time, they are often used to study [reinforcement learning](/projects/RL_diff_limit/) by stripping away the control component, while retaining most of the statistical complexity. Bandits have a well-documented history going back to the 1930s, which I won't recount here. 

What this project is interested in is the interplay between optimisation and statistics in bandit problems, and in particular I'm interested in situations where $\Ab$ is continuous and possibly infinite-dimensional. From a classical-statistics point of view, this isn't much of an issue, non-parametric statistics is a well-developed field afterall. However, the interplay with optimisation and the nature of regret evaluation muddies this picture. I believe these corner case questions can teach us a lot about the core nature of bandit problems, and more generally of reinforcement learning, which is why I study them. Below are some of the topics on which I've worked in this vein.

## Bandits Optimal Transport

Optimal Transport (OT) is a mathematical theory which studies the problem of transforming one probability distribution into another in an optimal way. It has found applications in many fields, principally logistics and economics more broadly, but also in machine learning<d-footnote>For economics see the survey <d-cite key="galichon_unreasonable_2021">Galichon et al. (2021)</d-cite>, for machine learning, see e.g. <d-cite key="salimans_improving_2018">Salimans et al. (2018)</d-cite>.</d-footnote>. Let $\mu,\nu$ be two probability distributions on $\Rb^d$, and $c^*:\Rb^d\x\Rb^d\to\Rb_+$ a cost function. The Kantorovich OT problem, named after its formaliser, see <d-cite key="kantorovich_translocation_2006">Kantorovich (1960)</d-cite>, consists in finding a coupling<d-footnote>I.e. a joint probability measure with marginals $\mu$ and $\nu$ over its first and second arguments, respectively.</d-footnote>  $\pi$ between $\mu$ and $\nu$ which minimises the expected cost of transporting mass from $\mu$ to $\nu$, i.e.
\\[
\inf_{\pi\in\Pi(\mu,\nu)}\int c^\*(x,y)\pi(\de x,\de y),
\\]
where $\Pi(\mu,\nu)$ is the set of couplings between $\mu$ and $\nu$. 


This problem is interesting beyond its applicability because it lies in a very complex optimisation space, but is also highly regular, see e.g. <d-cite key="villani_optimal_2009">Villani (2008)</d-cite> for a comprehensive treatment. 
The interesting question from a statistical standpoint is whether we can exploit this regularity, and this is what this paper aims to answer.

What does a Bandit Optimal Transport (BOT) problem look like? The agent knows $\Ab:=\Pi(\mu,\nu)$, but ignores the cost function $c^*$. They can query transport plans $\pi_1,\ldots,\pi_n\in\Ab$, and observe noisy values of the cost 
\\[
y_i = \int c^\*(x,y)\pi_i(\de x,\de y) + \xi_i
\\]

where $\xi_i$ is some noise. Since the functional $g:\pi\to\int c^*\de \pi$ is linear, this is an instance of the well-studied linear bandit problem, see the reference treatment in <d-cite key="abbasi-yadkori_improved_2011">Abbasi-Yadkori et al. (2011)</d-cite>.

However, this is where the corner case comes in: the space $\Pi(\mu,\nu)$ is not a Hilbert space, and in fact is quite complex geometrically, there is no good way to put into an inner product structure with a hypothesis class on the cost $c^*$. This turns out to be a key issue, as it breaks the careful infinite-dimensional analysis of <d-cite key="abbasi-yadkori_improved_2011">Abbasi-Yadkori et al. (2011)</d-cite>, which crucially relies on an inner-product structure. This begs the question, is linearity not sufficient to obtain good regret bounds in infinite dimension? Is the name <it>linear bandits</it> a misnomer?

While a definitive negative answer is not yet established, I have shown that the BOT problem is learnable with sub-linear regret, interpolating all the way from $\Oc(\sqrt{n})$ regret in finite dimension to $\Oc(n)$ in unlearnable instances. The interpolation is obtained through the use of infinite-dimensional statistics tools, in particular functional-regression. See <d-cite key="Croissant_BOT_25">Croissant (2025)</d-cite> for details.

<!-- ## (Semi-)Bandits with contracts

## Geometric aspects of optimism -->