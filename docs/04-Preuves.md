---
output:
  pdf_document: default
  html_document: default
---
# Preuves 

##Théorème (\@ref(thm:fn-quantile)) de la fonction quantile 
\label{preuves:fn-quantile}
\BeginKnitrBlock{proof}<div class="proof">\iffalse{} <span class="proof"><em>Proof. </em></span>  \fi{}\begin{align*}
F_{F_X^{-1}(u)}(x)& =P(F_X^{-1} \le x)\\
& =P(U \le F_X(x))\\
& =F_X(x)
\end{align*}</div>\EndKnitrBlock{proof}

##Fonction Stop-Loss(\@ref(intro:fn-stop))
\label{preuves:fn-stop}
\BeginKnitrBlock{proof}<div class="proof">\iffalse{} <span class="proof"><em>Proof. </em></span>  \fi{}\begin{align*}
\Pi_X(d)& = E[\max(X-d, 0)]\\
& =E\left[X \times \mathrm{1}_{ \{X > d\} } -d\times \mathrm{1}_{\{X > d\}}\right]\\
& =E\left[X \times \mathrm{1}_{\{X > d\}}\right]-d \bar{F}(d)\\
\end{align*}</div>\EndKnitrBlock{proof}

##Tvar
###Expresion alternative 1(\@ref(intro:tvar:alt1)) 
\label{preuves:tvar:1}
\BeginKnitrBlock{proof}<div class="proof">\iffalse{} <span class="proof"><em>Proof. </em></span>  \fi{}On applique \@ref(intro:fn-quantile:1), ainsi:
\begin{align*}
\text{TVaR}_k(X)& =\frac{1}{(1-k)}\int_k^1\text{VaR}_k(u)\,du\\
& =\frac{1}{1-k}\left(\Pi_X(\text{VaR}_k(X))\right)+\text{VaR}_k(X)
\end{align*}</div>\EndKnitrBlock{proof}

###Expression alternative 2(\@ref(intro:tvar:alt2))
\label{preuves:tvar:2}
\BeginKnitrBlock{proof}<div class="proof">\iffalse{} <span class="proof"><em>Proof. </em></span>  \fi{}On remplace $\Pi_X(\text{VaR}_k(X))$ dans \@ref(preuves:tvar:2) par sa définition \@ref(intro:fn-stop)
\begin{align*}
\text{TVaR}_k(X)& = \text{VaR}_k(X)+\frac{1}{(1-k)}\left(E[X\times\mathrm{1}_{\{X>\text{VaR}_k(X)\}}]-\text{VaR}_k(X)\bar{F}_X(\text{VaR}_k(X))\right)\\
& =\frac{1}{(1-k)}\left[E\left[X\times\mathrm{1}_{\{X>\text{VaR}_k(X)\}}\right]-\text{Var}_k(X)\left(\bar{F}_X(\text{VaR}_k(X))-(1-k)\right)\right]\\
& =\frac{1}{(1-k)}\left[E\left[X\times\mathrm{1}_{\{X>\text{VaR}_k(X)\}}\right]-\text{Var}_k(X)\left(F_X(\text{VaR}_k(X))-k\right)\right]
\end{align*}</div>\EndKnitrBlock{proof}
Pour une V.A. continue $\text{VaR}_k(X)\left(F_X(\text{VaR}_k(X))-k\right)=0$ donc,
$$\text{TVaR}_k(X)= \frac{E\left[X\times\mathrm{1}_{\{X>\text{VaR}_k(X)\}}\right]}{P(X>\text{VaR}_k(X))}= E\left[X|X>\text{VaR}_k(X)\right]$$

