---
output:
  pdf_document: default
  html_document: default
---
# Stats


##Définitions  
Observation: réalisation d'une variable aléatoire  


Échantillon aléatoire de F: ensemble de V.A. iid  


Statistiques: fonction d'un échantillon aléatoire et de constantes connues  


Paramètres: quantité d'intérêt($E[X],\;Var(x),\;etc$) ou le paramètre $\theta$ d'un modèle paramétrique.  

Statistique exhaustive: statistique qui contient toute l'information pertinente sur le paramètre visé. 


Estimateur: Statistique $S(X_1,\dots,X_n)$ qui prend des valeurs qu'on espère proche de $\theta$ noté $\hat{\theta}_n$(Variable aléatoire)  


Estimation de $\theta$: données observées $x_1,x_2,\dots$ de la valeur observée $\hat{\theta}$, $s(x_1,x_2,\dots)$(réalisations)  


##Moyenne échantilonnale:
$$
\bar{X}_n=\frac{1}{n}\sum_{i=1}^n x_i
$$

##Variance échantillonale:

$$
S^2_n= \frac{1}{n-1}\sum^n_{i=1}\left(X_i-\bar{X}_n\right)^2
$$  

##Loi faible des grands nombres:  


Soit $X_1,X_2,...,$ une suite de V.A. iid. On suppose $var(X_i)< \infty$ et $E[X] = \mu$, lorsque $n \to \infty$  


$$ 
P\left(|\left(\bar{X}_n-\mu\right)|>\epsilon\right)\to 0\quad \forall\epsilon>0
$$
$\bar{X}_n$ converge en probabilité vers $\mu$
$$
\bar{X}_n\overset{p}\to\mu\\  
$$
Preuve par Tchebycheff:
$$
P\left(|\bar{X}_n-\mu|>\epsilon\right)\leq\frac{var(X_i)}{n\epsilon^2}
$$

##Statistiques d'ordre d'un échantillon:
\begin{gather*}
    X_{(1)}=\min(X_1,\dots, X_n) \\  
    F_{X_{(1)}} (x)= 1 -{(1- F_X (x))}^n \\  
    \\
    X_{(n)}= \max(X_1,\dots,X_n) \\  
    F_{X_{(n)}}(x)={F_X(x)}^n\\
    \\
    f_{X_{(k)}}(x)= \frac{{n!}}{{(k-1)!}1{(n-k)!}}{F_X(x)}^{k-1}{(1-F_X(x))}^{n-k}f_X(x)
\end{gather*}


##Distribution de $\bar{X}$:

Soit $X_1,\dots,X_n$, un échantillon de $N(\mu,\frac{\sigma^2}{n})$,

\begin{gather*}
    \bar{X}_n=\frac{1}{n}\sum_{i=1}^n X_i\, \sim N\left(\mu,\frac{\sigma^2}{n}\right)\\
    \\
    Z_n=\frac{\bar{X}-\mu}{\frac{\sigma}{\sqrt{n}}}\,\sim N(0,1)
\end{gather*}

Utilisation de la distribution d'échantillonage de $\bar{X}_n$:

1. Vérifier une affirmation 
2. Trouver un interval plausibe
3. Déterminer une taille d'échantillon minimal


##Somme de normales au carré
Soit $Z_1,\dots,Z_n\sim N(0,1)$
$$
\sum_{i=1}^n Z_i^2\sim \chi^2_n
$$

Soit $X_1,\dots,X_n\sim N(\mu,\sigma^2)$
$$
\frac{(n-1)S^2_n}{\sigma^2}= \frac{1}{\sigma^2}\sum^n_{i=1}(X_i-\bar{X}_n)^2\sim \chi^2_{(n-1)}
$$
$S^2_n\bot\,\bar{X}_n$ 
$$
E[S^2_n]= \frac{\sigma^2}{(n-1)}E\left[\frac{(n-1)}{\sigma^2}S^2_n\right]=\frac{\sigma^2}{(n-1)}(n-1)=\sigma^2
$$

##Statistique Student {#stats:stats:student}

$$
\text{T}_n= \sqrt{n}\frac{\bar{X}_n-\mu}{\sqrt{S_n^2}}
$$

## Distribution de la Statistique Student {#stats:dist:student}

