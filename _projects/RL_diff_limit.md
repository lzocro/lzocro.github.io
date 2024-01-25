---
layout: distill
title: Reinforcement Learning with continuous states
description: Learning to control along a single trajectory.
img: assets/img/project_covers/IMG_5210.jpg
authors:
  - name: Lorenzo Croissant
    affiliations:
      name: CEREMADE
  - name: Marc Abeille
    affiliation:
      name: Criteo AI Lab
  - name: Bruno Bouchard
    affiliations:
      name: CEREMADE
toc:
  - name: Learning to control
  - name: The OFU principle
  - name: Methodology
  - name: Results
  - name: Ongoing and future work
importance: 8
category: [Reinforcement Learning]
bibliography: RLdifflimit.bib
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

## Learning to control

The Reinforcement Learning (RL) problem can be generally understood as the problem of learning to control from the feedback of the controls used. In my opinion, what makes this framework interesting from a mathematical standpoint is the interplay between learning and the control problem. Since feedback is obtained only by visiting state and control pairs, gathering information about the system is itself a control problem, which may conflict with the control problem we're actually trying to solve.

In order to focus on the control/learning interplay, I will choose a very restrictive RL framework which I call non-episodic online model-based RL. Let us consider a family of $\Rb^d$-valued controlled stochastic processes $(X^{\alpha})\_{\alpha\in\Ac}$, and a reward function $r:\Rb^d\x\Ab\to\Rb$, in which $\Ab$ is the set of control values. To represent the uncertainty, we consider a finite-dimensional collection of models $\theta\in\Theta\subset\Rb^{d\_\Theta}$, amongst which lies an unknown real value $\theta^*$. For each $\theta\in\Theta$, we denote by $(X^{\theta,\alpha})\_{\alpha\in\Ac}$ the corresponding family of controlled processes whose dynamics are parametrised by $\theta$. Our objective<d-footnote>We consider measurability requirements, e.g. in admissible controls $\Ac$, w.r.t $X^{\theta^*,\alpha}$ henceforth.</d-footnote> is to solve 

$$\begin{align}
    \rho^*_{\theta^*}:=\sup_{\alpha\in\Ac} \liminf_{T\to+\infty}\frac1T\Eb\left[\sum_{s=0}^T r(X^{\theta^*,\alpha}_s,\alpha_s)\right],\label{eq:rho*}
\end{align}$$
 without a priori knowledge of $\theta^*$. 

The use of an ergodic (i.e. long-term average) criterion is motivated by 
<ol type='i'>
    <li> The absence of episodes: it allows the learning game to run forever along the same trajectory, </li>
    <li> Analytical reasons: absence of terminal times forces us to rely only on the inherent regularity of the process</li>
    <li> The existence of turnpike properties, which will allow us to move back to finite-horizon systems, in some learnable regimes.</li>
</ol>

As usual in RL theory, we use the regret as a performance measure, which is defined, for any $\alpha\in\Ac$ as
$$\begin{align}
   \Rc_{T}(\alpha):= T\rho^*_{\theta^*} - \sum_{s=1}^T r(X^{\theta^*,\alpha^*}_s,\alpha^*_s),
\end{align}$$

This is natural for studying the interplay of decisions and learning since it prices ignorance of $\theta^*$ directly in terms of the control problem via $r$.

## The OFU principle

The study of optimal exploration in non-episodic online RL problems has been underpinned since <d-cite key='auer_finite-time_2002'></d-cite> by the optimism in the face of uncertainty (OFU) principle. This principle states that optimal exploration is obtained by playing greedily with respect to $\tilde\theta\_t$, the most optimistic<d-footnote>In terms of $\rho^*_{\tilde\theta_t}$, defined by analogy to \eqref{eq:rho*}.</d-footnote> estimate of $\theta^*$ at time $t$ inside some reasonable confidence region. 

This methodology originates in bandit theory, see e.g. <d-cite key="lattimore_bandit_2020"></d-cite> and has been applied to the RL setting to finite state Markov Decision Processes (MDPs) <d-cite key='jaksch_near-optimal_2010'></d-cite> and Linear Quadratic Systems <d-cite key='abeille_efficient_2020'></d-cite>. It has generally been shown to be optimal in the sense that it achieves the minimax regret rate, up to logarithmic factors. However, I find this picture quite unsatisfactory for two reasons:

<ol type='i'>
    <li> Arbitrary continuous systems don't translate well into finite MDPs. This is because finite MDPs can't represent structural regularity which exists in non-chaotic continuous systems. Discretising a problem a priori is therefore a bad idea.  </li>
    <li> Linear-quadratic problems are fully continuous, but unfortunately, they are limited in their application to a single type of problem, which prevents efficient exploration from being employed in non-linear systems. </li>
</ol>

Therefore, in this project, I strive to generalise the OFU principle to non-linear systems. I would like to highlight that this is primarily an analysis issue and not a new problem. Indeed, the OFU principle is a general methodology and it is expected to work as is in non-linear systems. The main difficulty is to prove that it does, and in particular to adapt/generalise existing analyses and quantities.

