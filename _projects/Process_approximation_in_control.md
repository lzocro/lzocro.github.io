---
layout: distill
title: Process Approximation Methods in Control Theory
description: Surrogate stochastic objects
img: assets/img/project_covers/IMG_4044.jpg
authors:
  - name: Lorenzo Croissant
    affiliations:
      name: CEREMADE, Université Paris Dauphine
importance: 5
category: [Control Theory]
bibliography: DiffusionLimit1.bib
date: 2023--01
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



## Background

This technical note assumes extensive control theory and functional analysis background, to provide a higher level overview extending [this project on diffusion limits of pure jump processes](/projects/Diffusion_limit/). 

In optimisation theory in $\Rb^d$ it is common to study a difficult optimisation problem via a surrogate objective, which has more desirable properties (typically convexity) but has an optimum near or identical to the original objective. However, in functional optimisation and in particular in control theory this is perhaps a less popular angle of attack into practical problems. 

 A similar approach in control theory would lead us to change our gain/cost functional, and we are confronted here with a "paralysis of choice", if you will, due to the size of the spaces involved and their complexity. To break out of it, I see three fundamental surrogate types we could construct 

<ul>
<li> On the control space, replace admissible controls $\Ac$ by a simpler set;</li>
<li> On the cost function, replacing it by another one;</li>
<li> On the controlled stochastic process itself.</li>
</ul>

We will now abandon the first two in this project, but I would like you to consider them too, as they may turn up to be useful in practical applications. It is no secret, for instance, that Linear Quadratic Control owes a large part of its popularity to its ability to lead systems to behave like we would want them too without needing to use a complicated <i> intrinsic </i> cost of the problem. 

## Comparing Stochastic Processes 

Let us suppose we have two stochastic process $X^1$, $X^2$ whose values are say $\Rb^d$-valued càdlàg functions in the Skorohod space $\Omega:=\Db(\Rb_+;\Rb^d)$, but otherwise perhaps defined on different probability spaces $(\Omega,\Fc^1,\Fb^1,\Pb^1)$ and $(\Omega,\Fc^2,\Fb^2,\Pb^2)$. Let's fix a control set $\Ab$ and let $\Ac^1$ and $\Ac^2$ be the set of admissible controls of both processes. I will now pose a control problem on each process, say $J_1$ and $J_2$.

I would like to ask, in this post, how one should compare $J_1$ and $J_2$? The surrogacy conversation above suggests this could help me to solve an easier problem $J_1$ instead of, or as an approximation to, a difficult $J_2$. I will present in the rest of this piece a possible path based on HJB equations, but I would like to acknowledge that there are several other possible angles, which I won't get into to save time. 


In the following I will write $J_1$ and $J_2$ in a peculiar form, since I will pose them as  functionals not only of $\alpha$ but also of the reward function $r$ for $r$ in some vector space of functions $\Rc$.
From this perspective I will ask only that $J_1:\Rc\x\Ac^1\to \Rb$ and $J_2:\Rc\x\Ac^2\to \Rb$, in such a way that $J_2$ is linear in $r$. By this I mean that for any $(f,g)\in\Rc^2$, 

$$ J_2[f+g] = J_2[f] + J_2[g]\,. $$

<div class="example">
If $X_2$ is a Levy Process, letting $\Ac^2$ be the set of $\Fb^2$-predictable controls, and $\Rc=\Cc^0_b$, then any cost functional of the form 
$$ J_2[r,\alpha] := \Eb\left[\int_0^t r(X^2_{s-},\alpha_s)  m(\de t) \right] $$
in which $m(\de t)$ could be the Lebesgue measure or a Poisson random measure, is linear.
</div>

## A Unique Property of HJB Equations for Controlled Markov Processes

Using customary notation, I will note $V_1$, $V_2$ the value functions of $J_1$ and $J_2$. Under suitable conditions, which are already clearly outlined in ample detail in the literature, they will both satisfy a Dynamic Programming Principle and a HJB equation. Let's focus for illustration on finite horizon problems whose equations would write themselves as 

$$ \begin{align*} 0&\equiv F_1(r,V_1) = \partial_t  V_1 -\max_{a\in\Ab}\{\Lc^a_1 V_1 +r\} \\
 0&\equiv F_2(r,V_2) = \partial_t  V_2 -\max_{a\in\Ab}\{\Lc^a_2 V_2 +r\} \end{align*}$$

The key observation is that (assuming $\Lc^a_1V_1\in\Rc$) we can write
\\[ 0\equiv F_1(r,V_1) = F_2(r + (\Lc^a_1 -\Lc^a_2)V_1,V_1 ) \\] 
so that we now have the probabilistic representation
\\[ V_1 = \sup_{\alpha\in\Ac_2}J_2[r + (\Lc^a_1 -\Lc^a_2)V_1, \alpha] \\]
if we have verification for $F_2$. Finally, if we combine this with the linearity in $r$ assumption on $J_2$, we obtain a bound 
\\[ \vert V_1-V_2\vert \le \sup_{\alpha\in\Ac_2} \vert J_2[(\Lc^a_1-\Lc^a_2)V_1 ,\alpha]\vert \,.\\]

## Reducing to a Regularity Problem

Thus, obtaining bounds on $(\Lc^a_1 -\Lc^a_2)V_1$ is sufficient to quantify the error in the approximation. This is a marked improvment over requiring bounds on $\Lc^a_1 -\Lc^a_2$ because they are directly applied in $V_1$, which might be quite regular if the approximating process (whose generator is $\Lc^a_1$) is well chosen. 

A good example is when $\Lc^a_2$ is the generator of a finite difference approximation to a diffusion process $\Lc^a_1$. In this case, we can use the regularity of the solution $V_1$ to the HJB equation for the diffusion process to obtain bounds on $(\Lc^a_1 -\Lc^a_2)V_1$ and thus on the error in the approximation, which is the classical methodology of numerical schemes on diffusive HJB equations. 

This can also be used with other approximation methods, as we demonstrated in <d-cite key="ABC23"></d-cite>, in which we approximated a high-frequency pure jump process by its diffusion limit process, whose solutions can be shown to be quite regular. There are probably many interesting examples in which this kind of approximation can be useful, either for numerical approximation or for theoretical analysis.

## Final Remarks

The idea for this general analysis came out from work with my Ph.D. supervisors, see [this project](/_projects/Diffusion_limit.md). I would like to credit them for the ideas and technical work which lead to the above. However, as they have had no authorship in this note, any and all mistakes made and opinions voiced must be understood as purely my own.
