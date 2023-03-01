---
layout: distill
title: Online Learning in Online Auctions
description: Dynamics in markets
date: 2020-12-01
img: assets/img/IMG_4044.jpg
authors:
  - name: Lorenzo Croissant
    affiliations:
      name: Criteo AI Lab
  - name: Clément Calauzènes
    affiliation:
      name: Criteo AI Lab
  - name: Marc Abeille
    affiliation:
      name: Criteo AI Lab
importance: 3
category: [Online Learning]
toc:
  - name: Introduction
  - name: The Second Price Auction
  - name: A Peculiar ERM
  - name: Smoothed Gradient Descent
  - name: Convergence Notions
  - name: Conclusion
  - name: Extensions
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



## Introduction

How complicated can it possibly be to sell a bottle of wine? 

From this surprisingly straightforward question has arisen the fertile, if somewhat obscure, field of Auction Theory<d-footnote> This theory is more properly referred to as Mechanism Design, but this generalisation is not relevant here so I will use Auction Theory for clarity.</d-footnote>. It is fertile in part because it sits neatly at the confluence of mathematics, computer science, economics, sociology and psychology, very much like the related field of Game Theory. It has led to several economics Nobel prizes, influenced real-world market design for public tenders in telecom and other sectors, and it underpins key questions regarding the funding model of the internet.

Indeed, almost all ads on the internet are sold at auction in a highly automated manner (all of it happens while your page is loading, in about $50$ ms). Whether these auctions are priced efficiently, fairly, and transparently, is therefore a key, if largely ignored, question concerning our daily lives. 

I won't go into fairness here, only into questions of efficiency. In particular, I would like to answer the following questions:
 <ol type='i'>
  <li>How can I accurately determine the price to sell each bottle of wine to a buyer if I have, say, $10^{10}$ bottles? </li>
  <li>If I have $50$ ms between each sale to determine the price, can I still price effectively</li>
</ol> 

## The Second Price Auction

To begin to answer i. we need to start by thinking about the design of the auction itself. Having collected prospective buyers, do I ask them to submit rising bids publicly? Do I ask them to submit sealed envelopes and take the highest bid? Do I name descending prices until someone accepts? How much should the winner pay? Why shouldn't I charge losers pay too? 

The answers to the last two questions probably seem obvious, but they are surprisingly complex, and they heavily impact the equilibrium behaviour of the bidders. The choice of the seller often lands on the <i>second price</i> auction, in which the highest bidder wins and pays the smallest bid which still wins her the auction. Unlike the <i>first price</i> auction, in which you pay your own bid, this format incentivises players to bid according to the true value they assign to the item. 

We will therefore study a second price auction, but in order to avoid large losses, we will set a minimum price of sale, a <i>reserve price</i>, for each item and bidder, and announce them publically. Setting an individualised reserve price is particularly important when there is strong asymmetry amongst the buyer's value for the item, leading the second-highest bid to be much lower than the winning bid and therefore poor pricing.

## A Peculiar ERM

discontinuous function + plot, ERM can have many minima
SGD can't converge properly on it.


## Smoothed Gradient Descent

remove discontinuity, swap integral and gradient
what functions preserve pseudo-conv by convolution? old paper by Ibragimov


## Convergence Notions

trade-off between bias and variance for rate + plot from paper


## Conclusion

Real-time alg, fully online 

All in all, it is surprisingly hard to sell a bottle of wine properly!

## Extensions

First price auctions, stationary bandit, optimal rate or no optimal rate at $O(1)$ alg?

Question of pseudo-concavity when adding a model in higher dimensions

Newton methods?