###Expression alternative 3(\@ref(intro:tvar:alt3))
\label{preuves:tvar:3}
On fait la preuve à partir de l'expression alternative 2:
\BeginKnitrBlock{proof}<div class="proof">\iffalse{} <span class="proof"><em>Proof. </em></span>  \fi{}\begin{align*}
\text{TVaR}_k(X)& =\frac{1}{(1-k)}\left[E[X\times\mathrm{1}_{\{X>\text{VaR}_k(X)\}}]-\text{VaR}_k(X)(F_X(\text{VaR}_k(X))-k)\right]\\
& =\frac{1}{(1-k)}\left[E[X\times\mathrm{1}_{\{X>\text{VaR}_k(X)\}}+X\times\mathrm{1}_{\{X=\text{VaR}_k(X)\}}-X\times\mathrm{1}_{\{X=\text{VaR}_k(X)\}}\right]\\
& -\text{VaR}_k(X)\left(1-\bar{F}_X(\text{VaR}_k(X))-(1-(1-k))\right)\\
& =\frac{1}{(1-k)}\left\{E[X\times\mathrm{1}_{\{X\ge\text{VaR}_k(X)\}}]-E[X\times\mathrm{1}_{\{X=\text{VaR}_k(X)\}}]+\text{VaR}_k(X)\left[(1-k)-P(X>\text{VaR}_k(X))\right]\right\}\\
& =\frac{1}{(1-k)}\left\{E[X\times\mathrm{1}_{\{X\ge\text{VaR}_k(X)\}}]-(E[X\times\mathrm{1}_{\{X=\text{VaR}_k(X)\}}]+P(X>\text{VaR}_k(X))\times\text{VaR}_k(X))\right\}
\end{align*}
Deux cas possibles:  

1. V.A. discrète $P(X=\text{VaR}_k(X))>0$   

2. V.A. continue $P(X=\text{VaR}_k(X))=0$  


Donc la portion $(E[X\times\mathrm{1}_{\{X=\text{VaR}_k(X)\}}]+P(X>\text{VaR}_k(X))\times\text{VaR}_k(X))=  \text{VaR}_k(X)[1-\frac{P(X\ge\text{VaR}_k(X))}{(1-k)}]$</div>\EndKnitrBlock{proof}

###Propriété {-}
####Sous-additivité {-}
\label{preuves:tvar:prop:sousadd}
3 preuves. La première est basée sur les statistiques d'ordre, la deuxième est basée sur la représentation de la $\text{TVaR}$ par la stop-loss.  
1ere preuve:
\BeginKnitrBlock{proof}<div class="proof">\iffalse{} <span class="proof"><em>Proof. </em></span>  \fi{}1er lemme: Soit une V.A. $X$ quelconque, dont $E[X]<\infty$.   
Soit m réalisations indépendantes de $X$: $X^{(1)},\dots,X^{(m)}$.

$$
\text{TVaR}_{\kappa}(X) =\frac{\lim_{m\to\infty} \left(\sum^n_{j=\lfloor m\kappa\rfloor +1} X^{[j]} \right)}{\lfloor m(1-\kappa)\rfloor},\;\text{pour}\;\lfloor m\kappa \rfloor <m
$$  
Où,  
\begin{align*}
\lfloor x \rfloor& =\text{partie entière de}\;x\\
X^{[1]}\le X^{[2]}\le \dots \le X^{[m]}& =\text{réalisations triées de} X
\end{align*}
2e lemme:  
Soit les réalisations : $X^{(1)},\dots,X^{(m)}$  
On définit $X^{[1]}\le X^{[2]} \le \dots \le X^{[m]}$ comme les réalisations triées de $X$.  
\begin{align*}
\sum^m_{j=m-1}X^{[j]}& = \sup\{X^{(j_1)}+X^{(j_2)},\; 1\le j_1 \le j_2 \le m\}\\
\sum^m_{j=m-2}X^{[j]}& = \sup\{X^{(j_1)}+X^{(j_2)}+X^{(j_3)},\; 1\le j_1 \le j_2 \le j_3 \le m\}\\
\sum^m_{j=k_0+1}X^{[j]}& = \sup\{X^{(j_1)}+X^{(j_2)}+\dots+X^{(j_{m-k_0})},\; 1\le j_1 \le j_2 \le \dots \le j_{m-k_0} \le m\}
\end{align*}
   
Soit les V.A. $X_1,X_2$ avec $E[X_i]<\infty,\;i=1,2$.   
$S=X_1+X_2$  

Avec le 1er lemme:   
$$\text{TVaR}_{\kappa}(S) =\frac{\lim_{m\to\infty} \left(\sum^n_{j=\lfloor m\kappa\rfloor +1} S^{[j]} \right)}{\lfloor m(1-\kappa)\rfloor}$$  

On développe $\sum^m_{j=\lfloor m\kappa\rfloor +1} S^{[j]}$ en utilisant le 2e lemme et on pose $\kappa_0=\lfloor m\kappa \rfloor$

\begin{align*}
\sum^m_{j = \lfloor m \kappa\rfloor +1} S^{[j]}& = \sup\{S^{(j_1)}+\dots+S^{(j_{m-\lfloor m\kappa \rfloor})},1\le j_1\le \dots\le j_{m-\lfloor m\kappa \rfloor}\le m\}\\
& = \sup\{\left(X^{(j_1)}_1+X^{(j_1)}_2\right)+\left(X^{(j_2)}_1+X^{(j_2)}_2\right)+\dots+\left(X^{(j_{m-\kappa_0})}_1+X^{(j_m-\kappa_0)}_2\right)\\
,1\le j_1\le \dots\le j_{m-\kappa_0}\le m\}\\
& = \sup\{\left( X_1^{(j_1)}+X_1^{(j_2)}+\dots+X_1^{(j_{m-\kappa_0})}\right)+\left( X_2^{(j_1)}+X_2^{(j_2)}+\dots+X_2^{(j_{m-\kappa_0})}\right)\\
,1\le j_1\le \dots\le j_{m-\kappa_0}\le m\}\\
& \le sup\{\left( X_1^{(j_1)}+X_1^{(j_2)}+\dots+X_1^{(j_{m-\kappa_0})}\right),1\le j_1\le \dots\le j_{m-\kappa_0}\le m\}\\
& + sup\{\left( X_2^{(j_1)}+X_2^{(j_2)}+\dots+X_2^{(j_{m-\kappa_0})}\right),1 \le j_1 \le \dots\le j_{m - {\kappa_0}} \le m\}\\
& =\sum^m_{j=\kappa_0 +1} X_1^{[j]}+\sum^m_{j=\kappa_0 +1} X_2^{[j]}
\end{align*}  



On applique le 1er lemme de chaque coté de l'inégalité   
$\sum^m_{j=\kappa_0 +1} S^{[j]}\le\sum^m_{j=\kappa_0 +1} X_1^{[j]}+\sum^m_{j=\kappa_0 +1} X_2^{[j]}$   

\begin{align*}
\text{TVaR}_\kappa(S)& = \lim_{m\to\infty}\frac{1}{\lfloor m(1-\kappa)\rfloor} \sum^m_{j=\kappa_0 +1} S^{[j]}\\
& \le \lim_{m\to\infty}\frac{1}{\lfloor m(1-\kappa)\rfloor} \sum^m_{j=\kappa_0 +1} X_1^{[j]} + \lim_{m\to\infty}\frac{1}{\lfloor m(1-\kappa)\rfloor} \sum^m_{j=\kappa_0 +1} X_2^{[j]}\\
& =\text{TVaR}_\kappa(X_1)+\text{TVaR}_\kappa(X_2)
\end{align*}</div>\EndKnitrBlock{proof}
2e preuve:
\begin{align*}
\text{TVaR}_\kappa(X)& =\text{VaR}_\kappa+\frac{1}{1-\kappa}\Pi_X(VaR_\kappa(X))\\
& =\phi(VaR_\kappa(X))\\
\text{où}\;\phi(X)& =x + \frac{1}{1-\kappa}\Pi_X(x)\\
\text{et}\; \Pi_X(x)& = E\left[\max(X-x;0)\right]
\end{align*}   
Donc,
$$
\text{TVaR}_\kappa(X)= \inf \phi(X),\; \text{où}\;\phi(X) \text{est une fonction convexe}   
\\
\text{le minimum est atteint à}\; \text{VaR}_\kappa(X)
$$
![](04-Preuves_files/figure-latex/unnamed-chunk-7-1.pdf)<!-- --> 
Vérification que $\phi(X)$ ext convexe en $x$:   
Supposons que $X$est continue:
\begin{align*}
\phi(X)& =x + \frac{1}{1-\kappa} \int^{\infty}_x \bar{F}_X(y)dy,\;x\geq 0\\
\text{Dérivée première de }\phi(X)\:\\
\frac{d\phi(X)}{dx}& =1+\frac{1}{1-\kappa}(-\bar{F}_X(x))\\
\text{Dérivée seconde de }\phi(X)\:\\
\frac{d^2\phi(x)}{d^2x}& =\frac{1}{1-\kappa}f_X(x)\geq 0,\quad x\geq 0
\end{align*}  
Valeur qui minimise $\phi(X$):
\begin{align*}
\frac{d\phi(X)}{dx}& = 1+\frac{1}{1-\kappa}(-\bar{F}_X(x))=0\\
\bar(F_X(x))& =1-\kappa\\
F_X(x)& =\kappa
\end{align*}  
Alors,
\begin{align*}
\text{TVaR}_\kappa(X)& =\phi_X(\text{VaR}_\kappa(X))
& \leq \phi_X(x),\quad x\in \mathrm{R}
\end{align*}  
Soit $X_1$ et $X_2$ tel que $E[X_i]\le\infty$, pour $i=1,2$  
$S=X_1+X_2$, $\kappa\in(0,1)$.  
On développe $\text{TVaR}_\kappa((1-\alpha)X_1+\alpha X_2)$, où $\alpha\in(0,1)$
\begin{align*}
\text{TVaR}_\kappa((1-\alpha)X_1+\alpha X_2)& = \phi_((1-\alpha)X_1+\alpha X_2)(x)\\
& \leq x\frac{1}{1-\kappa}\Pi_{((1-\alpha)X_1+\alpha X_2)}(x),\quad x\in\mathrm{R}\\
& =x+\frac{1}{1-\kappa}E\left[ \max\left((1-\alpha)X_1+\alpha X_2;0\right)\right],\quad x\in\mathrm{R}\\
\text{On fixe }x=(1-\alpha)\text{VaR}_\kappa(X_1)+\alpha \text{VaR}_\kappa(X_2)\\
\\
\text{TVaR}_\kappa((1-\alpha)X_1+\alpha X_2)& \leq (1-\alpha)\text{VaR}_\kappa(X_1)+\alpha \text{VaR}_\kappa(X_2)\\
& +\frac{1}{1-\kappa}E\left[ \max((1-\alpha)X_1+\alpha X_2-(1-\alpha)\text{VaR}_\kappa(X_1)-\alpha \text{VaR}_\kappa(X_2);0)\right],\\
\;\text{vrai pour }\alpha\in(0,1)\\
& =(1-\alpha)\text{VaR}_\kappa(X_1)+\alpha \text{VaR}_\kappa(X_2)\\
& +\frac{1}{1-\kappa}E\left[ \max((1-\alpha)(X_1-\text{VaR}_\kappa(X_1))\alpha (X_2-\text{VaR}_\kappa(X_2));0)\right]\\
& \leq (1-\alpha)\text{VaR}_\kappa(X_1)+\alpha \text{VaR}_\kappa(X_2)\\
& +\frac{1}{1-\kappa}E\left[\max((1-\alpha)(X_1-\text{VaR}_\kappa(X_1));0)\right]\\
& +\frac{1}{1-\kappa}E\left[\max((\alpha)(X_2-\text{VaR}_\kappa(X_2));0)\right]\\
& = \text{VaR}_\kappa((1-\alpha)X_1)+\text{VaR}_\kappa(\alpha X_2)\\
& +\frac{1}{1-\kappa}E\left[\max((1-\alpha)X_1-\text{VaR}_\kappa((1-\alpha)X_1))\right]\\
& +\frac{1}{1-\kappa}E\left[\max(\alpha X_2-\text{VaR}_\kappa(\alpha X_2)\right]\\
& =\text{TVaR}_\kappa((1-\alpha)X_1)+\text{TVaR}_\kappa(\alpha X_2),\quad \alpha\in(0,1)\\
\text{On fixe }\alpha=\frac{1}{2}\\
\text{TVaR}_\kappa(\frac{1}{2} X_1+\frac{1}{2} X_2)& =\text{TVaR}_\kappa(\frac{1}{2}(X_1+X_2))\\
& =\frac{1}{2}\text(TVaR)_\kappa(X_1+X_2)\\
& \leq \frac{1}{2}\text(TVaR)_\kappa(X_1)+\frac{1}{2}\text(TVaR)_\kappa(X_2)\\
\text{On multiplie par 2 et on déduit}:\\
\text(TVaR)_\kappa(X_1+X_2)& \leq \text(TVaR)_\kappa(X_1)+\text(TVaR)_\kappa(X_2)
\end{align*}   

##Biais moyenne échantillonale (voir \@ref(stats:criteres:biais))
\label{preuves:biais:xn}
\BeginKnitrBlock{proof}<div class="proof">\iffalse{} <span class="proof"><em>Proof. </em></span>  \fi{}\begin{align*}
B(\hat{\theta}_n)& =E[\bar{X}_n]-E[X]\\
& =E[X]-E[X]=0
\end{align*}</div>\EndKnitrBlock{proof}

##Biais variance échantillonale (voir \@ref(stats:criteres:biais))
\label{preuves:biais:sn}
\BeginKnitrBlock{proof}<div class="proof">\iffalse{} <span class="proof"><em>Proof. </em></span>  \fi{}\begin{align*}
S_n^2& =\frac{1}{n-1}\left(\sum_{i=1}^n {(X_i-\bar{X}_n)}^2\right)\\
=\frac{1}{n-1}\left(\sum_{i=1}^n (X_i^2-2X_i\bar{X}_n+\bar{X}_n^2)\right)\\
& =\frac{1}{n-1}\left[\left(\sum_{i=1}^n X_i^2\right)  -\frac{2}{n-1}\left(\bar{X}_n\sum_{i=1}^n X_i\right) +\frac{n}{(n-1)}\bar{X}_n^2\right]\\
& =\frac{1}{n-1}\left(\sum_{i=1}^n X_i^2\right) - \frac{n}{(n-1)}\bar{X}_n^2
\end{align*}

\begin{align*}
E\left[S_n^2\right]& =E\left[\frac{1}{n-1}\left(\sum_{i=1}^n X_i^2\right)\right]-E\left[\frac{n}{(n-1)}(\bar{X}_n)\right]\\
& =\frac{n}{n-1}((Var(X)+E^2[X])) - \frac{1}{(n-1)}(Var(X))-\frac{n}{n-1}(E[X^2])\\
& =Var(X)
\end{align*}

\begin{gather*}
B(S^2_n)= Var(X)-\sigma^2 = 0
\end{gather*}</div>\EndKnitrBlock{proof}

##Convergence (voir \@ref(stats:convergence))
\label{preuves:convergence}
\BeginKnitrBlock{proof}<div class="proof">\iffalse{} <span class="proof"><em>Proof. </em></span>  \fi{}On prouve avec Tchebycheff  
Un estimateur sans biais est convergent si:
$$
\lim_{n\to \infty} Var(\hat{\theta}_n) =0
$$
\begin{gather*}
\text{On fixe}\; \epsilon>0,\\
P(|\hat{\theta}_n-\theta|>\epsilon)= P(|\hat{\theta}_n-E[\hat{\theta}_n]|>\epsilon)\\
=P(|\hat{\theta}_n-E[\hat{\theta}_n]|>\frac{\epsilon\times \sqrt{Var(\hat{\theta}_n)}}{\sqrt{Var(\hat{\theta}_n)}})\\
\le \frac{Var(\hat{\theta}_n)}{\epsilon^2}
\end{gather*}
Donc si $Var(\hat{\theta}_n)\to 0$ quand $n \to \infty$, $\hat{\theta}_n$ est convergent</div>\EndKnitrBlock{proof}

##Téorème de Rao-Blackwell (voir \autoref{stats:rao})
\label{preuves:rao}
Puisque $T$ est exhaustive pour $\theta$, la distribution conditionnelle de $(X_1,\dots,X_n)$ sachant $T$ ne dépend pas de $\theta$. Alors,
$$
\theta^{*}_n=E[\hat{\theta}_n|T]
$$
ne dépend pas de $\theta$. Donc, $\theta^{*}_n$ est une statistique. Par l'espérance totale,
$$
E[\theta^{*}_n]=E[E[\hat{\theta}_n|T]]=E[\hat{\theta}_n]=\theta,
$$
$\theta^{*}_n$ est donc sans biais. Par la variance totale,
\begin{align*}
var(\hat{\theta}_n) &=var(E[\hat{\theta}_n|T])+E[var(\hat{\theta}_n|T)] \\
&= var(\theta^{*}_n)+E[var(\hat{\theta}_n|T)]\\
\end{align*}
Sachant que
$$
E[var(\hat{\theta}_n|T)] \ge 0 
$$
$$
var(\theta^{*}_n)\le var(\hat{\theta}_n)
$$