\begin{align*}
    \text{T}_n& =\sqrt{n} \frac{\bar{X}_n -\mu}{\sqrt{S^2_n}}\sim t(n-1)\\
    \text{T}_n& =\frac{\bar{X}_n-\mu}{\sqrt{\frac{\sigma^2}{n}}}\times\sqrt{\frac{\sigma^2}{S^2_n}}\\
    & =\underbrace{\frac{\bar{X}_n-\mu}{\sqrt{\frac{\sigma^2}{n}}}}_{\sim N(0,1)}\times\underbrace{\sqrt{\frac{(n-1)}{(n-1)\frac{S^2_n}{\sigma^2}}}}_{\sim \chi_{(n-1)}^2}
\end{align*}

## Distribution Student
Soit $Z\sim N(0,1)$ et $W\sim \chi^2_(v)$ 
$Z\bot W$
$$
T=\frac{Z}{\sqrt{\frac{W}{n}}}\sim t(v)
$$
Propriété

Si $v>1$: 
$E[T]=0$  

Si $v>2$: 
$Var(T)=\frac{v}{v-2}$   
Si $v\rightarrow \infty,\;t(v)\;\text{converge vers}\;N(0,1)$

##Statistique F {#stats:stats:f}

Soit $X_i,\dots,X_n\sim N(\mu_1,\sigma^2_1)$ et $Y_1,\dots,Y_n \sim N(\mu_2,\sigma_2^2)$  
Pour comparer: $\sigma_1^2$ et $\sigma^2_2$
$$
\frac{S_n^2}{S_m^2}=\frac{\frac{1}{n-1}\sum_{i=1}^n(X_i-\bar{X}_n)^2}{\frac{1}{m-1}\sum_{i=1}^m(Y_i-\bar{Y}_m)^2}
$$

##Distribution F {#stats:dist:f}
Soit $W_1\sim\chi^2_{(v_1)},\;W_2\sim\chi^2_{(v_2)}$ 

$W_1 \bot\, W_2$ 

$$
F=\dfrac{W_1}{v_1}\div\dfrac{W_2}{v_2}\quad
F\sim F(v_1,v_2)
$$

Si $X \sim F(v_1,v_2)$ et $v_2>2$ 
$E\left[X =\frac{v_2}{v_2-2}\right]$

##Comparer variance échantionnale {#stats:stats:f:varéchan}

Soit $X_1,\dots,X_n\sim N(\mu_1,\sigma^2_1)$ et $Y_1,\dots,Y_m\sim N(\mu_2,\sigma^2_2)$ 
$$
\dfrac{S^2_n}{\sigma^2_1}\div\dfrac{S_m^2}{\sigma^2_2}\sim F(n-1,m-1)
$$

##Lemme de Slutsky

Soit $X_1,X_2,\dots$ et $Y_1,Y_2,\dots$ 
Lorsque $n \rightarrow \infty$ et $X_n \rightsquigarrow X$ et $Y_n \rightsquigarrow c$
 
1. $X_n+Y_n \rightsquigarrow X+c$
2. $X_n\times Y_n \rightsquigarrow X\times c$
3. Si $c>0,\; \frac{X_n}{Y_n} \rightsquigarrow \frac{X}{c}$

##Théorème Central Limite {#stats:tcl}

\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-1"><strong>(\#thm:unnamed-chunk-1) </strong></span>Soit $X_1,\dots,X_n$, un échantillon d'une V.A. quelconque:
$$
Z_n=\sqrt{n}\times\frac{\bar{X}_n-\mu}{\sigma}
$$
quand $n \to \infty$: 
$$
P(Z_n\le X)\to\phi(X)
$$
Convergence en distribution:
$$
Z_n\rightsquigarrow N(0,1)
$$</div>\EndKnitrBlock{theorem}

##Distribution Statistique Student lorsqu'on ne connait pas la variance et X ne provient pas d'une loi Normale

$T \not\sim t(n-1)$   
Soit $X_1,\dots,X_n$, un échantillon d'une V.A quelconque:   
$E[X^4]<\infty$, lorsque $n\to\infty$:
$$
T_n = \sqrt{n}\frac{\bar{X}_n-\mu}{S_n}\rightsquigarrow N(0,1)
$$


##Aproximation de la loi Binomiale avec la loi Normale

$$
Z=\sqrt{n}\times \frac{\bar{X}_n-p}{\sqrt{p(1-p)}}\approx N(0,1)
$$
Correction de la continuité: 
$$
P(Y\le y)\approx P(Z \le y+0.5 )
$$


