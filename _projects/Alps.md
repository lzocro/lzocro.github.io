---
layout: distill
title: Algorithms with Predictions
description: Dynamics in markets
date: 2025-07-01
img: assets/img/project_covers/IMG_4044.jpg
authors:
  - name: Lorenzo Croissant
    affiliations:
      name: CREST, ENSAE, & Inria FairPlay
toc:
  - name: "What are the core problems?"
  - name: "Example: the one-max-search problem"
  - name: "Open questions for learning theorists"
importance: 3
category: [Online Learning]
bibliography: ALPS.bib
---
<div style="display:none">
  $$ 
    \def\de{\mathrm{d}}
    \def\De{\mathrm{D}}
    \def\x{\times}
    \def\ve{\varepsilon}
    \def\dre{\delta r^\ve}
    \def\de{\mathrm{d}}
    \def\De{\mathrm{D}}
    \def\x{\times}
    \def\ve{\varepsilon}
    \def\dre{\delta r^\ve}
    \def\1{\mathbb{1}} 
    \def\argmax{\mathrm{arg}\max}
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



Algorithms with predictions (also called learning‑augmented or prediction‑augmented algorithms) augment classical algorithmic procedures with side information about the future, which could be predictions produced by ML models, domain experts, or simple heuristics. The basic philosophy is pragmatic: predictions are available in many real systems (forecasted demand, estimated user behavior, model outputs used by human operators), and algorithms that can use these signals profit from improved average performance while still providing safeguards against bad forecasts.

While this problem is primarily studied in the computer science algorithms community, it should interest learning theorists and statisticians, especially those interested in the interface between learning and decision-making. Indeed, informing traditional decision-making is the main way statistical learning is applied in practice. Whether our concern (as an accademic community) is the quality of decision making by policymakers or how to correctly train students to <it>use</it> ML models, it is crucial to expand our understanding of this aspect of decision-making under uncertainty.


# What are the core problems? 

Of course, aspects of algorithm design for specific problems are not within the scope of statistical learning theory. However, several conceptual and technical questions arise naturally at the intersection of learning and decision-making that should interest learning theorists. These stem from the key properties that learning-augmented algorithms aim to achieve:

<ul>
<li> Consistency: when predictions are accurate (or calibrated), a good algorithm should (almost) match the performance of an ideal clairvoyant method (fast, high performance, low regret, etc.).</li>
<li> Robustness: when predictions are catastrophically wrong (worst-case), the algorithm should not be much worse than the classical worst‑case algorithms' guarantees.</li>
<li> Smoothness: in between these two extremes, an algorithm's performance should degrade smoothly: small prediction error should cause only small performance loss. Smoothness is a necessary condition for actual deployability, as real predictors will never be perfect.</li>
</ul>

Naturally, each criterion individually is trivial to optimise: always trust the predictor (perfect consistency) or always ignore it (perfect robustness, and smoothness). The challenge is in the multi-objective problem. The opposition between consistency and robustness for example, is quite self-evident: the heart of the question is in characterising, for a given problem, the shape of the Pareto frontier of achievable trade-offs. Most early work focused only on achieving consistency and robustness, with smoothness being a more recent (but already widely accepted) goal. 

Further reading and a curated overview are available at the Algorithms with Predictions initiative <a href='https://algorithms-with-predictions.github.io/'>website</a>.

# Example: The one-max-search problem

As an illustration of the concepts of algorithms with predictions, this section sumarises the contents of <d-cite key="Benomar25"></d-cite> on the problem of one-max-search.

The one-max-search problem is a simple online decision problem, but despite its simplicity the prediction augmented problem is already very rich in challenges. One-max-search is an optimal stopping problem generally presented as an optimal execution problem: we have a single asset to sell over a time horizon of $T$ periods, and at each period $t\in[T]$ we observe a price $X_t$ which we can either accept or forfeit to move to $t+1$.  

This problem is very similar to the Prophet and Secretary problems, so to clear up any confusion, let's contrast these optimal stopping problems before moving on. A Prophet problem is characterised by the <it>independent</it> between the prices $X_t$. A Secretary problem is characterised by the <it>randomisation of arrival order</it> of the prices $X_t$, which are otherwise adversarially chosen. In contrast, the prices in one-max-search are adversarially chosen, including their order of arrival. Still, these problems are analysed by similar techniques, including the competitive ratio of an algorithm, defined as the worst-case ratio between the algorithm's performance and that of a clairvoyant (a.k.a. offline) planner who knows all prices in advance<d-footnote>Note that the expectation may be outside the ratio in some analyses, see e.g. <d-cite key="lee1988expectation"></d-cite>,<d-cite key="ezra2023prophet"></d-cite>, and references therein. This is a design choice.</d-footnote>
$$\begin{align}
\text{CR} = \inf_{X_1,\ldots,X_T} \frac{\mathbb{E}[\text{ALG}(X_1,\ldots,X_T)]}{\mathbb{E}[\text{OPT}(X_1,\ldots,X_T)]}.
\end{align}$$

