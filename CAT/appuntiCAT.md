---
title: CONTROLLI AUTOMATICI
author: Pierluca Pevere
geometry: margin=2.5cm
---

```{=latex}
\begin{center}
```

![](libro.jpeg)

```{=latex}
\end{center}
```

\newpage

# SISTEMI IN FORMA DI STATO

Un sistema si dice **tempo continuo** se la variabile t è una variabile reale ($t \in \mathbb{R}$).\
Si definiscono le seguenti equazioni:

* $\dot x(t) = f(x(t),u(t),t)$\space \space \space \space detta equazione di stato
* $y(t) = h(x(t),u(t),t)$\space \space \space \space detta equazione (o trasformazione) di uscita

Con ovviamente $\dot x(t) := \frac{d}{dt}x(t)$\
Dove:

* $x(t)\in \mathbb{R}^n$ stato del sistema all'istante t
* $u(t)\in \mathbb{R}^m$ ingresso del sistema all'istante t
* $y(t)\in \mathbb{R}^p$ uscita del sistema all'istante t

Quindi: $x(t)=\begin{bmatrix} x_{1}(t) \\  \vdots \\ x_{n}(t)\end{bmatrix}$ $u(t)=\begin{bmatrix} u_{1}(t) \\  \vdots \\ u_{m}(t)\end{bmatrix}$ $y(t)=\begin{bmatrix} y_{1}(t) \\  \vdots \\ y_{p}(t)\end{bmatrix}$

#### Equazione di stato

È un'equazione differenziale ordinaria vettoriale del prim'ordine:\ $$ \dot x_{1}(t)=f_{1}(\begin{bmatrix} x_{1}(t) \\  \vdots \\ x_{n}(t)\end{bmatrix},\begin{bmatrix} u_{1}(t) \\  \vdots \\ u_{m}(t)\end{bmatrix},t) $$ $$ \vdots $$ $$  \dot x_{n}(t)=f_{n}(\begin{bmatrix} x_{1}(t) \\  \vdots \\ x_{n}(t)\end{bmatrix},\begin{bmatrix} u_{1}(t) \\  \vdots \\ u_{m}(t)\end{bmatrix},t) $$
Dove $\mathbb{R}^n$ si dice spazio di stato e $n$ ordine del sistema.\
Mentre $f : \mathbb{R}^n \times \mathbb{R}^m \times \mathbb{R} \rightarrow \mathbb{R}^n$ è detta funzione di stato

#### Equazione di uscita

È un'equazione algebrica: $$ \dot y_{1}(t)=h_{1}(\begin{bmatrix} x_{1}(t) \\  \vdots \\ x_{n}(t)\end{bmatrix},\begin{bmatrix} u_{1}(t) \\  \vdots \\ u_{m}(t)\end{bmatrix},t) $$ $$ \vdots $$ $$  \dot y_{p}(t)=h_{p}(\begin{bmatrix} x_{1}(t) \\  \vdots \\ x_{n}(t)\end{bmatrix},\begin{bmatrix} u_{1}(t) \\  \vdots \\ u_{m}(t)\end{bmatrix},t) $$
Dove $h : \mathbb{R}^n \times \mathbb{R}^m \times \mathbb{R} \rightarrow \mathbb{R}^p$ è detta funzione di uscita


Se la soluzione $x(t)$ a partire da un istante iniziale $t_{0}$ è univocamente determinata da $x(t_{0})$ e $u(\tau)$, $\tau \ge t_{0}$, allora il sistema è detto **causale**.
\newpage
Un sistema di dice **tempo discreto** se $t$ è una variabile intera ($t \in \mathbb{Z}$).\
Si definiscono: 

* $x(t + 1) = f(x(t),u(t),t)$\space \space \space \space detta equazione di stato
* $y(t) = h(x(t),u(t),t)$\space \space \space \space detta equazione (o trasformazione) di uscita


**NB**: l'equazione di stato non è più differenziale ordinaria ma è un'equazione alle differenze finite.\
\
La definizione di stato, uscita e ingresso rimane invariata rispetto al caso tempo continuo.

### ESEMPIO carrello massa molla