##Critères pour évaluer la performance d'un estimateur {#stats:criteres}

###Critère 1: Biais {#stats:criteres:biais}

\begin{gather*}
B(\hat{\theta}_n)= E\left[\hat{\theta}_n-\theta\right]=E\left[\hat{\theta}_n\right]-\theta\\
\intertext{Estimateur sans biais:}\\
B(\hat{\theta}_n)=0\\
\intertext{Estimateur asymptotiquement sans biais:}\\
\lim_{n\to \infty} B(\hat{\theta}_n)=0
\end{gather*}

Voir preuve \@ref(preuves:biais:xn) et \@ref(preuves:biais:sn) pour le développement des biais de $\bar{X}_n$ et $S_n^2$ 

###Critère 2: Variance {#stats:criteres:variance}

Parmi 2 estimateurs sans biais, on préfère celui avec une plus petite variance.  

Pour deux estimateur avec biais, on préfère celui avec la plus petite Erreur quadratique moyenne(EQM):
$$
EQM\left(\hat{\theta}_n\right)= E\left[(\hat{\theta}_n-\theta)^2\right]= Var\left(\hat{\theta}_n\right)+\left[B(\hat{\theta}_n)\right]^2
$$

###Critère 3: Convergence  {#stats:convergence}

L'estimateur $\hat{\theta}_n$ est un estimateur convergent de $\theta$ si, quand $n\to \infty$,
$$
\hat{\theta}_n\xrightarrow{P}\theta
$$
ce qui signifie que pour tout $\epsilon>0$,
$$
\lim_{n\to\infty}P(|\hat{\theta}-\theta|>\epsilon)=0
$$

Voir \@ref(preuves:convergence) pour prouver la convergence


##Efficacité relative {#stats:effrela}

Soit $\hat{\theta}_n$ et $\tilde{\theta}_n$, 2 estimateurs sans biais et convergent.

$$
\text{eff}(\hat{\theta}_n,\tilde{\theta}_n)= \frac{Var(\tilde{\theta}_n)}{Var(\hat{\theta}_n)}
$$
Si $eff(\hat{\theta}_n,\tilde{\theta}_n)>1$, $\hat{\theta}_n$ est préférable, sinon $\tilde{\theta}_n$ est préférable.
 


##Définition formelle statistique exhaustive

Une statistique exhaustive est une statistique qui contient toute l'information pertinente sur le paramètre visé.

Soit $X_1,\dots,X_n$ un échantillon aléatoire d'une distribution avec paramètre $\theta$ inconnu. Alors, la statistique
$$
T=T(X_1,\dots,X_n)
$$
est exhaustive pour $\theta$ ssi la distribution conditionnelle de $X_1,\dots,X_n$ sachant $T$ ne dépend pas de $\theta$.

##Théoreme de factorisation de Fischer-Neyman

Soit $X_1,\dots,X_n$ un échantillon aléatoire d'une distribution avec densité $f(\cdot;\theta)$ et paramètre $\theta$ inconnu. Alors, la statistique
$$
T=T(X_1,\dots,X_n)
$$
est exhaustive pour $\theta$ ssi, $\forall\;x_1,\dots,x_n\;\in\mathbb{R}$,
$$
f(x_1;\theta)\times\dots\times f(x_n;\theta)=g(t;\theta)\times h(x_1,\dots,x_n)
$$
où  

- $g(t;\theta)$ ne dépend de $x_1,\dots,x_n$ qu'à travers $t$.
- $h(x_1,\dots,x_n)$ ne dépend pas de $\theta$.  

Avec plus d'un paramètre: 

Soit $X_1,\dots,X_n$ un échantillon aléatoire d'une distribution avec densité $f(\cdot;\theta)$ et paramètres $\theta=\theta_1,\dots,\theta_n$ inconnus. Alors, les statistiques
$$
T_1=T_1(X_1,\dots,X_n),\dots,T_k=T_k(X_1,\dots,X_n)
$$
sont conjointements exhaustives pour $\theta$ ssi, $\forall\;x_1,\dots,x_n\;\in\mathbb{R}$,
$$
f(x_1;\theta)\times\dots\times f(x_n;\theta)=g(t_1,\dots,t_k;\theta)\times h(x_1,\dots,x_n)
$$
où  

- $g(t_1,\dots,t_n;\theta)$ ne dépend de $x_1,\dots,x_n$ qu'à travers $t_1,\dots,t_k$.
- $h(x_1,\dots,x_n)$ ne dépend pas de $\theta$. 

