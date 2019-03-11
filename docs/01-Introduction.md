---
output:
  pdf_document: default
  html_document: default
---
# Introduction actuariat 2

##Théorème de la fonction quantile
\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:fn-quantile"><strong>(\#thm:fn-quantile) </strong></span>\begin{align*}
U &\sim Unif(0,1)\\
Y &=F_x^{-1}(u) \Rightarrow Y \sim X\\
F_Y(x) &=F_{F_X^{-1}(u)}(x)=F_X(x)\, \text{pour}\, x \in \mathbb{R}\\
\intertext{ainsi:}\\
X &=F_X^{-1}(u)
\end{align*}
Voir preuve \ref{preuves:fn-quantile}</div>\EndKnitrBlock{theorem}

##Espérance tronqué {#intro:espétron}

\begin{gather*}
\begin{align*}
E[X \times \mathrm{1}_{ \{ X \ge x \} }]& =\int_{-\infty}^\infty y \times \mathrm{1}_{ \{ y \ge x\}}f_X(y)\, dy \notag \\ 
& =\int_{-\infty}^x 0\times f_X(y) dy + \int_x^\infty y f_X(y)\,dy \notag \\
& =\int_x^\infty y f_X(y)\,dy 
\end{align*}
\end{gather*}





##Fonction Stop-Loss {#intro:fn-stop}

$$
    \Pi_X(d) = E[\max(X-d,0)]\quad\text{pour}\,d \,\in \mathbb{R}
$$
Voir preuve \ref{preuves:fn-stop}

###Variable continue

$$
    \Pi_X(d) = \int_0^\infty \max(X-d, 0)f_X(x)\,dx
$$


###Variable discrète sur $({0,1h,2h,\dots})$

\begin{gather*}
\begin{align*}
f_X(kh) =& P(X=kh),\, k\in \mathrm{N},\, h > 0,\, d =k_0 h\\
\\
\Pi_X(k_0 h) =& E[\max(X-k_0 h, 0)]\\
=&\sum_{k=0}^\infty \max(kh-k_0 h, 0) P(X=kh)\\
=&\sum_{k_0=k+1}^\infty (kh-k_0 h) P(X=kh)\\
\end{align*}
\end{gather*}


###Propriété

\begin{gather*}
\begin{align*}
\Pi_X(0) =& \lim_{d \to 0} \Pi_X(d)\\
=& \lim_{d \to 0} E[\max(X-d, 0)]\\
=& E[X] \\
\end{align*}
\end{gather*}

##Fonction quantile {#intro:fn-quantile}
###Première forme {#intro:fn-quantile:1}
\begin{gather*}
\begin{align*}
\int_k^1 F_X^{-1}(u)\,du& =\int_k^1 [F_X^{-1}(u)-F_X^{-1}(k)+F_X^{-1}(k)]\,du\\
& =\int_k^1(F_X^{-1}(u)-F_X^{-1}(k))\,du + F_X^{-1}(k)\int_k^1 (1)\,du\\
& =\int_0^1\max(F_X^{-1}(u)-F_X^{-1}(k),\, 0)\, du + F_X^{-1}(k)(1-k)\\
& = E[\max(F_X^{-1}(u)-F_X^{-1}(k),\, 0)]+(1-k)F_X^{-1}(k)\\
& = E[\max(X-F_X^{-1}(k),\, 0)]+(1-k)F_X^{-1}(k)
\end{align*}
\end{gather*}

###Deuxième forme {#intro:fn-quantile:2}
\begin{gather*}
\begin{align*}
\int_k^1 F_X^{-1}(u)\, du& =\Pi_X(F_X^{-1}(k))+(1-k)F_X^{-1}(k)\\
\text{En remplaçant $\Pi_X(F_X^{-1}(k))$ par}\; \ref{preuves:fn-stop}\;\text{on obtient:}\\
& =E[X \times \mathrm{1}_{\{X > F_X^{-1}(k)\}}]-F_X^{-1}(k)\bar{F}_X(F_X^{-1}(k))+(1-k)F_X^{-1}(k)\\
& =E[X \times \mathrm{1}_{\{X > F_X^{-1}(k)\}}]+F_X^{-1}(k)(F_X(F_X^{-1}(k))-k)
\end{align*}
\end{gather*}

## Fonction quantile et espérance {#fn-et-Ex}


\begin{gather*}
\int_0^1 F_X^{-1}(u)\,du =E[F_X^{-1}(x)]\\
\int_0^1 F_X^{-1} (u)(1)\,du = E[X]\\
\intertext{Généralisation:}\\
\int_0^1 \phi(F_X^{-1}(u))\,du =E[\phi(F_X^{-1}(u))] =E[\phi(X)]
\end{gather*}

##TVaR {#intro:tvar}

$$
\text{VaR}_k(X)= F_X^{-1}(k)
$$

$$
\text{TVaR}_k(X)= \frac{1}{1-k}\int_k^1\text{VaR}_u(X)\,du
$$

###Expression alternative 1 {#intro:tvar:alt1}
$$
\text{TVaR}_k(X)= \frac{1}{1-k}\Pi_X(\text{VaR}_k(X))+\text{VaR}_k(X)
$$
Voir preuve \@ref(preuves:tvar:1)

###Expression alternative 2 {#intro:tvar:alt2}
$$
\text{TVaR}_k(X)= \frac{1}{1-k}(E[X\times\mathrm{1}_{\{X>{\text{VaR}_k(X)}\}}]+\text{VaR}_k(X)\times(F_X[\text{VaR}_k(X)]-k))
$$
Voir preuve \@ref(preuves:tvar:2)

###Expression alternative 3 {#intro:tvar:alt3}
$$
\text{TVaR}_k(X)= \frac{P(X\ge \text{VaR}_k(X))}{(1-k)} \times E[X|X \ge \text{VaR}_k(X)]+(1-\frac{P(X\ge \text{VaR}_k(X))}{(1-k)})\times\text{VaR}_k(X),\quad k\in (0,1)
$$
Voir preuve \@ref(preuves:tvar:3)

###Propriété {-}

####Sous-additivité {-}
\label{intro:tvar:prop:sousadd}
Soit $S=X_1+X_2$,
$$
\text{TVaR}_{\kappa}(S)\le \text{TVaR}_{\kappa}(X_1)+\text{TVaR}_{\kappa}(X_2)
$$
Voir \autoref{preuves:tvar:prop:sousadd}

##Transformée de Laplace

Existe pour toute loi de X.   

Lien avec $E[X]$: 
\begin{align*}
\text{V.A. X positive tel que}\; E[X]<\infty& \\ 
(-1)\frac{d}{dt}\mathcal{L}_X(t)\vert_{t=0}& =(-1)\frac{d}{dt}E[e^{-tX}]\vert_{t=0}\\
& =(-1)E[\frac{d}{dt}e^{-tX}]\vert_{t=0}\\
& =(-1)E[-Xe^{-tX}]\vert_{t=0}\\
& =(-1)E[-X] = E[X]
\end{align*}  

Lien avec$E[X^m]$:
$$
E[X^m]=(-1)^m\frac{d^m}{dt^m}\mathcal{L}_X(t)\vert_{t=0}
$$