```{=latex}
\begin{center}
```

![](massaMolla.PNG)

```{=latex}
\end{center}
```

Utilizzando la legge di Newton (prendendo $z$ come la posizione del centro di massa) si ha: $$ M\ddot{z}=-F_{e}+F_{m} $$ con M massa e $F_{e}$ forza elastica data da: $$ F_{e}(z(t),t) = k(t)z(t) $$ sostituendo: $$ M\ddot z(t) = -k(t)z(t) + F_{m}(t) $$ Definiamo:

- $x_{1} := z$ (posizione), $x_{2} := \dot z$ (velocità) di conseguenza lo stato risulta $x := [x_{1}x_{2}]^T$
- $u := F_{m}$ ingresso

Supponendo di misurare z(t) con un sensore allora $y:=z$, sia $k(t)=k$ e considerando come uscita l'energia totale $E_{T}(t)=\frac{1}{2}(k z^{2}(t) + M\dot z^{2}(t))$: $$ \dot x_{1} = x_{2}(t) $$ $$ \dot x_{2}(t)=-\frac{k(t)}{M}x_{1}(t)+\frac{1}{M}u(t)=-\frac{k}{M}x_{1}(t)+\frac{1}{M}u(t) $$ $$ y(t)=x_{1}(t)=\frac{1}{2}(k x_{1}^{2}(t)+M x_{2}^{2}(t)) $$


### ESEMPIO pendolo

```{=latex}
\begin{center}
```

![](pendolo.PNG)

```{=latex}
\end{center}
```

Equazione dei momenti ($C_{m}$ coppia motore): $$ M l^{2} \ddot \theta = C_{grav} + C_{drag} + C_{m} $$ con M massa e $C_{grav}$ e $C_{drag}$ date da $$ C_{grav} = -Mgl\textrm{sin}(\theta),\quad C_{drag}=-b\dot \theta$$ con $b$ coefficiente d'attrito.\
Definiamo:

- $x_{1}:=\theta$ (posizione angolare) e $x_{2}:=\dot \theta$ (velocità angolare), di conseguenza lo stato $x := [x_{1}x_{2}]^T$
- $u:=C_{m}$ ingresso

Supponiamo di misurare $\theta$ tramite un sensore angolo, allora $y:=\theta$: $$ \dot x_{1}(t) = x_{2}(t) $$ $$ \dot x_{2}(t) = -\frac{g}{l}\textrm{sin}(x_{1}(t)) -\frac{b}{M l^2}x_{2}(t) +\frac{1}{M l^2}u(t) $$ $$ y(t)=x_1(t) $$ Se invece misuriamo la posizione verticale tramite sensore, allora $y:=-l\textrm{cos}(\theta)$: $$ \dot x_{1}(t) = x_{2}(t) $$ $$ \dot x_{2}(t) = -\frac{g}{l}\textrm{sin}(x_{1}(t)) -\frac{b}{M l^2}x_{2}(t) +\frac{1}{M l^2}u(t) $$ $$ y(t)=-l\textrm{cos}(x_1(t)) $$

##### Definizione di traiettoria

> Dato un istante iniziale $t_0$ e uno stato iniziale $x_{t_{0}}$, la funzione del tempo $(x(t),u(t))$, $t\ge t_0$, che soddisfa l'equazione di stato $\dot x(t)=f(x(t),u(t),t)$ si dice **traiettoria**  (o movimento) **del sistema**. In particolare, $x(t)$ si dice traiettoria dello stato. Consistentemente, $y(t)$ si dic traiettoria dell'uscita.\
Per sistemi senza ingresso (detti non forzati) la traiettoria (dello stato) $x(t)$, $t\ge t_0$, è determinata solo dallo stato iniziale $x_{t_0}$.

### EQUILIBRIO DI UN SISTEMA

#### Equilibrio di un sistema non forzato

Dato un sistema non forzato $\dot x(t) = f(x(t),t)$, uno stato $x_e$ si dice __equilibrio__ del sistema se $x(t) = x_e$, $t \ge t_0$ è una traiettoria del sistema.

#### Coppia di equilibrio 