## Methodology

When considering general non-linear problems on continuous state spaces, problems arise immediately from the definition of $$\rho^*_{\theta^*}$$ due to the limit inferior. This limit exists if the process is ergodic in some meaningful way, which is unpleasant to study for infinite MDPs in discrete time. On the other hand, control theorists and stochastic analysts who work in continuous time have a good grasp of these ideas. Therefore, the first step of my methodology is to translate the problem into a continuous time setting. This is done by considering that arrival times for jumps of the process $X^{\theta,\alpha}$ are given by a Poisson process with intensity $\eta_\ve:=\ve^{-1}$. For the technical details of this formalism, see [this other project](/_projects/diffusion_limit.md). Let $N_t$ be the counting process associated with this Poisson process. Then, the ergodic criterion becomes, for any $\theta\in\Theta$,
$$\begin{align}
    \rho^*_{\theta^*}:=\sup_{\alpha\in\Ac} \liminf_{T\to+\infty}\frac1{T\eta_\ve}\Eb\left[\int_0^T r(X^{\theta^*,\alpha}_{s-},\alpha_{s-})\de N_s\right].\label{eq:rho*CT}
\end{align}$$

In order to write the learning problem more clearly, let's specify the model structure a bit by assuming that the dynamics of $X^{\theta,\alpha}$ are the solution to the Stochastic Difference Equation:
$$\begin{align}
    X^{\theta,\alpha}= x+ \sum_{s=0}^{N_\cdot -1} \mu_{\theta}(X^{\theta,\alpha}_{s},\alpha_{s}) + \Sigma\xi_{s+1} \label{eq:SDE}
\end{align}$$
in which $(\xi_s)\_{s\in\Nb}$ are $\Rb^d$-valued standard Gaussians independent of everything else, $\Sigma\in\Rb^{d\times d}$
and $\mu_{\theta}:\Rb^d\x\Ab\to\Rb^d$ is a measurable function.

<div class="assumption">
Uniformly in $(\theta,a)\in\Theta\times\Ab$
<ol type='i'>
  <li> $\mu_{\theta}(\cdot,a)$ is Lipschitz continuous (but not necessarily bounded) </li>
  <li> $r(\cdot,a)$ is Lipschitz continuous and bounded </li>
  <li> $\Sigma\Sigma^\top$ is Positive Definite and bounded (non-degenerate noise). </li>
</ol>
</div>

