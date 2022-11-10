---
layout: distill
title: Diffusive Limit Control
description: Efficient approximation of high-frequency pure jump problems.
img: assets/img/IMG_2987.jpg
authors:
  - name: Lorenzo Croissant
    affiliations:
      name: CEREMADE
  - name: Bruno Bouchard
    affiliations:
      name: CEREMADE
  - name: Marc Abeille
    affiliation:
      name: Criteo AI Lab 
importance: 7
category: [Control Theory]
---

<div style="display:none">
  \(
    %\newcommand{\CB}{\mathbb{C}}
    \def\CB{\mathbb{C}}
    \newcommand{\CC}{\mathcal{C}}
    %
    \def\de{\mathrm{d}}
    \def\De{\mathrm{D}}
    \def\x{\times}
    \def\ve{\varepsilon}
    \def\dre{\delta r^\ve}
    %
    %% Blackboard Bolds %%
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
    %% Caligraphics %%
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
    %% Romans %%
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
    %% Scripts %%
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
    %% Bold face %%
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
    %% Fraktur %%
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
  \)
</div>


Control problems are omnipresent in industrial applications of online decision making. In many of these application time evolves in a naturally discrete manner. While discrete time problems are well studied and are relatively easily solved by Dynamic Programming, the frequencies of real-world applications often make this an infeasible approach. This problem is generally avoided using some time-aggregation approximation, such as a continuous time limit. A standard example of this situation is in financial markets: at the microscopic scale there are only order books, which evolve only when the asset is traded; control problems however are often formulated on a (continuous time) diffusion process.

In this project the goal is to assess quantitatively the benefits of such changes of scale in terms of the control problem. More precisely my coauthors and I focus on two directions:
 <ol type='i'>
  <li>Can regularity of the continuous approximation yield convergence rates in the value of the control problem?</li>
  <li>Can we use the continuous approximation to create efficient numerical solvers for the discrete problem?</li>
</ol> 
Below I will detail in what precise sense the answer to both is yes, but first I would like to highlight the practical implications of these answers. From i. one can identify if the error in the value of the control problem is of acceptable order for the application, and therefore determine via ii. into which problems to invest the time and energy of a proper resolution.  



## The Setting

In what follows we will consider that the evolution times follow a Poisson process, although it could be interesting to look at extensions to other cases. Let $\Omega:=\Db_{[0,T]}$ be the Skorohod space on $[0,T]$, for $T>0$ possibly infinite, and consider a positive finite random measure $N$ on $\Rb^{d'}\times[0,T]$ and a measure $\Pb$ on $\Omega$ such that $N$ is a $\Pb$-Poisson process with compensator $\eta\nu(\de e)\de t$, for $\eta>0$ and $\nu$ a probability measure on $\Rb^{d'}$. Denote $\Fb$ the augmentation of the natural filtration of the (marked) Poisson process. For ease of notations, we set $N_{t}:=N(\Rb,[0,t])$ for $t\ge 0$. 

Let $$\Fb=(\Fc_{s})_{s\ge 0}$$ be the $\Pb$-augmentation of the raw filtration generated by the random measure $N$. Given a compact subset $\Ab$ of $\Rb$, let $\Ac$ be the collection of $\Fb$-predictable processes with values in $\Ab$. We will work on the filtered probability space $(\Omega,\Fc, \Fb, \Pb)$, where $\Fc=\Fc_{T}$ for $T>0$ given. 

For some $x\in\Rb^d$, $\alpha\in\Ac$, a bounded measurable map $b$ (from $ \Rb^d \x \Ab\times \Rb^d$ into $\Rb^d$), let $X^{x,\alpha}$ denote the solution to the SDE