Dato un sistema forzato $\dot x(t) = f(x(t),u(t),t)$, $(x_e$,$u_e)$ si dice coppia di equilibrio se $(x(t)$,$u(t)) = (x_e$,$u_e)$, $t \ge t_0$, è traiettoria del sistema. 
\
Per sistemi $\dot x(t) = f(x(t),u(t))$ (tempo invarianti) vale la seguente proprietà: data una coppia di equilibrio $(x_e$,$u_e)$ vale $f(x_e$,$u_e) = 0$, vale lo stesso per sistemi non forzati (se $x_e$ equilibrio allora $f(x_e) = 0$).

Quindi ricapitolando:

- se $x(t) = x_e \forall t \Longrightarrow \dot x(t)=0 \Longrightarrow f(x(t),t)=0$ (sistemi non forzati)
- se $\dot x(t) = f(x(t))$: $f(x_e)=0 \Longrightarrow x_e$ equilibrio (sistemi non forzati tempo invarianti).
- se $\dot x(t) = f(x(t),u(t))$: $f(x_{e},u_{e}) = 0 \Longrightarrow (x_{e},u_{e})$ coppia di equilibrio (sistemi forzati tempo invarianti). 

### CLASSIFICAZIONE DI SISTEMI IN FORMA DI STATO

Dato il caso generale, $x \in \mathbb{R}^n , u \in \mathbb{R}^m , y \in \mathbb{R}^p$ $$ \dot x(t) = f(x(t),u(t),t) \textrm{equazione di stato} $$ $$ y(t) = h(x(t),u(t),t) \textrm{equazione di uscita} $$

I sistemi in forma di stato si possono classificare in:

* **SISO** (Single Input Single Output), sotto classe dei sistemi MIMO (Multiple Input Multiple Output): se $m=p=1$ altrimenti MIMO
* **Strettamente propri**, sotto classe di propri: se $y=h(x(t),t)$
* **Non forzati**, sotto classe di forzati:
    $\dot x(t)=f(x(t),t)$
    $y(t)=h(x(t),t)$
* **Tempo invarianti** sotto classe dei tempo varianti: se data una traiettoria $(x(t),u(t),t), t\ge t_0$, con $x(t_{0})=x_{0}, \forall \Delta \in \mathbb{R}$, vale che per $x(t_{0}+\Delta)=x_{0}$ allora $(x_{\Delta}(t),u_{\Delta}(t)) = (x(t-\Delta),u(t-\Delta))$ è una traiettoria.
    Si può dimostrare che i sistmei tempo invarianti sono del tipo:\
    $\dot x(t) = f(x(t),u(t)) \quad x(0)=x_0$\
    $y(t) = h(x(t),u(t))$\
    senza perdita di generalità si può porre $t_{0}=0$
* **Linearità** sotto classe dei non lineari

### SISTEMI LINEARI