<div class='assumption'>
    There is $(\ell_\Vs,L_\Vs,\cf_\Vs,M_\Vs,M_\Vs')\in\Rb_+^5$  and a Lyapunov function $\Vs\in\Cc^{2}(\Rb^d_*;\Rb_+)$ satisfying, for any $(x,x',a,\theta)\in\Rb^d\x\Rb^d\x\Ab\x\Theta$, $x\neq x'$, and $\ve \in (0,1)$:
  $$\begin{align}
      % &\mbox{$\rm{(i.)}$}
      &\qquad\qquad \ell_\Vs\lVert x-x'\rVert\le \Vs(x-x')\le L_\Vs\lVert x-x'\rVert\,,\notag\\
      % &\mbox{$\rm{(ii.)}$}
      &\quad\quad \sup_{x\in\Rb^d_*}\lVert \nabla \Vs(x) \rVert \le M_\Vs \mbox{ and } \sup_{x\in\Rb^d_*}\lVert \nabla^2\Vs(x)\rVert_{\rm op}\le M_\Vs'\,,\notag\\
      % &\mbox{$\rm{(iii.)}$}
      &\quad \Vs(x+ \mu(x,a)-x'-\mu(x',a))\le (1-\ve \cf_\Vs)\Vs(x-x')\,. \notag%\label{eq:lyapunov asmp joint on jump problem}
  \end{align}$$
  in which $\Rb^d_*:=\Rb^d\setminus\{0\}$.
</div>

Using ergodic control results, we can characterise the optimal value of this problem as the unique solution of the Hamilton-Jacobi-Bellman (HJB) equation associated with the ergodic control problem. This integral equation also characterises an optimal control. To apply OFU to this class we still need a learning methodology to build confidence sets for non-linear systems. This can be done in the framework of <d-cite key='russo_eluder_2013'></d-cite> using Non-Linear Least-Square, in which 

$$\begin{align}
    \hat\theta_t:\in\arg\min_{\theta\in\Theta} \sum_{s=0}^{N_t-1} \left\lVert X^{\theta^*,\alpha}_{s+1} - X^{\theta^*,\alpha}_{s} - \mu_{\theta}(X^{\theta,\alpha^*}_{s},\alpha^*_{s})\right\rVert^2.
\end{align}$$

This estimator can be used to construct a well-calibrated $\delta$-confidence set in the following way 
$$\begin{align}
\Cc_{t}(\delta)&:= \left\{\theta\in\Theta: \sqrt{\sum_{s=0}^{N_t-1} \left\lVert\mu_\theta(X_{s}^{\theta^*,\alpha},\alpha_s)-\mu_{\hat\theta_{t}}(X_{t}^{\theta^*,\alpha},\alpha_s)\right\rVert^2} \le \beta_{t}(\delta)\right\}\,.\label{eq: def conf sets}
\end{align}$$
for a suitable choice of $\beta_t(\delta)$ which is of the order of $\sqrt{\log(N_T)}$ up to complexity metrics.

With these two components, up to the analysis, we should be able to apply the OFU principle to generic non-linear problems.


## Results

Unfortunately, the analysis can't quite be extended as is from the literature for a handful of reasons:
<ol type='i'>
    <li> The complexity measures of the confidence radius $\beta_t(\delta)$ scale with the boundedness of coefficients and thus are infinite under Assumption 1. Since $\beta_t(\delta)$ appears in the regret bound, this makes the bounds meaningless. </li>
    <li>  Since the optimal controls we compute are only optimal in the infinite horizon limit, they are arbitrarily bad in finite time, so an efficient algorithm must update its behaviour lazily (i.e. infrequently) through time. This update scheme needs to be designed.</li>
    <li>  We need some improved concentration bounds beyond simple ergodicity to ensure the regret from the process of trying to escape to infinity is small. </li>
</ol>

In <d-cite key="CAB23"></d-cite> we solve the first problem by localising complexity measures to only consider regions effectively traversed instead of the whole space. This clips the complexity bounds in terms of the concentration of the process and makes the regret meaningful again since we also solve the third problem by deriving a concentration inequality from a Stochastic Lyapunov Condition. The second problem is solved by using a functional inequality to enrich the results of <d-cite key="russo_eluder_2013"></d-cite>. The resulting regret bound is given by Theorem 1, details can be found in the paper <d-cite key='CAB23'></d-cite> which is being published at ALT2024 and also appeared in the EWRL workshop as <d-cite key='CAB23EWRL'></d-cite>.

<div class="theorem">
Under Assumptions 1 and 2, for any $\delta\in(0,1)$, there is a constant $C\in\Rb_+$ independent of $\ve$ such that our algorithm $\alpha$ achieves 
    $$\begin{align}
        R_T(\alpha) \le  C\sqrt{\mathrm{d}_{E,N_T}\log(\Ns_{N_T}^\ve) T\log(T\delta^{-1})} 
    \end{align}$$
    with probability at least $1-\delta$, in which $\mathrm{d}_{E,N_T}$ is the $2\ve/\sqrt{T}$-effective<d-footnote>Meaning the eluder dimension of the set of restrictions to the ball of radius $\sup_{s\le T}\lVert X^{\theta^*,\alpha}_s\rVert$.</d-footnote> eluder dimension and $\log(\Ns_{N_T}^\ve)$ is the $\ve^{2}\lVert\bar\Sigma\rVert_{\rm{op}}^2/T$-effective<d-footnote>Essentially likewise.</d-footnote> log-covering number.
</div>

## Ongoing and future work

While we were able to design an optimal algorithm there are several directions for improvement which I am currently working on:
<ol>
    <li> Improving the computational efficiency of the lazy update steps to eliminate the supremum. While I can reduce the complexity of the optimisation problem in one step, it isn't clear if is possible to completely remove the supremum in the lazy updates to replace it with a simpler geometric object. In the linear case, one can use the determinant, but this is only because of the regularity of the map $\theta\mapsto\mu_\theta$. It is apparent that regularity conditions in the parametrisation are required at this step (which they weren't in previous arguments).</li>
    <li> Efficient optimistic planning remains complicated. While I can show easily how to solve the equivalent of Extended value iteration from <d-cite key='jaksch_near-optimal_2010'></d-cite>, I would like to get some efficient computational complexity bounds on the resolution of this type of HJB  equation. Of course, it would be exponential in the dimension, but I believe it might be possible to obtain fast convergence of the finite horizon value from Assumption 1 if one can inherit the regularity of the continuous equation.</li>
    <li> Reducing the strength of the Lyapunov assumption (Assumption 2) and studying the concentration properties of ergodic processes in order to generalise to more systems. This might also lead to the reduction of the stability assumption to a controllability assumption. The challenge here is the interplay between the reward's shape and the properties of $X^{\alpha,\theta^*}$ in \eqref{eq:rho*}. </li>
</ol>

On the other hand, our algorithm and analysis are too general to be useful for practitioners, so I would like to build based on this framework to explore more specific problems. In particular, I am interested in the following:

<ol>
  <li> Specialisation: deriving learning instances of NLLS which are more effective on specific dynamics. This also applies to the resolution of the HJB equation. </li>
  <li> Exotic noise structures: the HJB can be solved for more complex noise structures than just additive Gaussian martingale difference sequences such as multiplicative noise. This poses interesting statistical problems from a learning theory perspective (construction of confidence sets). </li>
  <li> Other kinds of stochastic processes could be considered too, such as self-exciting processes, which could find interesting use cases for RL in some new applications.</li>
</ol>