The notations $\text{ALG}(X_1,\ldots,X_T)$ and $\text{OPT}(X_1,\ldots,X_T)$ are left intentionally vague in this literature to emphasise that the competitive ratio is a very general concept that can be applied to many different problems and performance metrics (e.g., the value $X_t$ chosen for prophets and one-max-search, vs. the probability of selecting the maximum value in secretary problems). Due to independence, the optimal competitive ratio for Prophet problems is $1/2$, see <d-cite key="krengel_semiamarts_1977"></d-cite>, while for Secretary problems it is $1/e$, see <d-cite key="dynkin1963optimum"></d-cite>. In one-max-search, one must assume that the prices are bounded in $[1,\theta]$ for some $\theta>1$ to get non-trivial guarantees, and the optimal competitive ratio is $\theta^{-1/2}$, see <d-cite key="el-yaniv_competitive_1998"></d-cite>.

What about predictions? How much can they improve this $\theta^{-1/2}$ ratio? The <it>robust</it> algorithm of El-Yaniv, in <d-cite key="el-yaniv_competitive_1998"></d-cite>, buys the first price above $\sqrt{\theta}$, and gives us a bound on the robustness achievable. At the other end, given a prediction $Y$ of the maximum price $\max_{t\in[T]} X_t$, a consistent algorithm sets its threhold price at $Y$, achieving a consistency of $1$. In between, Sun et al. already gave, in <d-cite key="sun_pareto-optimal_2021"></d-cite>, the Pareto frontier of achievable trade-offs between consistency and robustness. I will spare you the equations for the front, which aren't very enlightening. 

However, the algorithm of Sun et al. is not smooth: a small error in the prediction $Y$ can cause a large drop in performance. In order to obtain smoothness, my coauthors and I (chiefly <a href='https://scholar.google.com/citations?user=ZhWGR7QAAAAJ&hl=fr'>Ziyad Benomar</a>) reanalysed the Pareto front to characterise <it>all</it> smooth threshold algorithms through the geometry of the set of Pareto-optimal threshold functions. This formalism allowed us to then study the smoothness of these functions to derive competitive ratio bounds in terms of the prediction error 
$$\begin{align}
\Ec(Y,X^*):= \min\left\{\frac Y{X^*}, \frac{X^*}{Y}\right\},
\end{align}$$

where $$X^*:=\max_{t\in[T]} X_t$$ is the maximum price. Precisely, we show that the competitive ratio degrades as a power of the prediction error $\Ec(Y,X^*)$ which relates directly to the smoothness of the algorithm. Finding the optimal smoothness can then be characterised through a triple consistency-robustness-smoothness Pareto front. 

I will leave technical details to the paper, the instructive conclusions in my view are that: 
<ul>
<li>answering the multi-objective problem of consistency, robustness, and smoothness is quite difficult even on simple problems,</li>
<li>that, instead of searching for a single optimal algorithm, a keener understanding of the problem's constraints and geometry is needed to conclusively answer the trade-offs,</li>
<li>and that, while the high-level ideas transfer well, the nitty-gritty of analysis is ad-hoc and problem dependent and it's not clear if a general form akin to dynamic programming can be found.</li>
</ul>

# Open questions for learning theorists

This leaves us with an awkward feeling: the problem of algorithms with predictions is cool, challenging, and highly relevant for practical applications, but its ungeneralisability leaves an unpleasant aftertaste. Perhaps a new perspective is needed, and learning theorists and statisticians are well equiped to provide it.
In my view, there are several conceptual and technical questions that are particularly natural for learning theorists and statisticians.

<ol type='1'>
<li> <b>Bridging prediction error and generalisation guarantees.</b> In algorithms with predictions, analysis is generally worst-case and purely deterministic: the predictor is just some scalar. In contrast, learning theory has cut its teeth on stochastic generalisation frameworks. Can we bring these together to obtain meaningful performance guarantees?</li>
<li> <b>From static predictions to control and dynamic programming.</b> Many decision problems are inherently sequential and can be solved via the general dynamic programming principle. The generality of this framework is a huge achievement and a powerful tool. Can we find an analogue general decision framework for algorithms with predictions? In the context of control, this has been studied a bit<d-footnote>See, e.g., papers on <it>lookahead</it> in control and reinforcement learning such as <d-cite key='nadav1'></d-cite> and <d-cite key='nadav2'></d-cite>.</d-footnote>, but a general theory is still missing.</li>
<li> <b>Classifying brittleness and stability of problems.</b> There's an interesting question going around in the community: which problems are inherently brittle, i.e., for which <it>no</it> algorithm can be both robust and consistent, while being smooth? See for example <d-cite key="elenter2024overcoming"></d-cite> for a recent example.  On the one hand, classifying problems into brittle and stable families is an interesting theoretical question, but perhaps one ill suited to statistics. But, on the other hand, us learning theorists should probably be considering the consequences of this brittleness when predicting information for decision-making problems. </li>
<li> <b>Distributional predictions.</b> On many problems, point predictions are not the most natural output of a predictor. One would be better served by a prediction about the whole distribution of a key variable, such as $X^*$ in one-max-search. There is a strong demand for the study of this problem from computer scientists, who often find their tools inadequate for the task. There's strong potential for statisticians and applied mathematicials to contribute here. One might hasard to guess conections to questions of calibration in learning theory</li>
</ol>

This area is still new and emerging, but already very active. If you are interested in any of the above questions, feel free to reach out, I can put you in contact with other researchers in the area. If you want to learn more about algorithms with predictions, I highly recomend the curated Algorithms with Predictions initiative <a href='https://algorithms-with-predictions.github.io/'>website</a>, every research field should have one!