Un sistema è detto lineare se le funzioni di stato e di uscita sono lineari in $x$ ed $u$. $$\dot x_{1}(t)=a_{11}(t)x_{1(t)}+\cdots+a_{1n(t)}x_{n}(t)+b_{11}(t)u_{1}(t)+\cdots+b_{1m}(t)u_{m}(t) $$ $$ \vdots $$ $$ \dot x_{n}(t)=a_{n1}(t)x_{1}(t)+\cdots+a_{nn}(t)x_{n}(t)+b_{n1}(t)u_{1}(t)+\cdots+b_{nm}(t)u(t)$$ \ $$ y_{1}(t)=c_{11}(t)x_{1}(t)+\cdots+c_{1n}(t)x_{n}(t)+d_{11}(t)u_{1}(t)+\cdots+d_{1m}(t)u_{m}(t) $$ $$ \vdots $$ $$ y_{p}(t)=c_{p1}(t)x_{1}(t)+\cdots+c_{pn}(t)x_{n}(t)+d_{p1}(t)u_{1}(t)+\cdots+d_{pm}(t)u_{m}(t) $$
Quindi raggruppando tutti i coefficienti in matrici del tipo:
$$ A(t)=\left[ {\begin{array}{ccc} a_{11}(t) & \cdots & a_{1n}(t)\\ \vdots & \ddots\\ a_{n1}(t) & \cdots & a_{nn}(t)\\ \end{array} } \right] \quad B(t)=\left[ {\begin{array}{ccc} b_{11}(t) & \cdots & b_{1m}(t)\\ \vdots & \ddots\\ b_{n1}(t) & \cdots & b_{nm}(t)\\ \end{array} } \right]$$
$$ C(t)=\left[ {\begin{array}{ccc} c_{11}(t) & \cdots & c_{1n}(t)\\ \vdots & \ddots\\ c_{p1}(t) & \cdots & c_{pn}(t)\\ \end{array} } \right] \quad D(t)=\left[ {\begin{array}{ccc} d_{11}(t) & \cdots & d_{1m}(t)\\ \vdots & \ddots\\ d_{p1}(t) & \cdots & d_{pm}(t)\\ \end{array} } \right] $$\
Dove $A(t) \in \mathbb{R}^{n\times n}$, $B(t) \in \mathbb{R}^{n\times m}$, $C(t) \in \mathbb{R}^{p\times n}$, $D(t) \in \mathbb{R}^{p \times m}$\
Di conseguenza le equazioni di stato e di uscita diventano: $$ \dot x(t) = A(t)x(t) + B(t)u(t) $$ $$ y(t) = C(t)x(t) + D(t)u(t) $$

## SISTEMI LINEARI TEMPO INVARIANTI

Un sistema si dice **lineare tempo invariante** se è lineare e le funzioni del movimento sono indipendenti dal tempo: $$ \dot x(t) = Ax(t) + Bu(t) $$ $$ y(t) = Cx(t) + Du(t) $$ $A(t) \in \mathbb{R}^{n\times n}$, $B(t) \in \mathbb{R}^{n\times m}$, $C(t) \in \mathbb{R}^{p\times n}$, $D(t) \in \mathbb{R}^{p \times m}$\
Se **SISO**: $A(t) \in \mathbb{R}^{n\times n}$, $B(t) \in \mathbb{R}^{n\times 1}$, $C(t) \in \mathbb{R}^{1\times n}$, $D(t) \in \mathbb{R}^{1 \times 1} \Longrightarrow B$ è un vettore, $C$ è un vettore riga e $D$ è uno scalare.

#### Principio di sovrapposizione degli effetti

> Sia $(x_{a}(t), u_{a}(t))$ traiettoria con $x_{a}(t_{0}) = x_{0a}$\
Sia $(x_{b}(t), u_{b}(t))$ traiettoria con $x_{b}(t_{0}) = x_{0b}$\
Allora $\forall \alpha , \beta \in \mathbb{R} \textrm{ dato lo stato iniziale } x_{ab}(t_0) = \alpha x_{0a} + \beta x_{0b}, \textrm{si ha che: }$ $$ (x_{ab}(t),u_{ab}(t)) = (\alpha x_{a}(t) + \beta x_{b}(t), \alpha u_{a}(t) + \beta u_{b}(t)) $$ è una **traiettoria del sistema**. Ovvero applicando in ingresso $u_{ab}(t) = \alpha u_{a}(t) + \beta u_{b}(t)$  la traiettoria di stato è $x_{ab}(t)=\alpha x_{a}(t) + \beta x_{b}(t)$\
**Importante**: NON vale per sistemi non lineari

#### Evoluzione libera e forzata

\
\
Sia $x_{\ell}(t)\textrm{, } t\ge t_0$ la traiettoria di stato ottenuta per $x_{\ell}(t_{0}) = x_{0}$ e $u_{l}(t)=0 \textrm{, } t\ge t_{0}$, detta **evoluzione libera**\
Sia $x_{f}(t)\textrm{, } t\ge t_0$ la traiettoria di stato ottenuta per $x_{f}(t_{0}) = 0$ e $u_{f}(t)=u(t) \textrm{, } t\ge t_{0}$, detta **evoluzione forzata**\
Applicando il principio di sovrapposizione degli effetti si ha che fissato lo stato iniziale $x(t_0)=x_{0}$ e applicando l'ingresso $u(t)$, $t\ge t_0$ la traiettoria di stato è data da $$ x(t) = x_{\ell}(t) + x_{f}(t) $$ Ciò NON vale per sistemi non lineari (il principio di sovrapposizione vale solo per sistemi lineari)