##Critère de Lehmann-Scheffé

Soit $X_1,\dots,X_n$ un échantillon aléatoire d'une distribution avec densité $f(\cdot;\theta)$ et paramètre $\theta$ inconnu. Alors, la statistique
$$
T=T(X_1,\dots,X_n)
$$
est exhaustive minimale pour $\theta$ ssi, $\forall\;x_1,\dots,x_n,y_1,\dots,y_n\;\in\mathbb{R}$,
$$
\frac{f(x_1;\theta)\times\dots\times f(x_n;\theta)}{f(y_1;\theta)\times\dots\times f(y_n;\theta)}
$$
ne dépend pas de $\theta$ ssi
$$
T(X_1,\dots,X_n)=T(Y_1,\dots,Y_n)
$$

##Théorème de Rao-Blackwell
\label{stats:rao}
$\hat{\theta}_n$ un estimateur sans biais tel que $var(\hat{\theta}_n)<\infty$. Si $T$ est exhaustive pour $\theta$, la statistique:
$$
\theta^{*}_n=E[\hat{\theta}_n|T]
$$
est un estimateur sans biais et
$$
var(\theta^{*}_n)\le var(\hat{\theta}_n)
$$
Voir \autoref{preuves:rao}.

##Estimateur sans biais et de variance minimale(MVUE)

Un estimateur $\hat{\theta}_n$ est sans biais et de variance minimale si:

1. $\hat{\theta}_n$ est sans biais.
2. $\hat{\theta}_n=g(T)$, où $T$ est une statistique exhaustive (minimale) obtenue avec le théorème Fischer-Neymann.

###Construire un MVUE

1. Trouver une statistique exhaustive (minimale) $T$ avec le théorème Fischer-Neymann.
2. Trouver une fonction $g$ tel que: $E[g(T)]=\theta$
3. Poser $\hat{\theta}_n=g(T)$.

##Méthode des moments

Si $t$ paramètres sont inconnus, on résout le système à $t$ équations:
$$
m_k=E\left[X^k\right],\quad k=1,\dots,t
$$
Les estimateurs obtenus sont appelés les estimateurs des moments.

##Méthode des quantiles

Pour certaine loi, les moments n'existent pas. Pour estimer $t$ paramètres inconnus, on pourrait résoudre le système à $t$ équations:
$$
\hat{\pi}_{\kappa j}=VaR_{\kappa j}(X)\quad j=1,\dots,t
$$

##Quantile empirique lissé

Pour un échantillon aléatoire $X_1,\dots,X_n$ le quantile empirique de niveau $\kappa\in(0,1)$ est:
$$
\hat{\pi}_{\kappa,n}=(1-h)X_{(j)}+hX_{(j+1)}\quad j=\lfloor(n+1)\kappa\rfloor\;et \; h=(n+1)\kappa-j 
$$

##Fonction de vraissemblance

Soit $X_1,\dots,X_n$ un échantillon aléatoire d'une distribution avec fmp ou fdd:
$$
f(x;\theta),\quad \theta \in \Theta
$$
où $\Theta$ est l'ensemble des valeurs possibles du paramètre. Si $x_1,\dots,x_n$ sont des valeurs observées de l'échantillon, la vraissemblance de $\theta$ basée sur $x_1,\dots,x_n$ est définie comme:
$$
L(\theta)=f(x_1;\theta)\times\dots\times f(x_n;\theta)
$$

###Observation

- $X$ est discrète: vraisemblance de $\theta$ basée sur $x_1,\dots,x_n$ est exactement la probabilité d'observer $x_1,\dots,x_n$.
- $X$ est continue: vraisemblance de $\theta$ basée sur $x_1,\dots,x_n$ est la densité et est proportionelle à la probabilité d'observer  $x_1,\dots,x_n$.
- la vraisemblance est vue comme une fonction réelle déterministe de $\theta$ 
- La vraisemblance est l'objet dans le théorème de factorisation de Fischer-Neymann
- la vraisemblance $L(\theta)$ devrait être plus grande pour des valeurs de $\theta$ proche de celle du mécanisme générateur de données.
- on estime donc $\theta$ par la valeur $\hat{\theta}_n$ qui maximise $L(\theta)$:
$$
\hat{\theta}_n=\underset{\theta\in\Theta}{arg\,max}L(\theta)
$$