$$\begin{align} X_\cdot^{x,\alpha} = x + \int_0^\cdot\int_{\Rb^{d'}} b(s,X_{s-}^{x,\alpha}, \alpha_s, e) N(\de e,\de s)\,.\label{eq: def pure jump process}\end{align}$$

We consider some instantaneous gain $r:[0,T]\x\Rb^d\x\Ab \mapsto \Rb$ obtained at each jump of the system. We can now define a cost functional for all $(t,x)\in[0,T]\x\Rb^d$ by

$$\begin{align}
 J(t,x;\alpha):&[0,T]\x\Rb^d\x\Ac^t \to\Rb \notag \\
 &\alpha\mapsto \Eb\left[\int_t^T r(s, X_s^{t,x,\alpha},\alpha_s)\de N_s \right]\,, \notag
\end{align}$$

where $X^{t,x,\alpha}$ represents a process like \eqref{eq: def pure jump process} started from time $t$ instead of $0$, and $\Ac^t$, $\Fc^t$, and $\Fb^t$ are the corresponding analogues of $\Ac$, $\Fc$, and $\Fb$ respectively.

## The Control Problem

The control problem associated to $J$ is given by the value function $V$ defined below in terms a functional optimisation problem of $\Ac$.

\\[ V(t,x):=\sup_{\alpha \in \Ac^{t}} J(t,x;\alpha)\,.\\]
for any $(t,x)\in [0,T]\x \Rb$. 

The interconnection at the infinitesimal scale between $X^{x,\alpha}$ and $\alpha$ is the key complexity of control theory. The usual method involves recasting the optimisation problem as the solution of a PDE. Indeed, assuming $(b,r)$ is a continuous and bounded map, $V$ is the unique (bounded) viscosity solution of the associated Hamilton-Jacobi-Bellman equation

$$\begin{align}
&\partial_{t}V + \eta \sup_{a\in \Ab}\left( \int V(\cdot,\cdot+b(\cdot,a,e))-V\nu(\de e)+r(\cdot,a)\right)=0 \mbox{ on }[0,T)\times\Rb^d \notag \\
&V(T,\cdot)=0 \mbox{ on $\Rb^d$ }\notag\,.
\end{align}$$

This equation is integro-differential, so it is rather unpleasant to solve numerically. The real issue in high-frequency applications is the multiplicative term in the frequency of jumps $\eta$ in front of the integral. This scaling implies that errors are blown up, and therefore that the numerical approximation of the integral must be very fine, and increasingly so as $\eta\to+\infty$.

However, there are certain instances where the death sentence given by this intuition can be avoided. In many applications a \emph{diffusion limit} problem is solved efficiently as an approximation. In this project we seek to investigate precise convergence rates for this approximation. The remainder of this post gives an overview of the approach, starting with the details of the diffusion limit and continuing with some high-level results, and then a quick review of explored aspects of the problem and possible extensions.

## The Diffusion Limit 

This particular regime consists of problems with the following scaling, for some $\ve\in(0,1)$
\\[ \eta=\eta_\ve := \ve^{-1}\,,\; b=b_\ve:=\ve b_1 + \ve^{\frac12}b_2\,.\\]
We are studying the limit as $\ve\to0^+$, therefore the relevant renormalisation of the cost functional to take is 
\\[ J_\ve(t,x;\alpha):= \frac1{\eta_\ve} \Eb\left[\int_t^T r(s, X_s^{t,x,\alpha},\alpha_s)\de N_s \right]\,,\\]
which is strategically equivalent for any $\eta>0$ to the original problem $J$. 

By the functional central limit theorem, the process $X^{x,\alpha}$ defined by \eqref{eq: def pure jump process} with $b_\ve,\eta_\ve$ converges weakly to $\bar X^{x,\alpha}$ the solution of the Itô SDE 

\\[ \bar X^{x,\bar\alpha}=x+\int_{0}^{\cdot} \mu(\bar X^{t,x,\bar\alpha}_s, \bar\alpha_s)\de s + \int_0^\cdot \sigma(\bar X^{t,x,\bar\alpha}_s, \bar\alpha_s)\de W_s\\]

with coefficients

\\[\mu(x,a):=  \int b_{1}(x,a,e) \nu(\de e),\; \sigma(x,a):= \left( \int b_2b_2^\top(x,a,e) \nu(\de e)\right)^{\frac12},\\]

for all $(x,a)\in \Rb^d \x \Ab$. The solution to this SDE exists and is unique under some continuity assumptions on $b_1$ and $b_2$. Here $W_s$ is a Wiener process on $\Rb^d$, and one has to reform the probability space considered to $(\Omega,\bar\Fc,\bar\Fb,\bar\Pb)$ using the standard construction for $\bar X^{x,\alpha}$. Likewise one defines $\bar\Ac,\bar\Ac^t$ analogous to $\Ac,\Ac^t$. 

Then, given some regularity on $r$, we can define the diffusive control problem

\\[ \bar V(t,x):=\sup_{\bar\alpha \in \bar \Ac^{t}} \bar \Eb\left[\int_{t}^{T}r(\bar X^{t,x, \bar\alpha}_s, \bar\alpha_s) \de s\right]\,, \\]
for any $(t,x)\in [0,T]\x \Rb$. As in the pure-jump case, it is well known that $\bar V$ is the unique bounded viscosity solution of the PDE

$$\begin{align}
&\partial_{t} \bar V +\sup_{\bar a\in \Ab}\left(\mu(\cdot,\bar a)\partial_{x} \bar V  +\frac12 \Tr[\sigma\sigma^\top(\cdot,\bar a) \partial^{2}_{xx}\bar V] +r(\cdot,\bar a)\right)=0,\; \mbox{on } [0,T)\x \Rb^d,\label{eq: PDE bar V}\\
&\bar V(T,\cdot)=0,\; \mbox{on } \Rb^d. \notag
\end{align}$$

The diffusive PDE \eqref{eq: PDE bar V} is still non-linear but it doesn't involve an expectation anymore, and it has been studied at great length. This advantage is both analytic (regularity results and methods are readily found in the litterature), and numeric (there is a plethora of well studied schemes for \eqref{eq: PDE bar V}). Nevertheless, it is non-trivial to ascertain that in this general framework the control problems converge as $\ve\to0^+$ and the rate of convergence isn't known. Such approximation certificates would provide the rigourous grounding of the use of numerical resolution of the much simpler equation \eqref{eq: PDE bar V} for high-frequency control problems.

## Approximation results

To quantify the approximation error we employ an analytic-probabilistic method, using the PDE and IDE in analytic arguments to represent the error, and then concluding via the probabilistic formulation to obtain a bound on the error. More precisely we introduce a Taylor remainder 

\\[\dre:=\mu\partial_{x} \bar V  +\frac12 \Tr[\sigma\sigma^\top \partial_{xx}^{2}\bar V] - \frac1\ve\int \bar V(\cdot,\cdot+b_\ve(\cdot,e))-\bar V\nu(\de e)\,.  \\] 

The analysis rests upon the following observation: if $\bar V$ is a solution to equation \eqref{eq: PDE bar V}, then it is a solution to a pure-jump HJB equation with modified source term, namely:

\\[ \partial_{t} \bar V +\eta_\ve\sup_{\bar a\in \Ab}\left( \int \bar V(\cdot,\cdot+b_\ve(\cdot,\bar a,e))-\bar V\nu(\de e)+(r+\dre)(\cdot,\bar a)\right)=0,\\]

on $[0,T)\x \Rb^d$. From here the probabilistic interpretation gives us 

\\[ \vert \bar V - V_\ve \vert \le \sup_{\alpha\in \Ac}\Eb\left[ \int_0^T \vert \dre \vert (X^{t,x, \alpha}_s, \alpha_s)\de N_s \right] \\]

and it remains to bound $\Vert\dre\Vert_\infty$. This is achieved through regularity analysis of solutions of \eqref{eq: PDE bar V}. Details can be found in the various articles attached to this project.

Theorem .... goes here

Diagram of numerical approximation.



## Other Aspects

Theorem ... represents only the essential first step in this line of work. There are many technical points which I haven't highlighted here for the sake of brevity, and some interesting directions beyond this first result. For instance, I considered here a finite horizon control problem but in [cite] we extended this study to the ergodic setting and also from bounded growth to $b$ of linear growth. We also studied the possibility of correcting the error by repeating this procedure to higher orders involving a set of (possibly coupled) differential equations. 

In the context of another project page, we studied the extension to the reinforcement learning problem, i.e. where $b$ and $r$ are unknown a priori and are learned from sequential interaction.



## Extensions

There are some interesting extensions that would merit consideration in this setting.

First, some matters of generalisation. The lynchpin of this method is the approximation of the generator $\Lc$ of the pure-jump process by $\bar\Lc$, insofar as they are applied to $\bar V$. These are the only terms that differ between the two HJB equations. The analysis above should then be applicable to any process for which we can bound the difference $\vert \Lc -\bar\Lc\vert \bar V$. There are many possible candidates for extensions here, whose inventory would be interesting from a probabilistic standpoint. Another generalisation would of course involve the study of different control problems, such as optimal stopping. 

Second, there is the interesting point of the iterated error correction. Suppose the rescaled error term $\ve^{-\frac\gamma2}\dre$ is regular, and consider the equation.
\\[ \partial_{t} \bar v +\eta_\ve\sup_{\bar a\in \Ab}\left( \int \bar v(\cdot,\cdot+b_\ve(\cdot,\bar a,e))-\bar v\nu(\de e)+\ve^{\frac\gamma2}\dre(\cdot,\bar a)\right)=0 \\]
If the solution remains bounded and regular, we can construct an approximation $\bar V + \ve^{\frac\gamma2}\bar  v$ which improves the rate. In particular, if the solution $\bar v$ is $\delta\gamma$ Hölder, then 
\\[ \Vert V_\ve - (\bar V + \ve^{\frac\gamma2}\bar  v)\Vert_\infty \le \ve^{\frac{\gamma+\delta\gamma}{2}}\\]
In theory, if the resulting error is smooth enough we could repeat the process. This begs the question: if $r\equiv0$, can this be used to represent an arbitrary diffusion pre-limit pure-jump process as a sort of frequency decomposition.


Finally, from a practical perspective there is a question over the learning of coefficients, see also [cite other project], and especially the possibility of estimating $\ve$ in real systems. There might be some connections here to the estimation of Hurst-coefficients in fractional Brownian motions.


## Conclusion




## Bibliography