\newpage

### Traiettorie di un SLTI e rappresentazioni equivalenti

Dato il SLTI generico: $x \in \mathbb{R}^{n}$, $u \in \mathbb{R}^{m}$, $y \in \mathbb{R}^{p}$ $$ \dot x(t) = Ax(t) + Bu(t) \quad \quad x(0) = x_{0} $$ $$ y(t) = Cx(t) + Du(t) $$ Dalla notazione introdotta nel paragrafo precedente si può scrivere: $$ x(t) = e^{At}x_{0} + \int_{0}^{t} e^{A(t-\tau)}Bu(\tau)d\tau $$ $$ y(t) = Ce^{At}x_{0} + C \int_{0}^{t} e^{A(t-\tau)}Bu(\tau)d\tau + Du(t) $$ Ricorda: $$ e^{At} = I + At + \frac{(At)^2}{2!} + \frac{(At)^3}{3!} + \cdots = \sum_{n=0}^{\infty} \frac{(At)^n}{n!} $$

Proprietà della matrice esponenziale:

* Esponenziale e cambio di base: $e^{TAT^{-1}t}=Te^{At}T^{-1}$
* Esponenziale di una matrice diagonale a blocchi (forma di Jordan): l'esponenziale di una matrice di questo tipo è una matrice diagonale a blocchi in cui ciascun blocco è l'esponenziale del blocco corrispondente della matrice di partenza

Difatti l'esponenziale di una matrice diagonale $\Lambda = diag\{\lambda _{1}, \ldots, \lambda _{n}\}$ è: $e^{\Lambda t}=diag\{e^{\lambda _{1}}, \ldots, e^{\lambda _{n} t}\}$\
\
\
Dalle proprietà sopraelencate si può giungere ad una rappresentazione equivalente delle equazioni di traiettorie e uscite dei SLTI effettuando un cambio di vase mediante una matrice $T$ (invertibile):
$$ \hat x(t) = Tx(t) $$ $$ x(t) = T^{-1}\hat x(t) $$ $$ \dot{\hat x}(t) = \hat A \hat x(t) + \hat B u(t) $$ $$ y(t) = \hat C \hat x(t) + \hat D u(t) $$ con: $\hat A = TAT^{-1}$, $\hat B = TB$, $\hat C = CT^{-1}$, $\hat D = D$

### Modi naturali

Dato il SLTI generico: $x \in \mathbb{R}^{n}$, $u \in \mathbb{R}^{m}$, $y \in \mathbb{R}^{p}$ $$ \dot x(t) = Ax(t) + Bu(t) \quad \quad x(0) = x_{0} $$ $$ y(t) = Cx(t) + Du(t) $$ Indicando con $\lambda _{1}, \ldots, \lambda _{r}$ gli $r\le n$ autovalori (reali e complessi coniugati) distinti della matrice $A$, con molteplicità algebrica $n_{1}, \ldots, n_{r} \ge 0$ tali che $\sum_{i=1}^{r} n_{i} = n$.\
Le componenti dell'evoluzione libera dello stato $x_{l}(t)$ si possono scrivere come: $$ x_{\ell,j}(t) = \sum_{i=1}^{r} \sum_{q=1}^{h_{i}} \gamma _{jiq}t^{q-1}e^{\lambda _{i}t} \textrm{, } \quad j=1,\ldots,n $$ per opportuni valori di $h_{i}\le n_{i}$, dove i coefficienti $\gamma _{jiq}$ dipendono dallo stato iniziale $x(0)$.\
I termini $t^{q-1}e^{\lambda _{i} t}$ sono detti **modi naturali** del sistema. L'evoluzione libera è **combinazione lineare dei modi**.\
Inoltre poichè l'uscita è lineare nello stato, anche l'evoluzione libera dell'uscita è combinazione lineare dei modi.