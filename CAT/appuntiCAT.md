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
$$ \hat x(t) = Tx(t) $$ $$ x(t) = T^{-1}\hat x(t) $$ $$ \dot{\hat x}(t) = \hat A \hat x(t) + \hat B u(t) $$ $$ y(t) = \hat C \hat x(t) + \hat D u(t) $$ con: $\hat A = TAT^{-1}$, $\hat B = TB$, $\hat C = CT^{-1}$, $\hat D = D$\
Tutto questo per cambiare la posizione dell'origine in modo tale da non avere errore (non avere un gap fra l'origine e lo stato iniziale).

### Modi naturali

Dato il SLTI generico: $x \in \mathbb{R}^{n}$, $u \in \mathbb{R}^{m}$, $y \in \mathbb{R}^{p}$ $$ \dot x(t) = Ax(t) + Bu(t) \quad \quad x(0) = x_{0} $$ $$ y(t) = Cx(t) + Du(t) $$ Indicando con $\lambda _{1}, \ldots, \lambda _{r}$ gli $r\le n$ autovalori (reali e complessi coniugati) distinti della matrice $A$, con molteplicità algebrica $n_{1}, \ldots, n_{r} \ge 0$ tali che $\sum_{i=1}^{r} n_{i} = n$.\
Le componenti dell'evoluzione libera dello stato $x_{\ell}(t)$ si possono scrivere come: $$ x_{\ell,j}(t) = \sum_{i=1}^{r} \sum_{q=1}^{h_{i}} \gamma _{jiq}t^{q-1}e^{\lambda _{i}t} \textrm{, } \quad j=1,\ldots,n $$ per opportuni valori di $h_{i}\le n_{i}$, dove i coefficienti $\gamma _{jiq}$ dipendono dallo stato iniziale $x(0)$.\
I termini $t^{q-1}e^{\lambda _{i} t}$ sono detti **modi naturali** del sistema. L'evoluzione libera è **combinazione lineare dei modi**.\
Inoltre poichè l'uscita è lineare nello stato, anche l'evoluzione libera dell'uscita è combinazione lineare dei modi.

#### Forma reale dei modi di un sistema

Se la matrice $A$ del SLTI è reale e $\lambda _{i} = \sigma _{i} + j \omega _{i}$ è un autovalore complesso, allora il suo complesso coniugato $\bar \lambda _{i} = \sigma _{i} - j \omega _{i}$ è autovalore di $A$, inoltre si può dimostrare che i coefficienti $\gamma _{jiq}$ corrispondenti agli autovalori complessi coniugati sono anch'essi complessi coniugati. Si verifica inoltre per calcolo diretto che $x_{\ell,j}(t)$ sono sempre reali e che i modi del sistema corrispondenti ad autovalori complessi coniugati $\lambda _{i}$ e $\bar \lambda _{i}$ sono del tipo: $$ t^{q-1}e^{\sigma _{i}t}cos(\omega _{i}t + \phi _{i}) $$ con opportuni valori della fase $\phi _{i}$.\
Nel caso in cui le molteplicità algebriche $n_{1},\ldots,n_{r}$ degli autovalori di $A$ coincidano con le molteplicità geometriche, allora i coefficienti $h_{i}$ sono tutti pari ad 1 e l'espressione dei modi si semplifica in $$ e^{\lambda _{i}t} \quad \quad \textrm{per autovalori reali} $$ $$ e^{\sigma _{i}t}cos(\omega _{i}t + \phi _{i}) \quad \quad \textrm{per autovalori complessi coniugati} $$
\
$$ \textrm{\bf Modi naturali: autovalori reali semplici (m.a. = m.g.)} $$

+----------------------------------------------------------------+-------------------------------------------------------------------+-----------------------------------------------------------------+
|\ \ \ \ \ \  $$ e^{\lambda_{i}t}, \lambda_{i} > 0 $$            |\ \ \ \ \ \  $$ e^{\lambda_{i}t}, \lambda_{i} = 0 $$               |\ \ \ \ \ \  $$ e^{\lambda_{i}t}, \lambda_{i} < 0 $$             |
|                                                                |                                                                   |                                                                 |
+----------------------------------------------------------------+-------------------------------------------------------------------+-----------------------------------------------------------------+
| ![](autPos.png){#uno height=150px}                             | ![](autNul.png){#due height=150px}                                | ![](autNeg.png){#tre height=150px}                              |
+----------------------------------------------------------------+-------------------------------------------------------------------+-----------------------------------------------------------------+
$$ \textrm{\bf Modi naturali: autovalori complessi coniugati semplici (m.a. = m.g.)} $$

+-----------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------+
|\ \  $$ e^{\sigma_{i}t}cos(\omega_{i}t + \phi_{i}), \sigma_{i} > 0 $$  |\ \  $$ e^{\sigma_{i}t}cos(\omega_{i}t + \phi_{i}), \sigma_{i} = 0 $$ |\ \  $$ e^{\sigma_{i}t}cos(\omega_{i}t + \phi_{i}), \sigma_{i} < 0 $$ |
|                                                                       |                                                                      |                                                                      |
+-----------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------+
| ![](autccPo.png){#qua height=150px}                                   | ![](autccNu.png){#cin height=150px}                                  | ![](autccNe.png){#sei height=150px}                                  |
+-----------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------------------------------------+

\newpage

$$ \textrm{\bf Modi naturali: autovalori reali (m.a. > m.g.)} $$

+-------------------------------------------------------------------+----------------------------------------------------------------------+--------------------------------------------------------------------+
|\ \ \ \ \  $$ t^{q}e^{\lambda_{i}t}, \lambda_{i} > 0 $$            |\ \ \ \ \  $$ t^{q}e^{\lambda_{i}t}, \lambda_{i} = 0 q > 1 $$         |\ \ \ \ \  $$ t^{q}e^{\lambda_{i}t}, \lambda_{i} < 0 $$             |
|                                                                   |                                                                      |                                                                    |
+-------------------------------------------------------------------+----------------------------------------------------------------------+--------------------------------------------------------------------+
| ![](auRePM.png){#set height=150px}                                | ![](auRNuM.png){#ott height=150px}                                   | ![](auRNeM.png){#nov height=150px}                                 |
+-------------------------------------------------------------------+----------------------------------------------------------------------+--------------------------------------------------------------------+

$$ \textrm{\bf Modi naturali: autovalori complessi coniugati (m.a. > m.g.)} $$

+--------------------------------------------------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------+
|\  $$ t^{q}e^{\sigma_{i}t}cos(\omega_{i}t + \phi_{i}), \sigma_{i} > 0 $$  |\  $$ t^{q}e^{\sigma_{i}t}cos(\omega_{i}t + \phi_{i}), \sigma_{i} = 0 $$ |\  $$ t^{q}e^{\sigma_{i}t}cos(\omega_{i}t + \phi_{i}), \sigma_{i} < 0 $$ |
|                                                                          |                                                                         |                                                                         |
+--------------------------------------------------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------+
| ![](autCPM.png){#die height=150px}                                       | ![](auCNuM.png){#und height=150px}                                      | ![](auCNeM.png){#dod height=150px}                                       |
+--------------------------------------------------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------+

$$ \textrm{\bf Modi naturali: tabella riassuntiva} $$

+-----------------------------------------------------------------+-------------------------------------------------------------+
|\ \ \ \ \  Modi naturali m. algebrica = m. geometrica            |\ \ \ \ \  Modi naturali m. algebrica > m.geometrica         |
|                                                                 |                                                             |
+-----------------------------------------------------------------+-------------------------------------------------------------+
| ![](mnatU.png){#set width=300px}                                | ![](mnatM.png){#ott width=300px}                            |
+-----------------------------------------------------------------+-------------------------------------------------------------+

\newpage

#### Forma di Jordan di una matrice

\
Per una generica matrice $A$ si può dimostrare che esiste sempre $T$ tale che: $$ J = TAT^{-1} $$ di $\mu$ autovalori distinti $\lambda _{1}, \ldots, \lambda _{\mu}$ con $n_{i}$ molteplicità algebrica di $\lambda _{i}$ $$ J = diag\{J_{1}, \ldots, J_{\mu}\} $$ con $J_i$ blocco di Jordan associato all'autovalore $\lambda _i$ dato da $$ J_{i} = diag\{J_{i1}, \ldots, J_{i\nu _{i}}\} $$ con $J_{ih} \in \mathbb{R}^{\eta _{ih} \times \eta _{ih}}$ miniblocchi di Jordan dell'autovalore $\lambda _{i}$ dati da $$ J_{ih} = \left[ {\begin{array}{ccccc} \lambda _{i} & 1 & 0 & \cdots & 0\\ 0 & \lambda _{i} & 1 & \cdots & 0\\ \vdots &  & \ddots\\ 0 & \cdots & 0 & \lambda _{i} & 1\\ 0 & \cdots & 0 & 0 & \lambda _{i} \end{array} } \right] $$ dove $\sum_{h=1}^{\nu_i} \eta_{ih} = n_i$

#### Esponenziale di un miniblocco

\
Dato $J_{ih}$ definito come nel paragrafo precedente allora il suo esponenziale $e^{J_{ih}t}$ è dato da ($\lambda _{i}$ reale o complesso)
$$ e^{J_{ih}t} = e^{\lambda _{i}t} \left[ {\begin{array}{ccccc} 1 & t & \frac{t^2}{2!} & \cdots & \frac{t^{\eta _{ih} -1}}{(\eta _{ih} - 1)!}\\ 0 & 1 & t & \cdots\\ \vdots & \ddots & \ddots\\ 0 & \cdots & 0 & 1 & t\\ 0 & \cdots & 0 & 0 & 1 \end{array} } \right] $$

#### Esempio: carrello

\
Prendendo in esempio il carrello con la massa e la molla e considerando $k$ costante cosicchè il sistema sia LTI, si ha: $$ \begin{bmatrix} \dot x_{1}(t)\\ \dot x_{2}(t) \end{bmatrix} = \begin{bmatrix} 0 & 1\\ -\frac{k}{M} & 0 \end{bmatrix} \begin{bmatrix} x_{1}(t)\\ x_{2}(t)\end{bmatrix} + \begin{bmatrix} 0\\ \frac{1}{M}\end{bmatrix} u(t) $$ $$ y(t) = \begin{bmatrix} 1 & 0 \end{bmatrix} \begin{bmatrix} x_{1}(t)\\ x_{2}(t)\end{bmatrix} + 0u(t) $$ Autovalori: $\lambda _{1} = j\sqrt{\frac{k}{M}}$, $\lambda _{2} = -j\sqrt{\frac{k}{M}}$\
Se applichiamo un controllo $u=-hx_{2}$ gli autovalori diventano:\
$\lambda _{1}=-\frac{h}{2M}+\sqrt{\frac{h^2}{4M^2} - \frac{k}{M}}$, $\lambda _{2}=-\frac{h}{2M}-\sqrt{\frac{h^2}{4M^2} - \frac{k}{M}}$\
Se $h^2 > 4Mk$ allora autovalori reali, se $h^2 < 4Mk$ autovalori complessi coniugati.\
Se $h^2 = 4Mk \Longrightarrow \lambda _{1} = \lambda _{2} = -\frac{h}{2M}$ (m.a.$=2$), si può dimostrare che m.g.$=1$, quindi blocco di Jordan $2 \times 2$: $$ J = TAT^{-1} = \begin{bmatrix} -\frac{h}{2M} & 1\\ 0 & -\frac{h}{2M}\end{bmatrix} \quad \quad \quad e^{Jt} = e^{-\frac{h}{2M}t} \begin{bmatrix} 1 & t\\ 0 & 1\end{bmatrix} $$ $$ \hat x_{\ell}(t) = \begin{bmatrix} e^{-\frac{h}{2M}t}\hat x_{1}(0) + te^{-\frac{h}{2M}t}\hat x_{2}(0)\\ e^{-\frac{h}{2M}t}\hat x_{2}(0)\end{bmatrix} $$

# STABILITÀ

#### Equilibrio stabile

Uno stato di equilibrio $x_e$ si dice stabile se $\forall \epsilon > 0, \exists \delta > 0$ tale che $\forall x_0$ tale che $\Vert x_{0} - x_{e} \Vert \le \delta$ allora risulti $\Vert x(t) - x_{e} \Vert \le \epsilon$, $\forall t \ge 0$

#### Equilibrio instabile

Uno stato di equilibrio $x_e$ si dice instabile se non è stabile.

#### Equilibrio attrattivo

Uno stato di equilibrio $x_e$ si dice attrattivo se $\exists \delta > 0$ tale che $\forall x_0$ tale che $\Vert x_{0} - x_{e} \Vert \le \delta$ allora risulti $\lim_{t\to+\infty}{\Vert x(t) - x_{e} \Vert} = 0$

#### Equilibrio asintoticamente stabile

Uno stato di equilibrio $x_e$ si dice asintoticamente stabile se è stabile e attrattivo

#### Stabilità locale

Le definizioni date sottointendono la parola locale, cioè la proprietà vale in un intorno di $x_e$

#### Stabilità globale

Le proprietà di stabilità ed asintotica stabilità sono globali se valgono $\forall x_{e} \in \mathbb{R}^n$

#### Stabilità di una traiettoria

Le definizioni di stabilità si possono generalizzare a una traiettoria $\bar x(t)$, $t \ge 0$

## STABILITÀ INTERNA DI SLTI

Nei sistemi lineari se $u=0$ allora $x=0$ è **sempre** un equilibrio. Nei sistemi lineari si può dimostrare che tutti gli equilibri e tutte le traiettorie hanno le stesse proprietà di stabilità, per questo motivo si parla di **stabilità del sistema**. \
\
**Teorema 1**

> Un SLTI è asintoticamente stabile se e solo se tutti gli autovalori hanno parte reale strettamente negativa.

**Teorema 2**

> Un SLTI è stabile se e solo se tutti gli autovalori hanno parte reale minore o uguale a zero e tutti gli autovalori a parte reale nulla hanno molteplicità geometrica uguale alla molteplicità algebrica (i miniblocchi di Jordan associati hanno dimensione 1)

Conseguenza immediata è che se si ha almeno un autovalore a parte reale positiva o se almeno un autovalore a parte reale nulla ha m.a. $>$ m.g.\
\
Prendendo in esame l'esempio del carrello, se $h^2 > 4Mk$ o se $h^2 < 4Mk$ gli autovalori, in entrambi i casi, sono a parte reale negativa, quindi il sistema è asintoticamente stabile. Se, invece, $h^{2} = 4Mk$, $\lambda _{1} = \lambda _{2} = - \frac{h}{2M}$ (m.a. $=2$), si può però dimostrare che m.g. $=2$ e che gli autovalori sono a parte reale negativa quindi il sistema è asintoticamente stabile.

### RETROAZIONE DELLO STATO

$$ \dot x(t) = Ax(t) + Bu(t) $$ $$ y(t) = Cx(t) + Du(t) $$ 
Supponendo di misurare l'intero stato, ovvero se $y(t) = x(t)$ allora possiamo progettare $$ u(t)=Kx(t) + v(t) $$ con $K \in \mathbb{R}^{m\times n}$ una matrice di guadagni e $v(t)$ un ulteriore ingresso per il sistema retroazionato. Risulta quindi $$ \dot x(t) = (A+BK)x(t) + Bv(t) $$ Se vogliamo il sistema ad anello chiuso asintoticamente stabile dobbiamo progettare $K$ tale che $(A+BK)$ abbia autovalori tutti a parte reale negativa. La possibilità di scegliere gli autovalori di $(A+BK)$ dipende dalla coppia di matrici $(A,B)$ ed è legata alla proprietà di **raggiungibilità**.\
Se non è possibile misurare l'intero stato, ovvero se $x(t)\ne y(t)$, esistono tecniche per ricostruire lo stato a partire dalle misure mediante sistemi ausiliari detti **osservatori**. Se si possa ricostruire o meno lo stato dipende dalla coppia $(A,C)$ ed è legato alla proprietà di osservabilità.

## LINEARIZZAZIONE DI SISTEMI NON LINEARI (tempo invarianti)

$$ \dot x(t) = f(x(t), u(t)) $$ $$ y(t) = h(x(t), u(t)) $$ Sia $(x_{e}, u_{e})$ una coppia di equilibrio, $f(x_{e}, u_{e}) = 0$, consideriamo una traiettoria a partire da stato iniziale $x(0) = x_{e} + \tilde x_{0}$ $$ x(t) = x_{e} + \tilde x(t) $$ $$ u(t) = u_{e} + \tilde u(t) $$ $$ y(t) = h(x_{e}, u_{e}) + \tilde y(t) = y_{e} + \tilde y(t) $$ Essendo una traiettoria vale $$ \frac{d}{dt} (x_{e} + \tilde x(t)) = f(x_{e} + \tilde x(t), u_{e} + \tilde u(t)) $$ $$ y_{e} + \tilde y(t) = h(x_{e} + \tilde x(t), u_{e} + \tilde u(t)) $$
Sviluppando in serie di Taylor ($f$ e $h$ suff. regolari) in $(x_{e}, u_{e})$ $$ \frac{d}{dt} (x_{e} + \tilde x(t)) = f(x_{e}, u_{e}) + \frac{\partial}{\partial x} f(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} + \frac{\partial}{\partial u} f(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} + \textrm{term. ord. sup.} = $$ $$ = f(x_{e}, u_{e}) + A_{e}\tilde x(t) + B_{e}\tilde u(t)+ \textrm{term. ord. sup.} = $$ $$ = A_{e}\tilde x(t) + B_{e}\tilde u(t) $$ \
$$ y_{e} + \tilde y(t) = h(x_{e}, u_{e}) + \frac{\partial}{\partial x} h(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} + \frac{\partial}{\partial u} h(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} + \textrm{term. ord. sup.} $$ 
\newpage
Quindi $$ \dot {\tilde x}(t) = \frac{\partial}{\partial x} f(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} \tilde x(t) + \frac{\partial}{\partial u} f(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} \tilde u(t) + \textrm{term. ord. sup.} $$ $$ \tilde y(t) = \frac{\partial}{\partial x} h(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} \tilde x(t) + \frac{\partial}{\partial u} h(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} \tilde u(t)+ \textrm{term. ord. sup.} $$ Conseguentemente ponendo $$ \frac{\partial}{\partial x} f(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} = A_{e} \in \mathbb{R}^{n\times n} \quad \quad \quad  \frac{\partial}{\partial u} f(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} = B_{e} \in \mathbb{R}^{n\times m} $$ $$ \frac{\partial}{\partial x} h(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} = C_{e} \quad  \quad \quad \frac{\partial}{\partial u} h(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}} = D_{e} $$ \
$$ \dot {\tilde x}(t) = A_{e}\tilde x(t) + B_{e}\tilde u(t) + \textrm{term. ord. sup.} \quad \quad \tilde x(0) = \tilde x_{0} $$ $$ \tilde y(t) = C_{e}\tilde x(t) + D_{e}\tilde u(t) + \textrm{term. ord. sup.} $$ Approssimando $$ \dot {\tilde x}(t) \approx A_{e}\tilde x(t) + B_{e}\tilde u(t) $$ $$ \tilde y(t) \approx C_{e}\tilde x(t) + D_{e}\tilde u(t) $$ Quindi il sistema linearizzato risulta $$ \dot {\Delta x}(t) = A_{e}\Delta x(t) + B_{e}\Delta u(t) $$ $$ \Delta y(t) = C_{e}\Delta x(t) + D_{e}\Delta u(t) $$ Con $(\Delta x(t), \Delta u(t)), t\ge 0,$ traiettoria del linearizzato.\
Le traiettorie del sistema linearizzato soddisfano $$ x(t) = x_{e} + \tilde x(t) \approx x_{e} + \Delta x(t) $$ $$ u(t) = u_{e} + \tilde u(t) \approx u_{e} + \Delta u(t) $$ $$ y(t) = y_{e} + \tilde y(t) \approx y_{e} + \Delta y(t) $$ per variazioni sufficientemente piccole ($\Delta$ sufficientemente piccolo).
```{=latex}
\begin{center}
```

![](traiettorialinearizzata.jpg){#traitLin height=150px}

```{=latex}
\end{center}
```

**Teorema**

> Dato un sistema non lineare tempo invatiante, $\dot x(t) = f(x(t), u(t))$, sia $(x_{e}, u_{e})$ una coppia di equilibrio. Se il sistema linearizzato intorno a $(x_{e}, u_{e})$ è asintoticamente stabile, allora l'equilibrio $x_e$, relativo all'ingresso $u_e$ è (localmente) asintoticamente stabile.\
**Ricorda**: per vedere se il sistema linearizzato è asintoticamente stabile in un intorno della coppia di equilibrio si guardano gli autovalori di $A$ (o di $A+BK$ se è retroazionato).

**Teorema**

> Dato un sistema non lineare tempo invariante, $\dot x(t) = f(x(t), u(t))$, sia $(x_{e}, u_{e})$ una coppia di equilibrio. Se il linearizzato intorno a $(x_{e}, u_{e})$ ha almeno un autovalore a parte reale positiva, allora l'equilibrio $x_{e}$, relativa all'ingresso $u_{e}$, è instabile.

**N.B.**: non si può dire nulla in caso abbiano solo autovalori a parte reale minore o uguale a zero con almeno un autovalore a parte reale nulla.

### Controllo non lineare mediante linearizzazione

Consideriamo il sistema non lineare $$ \dot x(t) = f(x(t), u(t)) $$ Linearizzazione intorno all'equilibrio $(x_{e}, u_{e})$ $(A_{e} = \frac{\partial}{\partial x} f(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}}, \quad B_{e} = \frac{\partial}{\partial u} f(x,u)\bigg|_{\substack{x=x_{e}\\ u=u_{e}}})$ $$ \dot {\Delta x}(t) = A_{e}\Delta x(t) + B_{e}\Delta u(t) $$
_Obiettivo_: portare $\Delta x(t)$ a zero, ovvero $x(t)$ a $x_{e}$ "in modo approssimato". Usando retroazione dello stato $\Delta u(t) = K\Delta x(t) + \Delta v(t)$ otteniamo il sistema in anello chiuso: $$ \dot {\Delta x}(t) = (A_{e} + B_{e}K)\Delta x(t) + B_{e}\Delta v(t) $$ Posso progettare $K$ in modo che $(A_{e} + B_{e}K)$ sia asintoticamente stabile. Grazie ai teoremi sulla linearizzazione $x_e$ risulta un equilibrio (localmente asintoticamente stabile per il sistema lineare non in anello chiuso retroazionato).\
Visto che $\Delta x(t) \approx x(t) - x_{e}$: $$ u(t) = u_{e} + K(x(t) - x_{e}) + \tilde v(t) \approx u_{e} + K\Delta x(t) + \tilde v(t) $$ Perciò la legge di controllo finale sarà: $$ u(t) = u_{e} + K(x(t) - x_{e}) + \tilde v(t) \quad \quad \textrm{\textcolor{red}{feedback (retroazione) per il sistema non lineare}} $$ Con la $K$ progettata sul sistema linearizzato.
```{=latex}
\begin{center}
```

![](feedback.png){#feedback width=500px}

```{=latex}
\end{center}
```

\newpage

# TRASFORMATA DI LAPLACE 

### Richiami sui numeri complessi

Un numero complesso può essere rappresentato in 2 modi:

* **Forma cartesiana**:
    $$ s = \sigma + j\omega \quad \quad \textrm{$\sigma$ parte reale , $\omega$ parte immaginaria} $$
* **Forma polare**:
    $$ s = \rho e^{j\varphi} \quad \quad \quad \textrm{$\rho$ modulo , $\varphi$ argomento} $$

Ovviamente esistono le formule per il passaggio fra l'una e l'altra: $$ \rho = \sqrt{\sigma^2 + \omega^2} \quad \quad \varphi = atan(\frac{\omega}{\sigma}) $$ $$ \sigma = \rho cos(\varphi) \quad \quad \omega = \rho sin(\varphi) $$

## TRASFORMATA DI LAPLACE

Data una funzione complessa $f$ di variabile reale $t$, $f:\mathbb{R}\longrightarrow\mathbb{C}$\
Sia $s=\sigma + j\omega$ una varaibile complessa, allora: $$ F(s) = \int_{0^{-}}^{+\infty} f(t)e^{-st} dt \quad \quad \quad \textrm{Trasformata di Laplace di $f(t)$} $$ Se esiste per qualche $s$, ossia se l'integrale converge.\
**Notazione**: Trasformazione di Laplace $\mathcal{L}$\ \ \ \ \ $f(t) \xrightarrow[\ \ \ \ \ \ \ ]{\mathcal{L}} F(s)$ \
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ $F(s) = \mathcal{L}[f(t)]$

### OSSERVAZIONI

#### Ascissa di convergenza

Sia $\bar \sigma > -\infty$ estremo inferiore di $s = \sigma + j \omega$ per cui l'integrale converge. Allora la trasformata esiste nel semipiano $Re(s) > \bar \sigma$. $\bar \sigma$ è detta ascissa di convergenza. La definizione si estende anche a $Re(s) \le \bar \sigma$.\
**N.B.**: solo i valori di $f(t)$ per $t\ge 0$ determinano la trasformata.\
**N.B.**: L'integrale va da $0^{-}$ a $+\infty$ quindi gli impulsi in 0 sono considerati nell'integrazione.

#### Trasformate razionali

$$ F(s) = \frac{N(s)}{D(s)} $$ dove $N(s)$ e $D(s)$ sono polinomi primi fra loro.\
Se $f$ reale allora $N(s)$ e $D(s)$ a coefficienti reali.\
Gli **zeri** sono le radici di $N(s) = 0$\
I **poli** sono le radici di $D(s) = 0$

### ANTITRASFORMAZIONE

$$ f(t) = \frac{1}{2\pi j}\int_{\sigma - j\infty}^{\sigma + j\infty} F(s)e^{st}ds $$ con $\sigma > \bar \sigma$.\
**Notazione**: antitrasformazione di Laplace $\mathcal{L}^{-1}$\ \ \ \ \ $F(s) \xrightarrow[\ \ \ \ \ \ \ ]{\mathcal{L}^{-1}} f(t)$ \
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ $f(t) = \mathcal{L}^{-1}[F(s)]$ \
**N.B.**: $f(t)$ fornita solo per $t\ge 0$. Si assume $f(t)=0$ per $t<0$.\
**N.B.**: Considerando solo $f(t)$ t.c. $f(t)=0$ per $t<0$ allora c'è corrispondenza biunivoca tra $f(t)$ e $F(s)$, quindi hanno lo stesso contenuto informativo.\
**N.B.**: la definizione è poco usata per l'antitrasformazione.

### PROPRIETÀ

#### Linearità

$$ \mathcal{L}[\alpha f(t) + \beta g(t)] = \alpha \mathcal{L}[f(t)] + \beta \mathcal{L}[g(t)] = \alpha F(s) + \beta G(s) \quad \quad \quad \forall \alpha,\beta \in \mathbb{C} $$

#### Traslazione temporale

$$ \mathcal{L}[f(t-\tau)]=e^{-\tau s}F(s) \quad \quad \quad \forall \tau > 0 $$

#### Traslazione nel dominio della variabile complessa

$$ \mathcal{L}[e^{\alpha t}f(t)]=F(s-a) \quad \quad \quad \forall \alpha \in \mathbb{C} $$

#### Derivazione nel tempo

$$ \mathcal{L}\left[\frac{d}{dt}f(t)\right] = sF(s)-f(0) $$ Ne consegue iterando $$ \mathcal{L}\left[\frac{d^n}{dt^n}f(t)\right] = s^{n}F(s) - \sum_{i=1}^{n} s^{n-i}\frac{d^{i-1}}{dt^{i-1}}f(t)\big|_{t=0} $$

#### Integrazione nel tempo

$$ \mathcal{L}\left[\int_{0}^{t}f(\tau)d\tau \right] = \frac{1}{s}F(s) $$

#### Convoluzione nel tempo

$$ \mathcal{L}\left[\int_{0}^{t}f_{1}(t-\tau)f_{2}(\tau)d\tau \right] = F_{1}(s)F_{2}(s) $$


### TEOREMI DEL VALORE INIZIALE E FINALE

#### Teorema del valore iniziale

> Se $f(t)$ reale con trasformata razione $F(s)$ con grado del denominatore maggiore del grado del numeratore allora $$ f(0) = \lim_{s\to \infty} sF(s) $$

#### Teorema del valore finale

> Se $f(t)$ reale con trasformata razionale $F(s)$ con grado del denominatore maggiore del grado del numeratore e poli nulli o a parte reale negativa allora $$ \lim_{t\to \infty} f(t) = \lim_{s\to 0} sF(s) $$

### TRASFORMATA DI SEGNALI ELEMENTARI

#### Delta di Dirac

$\mathcal{L}[\delta (t)] = 1$

#### Gradino unitario

$\mathcal{L}[1(t)] = \frac{1}{t}$

#### Rampa

$\mathcal{L}[t 1(t)] = \frac{1}{s^2}$

#### Esponenziale

$\mathcal{L}[e^{\alpha t} 1(t)] = \frac{1}{s-\alpha}$

#### Seno

$\mathcal{L}[sin(\omega t)1(t)] = \frac{\omega}{s^2 + \omega^2}$

#### Coseno

$\mathcal{L}[cos(\omega t)1(t)] = \frac{1}{\omega}\mathcal{L}[\frac{d}{dt}sin(\omega t)1(t)] = \frac{s}{\omega}\mathcal{L}[sin(\omega t)1(t)]  = \frac{s}{\omega} \frac{\omega}{s^2 + \omega^2} = \frac{s}{s^2 + \omega^2}$

#### Seno con fase

$\mathcal{L}[sin(\omega t \pm \varphi)1(t)] = \frac{\omega\ cos(\varphi)\  \pm\  s\ sin(\varphi)}{s^2 + \omega^2}$

#### Coseno con fase

$\mathcal{L}[cos(\omega t \pm \varphi)1(t)] = \frac{s\ cos(\varphi) \ \mp\  \omega\ sin(\varphi)}{s^2 + \omega^2}$

## FUNZIONE DI TRASFERIMENTO

### Sistema non variante

$\dot x(t) = f(x(t),u(t))$ \
$\mathcal{L}[\frac{d}{dt} x(t)] = \mathcal{L}[f(x(t),u(t))]$ \
$sX(s)-x(0) = \int_{0^-}^{+\infty} f(x(t), u(t)) e^{-st} dt$

### Sistema lineare tempo variante

$\dot x(t) = A(t)x(t) + B(t)u(t)$ \
$sX(s)-x_0 = \mathcal{L}[A(t)x(t)+B(t)u(t)] = \mathcal{L}[A(t)x(t)]+\mathcal{L}[B(t)u(t)] = \int_{0^-}^{+\infty} A(t)x(t)e^{-st} dt + \int_{0^-}^{+\infty} B(t)u(t)e^{-st} dt$

### SISTEMA LINEARE TEMPO INVARIANTE

Dato il seguente SLTI con $x\in \mathbb{R}^n$ , $u \in \mathbb{R}^m$ ed $y \in \mathbb{R}^p$ $$ \dot x(t) = Ax(t) + Bu(t) $$ $$ y(t) = Cx(t) + Du(t) $$ con $x(0) = x_0$\
Siano $X(s) := \mathcal{L}[x(t)]$ , $U(s)=\mathcal{L}[u(t)]$ e $Y(s)=\mathcal{L}[y(t)]$.\
Trasformando entrambi i membri e ricordando che $\mathcal{L}[\dot x(t)] = sX(s) - x(0)$\ :
\begin{equation*}
    \begin{aligned}
    sX(s) - x(0) &= AX(s) + BU(s) \\
    Y(s) &= CX(s) + DU(s)
    \end{aligned}
\end{equation*}
\begin{equation*}
    \begin{aligned}
    (sI - A)X(s) &= x_0 + BU(s) \\
    Y(s) &= CX(s) + DU(s)
    \end{aligned}
\end{equation*}
\begin{equation*}
    \begin{aligned}
    X(s) &= (sI - A)^{-1} x_0 + (sI - A)^{-1} BU(s)\\
    Y(s) &= C(sI-A)^{-1} x_0 + (C(sI-A)^{-1}B + D)U(s)
    \end{aligned}
\end{equation*}
Si possono quindi individuare le traformate dell'evoluzione libera (quelle dipendenti da $x_0$) e dell'evoluzione forzata (quelle dipendenti da $U(s)$): 

* Evoluzione libera: $$ X_{\ell}(s) = (sI-A)^{-1}x_0 $$ $$ Y_{\ell}(s) = C(sI-A)^{-1} x_0 $$
* Evoluzione forzata: $$ X_{f}(s) = (sI-A)^{-1}BU(s) $$ $$ Y_{f}(s) = (C(sI-A)^{-1}B + D) U(s) $$

Considerando la trasformata dell'evoluzione forzata dell'uscita: $$ Y_{f}(s) = (C(sI-A)^{-1}B + D) U(s) $$ La matrice: $$ G(s) = C(sI-A)^{-1}B + D $$ è detta **funzione di traferimento**.\
Se il sistema è SISO allora è uno scalare.\
Dunque ora si ha una rappresentazione ingress-uscita (detta rappresentazione _esterna_) del tipo: $$ Y_{f}(s) = G(s)U(s) $$ Se si assumesse $x(0)=0$ allora si avrebbe $$ Y(s)=G(s)U(s) $$
**N.B.**: la funzione di trasferimento è data dal rapporto tra la trasformata dell'uscita e dell'ingresso nel caso $x(0) = x_0 = 0$: $$ G(s) = \frac{Y(s)}{U(s)} $$
Operativamente la funzione di traferimento può essere calcolata come: $$ G(s) = C(sI-A)^{-1}B + D = C\frac{adj(sI-A)}{det(sI-A)}B + D $$
\newpage
Nel caso sia SISO la funzione è una funzione razionale fratta: 

* il denominatore di grado $n$ e numeratore di grano $\le n$ ($= n$ se $D \ne 0$ e ne consegue che il sistema sarebbe proprio e NON strettamente proprio)
* il numeratore ed il denominatore possono avere radici comuni e quindi semplificabili, questo comporta un minore contenuto informativo rispetto alla forma di stato
* la relazione fra grado del numeratore e denominatore è detta _grado relativo_

E a livello dimensionale si avrebbe: $D\in\mathbb{R}$ , $C\in\mathbb{R}^{1\times n}$ , $B\in\mathbb{R}^{n\times 1}$ , $adj(sI-A)\in\mathbb{R}^{n\times n}$ e $det(sI-A)$ che è un polinomio di grado $n$.\
Nel caso in cui il sistema non sia SISO comunque $G(s)$ sarebbe una matrice i cui i singoli elementi sono rapporti di polinomi.\
\
La funzione di traferimento: $$ G(s) = C(sI-A)^{-1}B + D $$ Se vista come rapporto di polinomi, può essere scritta: $$ G(s)=\frac{N(s)}{D(s)}=\frac{\beta _{\nu}s^{\nu} + \beta _{\nu -1} s^{\nu - 1}+ ... + \beta _{1} s + \beta _{0}}{s^{\nu} + \alpha _{\nu -1} s^{\nu - 1} + ... + \alpha _{1} s + \alpha _{0}} $$
Le radici di $N(s)$ sono dette **zeri**.\
Le radici di $D(s)$ sono dette **poli**.\
**Molto importante**: i poli sono radici di di $det(sI-A)$ quindi sono gli autovalori di A.\
Un'altra osservazione può essere che poli e zeri sono reali o complessi coniugati poichè sono radici di polinomi a coefficienti reali.\
\
Ma perchè usiamo la traformata di Laplace?

> Perchè, usando la trasformata di Laplace, abbiamo un dominio (diverso da quello del tempo) nel quale non dobbiamo agire e risolvere equazioni differenziali potenzialmente molto complicate, bensì si riduce tutto a rapporti di polinomi di facile risoluzione.

#### Rappresentazioni e parametri della funzione di traferimento

\
Una forma fattorizzata è: $$ G(s) = \frac{\rho\prod_{i} (s+z_i) \prod_{i} (s^2 + 2\zeta _{i} \alpha _{ni} s + \alpha _{ni}^2)}{s^g \prod_{i} (s + p_i) \prod_{i} (s^2 + 2\xi _{i} \omega _{ni} s + \omega _{ni}^2)} $$ 
I cui poli reali sono: $-p_i$. \
E gli zeri reali: $-z_i$.\
Si può dimostrare che $|\xi _{i}| < 1$ perchè devono essere complesse coniugate: 
\begin{equation*}
    \begin{aligned}
        s^2 + \xi _{i} \omega _{ni} s + \omega _{ni}^2 \Rightarrow s_{p_{i_{1,2}}} &= -\xi _{i} \omega _{ni} \pm \sqrt{\xi _{i}^2 \omega _{ni}^2 - \omega _{ni}^2} \\
        &= -\xi _{i} \omega _{ni} \pm \omega _{ni} \sqrt{\xi _{i}^2 - 1} \\
        &= -\xi _{i} \omega _{ni} \pm j \omega_{ni} \sqrt{1 - \xi _{i}^2}
    \end{aligned}
\end{equation*}
Dalla forma presentata in precedenza si può arrivare ad una seconda forma particolarmente di interesse: $$ G(s) = \frac{\mu \prod_{i}(1+\tau _{i}s) \prod_{i}(1+\frac{2\zeta _i}{\alpha _{ni}}s + \frac{s^2}{\alpha _{ni}^2})}{s^g \prod_{i}(1+T_i s) \prod_{i} (1+\frac{2\xi _{i}}{\omega _{ni}} s +\frac{s^2}{\omega _{ni}^2})} $$
detta **forma di Bode**. 
\newpage
_Dimostrazione_:

> $$ G(s) = \frac{\rho\prod_{i} (s+z_i) \prod_{i} (s^2 + 2\zeta _{i} \alpha _{ni} s + \alpha _{ni}^2)}{s^g \prod_{i} (s + p_i) \prod_{i} (s^2 + 2\xi _{i} \omega _{ni} s + \omega _{ni}^2)} $$
$$ \prod_{i} (s+z_i) = \prod_{i} (1+\frac{1}{z_i}s)z_{i} \quad \quad \quad \quad \quad \prod_{i} (s^2 + 2\zeta _{i} \alpha _{ni} s + \alpha _{ni}^2) = \prod_{i} (\frac{s^2}{\alpha _{ni}^2} + \frac{s\zeta _{i}}{\alpha _{ni}}s + 1)\alpha _{ni}^2 $$
$$ \prod_{i} (s+p_i) = \prod_{i} (1+\frac{1}{p_i}s)p_{i} \quad \quad \quad \quad \quad \prod_{i} (s^2 + 2\xi _{i} \omega _{ni} s + \omega _{ni}^2) = \prod_{i} (\frac{s^2}{\omega _{ni}^2} + \frac{s\xi _{i}}{\omega _{ni}}s + 1)\omega _{ni}^2 $$
Quindi la $G(s)$ diventa: 
\begin{equation*}
    \begin{aligned}
        G(s) &= \frac{\rho\prod_{i} (s+z_i) \prod_{i} (s^2 + 2\zeta _{i} \alpha _{ni} s + \alpha _{ni}^2)}{s^g \prod_{i} (s + p_i) \prod_{i} (s^2 + 2\xi _{i} \omega _{ni} s + \omega _{ni}^2)} \\
        &= \frac{\rho\prod_{i} z_i \prod_{i} \alpha _{ni}^2 \prod_{i} (1+\frac{1}{z_i}s) \prod_{i} (1 + \frac{2\zeta _{i}}{\alpha _{ni}^2} s + \frac{s^2}{\alpha _{ni}^2})}{s^g \prod_{i} p_i \prod_{i} \omega _{ni}^2 \prod_{i} (1 + \frac{1}{p_i}) \prod_{i} (1 + \frac{2\xi _{i}}{\omega _{ni}} s + \frac{s^2}{\omega _{ni}^2})}
    \end{aligned}
\end{equation*}
Chiamando: 
$$ \mu = \rho\frac{\prod_{i} z_i \prod_{i} \alpha _{ni}^2}{\prod_{i} p_i \prod_{i} \omega _{ni}^2} \quad \quad \quad \quad \quad \quad \tau _{i} = \frac{1}{z_i} \quad \quad \quad \quad T_i = \frac{1}{p_i} $$
Si ha:
\begin{equation*}
    \begin{aligned}
        G(s) &= \frac{\rho\prod_{i} (s+z_i) \prod_{i} (s^2 + 2\zeta _{i} \alpha _{ni} s + \alpha _{ni}^2)}{s^g \prod_{i} (s + p_i) \prod_{i} (s^2 + 2\xi _{i} \omega _{ni} s + \omega _{ni}^2)} \\
        &= \frac{\rho\prod_{i} z_i \prod_{i} \alpha _{ni}^2 \prod_{i} (1+\frac{1}{z_i}s) \prod_{i} (1 + \frac{2\zeta _{i}}{\alpha _{ni}^2} s + \frac{s^2}{\alpha _{ni}^2})}{s^g \prod_{i} p_i \prod_{i} \omega _{ni}^2 \prod_{i} (1 + \frac{1}{p_i}) \prod_{i} (1 + \frac{2\xi _{i}}{\omega _{ni}} s + \frac{s^2}{\omega _{ni}^2})} \\
        &= \frac{\mu \prod_{i}(1+\tau _{i}s) \prod_{i}(1+\frac{2\zeta _i}{\alpha _{ni} s} + \frac{s^2}{\alpha _{ni}^2})}{s^g \prod_{i}(1+T_i s) \prod_{i} (1+\frac{2\xi _{i}}{\omega _{ni}} s +\frac{s^2}{\omega _{ni}^2})}
    \end{aligned}
\end{equation*}
Da qui una variante un po' più chiara della forma di Bode è: $$ G(s) = \mu \frac{\prod_{i}(1+\tau _{i}s) \prod_{i}(1+\frac{2\zeta _i}{\alpha _{ni} s} + \frac{s^2}{\alpha _{ni}^2})}{s^g \prod_{i}(1+T_i s) \prod_{i} (1+\frac{2\xi _{i}}{\omega _{ni}} s +\frac{s^2}{\omega _{ni}^2})} \quad \quad \quad \quad \quad \quad \quad \blacksquare $$

In cui:

* $\rho$ costante di trasferimento, $\mu$ guadagno
* $g$ tipo
* $-z_i$ zeri reali, $-p_i$ poli reali, $\tau _i$ e $T_i$ costanti di tempo
* $\alpha _{ni} > 0$, $\omega _{ni} > 0$ pulsazioni naturali di zeri e poli complessi coniugati
* $\zeta _{i}$, $\xi _{i}$ ($|\zeta _{i}| < 1$ e $|\xi _{i}| < 1$) smorzamenti di zeri e poli complessi coniugati

Esempio sistemi del II ordine: $G(s)=\frac{\rho}{s^2 + s\xi \omega _{n} + \omega _{n}^2}$\
Esempio: $G(s)=100\frac{s+1}{s(s+10)}=\frac{100}{10}\frac{s+1}{s(1+\frac{1}{10}s)}=10\frac{s+1}{s(1+\frac{1}{10}s)}$\
\ \ \ \ \ \ \ \ \ \ \ \ \ Quindi si ha: $\rho = 100$, $z=1$, $p=10$, $\mu = 10$, $\tau = 1$ e $T=\frac{1}{10}$ 

```{=latex}
\begin{center}
```

![Rappresentazione dei poli e degli zeri sul piano complesso](poliZeriCCeR.jpg)

```{=latex}
\end{center}
```

#### Esempio 1

\
Dato il sistema: $$ \dot x_1 = -x_1 + x_2 $$ $$ \dot x_2 = -2x_2 + u $$ $$ y = x_2 $$ Allora 
\begin{equation*}
    \begin{aligned}
        G(s) &= C(sI-A)^{-1}B \\
        &= \begin{bmatrix} 0 & 1 \end{bmatrix} \begin{bmatrix} s+1 & -1\\ 0 & s+2\end{bmatrix}^{-1} \begin{bmatrix} 0 \\ 1 \end{bmatrix} \\
        &= \begin{bmatrix} 0 & 1 \end{bmatrix} \begin{bmatrix} \frac{s+2}{(s+1)(s+2)} & \frac{1}{(s+1)(s+2)} \\ 0 & \frac{s+1}{(s+1)(s+2)} \end{bmatrix} \begin{bmatrix} 0 \\ 1 \end{bmatrix} \\
        &= \frac{s+1}{(s+1)(s+2)} = \frac{1}{s+2}
    \end{aligned}
\end{equation*}

#### Esempio 2

\
Dato il sistema: $$ \dot x_1 = -x_1 -2x_2 + u $$ $$ \dot x_2 = 4x_2 $$ $$ y = x_1 $$ Trasformando entrambi i membri:
\begin{equation*}
    \begin{aligned}
        sX_{1}(s) - x_{1}(0) &= -X_{1}(s) -2X_{2}(s) + U(s) \\
        sX_{2}(s) - x_{2}(0) &= 4X_{2}(s) \\
        Y(s) &= X_{1}(s) 
    \end{aligned}
\end{equation*}
In alternativa calcolandola con $G(s) = C(sI-A)^{-1}B$ si ha $G(s)=\frac{s-4}{(s-4)(s+1)}=\frac{1}{s+1}$

## ANTITRAFORMAZIONE DI LAPLACE

Ricordiamo che la trasformata della risposta di un SLTI SISO è data da: $Y(s) = C(sI-A)^{-1} x(0) + G(s)U(s)$ con $C(sI-A)^{-1} \in \mathbb{R}^{1\times n}$. \
Inoltre sappiamo che si può far vedere che gli elementi di $C(sI-A)^{-1}$ sono rapporti di polinomi.\
Quindi ora si può scrivere: $$ Y(s)=\frac{N(s)}{D(s)} $$ con $N(s)$ e $D(s)$ polinomi opportuni.\
Ora si ricorda che per $x(0) = 0$ (cioè in risposta forzata) si ha: $$ Y(s) = G(s)U(s) $$ E applicando a quest'ultima una delta di Dirac $u(t)=\delta (t)$ (che ha traformata $U(s)=1$) si arriva ad avere: $$ Y(s)=G(s) $$ Indi per cui per la risposta all'impulso le radici di $D(s)$ sono i poli della funzione di traferimento.

#### Esempio di antitrasformazione tramite sviluppo di Heaviside

\
Data la risposta: $$ Y(s) = \frac{10(s+2)}{(s+1)(s+5)} $$ e mettiamo di volerla scrivere come: $$ Y(s) = \frac{10(s+2)}{(s+1)(s+5)} = \frac{r_1}{s+1}+\frac{r_2}{s+5} $$ con $r_1$, $r_2$ coefficienti.\
Calcolando l'antitrasformata: 
\begin{equation*}
    \begin{aligned}
        y(t) = \mathcal{L}^{-1}[Y(s)] &= \mathcal{L}^{-1}\left[\frac{r_1}{s+1}+\frac{r_2}{s+5}\right] \quad \quad \textrm{per linearità della trasformata}\\
        &= \mathcal{L}^{-1}\left[\frac{r_1}{s+1}\right] + \mathcal{L}^{-1}\left[\frac{r_2}{s+5}\right] \\
        &= r_1 \mathcal{L}^{-1}\left[\frac{1}{s+1}\right] + r_2 \mathcal{L}^{-1}\left[\frac{1}{s+5}\right] \quad \quad \textrm{ricordando le trasformate fondamentali} \\
        &= r_1 e^{-t} 1(t) + r_2 e^{-5t} 1(t)
    \end{aligned}
\end{equation*}
Ma come calcolare $r_1$ e $r_2$? \
Si sceglie un polo e si calcola la $Y(s)$ moltiplicata per il fatto che corrisponde al polo per la $s\rightarrow polo$. Nel nostro caso scegliamo $(s+1)$ quindi $polo = -1$: $$ (s+1)Y(s)\bigg|_{s=-1} = (s+1) \frac{10(s+2)}{(s+1)(s+5)}\bigg|_{s=-1} = \frac{10}{4} = \frac{5}{2} $$ $$ (s+1)Y(s)\bigg|_{s=-1} = (s+1)\frac{r_1}{s+1} + (s+1)\frac{r_2}{s+5} \bigg|_{s=-1} = r_1 $$ Allora $$ r_1 = (s+1)Y(s)\bigg|_{s=-1} = \frac{10(s+2)}{s+5}\bigg|_{s=-1} = \frac{5}{2} $$ Si fa lo stesso per $r_2$ e risulta: $$ r_2 = (s+5)Y(s)\bigg|_{s=-5} = \frac{10(s+2)}{s+1}\bigg|_{s=-5} = \frac{15}{2} $$ Riassumento: $$ Y(s) = \frac{5}{2}\frac{1}{s+1}+\frac{15}{2}\frac{1}{s+5} $$ $$ y(t) = \frac{5}{2} e^{-t}1(t)+\frac{15}{2}e^{-5t}1(t) $$

### SVILUPPO DI HEAVISIDE O IN FRATTI SEMPLICI

#### Caso 1: poli reali o complessi coniugati distinti (molteplicità 1)

\
\
Si può scrivere $Y(s)$ come: $$ Y(s) = \frac{N(s)}{D(s)} = \frac{N(s)}{\prod_{i=1}^{n} (s+p_{i})} = \sum_{i=1}^{n} \frac{r_i}{s+p_i} $$ Gli $r_i$ sono detti **_residui_**.\
Consideriamo: $$ (s+p_i)\frac{N(s)}{D(s)}\bigg|_{s=-p_{i}} = \sum_{\substack{j=1\\ j\ne i}}^{n}\frac{r_{j}(s+p_{i})}{s+p_{j}}\bigg|_{s=-p_i} + r_i $$ Quindi ciascun residuo $r_i$ può essere calcolato come $$ r_i = (s+p_{i})\frac{N(s)}{D(s)}\bigg|_{s=-p_{i}} $$ Infine, antitrasformando: $$ Y(s) = \frac{N(s)}{\prod_{i=1}^{n} (s+p_{i})} = \sum_{i=1}^{n} \frac{r_i}{s+p_i} $$ $$ y(t) = \mathcal{L}^{-1}[Y(s)] = \sum_{i=1}^{n}r_{i}\mathcal{L}^{-1}\left[ \frac{1}{s+p_{i}}\right] = \sum_{i=1}^{n}r_{i}e^{-p_{i}t}1(t) $$ **Osservazione**: $r_i$ reali se associati a poli reali, $r_i$ complessi coniugati se associati a poli complessi coniugati.\
\
È interessante notare, inoltre, la forma reale dei poli complessi coniugati trovati col procedimento precedente, quindi cosideriamo la coppia di poli complessi coniugati seguente: $$ p_{i,1} = \sigma _{i} + j\omega _{i} \quad \quad \quad \quad p_{i,2} = \sigma _{i} - j\omega _{i} $$ E i residui associati sono: $$ r_{i,1} = M_{i} e^{-j\varphi _{i}} \quad \quad \quad \quad r_{i,2}=M_{i} e^{j\varphi _{i}} $$ Quindi l'antitrasformata dei due termini associati è data da: 
\begin{equation*}
    \begin{aligned}
        \mathcal{L}^{-1}\left[\frac{r_{i,1}}{s+p_{i,1}}+\frac{r_{i,2}}{s+p_{i,2}}\right] &= M_{i}e^{-j\varphi _{i}}e^{-p_{i,1}t}1(t) + M_{i}e^{j\varphi _{i}}e^{-p_{i,2}t}1(t) \\
        &= M_{i}e^{-j\varphi _{i}}e^{-(\sigma _{i} + j\omega _{i})t}1(t) + M_{i}e^{j\varphi _{i}}e^{-(\sigma _{i} - j\omega _{i})t}1(t) \\
        &= M_{i}e^{-\sigma _{i} t} (e^{-j(\omega _{i} t + \varphi _{i})}+e^{j(\omega _{i} t + \varphi _{i})})1(t) \\
        &= 2M_{i}e^{-\sigma _{i} t} \frac{(e^{-j(\omega _{i} t + \varphi _{i})}+e^{j(\omega _{i} t + \varphi _{i})})}{2}1(t) \\
        &= 2M_{i}e^{-\sigma _{i} t}cos(\omega _{i} t + \varphi _{i})1(t)
    \end{aligned}
\end{equation*}
Da cui valgono le regole di divergenza e convergenza viste per i modi naturali:

* $-\sigma _{i}>0 \Longrightarrow e^{-\sigma _{i} t}cos(\omega _{i} t + \varphi _{i})$ diverge
* $-\sigma _{i}=0 \Longrightarrow e^{-\sigma _{i} t}cos(\omega _{i} t + \varphi _{i})$ rimane costante
* $-\sigma _{i}<0 \Longrightarrow e^{-\sigma _{i} t}cos(\omega _{i} t + \varphi _{i})$ converge 

#### Caso 2: poli reali o complessi coniugati multipli (molteplicità > 1)

\
\
Si può scrivere $Y(s)$ come: $$ Y(s) = \frac{N(s)}{D(s)} = \frac{N(s)}{\prod_{i=1}^{q} (s+p_{i})^{n_i}} = \sum_{i=1}^{q}\sum_{h=1}^{n_i} \frac{r_{i,h}}{(s+p_i)^h} $$ con $r_{i,h}$, $h=1,...,n_i$, residui del polo $-p_i$.\
Si consideri: 
\begin{equation*}
    \begin{aligned}
        (s+p_i)^{n_i}\frac{N(s)}{D(s)} &= \\
        &= (s+p_i)^{n_i} \sum_{\substack{j=1\\ j\ne i}}^{q}\sum_{h=1}^{n_j}\frac{r_{j,h}}{(s+p_j)^h}+\sum_{h=1}^{n_i}(s+p_i)^{n_i-h}r_{i,h} \\
        &= (s+p_i)^{n_i} \sum_{\substack{j=1\\ j\ne i}}^{q}\sum_{h=1}^{n_j}\frac{r_{j,h}}{(s+p_j)^h}+\sum_{h=1}^{n_i-1}(s+p_i)^{n_i-h}r_{i,h} + r_{i,n_i}
    \end{aligned}
\end{equation*}
Quindi il residuo $r_{i,n_i}$ è dato da: $$ r_{i,n_i} = (s+p_i)^{n_i}\frac{N(s)}{D(s)}\bigg|_{s=-p_i} $$ Derivando $(s+p_i)^{n_i}\frac{N(s)}{D(s)}$ si calcolano gli altri residui come: $$ r_{i,h} = \frac{1}{(n_i-h)!}\frac{d^{n_i-h}}{ds^{n_i-h}}\left[(s+p_i)^{n_i}\frac{N(s)}{D(s)}\right]\bigg|_{s=-p_i} $$ Antitrasformando la $Y(s)$ sviluppata in fratti semplici: $$ Y(s) = \frac{N(s)}{D(s)} = \frac{N(s)}{\prod_{i=1}^{q} (s+p_{i})^{n_i}} = \sum_{i=1}^{q}\sum_{h=1}^{n_i} \frac{r_{i,h}}{(s+p_i)^h} $$
\begin{equation*}
    \begin{aligned}
        y(t) = \mathcal{L}^{-1}[Y(s)] &= \sum_{i=1}^{q}\sum_{h=1}^{n_i}r_{i,h}\mathcal{L}^{-1}\left[\frac{1}{(s+p_i)^h}\right] \\
        &\textrm{ricordando le regole di antitrasformazione}\\
        &= \sum_{i=1}^{q}\sum_{h=1}^{n_i}r_{i,h}\frac{t^{h-1}}{(h-1)!}e^{-p_it}1(t)
    \end{aligned}
\end{equation*}
Si può dimostrare che per una coppia di poli complessi coniugati $$ \sigma _{i} + j\omega _{i} \quad \quad \textrm{e} \quad \quad \sigma _{i} - j\omega _{i} $$ con molteplicità $n_i$, il contributo elementare associato è dato da: $$ \sum_{h=1}^{n_i}2M_{i,h}\frac{t^{h-1}}{(h-1)!}e^{-\sigma _{i}t}cos(\omega _{i}t+\varphi _{i,h})1(t) $$ I modi naturali per un polo reale (multiplo) $-p_i$ è dato da: $$ \frac{t^{h-1}}{(h-1)!}e^{-p_{i}t}1(t) $$ Mentre per una coppia di poli complessi coniugati (multipli) $-(\sigma _{i} + j\omega _{1})$ e $-(\sigma _{i} - j\omega _{1})$ è dato da: $$ \frac{t^{h-1}}{(h-1)!}e^{-\sigma _{i}t}cos(\omega _{i}t+\varphi _{i,h})1(t) $$ Da qui le regole di convergenza sono le stesse viste per i modi naturali con molteplicità algebrica maggiore di quella geometrica.

#### Esempio di antitrasformazione tramite sviluppo di Heaviside: caso 2

\
Data la funzione: $$ Y(s) = \frac{s+1}{s(s+2)^2} $$ Si vuole scrivere come: $$ Y(s) = \frac{s+1}{s(s+2)^2} = \frac{r_1}{s}+\frac{r_{2,1}}{s+2}+\frac{r_{2,2}}{(s+2)^2} $$ Si calcola $r_1$: $$ r_1 = s\frac{s+1}{s(s+2)^2}\bigg|_{s=0} = \frac{1}{4} $$ Si procede calcolando $Y(s)(s+2)^2\bigg|_{s=-2}$: $$ Y(s)(s+2)^2\bigg|_{s=-2} = \begin{cases} (s+2)^2\frac{s+1}{s(s+2)^2}\bigg|_{s=-2} = \frac{1}{2} \\ (s+2)^2\frac{r_1}{s}+(s+2)^2\frac{r_{2,1}}{s+2}+(s+2)^2\frac{r_{2,2}}{(s+2)^2}\bigg|_{s=-2} = r_{2,2}\end{cases} \quad \Longrightarrow r_{2,2}=\frac{1}{2} $$ Ora manca solo $r_{2,1}$, per calcolarlo si nota che: $$ Y(s)(s+2)^2=(s+2)^2\frac{r_1}{s}+(s+2)^2\frac{r_2,1}{s+2}+r_{2,2} $$ $$ \frac{d}{ds}\left[Y(s)(s+2)^{2}\right]\bigg|_{s=-2} = \left[2(s+2)\frac{r_1}{s}-(s+2)^2\frac{r_1}{s^2}+r_{2,1}+0\right]\bigg|_{s=-2}=r_{2,1} $$ Quindi: $$ r_{2,1}=\frac{d}{ds}Y(s)(s+2)^2\bigg|_{s=-2}=\frac{d}{ds}\frac{s+1}{s}\bigg|_{s=-2}=-\frac{1}{4} $$ Quindi rimettendo insieme i pezzi: 
\begin{equation*}
    \begin{aligned}
        y(t)&=\mathcal{L}^{-1}[Y(s)] \\
        &=\mathcal{L}^{-1}\left[\frac{s+1}{s(s+2)^2}\right] \\
        &=\mathcal{L}^{-1}\left[\frac{r_1}{s}+\frac{r_{2,1}}{s+2}+\frac{r_{2,2}}{(s+2)^2}\right] \\
        &=r_{1}\mathcal{L}^{-1}\left[\frac{1}{s}\right]+r_{2,1}\mathcal{L}^{-1}\left[\frac{1}{s+2}\right]+r_{2,2}\mathcal{L}^{-1}\left[\frac{1}{(s+2)^2}\right] \\
        &=r_{1}1(t)+r_{2,1}e^{-2t}1(t)+r_{2,2}te^{-2t}1(t) \\
        &=\left(\frac{1}{4}-\frac{1}{4}e^{-2t}+\frac{1}{2}te^{-2t}\right)1(t)
    \end{aligned}
\end{equation*}

### RISPOSTA AD UN INGRESSO GENERICO

Ricordando che: $$ Y(s)=C(sI-A)^{-1}x(0)+G(s)U(s) $$ in cui $C(sI-A)^{-1}$, $G(s)$ e $U(s)$ sono rapporti di polinomi, si può affermare che: $$ y(t)=y_{\ell}(t)+y_f(t)=y_{\ell}(t)+y_{f,G}(t)+y_{f,U}(t) $$ nella quale: 

* $y_{\ell}(t)$ e $y_{f,G}(t)$ sono combinazioni lineari di modi naturali del sistema di matrici $A$, $B$, $C$ e $D$
* $y_{f,U}(t)$ è combinazione lineare di "modi" presenti nell'ingresso $u(t)$ (dovuti alle radici del denominatore di $U(s)$)

### RISPOSTE DI SISTEMI ELEMENTARI

Si ricordi che $$ G(s) = \frac{\rho\prod_{i} (s+z_i) \prod_{i} (s^2 + 2\zeta _{i} \alpha _{ni} s + \alpha _{ni}^2)}{s^g \prod_{i} (s + p_i) \prod_{i} (s^2 + 2\xi _{i} \omega _{ni} s + \omega _{ni}^2)} $$ Considerando il caso di poli distinti. Da quanto visto fin'ora risulta che per $x(0)=0$ (risposta forzata): $$ Y(s)=G(s)U(s)=\sum_{i}\frac{r_i}{s+p_i}+\sum_{i}\frac{a_is+b_i}{s^2+2\xi _i\omega _{n,i}s+\omega _{n,i}^2} $$ Viene da se che è importante studiare le risposte di sistemi elementari.

#### Esempio 1: risposta al gradino sistema del prim'ordine

\
Ricordando: $$Y(s)=G(s)U(s) $$ Si studi la risposta del sistema descritto dalla seguente $G(s)$: $$ G(s)=\frac{\mu}{1+Ts}=\frac{\mu}{T}\frac{1}{s+\frac{1}{T}} $$ Ponendo in ingresso: $$ u(t)=k1(t) $$ Trasformando la $u(t)$ si trova: $$ U(s)=\mathcal{L}[u(t)]=\mathcal{L}[k1(t)]=\frac{k}{s} $$ Quindi la risposta nel dominio di Laplace è: $$ Y(s)=G(s)U(s)=\frac{\mu}{T}\frac{1}{s+\frac{1}{T}}\frac{k}{s}=\frac{k\mu}{s(s+\frac{1}{T})}=\frac{r_1}{s}+\frac{r_2}{s+\frac{1}{T}} $$ Calcolando i residui: $$ r_1=sY(s)\bigg|_{s=0}=\frac{k\mu}{T}\frac{1}{s+\frac{1}{T}}\bigg|_{s=0}=k\mu $$ $$ r_2=\left(s+\frac{1}{T}\right)Y(s)\bigg|_{s=-\frac{1}{T}}=\frac{k\mu}{Ts}\bigg|_{s=-\frac{1}{T}}=-k\mu $$ Si arriva ad una risposta del tipo: $$ Y(s)=\frac{r_1}{s}+\frac{r_2}{s+\frac{1}{T}}=k\mu\frac{1}{s}-k\mu\frac{1}{s+\frac{1}{T}}=k\mu\left(\frac{1}{s}-\frac{1}{s+\frac{1}{T}}\right) $$ Antitrasformando: $$ y(t)=k\mu(1(t)-e^{-\frac{t}{T}}1(t))=k\mu(1-e^{-\frac{t}{T}})1(t) $$

### STABILITÀ ESTERNA o BIBO

Un sistema si dice BIBO (Bounded-Input Nuonded-Output) stabile se la sua uscita forzzata è limitata per ogni ingresso limitato.\
Consideriamo l'uscita forzata ($x(0)=0$): $$ Y(s)=G(s)U(s) $$ Da quanto visto fino ad ora con lo sviluppo di Heaviside si può dedurre che un sistema con funzione di trasferiment $G(s)$ è BIBO stabile se e solo se tutti i poli della $G(s)$ sono a parte reale strettamente minore di zero.

#### Esempio 1
\
Data la seguente $G(s)$ si dica se il sistema descritto da essa è BIBO stabile: $$ G(s)=\frac{r}{s+p} \quad \quad \quad \quad p > 0 $$ In ingresso si ha un rapporto di polinomi: $$ U(s)=\frac{N_U(s)}{D_U(s)} $$ Quindi:
\begin{equation*}
    \begin{aligned}
        Y(s)=G(s)U(s)&=\frac{r}{s+p}\frac{N_U(s)}{D_U(s)} \\
        &=\frac{r_1}{s+p}+\frac{\alpha}{D_U(s)}
    \end{aligned}
\end{equation*}
Il primo addendo antitrasformandolo si ottiene $r_1e^{-pt}1(t) \rightarrow 0,\quad t\rightarrow 0$ e il secondo è la traformata di un segnale limitato, quindi è limitata, indi per cui il sistema è BIBO stabile.

#### Esempio 2

\
Il sistema descritto da: $$ G(s)=\frac{r}{s} \quad \quad \quad \quad u(t)=1(t) $$ è BIBO stabile?\
Trasformando la $u(t)$ si ottiene: $$ U(s)=\frac{1}{s} $$ Da cui $$ Y(s)=G(s)U(s)=\frac{r}{s^2} $$ Che antitrsformando corrisponde a $$ y(t)=rt1(t) $$ che per $t\rightarrow 0$ diverge, quindi la risposta è no, il sistema sopra descritto NON è BIBO stabile.

### ESEMPIO IMPORTANTE

**Risposta al gradino di un sistema del II ordine**\
Date le seguenti equazioni: $$ u(t)=k1(t)\Longrightarrow U(s)=\frac{k}{s} \quad \quad \quad \quad G(s)=\mu\frac{\omega _{n}^2}{s^2 +2\xi\omega _{n}s+\omega _{n}^2} $$ $$ Y(s)=G(s)U(s)=\frac{k\mu\omega _{n}^2}{s(s^2 +2\xi\omega _{n}s+\omega _{n}^2)} $$ Con poli: $$ s_{p_{1,2}}=-\xi\omega _{n}\pm j\omega_{n}\sqrt{1-\xi ^2} $$ Per trovare la risposta nel dominio del tempo come prima cosa bisogna, innanzitutto, la $Y(s)$ come: $$ Y(s)=k\mu\omega _{n}^2 \left(\frac{r_1}{s}+\frac{r_{2,1}}{s+\xi\omega _{n}+j\omega _{n}\sqrt{1-\xi ^2}}+\frac{r_{2,2}}{s+\xi\omega _{n}-j\omega _{n}\sqrt{1-\xi ^2}}\right) $$ Successivamente si trovano i residui: $$ r_1=sY(s)\bigg|_{s=0}=\frac{1}{s^2 +2\xi\omega _{n}s+\omega _{n}^2}\bigg|_{s=0}=\frac{1}{\omega _{n}^2} $$
\begin{equation*}
    \begin{aligned}
        r_{2,1}&=Y(s)\left(s+\omega _{n}\xi+j\omega _{n} \sqrt{1-\xi ^2}\right)\bigg|_{s=-\xi\omega _{n}-j\omega _{n}\sqrt{1-\xi ^2}} \\
        &=\frac{s+\omega _{n}\xi+j\omega _{n} \sqrt{1-\xi ^2}}{s\left(s+\omega _{n}\xi-j\omega _{n} \sqrt{1-\xi ^2}\right)\left(s+\omega _{n}\xi+j\omega _{n} \sqrt{1-\xi ^2}\right)}\bigg|_{s=-\xi\omega _{n}-j\omega _{n}\sqrt{1-\xi ^2}} \\
        &= \frac{1}{\left(-\xi\omega _{n}-j\omega _{n}\sqrt{1-\xi ^2}\right)\left(-\xi\omega _{n}-j\omega _{n}\sqrt{1-\xi ^2}+\omega _{n}\xi-j\omega _{n} \sqrt{1-\xi ^2}\right)} \\
        &=\frac{1}{\left(-\xi\omega _{n}-j\omega _{n}\sqrt{1-\xi ^2}\right)\left(-2j\omega _{n} \sqrt{1-\xi ^2}\right)}\quad\frac{j}{j} \\
        &= \frac{j}{\left(-\xi\omega _{n}-j\omega _{n}\sqrt{1-\xi ^2}\right)2\omega _{n} \sqrt{1-\xi ^2}}\quad\frac{\left(-\xi\omega _{n}+j\omega _{n}\sqrt{1-\xi ^2}\right)}{\left(-\xi\omega _{n}+j\omega _{n}\sqrt{1-\xi ^2}\right)} \\
        &= \frac{\left(-\xi\omega _{n}+j\omega _{n}\sqrt{1-\xi ^2}\right)j}{\left(\xi ^2 \omega _{n}^2+\omega_{n}^2\left(1-\xi ^2\right)\right)2\omega _{n} \sqrt{1-\xi ^2}} \\
        &= \frac{\omega _{n}\left(-\sqrt{1-\xi ^2}-j\xi\right)}{\omega _{n}^2 2\omega _{n}\sqrt{1-\xi ^2}} \\
        &= \frac{-\sqrt{1-\xi ^2}-j\xi}{2\omega _{n}^2\sqrt{1-\xi ^2}} = \frac{1}{2\omega _{n}^2\sqrt{1-\xi ^2}}e^{j\psi}=Me^{j\psi}
    \end{aligned}
\end{equation*}
Si arriva a $r_{2,2}$ con lo stesso procedimento ottenendo che è il complesso coniugato di $r_{2,1}$: $r_{2,2}=\bar r_{2,1}$\
Ricordando (vedi dimostrazione a pag. 23): $$ \mathcal{L} ^{-1}\left[\frac{r_{i,1}}{s+p_{i,1}}+\frac{r_{i,2}}{s+p_{i,2}}\right] = 2M_ie^{-\sigma _i t}cos(\omega _{i}t+\varphi _i)1(t) $$ Si ha:
\begin{equation*}
    \begin{aligned}
        y(t)&=k\mu\omega _{n}^2 \left(\mathcal{L}^{-1}\left[\frac{r_1}{s}\right]+\mathcal{L}^{-1}\left[\frac{r_{2,1}}{s+\xi\omega _{n}+j\omega _{n}\sqrt{1-\xi ^2}}+\frac{r_{2,2}}{s+\xi\omega _{n}-j\omega _{n}\sqrt{1-\xi ^2}}\right]\right) \\
        &=k\mu\omega _{n}^2 \left(\mathcal{L}^{-1}\left[\frac{1}{\omega _{n}s}\right]+\mathcal{L}^{-1}\left[\frac{Me^{j\psi}}{s+\xi\omega _{n}+j\omega _{n}\sqrt{1-\xi ^2}}+\frac{Me^{-j\psi}}{s+\xi\omega _{n}-j\omega _{n}\sqrt{1-\xi ^2}}\right]\right) \\
        &=k\mu\omega _{n}^2\left[\frac{1}{\omega _{n}}+2Me^{-\xi\omega _{n}t}cos\left(\omega _{n}\sqrt{1-\xi ^2}+\psi\right)\right]1(t)
    \end{aligned}
\end{equation*}
\
È utile partire da questo esempio per definire il concetto di **sovraelongazione**: il valore massimo raggiunto dalla $y(t)$ rispetto alla $y_{\infty}$.\
Da qui viene la definizione di **sovraelongazione percentuale**: $$ S\% := \frac{y_{max}-y_{\infty}}{y_{\infty}} $$ E **solo** per i sistemi del II ordine può essere anche scritta come: $$ S\% = 100e^{-\frac{\pi\xi}{\sqrt{1-\xi ^2}}} $$ Un'altra definizione importante è quella di **tempo di assestamento**: tempo $T_{a,\epsilon}$ tale che $$ (1-0.01\epsilon)y_{\infty}\le y(t)\le (1+0.01\epsilon)y_{\infty} \quad \quad \quad \forall t \ge T_{a,\epsilon} $$ Approssimazioni utili per $T_{a,\epsilon}$ sono: $T_{a,5} \approx \frac{3}{\xi\omega _{n}} \quad \quad T_{a,1} \approx \frac{4.6}{\xi\omega _{n}}$
\newpage
Inoltre:

* $\xi$ è detto _coefficiente di smorzamento_
* $\omega _{n}$ è detta _pulsazione naturale_
* $\mu$ è detto _guadagno_

Dato un valore massimo di sovraelongazione $S^*$, dalle formule precedenti, si può ricavare il valore massimo del coefficiente di smorzamento $\xi$ per i sistemi del secondo ordine: $$ S\%\le S^* \Longrightarrow \xi \ge \frac{\left|\ln\left(\frac{S^*}{100}\right)\right|}{\sqrt{\pi ^2+\ln ^2\left(\frac{S^*}{100}\right)}} $$

```{=latex}
\begin{center}
```

![Immagine rappresentativa di tutti i concetti introdotti](sistIIordParam.png){height=300px}

```{=latex}
\end{center}
```

```{=latex}
\begin{center}
```

![Mappatura dei parametri della risposta a gradino dei sistemi del secondo ordine sul piano complesso](descrParamPianoCompl.png)

```{=latex}
\end{center}
```

### Luogo di punti a tempo di assestamento costante

Si ricordi che abbiamo approssimato  $T_{a,5} \approx \frac{3}{\xi\omega _{n}} \quad T_{a,1} \approx \frac{4.6}{\xi\omega _{n}}$, inoltre si è visto che $-\xi\omega _{n}$ è la parte reale dei poli complessi coniugati. Ne consegue che sistemi con poli complessi coniugati che hanno la stessa parte reale avranno una risposta al gradino con **stesso tempo di assestamento**.\
Sul piano complesso i luoghi dei punti a tempo di assestamento costante sono rette parallele all'asse immaginario.

```{=latex}
\begin{center}
```

![Luogo dei punti a tempo di assestamento costante](luogpuntTassCost.png){height=200px}

```{=latex}
\end{center}
```

### Luogo dei punti a sovraelongazione costante

Si ricordi che per i sistemi del secondo ordine $S\%=100e^{-\frac{\pi\xi}{\sqrt{1-\xi ^2}}}$, inoltre $arcos(\xi)$ è l'angolo formato con l'asse reale sul piano complesso. Si evince, quindi, che sistemi con stesso coefficiente di smorzamento avranno una risposta al gradino con **stessa sovraelongazione**.\
Sul piano complesso i luoghi dei punti a sovraelongazione costante sono semirette uscenti dall'origine.

```{=latex}
\begin{center}
```

![Luogo dei punti a sovraelongazione costante](luogpuntScost.png){height=200px}

```{=latex}
\end{center}
```

### Mappatura di specifiche temporali nel piano complesso

Si vuole caratterizzare i sistemi del secondo ordine (con poli complessi coniugati) con $S\%\le S^*$ e, per esempio, $T_{a,5}\le T^*$. Tali specifiche sono, quindi, soddisfatte per: $\xi\ge\xi^*$ e $\xi\omega _{n} \ge\frac{3}{T^*}$. Quindi i poli complessi coniugati del sistema si devono trovare all'interno della zona colorata. 

```{=latex}
\begin{center}
```

![Mappatura specifiche temporali nel piano complesso](carattSistIIordSpecTemp.png){height=200px}

```{=latex}
\end{center}
```

### SISTEMI DEL SECONDO ORDINE CON POLI REALI

#### Caso $T_1 \ne T_2$, $T_1>T_2$

> Avendo $$ G(s)=\frac{\mu}{(1+T_1s)(1+T_2s)}\quad \quad \quad U(s)=\frac{k}{s} $$ Risulta $$ Y(s)=G(s)U(s)=\frac{k\mu}{s(1+T_1s)(1+T_2s)} $$ $$ \mu > 0, \quad k>0, \quad T_1>0, \quad T_2>0 $$ Antitrasformando si ottiene $$ y(t)=k\mu\left(1-\frac{T_1}{T_1-T_2}e^{-\frac{t}{T_1}}+\frac{T_2}{T1-T_2}e^{-\frac{t}{T_2}}\right)1(t) $$ $$ y(0)=0, \quad \dot y(t)=0, \quad \ddot y(0)=\frac{k\mu}{T_1T_2}, \quad y_{\infty}=k\mu $$ Da notare che i modi presenti sono $1(t)$ (dovuto all'ingresso), $e^{-\frac{t}{T_1}}$ e $e^{-\frac{t}{T_2}}$ (dovuti al sistema).

```{=latex}
\begin{figure}[!ht]
    \centering
    \includegraphics[width=0.3\linewidth]{sistIIordinePolR1.png}
    \includegraphics[width=0.3\linewidth]{sistIIordinePolR2.png}
    \label{Grafici corrispondenti all'esempio}
\end{figure}
```

#### Sistemi a polo dominante

Se nel precedente esempio considerassimo $T_1\gg T_2$, nella risposta $e^{-\frac{t}{T_2}}\rightarrow 0$ velocemente e $\frac{T_2}{T_1-T_2}\ll\frac{T_1}{T_1-T_2}\approx 1$, quindi $$ y(t)\approx k\mu\left(1-e^{-\frac{t}{T_1}}\right)1(t) $$

```{=latex}
\begin{center}
```

![Variazione uscita in base al polo dominante](sistIIordinePolR3.png){height=200px}

```{=latex}
\end{center}
```

#### Caso $T_1=T_2$ 

> Considerando $$ G(s)=\frac{\mu}{(1+T_1s)^2} \quad \quad \quad U(s)=\frac{k}{s} $$ Risulta $$ Y(s)=G(s)U(s)=\frac{k\mu}{s(1+T_1s)^2} $$ $$ \mu>0, \quad k>0, \quad T_1>0 $$ Antitrasformando $$ y(t)=k\mu\left(1-e^{\frac{t}{T_1}}-\frac{t}{T_1}e^{-\frac{t}{T_1}}\right)1(t) $$ Da notare che i modi presenti nel sistema sono $1(t)$ (dovuto all'ingresso), $e^{-\frac{t}{T_1}}$ e $te^{-\frac{t}{T_1}}$ (dovuti al sistema).

```{=latex}
\begin{center}
```

![Poli coincidenti](sistIIordinePolR4.png){height=100px}

```{=latex}
\end{center}
```
\newpage
A questo punto si possono trarre delle conclusioni riguardo ai sistemi del secondo ordine con poli reali: 

* la risposta è monotòna
* se $T_1\gg T_2$ polo dominante allora il comportamento è simile a quello di un sistema del prim'ordine
* $\dot y(t)=0$ quindi continuità in zero anche della derivata prima
* $T_{a,\epsilon}$ funzione non semplice di $T_1$ e $T_2$

### SISTEMI DEL PRIM'ORDINE CON UNO ZERO

> Considerando $$ \mu\frac{1+\alpha Ts}{1+Ts} \quad \quad \quad U(s)=\frac{k}{s} $$ Risulta $$ Y(s)=G(s)U(s)=k\mu\frac{1+\alpha Ts}{s(1+Ts)} $$ $$ \mu >0,\quad k>0, \quad T>0 $$ Antitrasformando l'uscita $$ y(t)=k\mu\left(1+(\alpha -1)e^{-\frac{t}{T}}\right)1(t) $$ $$ y(0)=k\mu\alpha, \quad y_{\infty}=k\mu $$ Si noti che il grado relativo è zero (grado numeratore uguale al grado del denominatore) quindi c'è collegamento algebrico ingresso-uscita ($y(0)=k\mu\alpha\ne 0$).


```{=latex}
\begin{figure}[!ht]
    \centering
    \includegraphics[width=0.3\linewidth]{sist1ordineZero1.png}
    \includegraphics[width=0.3\linewidth]{sist1ordineZero2.png}
    \label{Grafici corrispondenti all'esempio sistemi del primo ordine con uno zero}
\end{figure}
```

### SISTEMI DEL SECONDO ORDINE CON POLI REALI E ZERO

Considerando $$ G(s)=\mu\frac{1+\tau s}{(1+T_1s)(1+T_2s)} \quad \quad \quad U(s)=\frac{k}{s} $$ $$ Y(s)=G(s)U(s)=k\mu\frac{1+\tau s}{s(1+T_1s)(1+T_2s)} $$ $$ \mu>0,\quad k>0,\quad T_1 >0,\quad T_2>0 $$ Antitrasformando $$ y(t)=k\mu\left(1-\frac{T_1-\tau}{T_1-T_2}e^{-\frac{t}{T_1}}+\frac{T_2-\tau}{T_1-T_2}e^{-\frac{t}{T_2}}\right)1(t) $$ $$ y(0)=0,\quad \dot y(0)=\frac{k\mu\tau}{T_1T_2},\quad y_{\infty}=k\mu $$ Si noti che il segno della derivata $\dot y(0)=\frac{k\mu\tau}{T_1T_2}$ dipende da $\tau$.
\newpage
Da qui si distinguono 3 casi: 

#### Caso $T_1 > T_2$, $\tau < 0$, sistemi a fase NON minima

> si ha sottoelongazione ($\dot y(0)=\frac{k\mu\tau}{T_1T_2} < 0$), il sistema risponde in "senso contrario" ($<0$) rispetto all'ingresso $>0$.

```{=latex}
\begin{figure}[!ht]
    \centering
    \includegraphics[width=0.3\linewidth]{sistIIordinePolZer1.png}
    \includegraphics[width=0.3\linewidth]{sistIIordinePolZer2.png}
    \label{Grafici esempio sistemi del 2 ordine con poli reali e 1 zero tau neg}
\end{figure}
```

#### Caso $\tau >T_1>T_2>0$, sistemi a fase minima (sovraelongazione)

> è presente una sovraelongazione tanto più accentuata quanto più lo zero è vicino all'origine (ovvero al crescere di $\tau$).

```{=latex}
\begin{figure}[!ht]
    \centering
    \includegraphics[width=0.3\linewidth]{sistIIordinePolZer3.png}
    \includegraphics[width=0.3\linewidth]{sistIIordinePolZer4.png}
    \label{Grafici esempio sistemi del 2 ordine con poli reali e 1 zero tau pos}
\end{figure}
```

#### Caso $\tau\approx T_1 \gg T_2$, sistemi a fase minima (code di assestamento)

> a causa della non perfetta cancellazione polo/zero ($\tau\approx T_1$) il modo "lento" $e^{-\frac{t}{T_1}}$ è presente e il suo transitorio si esaurisce lentamente.

```{=latex}
\begin{figure}[!ht]
    \centering
    \includegraphics[width=0.3\linewidth]{sistIIordinePolZer5.png}
    \includegraphics[width=0.3\linewidth]{sistIIordinePolZer6.png}
    \label{Grafici esempio sistemi del 2 ordine con poli reali e 1 zero tau circa t1}
\end{figure}
```
\newpage

### INTERCONNESSIONE SCHEMI A BLOCCHI

#### Serie

```{=latex}
\begin{center}
```

![](InterconnessioneSerie.png){height=70px}

```{=latex}
\end{center}
```
\begin{equation*}
    \begin{aligned}
        Y(s)=G(s)U(s) \Longrightarrow Y_1(s)&=G_1(s)U_1(s) \\
        Y_2(s)&=G_2(s)U_2(s) \\
        &=G_2(s)Y_1(s)=G_2(s)G_1(s)U_1(s) \Longrightarrow G_{serie}(s)=G_1(s)G_2(s) \quad \blacksquare
    \end{aligned}
\end{equation*}

#### Parallelo

```{=latex}
\begin{center}
```

![](InterconnessionePar.png){height=100px}

```{=latex}
\end{center}
```
\begin{equation*}
    \begin{aligned}
        Y(s)&=G_1(s)U(s)+G_2(s)U(s) \\
        &=(G_1(s)+G_2(s))U(s) \Longrightarrow G_{parallelo}(s)=G_1(s)G_2(s) \quad \blacksquare
    \end{aligned}
\end{equation*}

#### Retroazione negativa

```{=latex}
\begin{center}
```

![](InterconnessioneRetroNeg.png){height=110px}

```{=latex}
\end{center}
```
\begin{equation*}
    \begin{aligned}
        Y(s)&=\left[U(s)Y_2(s)\right]G_1(s) \\
        &=\left[U(s)-Y(s)G_2(s)\right]G_1(s) \\
        &=\frac{G_1(s)}{G_2(s)G_1(s)+1}U(s) \Longrightarrow G_{retro-}(s)=\frac{G_1(s)}{1+G_1(s)G_2(s)} \quad \blacksquare
    \end{aligned}
\end{equation*}

\newpage

# RISPOSTA IN FREQUENZA

L'idea d'ora in poi sarà considerare ogni sistema come un filtro.

#### Esempio

\
Si calcoli l'uscita nel dominio del tempo del seguente sistema con il seguente ingresso $$ G(s)=\frac{\mu}{1+Ts} \quad \quad \quad \quad u(t)=Ucos(\omega t), \quad U>0 $$ Innanzitutto si trasforma la $u(t)$ (ricordando le trasformate fondamentali) $$ U(s)=\mathcal{L}[u(t)]=U\frac{s}{s^2+\omega^2} $$ Quindi l'uscita risulta $$ Y(s)=G(s)U(s)=\frac{\mu U s}{(1+Ts)(s^2+\omega ^2)}=\frac{\mu U}{T}\frac{s^2}{\left(s+\frac{1}{T}\right)(s^2+\omega ^2)} $$ Ora si scrive la $Y(s)$ come somma dei residui fratto i poli $$ Y(s)=\frac{r_1}{1+\frac{1}{T}}+\frac{r_u}{s-j\omega}+\frac{\bar r_u}{s+j\omega} \quad \quad \quad r_u=M_ue^{j\varphi _u}=|r_u|e^{jarg(r_u)} $$ Quindi la $y(t)$ risulta $$ y(t)=r_1e^{-\frac{t}{T}}1(t)+2M_ue^{-\sigma t}cos(\omega t+\varphi _u)1(t) $$ In questo esempio si ha $\sigma = 0$.\
Proseguendo $$ y(t)=r_1e^{-\frac{t}{T}}1(t)+2|r_u|cos(\omega t+arg\{r_u\})1(t) $$ Per $t\gg 0$ ($t\rightarrow \infty$): $$ y(t)\approx 2|r_u|cos(\omega t+arg\{r_u\})1(t) $$ Calcolando il residuo si arriva a $$ r_u=Y(s)(s-j\omega)\bigg|_{s=j\omega}=G(s)\frac{Us}{(s-j\omega)(s+j\omega)}(s-j\omega)\bigg|_{s=j\omega}=\frac{G(j\omega)Uj\omega}{2j\omega}=\frac{U}{2}G(j\omega) $$ Quindi la $y(t)$ risulta 
\begin{equation*}
    \begin{aligned}
        y(t)&=2\frac{|G(j\omega)|U}{2} cos(\omega t+arg\{G(j\omega)\})1(t) \\
        &=|G(j\omega)|Ucos(\omega t+arg\{G(j\omega)\})1(t)
    \end{aligned}
\end{equation*}

### RISPOSTA AD UN SEGNALE DI INGRESSO SINUSOIDALE

Dato un SLTI SISO con funzione di trasferimento $G(s)$ si vuole calcolare l'uscita in corrispondenza di un ingresso sinusoidale generico: $$ u(t)=Ucos(\omega t+\varphi) $$ Ricordando che $$ U(s)=U\frac{scos(\varphi)-\omega sin(\varphi)}{s^2+\omega ^2} $$ Quindi $$ Y(s)=G(s)U(s)=G(s)U\frac{scos(\varphi)-\omega sin(\varphi)}{s^2+\omega ^2} $$ Considerando $G(s)$ con poli distinti a parte reale negativa (BIBO stabile). Sviluppando in tratti semplici si ottiene
\begin{equation*}
    \begin{aligned}
        Y(s)&=\underbrace{\sum_{i=1}^{n}\frac{r_i}{s+p_i}}+\underbrace{\frac{r_u}{s-j\omega}+\frac{\bar r_u}{s+j\omega}} \\
        &= \quad Y_1(s) \quad + \quad \quad \ Y_2(s)
    \end{aligned}
\end{equation*}
Antitrasformando la $Y(s)$ si ha 
\begin{equation*}
    \begin{aligned}
        y(t)&=\mathcal{L}^{-1}\left[Y(s)\right] \\
        &=\underbrace{\sum_{i=1}^{n}r_ie^{-p_it}1(t)}+\underbrace{2|r_u|cos(\omega t+arg(r_u))1(t)} \\
        &= \quad \quad y_1(t) \quad \quad + \quad \quad \quad \quad \quad y_2(t)
    \end{aligned}
\end{equation*}
Poichè i poli della funzione di trasferimento sono a parte reale negativa, i contributi $e^{-p_it} sono tutti convergenti a zero. Pertanto $y_1(t)\rightarrow 0$ per $t\rightarrow \infty$.\
Mentre il residuo $r_u$ è dato da
\begin{equation*}
    \begin{aligned}
        r_u&=(s-j\omega)Y(s)\bigg|_{s=j\omega}= UG(j\omega)\frac{j\omega cos(\varphi)-\omega sin(\varphi)}{j\omega+j\omega} \\
        &= UG(j\omega)\frac{jcos(\varphi)-sin(\varphi)}{2j}=UG(j\omega)\frac{cos(\varphi)+jsin(\varphi)}{2}
    \end{aligned}
\end{equation*}
Ricordando che $e^{j\varphi}=cos(\varphi)+jsin(\varphi)$ si ha $$ r_u=UG(j\omega)\frac{e^{j\varphi}}{2}=\frac{U|G(j\omega)|}{2}e^{arg(G(j\omega))+\varphi} $$ dove si è scritto $G(j\omega)=|G(j\omega)|e^{arg(G(j\omega))}$.\
Antitrasformando $Y(s)$ si arriva a $$ y(t)=y_1(t)+U|G(j\omega)|cos(\omega t+\varphi+arg(G(j\omega))) $$ Ma si è visto che $y_1(t)\rightarrow 0$ per $t\rightarrow \infty$, quindi l'uscita $y(t)$ converge a $$ y_2(t)=U|G(j\omega)|cos(\omega t+\varphi+arg(G(j\omega))) $$ ovvero per $t$ sufficientemente grande si ha $$ y(t) \approx U|G(j\omega)|cos(\omega t+\varphi+arg(G(j\omega))) $$ Quanto trovato trova la sua generalizzazione nel seguente teorema.\
\
\
**Teorema**

> Se ad un sistema lineare tempo invariante con funzione di trasferimento $G(s)$ avente poli a parte reale negativa si applica l'ingresso sinusoidale $$ u(t)=Ucos(\omega t+\varphi) $$ l'uscita a transitorio esaurito è data da $$ y_2(t)=U|G(j\omega)|cos(\omega t+\varphi+arg(G(j\omega))) $$

### RISPOSTA A SEGNALI SVILUPPABILI IN SERIE DI FOURIER

In base a quanto visto per un ingresso sinusoidale e sfruttando il principio di sovrapposizione degli effetti per sistemi BIBO stabili si può dimostrare che per $t$ elevati $$ y(t)\approx Y_0+2\sum_{n=1}^{+\infty}|Y_n|cos\left(n\omega _0 t+arg(Y_n)\right) $$ con $$ \omega _0=\frac{2\pi}{T} \quad \quad \quad \quad Y_n=G(jn\omega _0)U_n \quad \quad n=0,1,... $$ $$ |Y_n|=|G(jn\omega _0)||U_n| \quad \quad arg\{Y_n\}=arg(U_n)+arg(G(jn\omega _0)) $$ \
_Osservazione_: $$ G(s)=\mu\frac{(1+\tau _1s)(1+\tau _2s)...}{(1+T_1s)(1+T_2s)...} $$ allora $$ G(0)=\mu $$ \
Tutto ciò può essere schematizzato come segue
```{=latex}
\begin{center}
```

![Risposta a segnali sviluppabili con Fourier](segnSvilFour1.png){height=100px}

```{=latex}
\end{center}
```
E a $t$ sufficientemente elevati anche con
```{=latex}
\begin{center}
```

![Risposta a segnali sviluppabili con Fourier a $t$ elevati](segnSvilFour2.png){height=100px}

```{=latex}
\end{center}
```
\newpage

### RISPOSTA A SEGNALI DOTATI DI TRASFORMATA DI FOURIER

Dato un segnale non periodico dotato di trasformata di Fourier, si può anche scrivere come $$ u(t)=\frac{1}{2\pi}\int_{-\infty}^{+\infty} 2|U(j\omega)|cos(\omega t+arg(U(j\omega)))d\omega $$ con $$ U(j\omega)=\int_{-\infty}^{+\infty} u(t)e^{-j\omega t}dt $$ Ovvero l'ingresso è scomponibile come un'infinità non numerabile di armoniche con valori di $\omega$ reali maggiori o uguali a $0$.\
Quindi se il sistema è BIBO stabile per $t$ elevati $$ y(t)\approx \frac{1}{2\pi}\int_{-\infty}^{+\infty} 2|Y(j\omega)| cos(\omega t+arg(Y(j\omega)))d\omega $$ con $$ Y(j\omega)=G(j\omega)U(j\omega) $$

## RISPOSTA IN FREQUENZA

La funzione complessa $G(j\omega)$ ottenuta valutando $G(s)$ in $s=j\omega$ è detta **risposta in frequenza**. Il concetto di risposta in frequenza viene esteso anche a sistemi non asintoticamente stabili.\
Per un certo valore di $\omega$, $G(j\omega)$ è un numero complesso 
```{=latex}
\begin{center}
```

![](Gjomega.png){height=130px}

```{=latex}
\end{center}
```
Nel caso in cui la risposta in frequenza non sia nota si possono sfruttare i risultati precedenti per ricavarla sperimentalmente.\
Si vedrà in seguito che dalla rappresentazione grafica di $G(j\omega)$ sarà possibile ricavare: guadagno statico, poli e zeri della funzione di trasferimento $G(s)$.\
Uno dei modi più utilizzati per rappresentare la $G(j\omega)$ sono i **diagrammi di Bode** in cui si rappresentano separatamente modulo ($|G(j\omega)|$) e fase ($arg(G(j\omega))$) in funzione di $\omega$.

### DIAGRAMMI DI BODE

Si parte dalla forma fattorizzata della funzione di trasferimento (detta forma di Bode): $$ G(s) = \mu \frac{\prod_{i}(1+\tau _{i}s) \prod_{i}(1+\frac{2\zeta _i}{\alpha _{n,i} s} + \frac{s^2}{\alpha _{ni}^2})}{s^g \prod_{i}(1+T_i s) \prod_{i} (1+\frac{2\xi _{i}}{\omega _{n,i}} s +\frac{s^2}{\omega _{n,i}^2})} $$ con risposta in frequenza associata $$ G(s) = \mu \frac{\prod_{i}(1+j\omega\tau _{i}) \prod_{i}(1+2j\zeta _i\frac{\omega}{\alpha _{n,i}} - \frac{\omega ^2}{\alpha _{n,i}^2})}{(j\omega)^g \prod_{i}(1+j\omega T_i) \prod_{i} (1+2j\xi _{i}\frac{\omega}{\omega _{ni}} -\frac{\omega ^2}{\omega _{n,i}^2})} $$
Come detto in precedenza si studiano $|G(j\omega)|$ e $arg(G(j\omega))$. \
Sull'asse delle ascisse si hanno sempre le frequenze **in scala logaritmica** di base 10 (ricorda: $\omega\ge 0$).\
Mentre sull'asse delle ordinate si ha:

* l'ampiezza in **decibel**: $|G(j\omega)|_{dB}=20 log(|G(j\omega)|)$
* nel diagramma delle fasi l'angolo: $arg(G(j\omega))$

È quindi utile ricordare che per quanto riguarda il diagramma del modulo la scala logaritmica è sia per l'asse delle ascisse che per quello delle ordinate, mentre per il diagramma della fase questa scala si usa solo per le ascisse. \
La seguente immagine riporta un esempio di diagramma di Bode.

```{=latex}
\begin{center}
```

![Esempio di diagramma di Bode della funzione: $G(j\omega)=\frac{1}{1+10j\omega}$](bode1.png){height=330px}

```{=latex}
\end{center}
```
Per la risposta in frequenza è utile studiare come risulta la funzione che restituisce $|G(j\omega)|_{dB}$ e $arg(G(j\omega))$
\begin{equation*}
    \begin{aligned}
        |G(j\omega)|_{dB} &=20log(|G(j\omega)|) \\
        &= 20\log{|\mu|} -20g\log{|j\omega|} \\
        &+\sum_{i} 20\log{|1+j\omega\tau _{i}|} + \sum_{i}20\log{\left|1+2j\zeta _{i}\frac{\omega}{\alpha _{n,i}}-\frac{\omega ^2}{\alpha _{n,i}^2}\right|} \\
        &- \sum_{i}20\log{|1+j\omega T_i|}-\sum_{i}20\log{\left|1+2j\xi _{i}\frac{\omega}{\omega _{n,i}}-\frac{\omega ^2}{\omega _{n,i}^2}\right|}\\
    \end{aligned}
\end{equation*}
\begin{equation*}
    \begin{aligned}
        \arg(G(j\omega)) &= \arg{(\mu)} -g\arg{(j\omega)} \\
        &+\sum_{i} \arg{(1+j\omega\tau _{i})} + \sum_{i}\arg{\left(1+2j\zeta _{i}\frac{\omega}{\alpha _{n,i}}-\frac{\omega ^2}{\alpha _{n,i}^2}\right)} \\
        &- \sum_{i}-\arg{(1+j\omega T_i)}-\sum_{i}\arg{\left(1+2j\xi _{i}\frac{\omega}{\omega _{n,i}}-\frac{\omega ^2}{\omega _{n,i}^2}\right)}\\
    \end{aligned}
\end{equation*}
**N.B.**: si noti che in entrambe le equazioni la prima e la terza sommatoria hanno lo stesso andamento ma con segno opposto, e stessa cosa vale per la seconda e la quarta.\
\
Si può passare, quindi, a studiare l'andamento dei contributi fondamentali per poi sommarli (grazie al principio di sovrapposizione degli effetti) per ottenere il risultato: 

* $G_a(j\omega)=\mu$ 
* $G_b(j\omega)=\frac{1}{(j\omega)^g}$ 
* $G_c(j\omega) = (1+j\omega\tau _i)$ e, per quanto visto nel nota bene, $G_c(j\omega)=\frac{1}{1+j\omega T_i}$ ha lo stesso andamento ma con segno opposto
* $G_d(j\omega)=\left(1+2j\zeta _{i}\frac{\omega}{\alpha _{n,i}}-\frac{\omega ^2}{\alpha _{n,i}^2}\right)$ e, per quanto visto nel nota bene, $G_c(j\omega)=\frac{1}{1+2j\xi _{i}\frac{\omega}{\omega _{n,i}}-\frac{\omega ^2}{\omega _{n,i}^2}}$ ha lo stesso andamento ma con segno opposto

#### Guadagno statico $\mu$

$$ G_a(j\omega)=\mu \quad \quad \quad |G_a(j\omega)|_{dB}=20\log{|\mu|} \quad \quad \quad \arg{(G(j\omega))}=\arg{(\mu)} $$ 
```{=latex}
\begin{center}
```

![](bodeMU.png){height=220px}

```{=latex}
\end{center}
```
**_Ampiezza_**: se $\mu\ge 1$ allora $20\log{|\mu|}\ge 0$ e si ha amplificazione, mentre se $\mu <1$ allora $20\log{|\mu|}<0$ e si ha attenuazione.\
**_Fase_**: se $\mu \ge 0$ allora $\arg{(\mu)}=0$, se $\mu <0$ allora $\arg{(\mu)}=-180^{\circ}$

\newpage

#### Zeri nell'origine

\
Consideriamo uno zero nell'origine ($g=-1$) $$ G_b(j\omega)=\frac{1}{(j\omega)^g}=j\omega \quad \quad \quad |G_b(j\omega)|_{dB}=20\log{(\omega)} \quad \quad \quad \arg{(G_b(j\omega))}=\arg{(j\omega)} $$ 
```{=latex}
\begin{center}
```

![](bodeZeroOrigine.PNG){height=220px}

```{=latex}
\end{center}
```
In scala logaritimica $\log{\omega}\mapsto 20\log{\omega}$ corrisponde ad una retta di pendenza $20$ dB/decade.\
Quindi se ho $g$ zeri nell'origine, la pendenza della retta sarà $20g$ dB/decade.\
$j\omega$ è un punto sul semiasse immaginario positivo $\forall\omega >0$, quindi ha fase $90^{\circ}\quad \forall\omega >0$.\
La fase sarà uguale, quindi, a $\arg{(j\omega)^g}=g90^{\circ}$.\
Sostanzialmente una funzione di trasferimento del genera è un derivatore, che amplifica le alte frequenze e quindi anche il rumore (che solitamente si trova ad alta frequenza).

#### Poli nell'origine

\
Si consideri, ora, un polo nell'origine ($g=1$) $$ G_b(j\omega)=\frac{1}{(j\omega)^g}=\frac{1}{j\omega} \quad \quad \quad |G_b(j\omega)|_dB=-20\log{(\omega)} \quad \quad \quad \arg{(G_b(j\omega))}=-\arg{(j\omega)} $$
```{=latex}
\begin{center}
```

![](bodePoloOrigine.PNG){height=220px}

```{=latex}
\end{center}
```
Sostanzialmente valgono li stessi discorsi fatti in precedenza per lo zero, ma col segno opposto.\
Quindi, in scala logaritmica $\log{\omega}\mapsto -20\log{\omega}$ corrisponde ad una retta di pendenza $-20$ dB/decade.\
Quando ho $g$ poli nell'origine la pendenza diventa $-20g$ dB/decade.\
$-j\omega$ è un punto sul semiasse immaginario positivo $\forall\omega >0$, quindi ha fase $-90^{\circ}\quad \forall\omega >0$.\
Più in generale, la fase è uguale a $\arg{(j\omega)^g}=g90^{\circ}\ \ g<0$.\
Questo tipo di funzione di trasferimento rappresenta un integratore, che attenua le alte frequenze ma introduce ritardo.\

#### Zero reale

\
Ora si consideri $G_c(j\omega)=1+j\omega\tau$ 
\begin{equation*}
    \begin{aligned}
        |G_c(j\omega)|_dB=20\log{(\sqrt{1+\omega^2\tau^2})}&\approx\begin{cases} 20\log{1}=0 \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \omega\ll\frac{1}{|\tau|} \\ 20\log{\omega |\tau|}=20\log{(\omega)}+20\log{|\tau|} \quad \ \omega\gg\frac{1}{|\tau|} \end{cases} \\
        &\approx \begin{cases} 20\log{1}=0 \quad \quad \quad \quad \quad \ \omega\ll\frac{1}{|\tau|} \\ 20\log{(\omega)}-20\log{\frac{1}{|\tau|}} \quad \ \omega\gg\frac{1}{|\tau|} \end{cases}
    \end{aligned}
\end{equation*}
$$ \left|G_d(j\omega)\bigg|_{\omega=\frac{1}{|\tau|}}\right|=\left|G\left(j\frac{1}{|\tau|}\right)\right|=\left|1+j\frac{1}{|\tau|}\tau\right|=|1\pm j|=\sqrt{2} $$
$$ \left|G_d\left(j\frac{1}{|\tau|}\right)\right|_{dB}=20\log{\sqrt{2}}=10\log{2}\approx 3\textrm{ dB} $$ In verde è rappresentato il grafico asintotico (approssimazione).\
In blu vi è rappresentato il diagramma reale.
```{=latex}
\begin{center}
```

![](bodeZeroReale.PNG){height=220px}

```{=latex}
\end{center}
```
Il riferimento per l'approssimazione è 1 decade, quindi: $$ \omega\ll\frac{1}{|\tau|}\Longrightarrow\omega <\frac{1}{|\tau|}\cdot~10^{-1} $$ $$ \omega\gg\frac{1}{|\tau|}\Longrightarrow\omega >\frac{1}{|\tau|}\cdot~10^{1} $$ Fino alla **_pulsazione di taglio_** $\omega=\frac{1}{|\tau|}$ l'andamento dell'approssimazione è costante a $0$ dB. \
Sempre in riferimento alla pulsazione di taglio $\omega=\frac{1}{|\tau|}$ entra in gioco la retta $\log{\omega}\mapsto -20\log{\frac{1}{|\tau|}}+20\log{\omega}$ con pendenza $20$ dB/dec.\
Per quanto riguarda. invece, il grafico reale ha un discostamento massimo proprio alla pulsazione di taglio $\omega=\frac{1}{|\tau|}$, tale scostamento vale proprio $3$ dB (come visto in precedenza).
\newpage
Per la fase, invece, considerando uno zero reale negativo ($\tau >0$):
\begin{equation*}
    \begin{aligned}
        \arg{\left(G_c(j\omega)\right)}=\arg{(1+j\omega\tau)}\approx \begin{cases} 0 \quad \quad \ \omega\ll\frac{1}{|\tau|} \\ 90^{\circ} \quad \ \omega\gg\frac{1}{|\tau|} \end{cases}
    \end{aligned}
\end{equation*}
```{=latex}
\begin{center}
```

![Fase di uno zero reale negativo $\tau >0$](bodeZeroRealeFase1.PNG){height=220px}

```{=latex}
\end{center}
```
Se, invece, si prende in considerazione uno zero positivo ($\tau <0$) si ha:
\begin{equation*}
    \begin{aligned}
        \arg{\left(G_c(j\omega)\right)}=\arg{(1+j\omega\tau)}\approx \begin{cases} 0 \quad \quad \ \ \ \omega\ll\frac{1}{|\tau|} \\ -90^{\circ} \quad \ \omega\gg\frac{1}{|\tau|} \end{cases}
    \end{aligned}
\end{equation*}
```{=latex}
\begin{center}
```

![Fase di uno zero reale positivo $\tau >0$](bodeZeroRealeFase2.PNG){height=220px}

```{=latex}
\end{center}
```
Come si evince da entrambe le immagini, il cambio di fase inizia circa una decade prima ($\frac{1}{5}\cdot~\frac{1}{|\tau|}$) e finisce circa una decade dopo ($5\cdot~\frac{1}{|\tau|}$) la pulsazione di taglio $\omega=\frac{1}{|\tau|}$.

#### Polo reale

\
Considerando $G_c(j\omega)=\frac{1}{1+j\omega T}$ (polo reale): $$ |G_c(j\omega)|_{dB}=-20\log{\sqrt{1+\omega^2T^2}} \quad \quad \quad \arg{(G_c(j\omega))}=-\arg{(1+j\omega T)} $$
```{=latex}
\begin{center}
```

![](bodePoloReale.PNG){height=220px}

```{=latex}
\end{center}
```
A destra il diagramma di Bode di un polo reale negativo ($T>0$), mentre a sinistra di un polo reale positivo ($T<0$).\
Il diagramma è ottenuto da quello dello zero ribaltando rispetto all'asse reale: fino alla pulsazione di taglio ha sempre andamento costante a $0$ dB, dopo $\omega=\frac{1}{|T|}$ si ha la retta $\log{\omega}\mapsto 20\log{\frac{1}{|T|}}-20\log{\omega}$ di pendenza $-20$ dB/dec.\
Anche lo scostamento massimo è uguale ma di segno opposto rispetto a quello dello zero: $$ |G_c(j\omega)|_{dB}=-20\log{\sqrt{1+1}}=-20\log{\sqrt{2}}\approx -3 \textrm{ dB} $$ Il cambio di fase inizia circa una decade prima e finisce circa una decade dopo la pulsazione di taglio $\omega =\frac{1}{|T|}$

#### Zeri complessi coniugati

\
Considerando $G_d(j\omega)=1+2j\zeta\frac{\omega}{\alpha _n}-\frac{\omega ^2}{\alpha _n^2}$ (coppia di zeri complessi coniugati): $$ |G_d(j\omega)|_{dB}=20\log{\sqrt{(1-\frac{\omega ^2}{\alpha _n^2})^2+4\zeta ^2\frac{\omega ^2}{\alpha _n^2}}}\approx \begin{cases} 20\log{(1)}=0 \quad \quad \quad \quad \quad \quad \quad \quad \quad \ \  \omega \ll \alpha _n \\ 20\log{\frac{\omega ^2}{\alpha _n^2}}=-40\log{\alpha _n}+40\log{\omega} \quad \omega \gg \alpha _n \end{cases} $$
```{=latex}
\begin{center}
```

![](bodeZeriCC.PNG){height=220px}

```{=latex}
\end{center}
```
Fino alla pulsazione di taglio $\omega =\alpha _n$ l'andamento è costante a $0$ dB. \
A partire dalla pulsazione di taglio ($\omega =\alpha _n$) si passa ad una retta $\log{\omega}\mapsto -40\log{\alpha _n}+40\log{\omega}$ di pendenza $40$ dB/dec.\
Si ha uno scostamento significativo nella zona tratteggiata del grafico che dipende dal valore di $\zeta$.
```{=latex}
\begin{center}
```

![](bodeZeriCCZeta.PNG){height=220px}

```{=latex}
\end{center}
```
Quello in blu rappresenta $\zeta = 0.01$ e così a salire. Al crescere di $\zeta$ il discostamento diminuisce.\
Se ideale, questo tipo di rappresentazione ha un nome: filtro di Notch, che, sempre a livello ideale, elimina solo una frequenza detta $\omega _r =\alpha _n\sqrt{1-2\zeta ^2}$.\
A tale pulsazione, $\omega _r =\alpha _n\sqrt{1-2\zeta ^2}$, $|G_d(j\omega _r)|_{dB}=2|\zeta|\sqrt{1-\zeta ^2}$.\
\
Per quanto riguarda la fase invece di zeri c.c. a parte reale negativa ($\zeta >0$) $$ \arg{(G_d(j\omega))} \approx \begin{cases} 0 \quad \quad \omega \ll \alpha _n \\ 180^{\circ} \ \ \omega \gg \alpha _n \end{cases} $$ 
```{=latex}
\begin{center}
```

![Zeri c.c. a parte reale negativa ($\zeta >0$)](bodeZeriCCFase1.PNG){height=220px}

```{=latex}
\end{center}
```
Invece per zeri c.c. a parte reale positiva ($\zeta <0$): $$ \arg{(G_d(j\omega))} \approx \begin{cases} 0 \quad \quad \quad \omega \ll \alpha _n \\ -180^{\circ} \ \ \omega \gg \alpha _n \end{cases} $$ In entrambi i casi il cambio di fase dipende in modo significativo dal valore di $\zeta$.
```{=latex}
\begin{center}
```

![Zeri c.c. a parte reale positiva ($\zeta <0$)](bodeZeriCCFase2.PNG){height=220px}

```{=latex}
\end{center}
```
$$ \omega _a = \frac{\alpha _n}{5^{\zeta}} \quad \quad \quad \omega _b = 5^{\zeta}\alpha _n $$ 
Questo tipo di effetto si chiama: effetto bloccante degli zeri.\
Esempio: 

> $$ \zeta =0 $$ $$ G(s)=\mu\frac{1+\frac{s^2}{\alpha _n^2}}{(1+T_1s)(1+T_2s)}=\frac{\mu}{\alpha _n^2T_1T_2}\frac{s^2+\alpha _n^2}{(s+\frac{1}{T_1})(s+\frac{1}{T_2})} \quad \quad T_{1,2} > 0 $$ Sistema a zeri puramente immaginari $$ u(t)=U\cos{(\alpha _nt)}1(t) \Longrightarrow U(s)=U\cdot\frac{s}{s^2+\alpha _n^2} $$ $$ Y(s)=G(s)U(s)=U\frac{\mu}{\alpha _n^2T_1T_2}\frac{s}{(s+\frac{1}{T_1})(s+\frac{1}{T_2})} = \frac{r_1}{s+\frac{1}{T_1}} + \frac{r_2}{s+\frac{1}{T_2}} $$ Che nel dominio del tempo corrisponde a $$ y(t)=r_1e^{-\frac{t}{T_1}}1(t)+r_2e^{-\frac{t}{T_2}}1(t) $$ La cosa da osservare è che dato un coseno in ingresso, non ci sono coseni in uscita.
\newpage 

#### Poli complessi coniugati

\
Considerando $|G_d(j\omega)|_{dB}=\frac{1}{1+2j\xi\frac{\omega}{\omega _n}+\frac{\omega ^2}{\omega _n^2}}$ con $\xi >0$ (coppia di poli c.c. a parte reale negativa)
```{=latex}
\begin{center}
```

![](bodePoliCCXiPos.PNG){height=220px}

```{=latex}
\end{center}
```
Si ha un picco di risonanza alla pulsazione di risonanza $\omega _r = \omega _n\sqrt{1-2\xi^2}$ con $|G_d(j\omega _r)|=\frac{1}{2|\xi|\sqrt{1-\xi^2}}$, conseguentemente alla frequenza $\omega _n$ si ha $|G_d(j\omega _n)|=\frac{1}{s|\xi|}$.\
\
Per quanto riguarda i poli c.c. con parte reale positiva ($\xi <0$)
```{=latex}
\begin{center}
```

![](bodePoliCCXiNeg.PNG){height=220px}

```{=latex}
\end{center}
```
Si noti che il grafico è ottenuto dal ribaltamento rispetto all'asse reale del diagramma visto per gli zeri (il caso $\xi <0$ corrisponde al caso $\zeta <0$).\
$\xi$ è detto coefficiente di smorzamento, in più d'ora in poi si approssimerà $$ \omega _r\approx\omega _n \Longrightarrow |G_d(\omega _n)|=\frac{1}{|\xi|} $$

#### Ritardo temporale

\
Considerando una $G(s)=e^{-\tau s}$ e quindi $G(j\omega)=e^{-j\omega\tau}$ si ha $$ |G(j\omega)|_{dB}=20\log{|1e^{-j\omega\tau}|}=20\log{1}=0 $$ $$ \arg{(G(j\omega))}=\arg{(e^{-j\omega\tau})}=-\omega\tau $$ 
\newpage
Che in termini di diagrammi di Bode si traduce in 
```{=latex}
\begin{center}
```

![](bodeRitardoTemp.PNG){height=220px}

```{=latex}
\end{center}
```

### PROPRIETÀ BLOCCANTE DEGLI ZERI

Si supponga di avere $G(s)=\mu\frac{s^2+\alpha _n^2}{(1+T_1s)(1+T_2s)}$, con $T_1,T_2 >0$ (asintoticamente stabile). Si calcoli l'uscita del sistema all'ingresso $u(t)=U\cos{(\omega _uT)}$ che ha trasformata $U(s)=U\frac{s}{s^2+\omega _u^2}$. Si distinguono 2 casi

#### Caso $\omega _u \ne \alpha _n$

\
La trasformata dell'uscita sarà $$ Y(s)=U\mu\frac{s(s^2+\alpha _n^2)}{(1+T_1s)(1+T_2s)(s^2+\omega _u^2)} $$ In base al denominatore i modi presenti nell'uscita sono: 

* $e^{-\frac{t}{T_1}}$, dovuto al termine $1+T_1s$
* $e^{-\frac{t}{T_2}}$, dovuto al termine $1+T_2s$
* $|G(j\omega _u)|U\cos{(\omega _ut+\arg{(G(j\omega _u))})}$, dovuto al termine $s^2+\omega _u^2$

#### Caso $\omega _u =\alpha _n$

\
La trasformata dell'uscita sarà $$ Y(s)=U\mu\frac{s(s^2+\alpha _n^2)}{(1+T_1s)(1+T_2s)(s^2+\omega _u^2)}=U\mu\frac{s}{(1+T_1s)(1+T_2s)} $$ In base al denominatore, i modi presenti nell'uscita saranno:

* $e^{-\frac{t}{T_1}}$, dovuto al termine $1+T_1s$
* $e^{-\frac{t}{T_2}}$, dovuto al termine $1+T_2s$

Pertanto, in questo caso l'uscita **non presenta** i modi corrispondenti agli zeri del sistema.

### RISONANZA

Si supponga di avere un sistema con poli immaginari coniugati $\pm j\omega$, ovvero $G(s)=\mu\frac{\omega _n^2}{s^2+\omega _n^2}$.\
Si è visto che il diagramma di bode ha un picco di risonanza infinito alla pulsazione $\omega _n$.\
Ma cosa significa?\
Per capirlo si calcola l'uscita del sistema in corrispondeza dell'ingresso $u(t)=U\cos{(\omega _nt)}$ che ha trasformata $U(s)=U\frac{s^2}{s^2+\omega _n^2}$. Quindi l'uscita è $$ Y(s)=G(s)U(s)=\mu\frac{U\omega _n^2 s}{(s^2+\omega _n^2)^2}=\frac{r_1}{s-j\omega _n}+\frac{\bar r_1}{s+j\omega _n}+\frac{r_2}{(s-j\omega _n)^2}+\frac{\bar r_2}{(s+j\omega _n)^2} $$ A causa dei termini al quadrato a denominatore avremo un'uscita del tipo $$ y(t)=A_1t\cos{(\omega _nt+\varphi _1)}+A_2\cos{(\omega _nt+\varphi _2)} $$ il cui valore assoluto tende ad infinito per $t\rightarrow\infty$.\
Conseguentemente si tornerebbe ad un grafico dell'uscita nel tempo simile a quello per i modi naturali di poli a parte reale positiva.\
Nella realtà non esistono sistemi con $\xi=0$ ma per valori molto piccoli del coefficiente di smorzamento il picco di risonanza può essere considerato infinito.

### AZIONE FILTRANTE DEI SISTEMI DINAMICI

Quanto visto fin'ora mostra che un sistema dinaminco si comporta come un filtro per l'ingresso "modellandolo" per produrre l'uscita.
```{=latex}
\begin{center}
```

![](filtri1.PNG){height=220px}

```{=latex}
\end{center}
```
```{=latex}
\begin{center}
```

![](filtri2.PNG){height=220px}

```{=latex}
\end{center}
```

# SISTEMI DI CONTROLLO: STABILITÀ e PRESTAZIONI

Si consideri il seguente sistema in retroazione
```{=latex}
\begin{center}
```

![](retroazione.PNG){height=400px}

```{=latex}
\end{center}
```
L'obiettivo è garantire che l'uscita $y(t)$ segua il riferimento $w(t)$ in presenza di:

* disturbi non misurabili in uscita $d(t)$ e disturbi di misura $n(t)$
* incertezze sul modello $G(s)$ del sistema fisico (impianto) considerato

soddisfacendo opportune specifiche di prestazione.\
A questo scopo si definisce la **funzione d'anello** $$ L(s)=R(s)G(s) $$ $$ \textrm{(funzione di trasferimento in anello aperto)} $$ Lo schema precedente cattura anche strutture più complesse che includono attuatori e trasduttori
```{=latex}
\begin{center}
```

![](retroazioneComplicata.PNG){height=400px}

```{=latex}
\end{center}
```
**N.B.**: il riferimento $w$ viene filtrato con una replica della dinamica del sensore $T(s)$ in modo che sia "compatibile" con la dinamica dell'uscita $y$ retroazionata.
\newpage
Usando le proprietà degli schemi a blocchi interconnessi si può riscrivere lo schema precedente come
```{=latex}
\begin{center}
```

![](retroazioneComplicata2.PNG){height=300px}

```{=latex}
\end{center}
```
Riferendo in maniera opportuna i vari blocchi, lo schema semplificato cattura anche lo schema generale:
```{=latex}
\begin{center}
```

![](retroazioneMenoComplicata.PNG){height=250px}

```{=latex}
\end{center}
```
Sistemi:

* $R(s)=T(s)\tilde R(s)$
* $G(s)=A(s)\tilde G(s)$

Segnali:

* $W(s)=\tilde W(s)$
* $N(s)=T^{-1}(s)\tilde N(s)$
* $D(s)=D_a(s)\tilde G(s)+D_u(s)$

**N.B.** il disturbo sull'attuatore $d_a(t)$ viene filtrato dal sistema. Bisogna tenerne conto quando si fanno considerazioni sul disturbo in uscita $d(t)$.
\newpage
Nelle applicazioni di carattere ingegneristico tipicamente le bande dei segnali di ingresso $w(t)$, $d(t) e $n(t)$ sono limitate in opportuni range
```{=latex}
\begin{center}
```

![](bandaSegnali.PNG){height=200px}

```{=latex}
\end{center}
```

* $w(t)$ e $d(t)$ hanno bande a "basse frequenze" (e.g. posizioni, rotazioni, velocità, etc. di sistemi meccanici)
* $n(t)$ hanno bande ad "alte frequenze" (e.g. disturbi termici in componenti elettronici, accoppiamenti con cambi elettromagretici etc.)

#### Stabilità nominale

\
Requisito fondamentale è l'asintotica stabilità o stabilità BIBO (esterna) se solo rappresentazione ingresso-uscita.

#### Stabilità robusta

\
La stabilità dev'essere garantita anche in situazioni perturbate (errori di modello o incertezze nei parametri).

#### Prestazioni statiche

\
Prestazioni a transitorio esaurito ($t\rightarrow\infty$): tipicamente $e(t)$ limitato o nullo a fronte di ingressi $w$, $d$, $n$ con determinate caratteristiche. Ad esempio:

* errore in risposta ad un ingresso a gradino (transizione ad un nuovo riferimento o disturbi costanti su attuatori/sensori) o rampa
* risposta ad un ingresso sinusoidale ad alte frequenze (disturbi con certe componenti frequenziali)

#### Prestazioni dinamiche

\
Prestazioni del sistema in transitorio relative a:

* risposta ad un riferimento $w$, date in termini di tempo di assestamento $T_{\alpha,\epsilon}$ e sovraelongazione $S\%$ massimi
* risposta a disturbi $d$ ed $n$, date in termini di attenuazione in certi range di frequenze (bande di frequenza dei disturbi)
* moderazione della variabile di controllo $u$, date in termini di contenimento dell'ampiezza (per evitare la saturazione degli attuatori, uscita dal range in cui la linearizzazione è valida, costi eccessivi)

```{=latex}
\begin{center}
```

![](prestazioni.PNG){height=200px}

```{=latex}
\end{center}
```

## STABILITÀ ROBUSTA DEL SISTEMA RETROAZIONATO

Poichè la stabilità di un sistema lineare non dipende dagli ingressi, si consideri il seguente schema a blocchi
```{=latex}
\begin{center}
```

![](sistemaRetroazionato.PNG){height=200px}

```{=latex}
\end{center}
```
Per studiare la stabilità robusta (in presenza di incertezze) del sistema retroazionato si enuncerà un risultato fondamentale: il **criterio di bode** che lega la stabilità del sistema retroazionato a quella del sistema in anello aperto.\
Prima di introdurre tale teorema è necessario introdurre un altro paio di concetti.

### MARGINE DI FASE E AMPIEZZA

Con $\omega _c$ detta pulsazione critica.

#### Margine di fase:

$M_f=180^{\circ}+\arg{(L(j\omega))}$ con $\omega _c$ tale che $|L(j\omega)|_{dB}=0$\
**N.B.** $M_f=\arg{(L(j\omega))}-(-180^{\circ})=180^{\circ}+\arg{(L(j\omega))}$

#### Margine di ampiezza:

$M_a=-|L(j\omega _{\pi})|_{dB}$ con $\omega _{\pi}$ tale che $\arg{(L(j\omega _{\pi}))}=-180^{\circ}$

```{=latex}
\begin{center}
```

![](margineFaseAmpiezza.PNG){height=200px}

```{=latex}
\end{center}
```
Si possono riscontrare alcuni casi in cui $M_f$ e $M_a$ non sono definiti o non sono informativi:

* _Intersezioni multiple_: il diagramma delle ampiezze $|L(j\omega)|_{dB}$ interseca l'asse a $0$ dB più di una volta
* _Assenza di intersezioni_: il diagramma delle ampiezze $|L(j\omega)|_{dB}$ non attraversa l'asse a $0$ dB
* _Segni discordi_: margini di fase e ampiezza $M_f$ e $M_a$ hanno segno discorde (per essere informativi $M_f$ ed $M_a$ devono avere lo stesso segno)

### CRITERIO DI BODE

**Teorema**

> Si supponga che:\
\ \ \ \ 1. $L(s)$ non abbia poli a parte reale (strettamente positiva) \
\ \ \ \ 2. il diagramma di Bode del modulo di $L(j\omega)$ attraversi una sola volta l'asse a $0$ dB\
Allora condizione necessaria e sufficiente perchè il sistema retroazionato sia asintoticamente stabile è che risulti $\mu >0$ (con $\mu$ guadagno statico di $L(j\omega)$) e $M_f >0$

Si osservino le seguenti:

* la stabilità del sistema in retroazione è determinata dalla lettura di un solo punto sul diagramma di Bode di $L(j\omega)$
* $M_f$ e $M_a$ in genere vanno considerati simultaneamente e forniscono una misura della robustezza rispetto ad incertezze su $L(s)$.

#### Robustezza rispetto a ritardi temporali

\
Un sistema che ritarda di $\tau$ ha funzione di trasferimento $G(s)=e^{-s\tau}$.\
Il diagramma di Bode delle ampiezze di un ritardo è costante a $0$ dB.\
Lo sfasamento è $\arg{G(j\omega)}=-\omega\tau$ che nel diagramma di Bode delle fasi, in scala semi-logaritmica, ha un andamento di tipo esponenziale.\
A questo punto ci sono un paio di osservazioni da fare:

* se $L(s)=e^{-s\tau}\tilde L(s)$ la pulsazione critica $\omega _c$ non cambia, ovvero quella di $L(s)$ è la stessa di $\tilde L(s)$
* un ritardo riduce quindi il margine di fase in quanto per $\omega=\omega _c$ riduce la fase, ovvero $$ \arg{(L(j\omega _c))} = \arg{(\tilde L(j\omega _c))} -\tau\omega _c $$ Quindi il massimo ritardo tollerabile $\tau _{\textrm{max}}$ deve soddisfare $$ \tau _{\textrm{max}} < \frac{M_f}{\omega _c} $$ 

Considerando il sistema $\tilde L(s)=\frac{1}{s(s+1)(s+10)}$\
Tale sistema con un ritardo di $\tau$ sarà $L(s)=e^{-s\tau}\tilde L(s)$ 
```{=latex}
\begin{center}
```

![](ritardiTemporali.PNG){height=250px}

```{=latex}
\end{center}
```

#### Robustezza rispetto ad incertezze sul guadagno

\
Il margine di ampiezza $M_a$ rappresenta la massima incertezza tollerabile sul guadagno statico $\mu$.\
È importante notare che variazioni di $\mu$ determinano solo traslazioni del diagramma delle ampiezze e non alterano il diagramma delle fasi.\
Ecco alcuni esempi:
```{=latex}
\begin{center}
```

![](incertezzeGuadagno.PNG){height=250px}

```{=latex}
\end{center}
```

## FUNZIONI DI SENSITIVITÀ

```{=latex}
\begin{center}
```

![](retroazione.PNG){height=150px}

```{=latex}
\end{center}
```
Ingressi:

* $w(t)$ riferimento (andamento desiderato per la $y(t)$)
* $d(t)$ disturbo in uscita
* $n(t)$ disturbo di misura

Uscite di interesse:

* $e(t)=w(t)-y(t)$ errore di inseguimento
* $y(t)$ uscita controllata
* $u(t)$ ingresso di controllo del sistema in anello aperto (impianto)

Le **funzioni di sensitività** sono funzioni di trasferimento tra ingressi ed uscite di interesse.\
$$ S(s)=\frac{1}{1+R(s)G(s)} \quad \quad \textbf{Funzione di sensitività} $$ 
$$ F(s)=\frac{R(s)G(s)}{1+R(s)G(s)} \quad \quad \textbf{Funzione di sensitività complementare} $$
$$ Q(s)=\frac{R(s)}{1+R(s)G(s)} \quad \quad \textbf{Funzione di sensitività del controllo} $$
Le relazioni che le legano ad ingressi ed uscite sono:
$$ \left[ {\begin{array}{c} Y(s)\\ U(s)\\ E(s)\\ \end{array} } \right] = \left[ {\begin{array}{ccc} F(s) & S(s) & -F(s)\\ Q(s) & -Q(s) & -Q(s)\\ S(s) & -S(s) & F(s)\\ \end{array} } \right]\left[ {\begin{array}{c} W(s)\\ D(s)\\ N(s)\\ \end{array} } \right] $$

```{=latex}
\begin{center}
```

![](funzioniSensitivita.PNG){height=150px}

```{=latex}
\end{center}
```
La funzione di sensitività $S(s)$ descrive, sostanzialmente, quanto l'uscita è sensibile ai disturbi quindi la si vuole "nulla" (la più piccola possibile).\
La $F(s)$ è detta funzione di sensitività complementare perchè: $S(s)+F(s)=1$.\
Il denominatore di tutte le funzioni di sensitività e lo stesso. Si ricordi che la stabilità e
determinata dai poli della funzione di trasferimento. Questo è consistente con il fatto che la stabilità del sistema (retroazionato) non dipende dal particolare ingresso considerato.
Dalle definizioni e dallo schema tramite sovrapposizione degli effetti $$ Y(s)=Y_w(s)+Y_d(s)+Y_n(s) $$ 
con

* $Y_w(s)$ uscita con ingresso $W(s)$ e ponendo $D(s)=0$ e $N(s)=0$
* $Y_d(s)$ uscita con ingresso $D(s)$ e ponendo $W(s)=0$ e $N(s)=0$
* $Y_n(s)$ uscita con ingresso $N(s)$ e ponendo $D(s)=0$ e $W(s)=0$

E allo stesso modo si possono definire $$ E(s)=E_w(s)+E_d(s)+E_n(s) $$ $$ U(s)=U_w(s)+U_d(s)+U_n(s) $$
È interessante notare, quindi che se avessi $S(s)=0$ (per complementarietà) allora $F(s)=1$, ma ciò vorrebbe dire $$ Y_n(s)=-F(s)N(s)\ne 0 $$ quindi mi ritroverei disturbo in uscita, quindi non si può annullare completamente $S(s)$. Quanto descritto è un motivo in più per passare a lavorare sempre nel dominio di $\omega$.\
Sostanzialmente l'obiettivo è arrivare ad avere:

* $|S(j\omega)|\approx 0$ per $\omega$ basse
* $|F(j\omega)|\approx 1$ per $\omega$ basse
* $|F(j\omega)|\approx 0$ per $\omega$ alte

perchè $d(t)$ ed $w(t)$ sono a basse $\omega$ mentre $n(t)$ è ad alte $\omega$. Per ottenre ciò è necessario progettare $R(j\omega)$ in modo tale che:

* $|L(s)| \gg 1$ per $\omega$ basse
* $|L(s)| \ll 1$ per $\omega$ alte

Quindi, facendo tale scelta di design, le approssimazioni che si possono fare sono:

* Ricordando che $F(j\omega)=\frac{L(j\omega)}{1+L(j\omega)}$ e che per $\omega=\omega _c$, $|L(j\omega _c)|_{dB}\Longrightarrow |L(j\omega _c)|=0$ si può approssimare $$ |F(j\omega)|\approx \begin{cases} 1 \quad \quad \quad \quad \omega\ll\omega _c \\ |L(j\omega)| \quad \ \omega\gg\omega _c \end{cases} \quad \quad \Longrightarrow \quad \quad |F(j\omega)|_{dB}\approx\begin{cases} 0 \textrm{ dB} \quad \quad \quad \quad \omega\ll\omega _c \\ |L(j\omega)|_{dB} \quad \quad \omega\gg\omega _c \end{cases} $$
* Ricordando $S(j\omega)=\frac{1}{1+L(j\omega)}$, si può approssimare $$ |S(j\omega)|\approx\begin{cases} \frac{1}{|L(j\omega)|} \quad \quad \omega\ll\omega _c \\ 1 \quad \quad \quad \quad \ \omega\gg\omega _c \end{cases} \quad \quad \Longrightarrow \quad \quad |S(j\omega)|_{dB}\approx\begin{cases} -|L(j\omega)|_{dB} \quad \ \ \omega\ll\omega _c \\ 0 \textrm{ dB} \quad \quad \quad \quad \ \ \omega\gg\omega _c \end{cases} $$

È utile, a questo punto, effettuare un'analisi in frequenza delle funzioni di sensitività.

#### Funzione di sensitività complementare

```{=latex}
\begin{center}
```

![](sensitivitaComplementare.PNG){height=300px}

```{=latex}
\end{center}
```

#### Funzione di sensitività

```{=latex}
\begin{center}
```

![](sensitivita.PNG){height=300px}

```{=latex}
\end{center}
```

#### Funzione di sensitività di controllo

A basse frequenze il modulo di $Q(j\omega)$ dipende da $G(j\omega)$, quindi non possiamo influenzarlo con il regolatore. Occore, inoltre, evitare valori di $\omega _c$ "troppo elevati". La parte fondamentale è progettare regolatori che attenuino a frequenze alte.

```{=latex}
\begin{center}
```

![](sensitivitaControllo.PNG){height=200px}

```{=latex}
\end{center}
```

### POLI COMPLESSI CONIUGATI DI $F(s)$ E MARGINE DI FASE

La funzione di sensitività può presentare una coppia di poli complessi coniugati dominanti, quindi l'obiettivo, ora, è mettere in relazione il picco di risonanza di $F(j\omega)$ con lo smorzamento $\xi$ associato, assumendo che $\omega _n\approx\omega _c$ $$ F(j\omega)=\frac{1}{1+2j\frac{\xi}{\omega _n}\omega-\frac{\omega^2}{\omega _n^2}} $$ La risposta al gradino di tale funzione di sensitività è la classica risposta al gradino vista nel capitoli precedenti.

```{=latex}
\begin{center}
```

![](rispostaGradSistIIOrdine.PNG){height=200px}

```{=latex}
\end{center}
```
Si ha un picco di risonanzadi $F(j\omega)$ per $\omega\approx\omega _c$ ($\omega _c$ pulsazione critica tale che $|L(j\omega _c)|=1\Rightarrow |L(j\omega)|_{dB}=0 \textrm{ dB}$).\
Si ricorda inoltre che si assume $$ \omega _c\approx\omega _n\approx\omega _r $$ $\omega _c$ pulsazione critica\
$\omega _n$ pulsazione naturale dei poli c.c.\
$\omega _r$ pulsazione di risonanza.\
Inoltre si ricorda l'approssimazione $$ |F(j\omega) _c|\approx |F(j\omega _n)|=\frac{1}{2\xi} $$ Però dalla definizione di funzione di sensitività $$ |F(j\omega _c)|=\frac{|L(j\omega _c)|}{|1+L(j\omega _c)|}=\frac{1}{|1+e^{j\arg{(L(j\omega _c))}}|} $$ Si pone $\arg{(L(j\omega _c))}=\varphi _c$\
Quindi si ha 
\begin{equation*}
    \begin{aligned}
        |F(j\omega _c)|=\frac{1}{|1+e^{j\arg{(L(j\omega _c))}}|}&=\frac{1}{\sqrt{(1+\cos{(\varphi _c)})^2+\sin^2(\varphi _c)}} \\
        &=\frac{1}{\sqrt{1+2\cos{(\varphi _c)}+\cos^2(\varphi _c)+\sin^2(\varphi _c)}}=\frac{1}{\sqrt{2(1+\cos{(\varphi _c)})}}
    \end{aligned}
\end{equation*}
Ricordando $$ \cos{(\varphi _c)}=-\cos{(\pi+\varphi _c)} $$ $$ M_f=180^{\circ}+\arg{(L(j\omega _c))} $$ $$ M_f^{\textrm{rad}}=\pi+\varphi _c $$ Quindi si arriva ad avere $$ |F(j\omega _c)|=\frac{1}{\sqrt{2(1+\cos{(\varphi _c)})}}=\frac{1}{\sqrt{2\left(1-\cos{\left(M_f^{\textrm{rad}}\right)}\right)}} $$ Grazie alla seguente regola trigonometrica $$ 1-\cos{(x)}=2\sin^2\left(\frac{x}{2}\right) $$ Si può scrivere $$ |F(j\omega _c)|=\frac{1}{\sqrt{2\left(1-\cos{\left(M_f^{\textrm{rad}}\right)}\right)}}=\frac{1}{\sqrt{4\sin^2\left(\frac{M_f^{\textrm{rad}}}{2}\right)}}=\frac{1}{2\sin{\left(\frac{M_f^{\textrm{rad}}}{2}\right)}} $$ A questo punto si possono uguagliare le due forme di $|F(j\omega _c)|$: $$ \frac{1}{2\xi}=\frac{1}{2\sin{\left(\frac{M_f^{\textrm{rad}}}{2}\right)}} $$ Conseguentemente si può scrivere $$ \xi=\sin{\left(\frac{M_f^{\textrm{rad}}}{2}\right)}\approx\frac{M_f^{\textrm{rad}}}{2}=\frac{M_f}{2}\frac{\pi}{180}\approx\frac{M_f}{100} $$ Quindi, riassumendo $$ \xi\approx\frac{M_f}{100} $$

### ANALISI STATICA

#### Errore a regime ad un gradino

\
Sia $e_{\infty}=\lim_{t\to\infty}e(t)$ con $e(t)=w(t)-y(t)$ errore in risposta ad un gradino $w(t)=W1(t)$.\
Utilizzando il teorema del valore finale (sistema in anello chiuso asintoticamente stabile, BIBO stabile) $$ e_{\infty}=\lim_{s\to 0}sE(s)=\lim_{s\to 0}sS(s)W(s)=\lim_{s\to 0}sS(s)\frac{W}{s}=W\lim_{s\to 0}S(s)=W\lim_{s\to 0}\frac{1}{1+L(s)} $$ Sia $L(s)=\mu\frac{N_L(s)}{D_L(s)}=\mu\frac{N_L(s)}{s^gD_L'(s)}$ con $N_L(0)=1$ e $D_L'(0)=1$ abbiamo $$ \lim_{s\to 0}S(s)=\lim_{s\to 0}\frac{D_L(s)}{\mu N_L(s)+D_L(s)}=\lim_{s\to 0}\frac{s^gD_L'(s)}{\mu N_L(s)+s^gD_L'(s)}=\lim_{s\to 0}\frac{s^g}{\mu+s^g} $$ Quindi, si ha $$ e_{\infty}=W\lim_{s\to 0}\frac{s^g}{\mu+s^g}=\begin{cases} \frac{W}{1+\mu} \quad \quad g=0 \\ 0 \quad \quad \quad g>0 \end{cases} $$

#### Errore a ingressi $\frac{W}{s^k}$

\
Sia $e_{\infty}=\lim_{t\to\infty}e(t)$ con $e(t)=w(t)-y(t)$ errore in risposta ad un segnale di trasformata $W(s)=\frac{W}{s^k}$ $$ e_{\infty}=\lim_{s\to 0}sS(s)\frac{W}{s^k}=W\lim_{s\to 0}\frac{s^{g-(k-1)}}{\mu+s^g}=\begin{cases} \infty \quad \  g<k-1 \\ \frac{W}{\mu} \quad \ g=k-1 \\ 0 \quad \quad g>k+1\ \ [g\ge k] \end{cases} $$ 
Quindi

* se $g<k-1$ l'errore a regime diverge
* se $g=k-1$ l'errore a regime è finito e diminuisce all'aumentare di $\mu$
* se $g>k-1$ l'errore a regime è nullo

**N.B.** il sistema in anello chiuso deve esere asintoticamente stabile.\
**N.B.** affinchè l'errore a regime a $W(s)=\frac{W}{s^k}$ sia nullo occorre che $L(s)$ abbia un numero di poli almeno pari a $k$ (pricipio del modello interno)\
\
**_Osservazione_**: 

> $L(s)=R(s)G(s)$\
Se $g>0$ c'è almeno un polo nell'orgine\
Se $R(s)$ o $G(s)$ hanno almeno un polo nell'origine non c'è bisogno di introdurlo conil regolatore

Perchè se ho un polo nell'origine l'errore è nullo?

> Perchè se voglio un $\frac{1}{s}$ in uscita ed $e(t)=0$ (idealmente) ho un anello spezzato, quindi, anche con ingresso nullo il sistema deve essere comunque in grado di produrre un $\frac{1}{s}$ in uscita.

#### Principio del modello interno

Il risultato precedentemente trovato può essere generalizzato come segue:\
Affinchè un segnale di riferimento (risposta ad un disturbo di misura) con una componente spettrale alla frequenza $\omega _0$ sia inseguito (risposta al neutralizzato) a regime perfettamente in uscita è necessario e sufficiente che:

1. il sistema chiuso in retroazione sia asintoticamente stabile
2. il guadagno d'anello $L(s)$ abbia una coppia di poli complessi coniugati sull'asse immaginario con pulsazione naturale pari a $\omega _0$

```{=latex}
\begin{center}
```

![](principioModInterno.PNG){height=150px}

```{=latex}
\end{center}
```

# SISTEMI DI CONTROLLO: PROGETTO DEL REGOLATORE

```{=latex}
\begin{center}
```

![](retroazioneConDipendezeTempo.PNG){height=200px}

```{=latex}
\end{center}
```
L'obiettivo, ora, è progettare $R(s)$ in modo che $y(t)$ sia "più vicina possibile" a $w(t)$

## RIEPILOGO SPECIFICHE

#### Stabilità robusta

rispetto a incertezze.\
\
Stabilità in presenza di errori di modello o incertezze di parametri, ad esempio: massimo ritardo temporale $\tau _{\textrm{max}}$ o massima incertezza sul guadagno statico $\Delta\mu _{\textrm{max}}$

#### Precisione statica

\
Sia $e_{\infty}=\lim_{t\to\infty}e(t)$ il valore a regime dell'errore in risposta a riferimenti $w(t)$ o disturbi in uscita $d(t)$ "canonici" (gradino $w(t)=W1(t)$, $d(t)=D1(t)$, o rampa $w(t)=t1(t)$, $d(t)=t1(t)$).\
\
Specifica: $|e_{\infty}|\le e^{\star}$ oppure $e_{\infty}=0$

#### Precisione dinamica

\
Tipicamente specifiche in termini di sovraelongazione e tempo di assestamento massimi:\
\
Specifiche: $S\%\le S^{\star}$ e $T_{\alpha,\epsilon}\le T^{\star}$

#### Attenuazione disturbo in uscita $d(t)$

\
Il disturbo in uscita $d(t)$, con banda limitata in un range di pulsazioni $[\omega _{d,\textrm{min}},\omega _{d,\textrm{max}}]$, deve essere attenuato di $A_d$ dB ($A_d>0$).

#### Attenuazione disturbo di misura $n(t)$

\
Il disturbo di misura $n(t)$, con banda limitata in un range di pulsazioni $[\omega _{n,\textrm{min}},\omega _{n,\textrm{max}}]$, deve essere attenuato di $A_n$ dB ($A_n>0$).\
\
**N.B.** in applicazioni ingegneristiche in genere $\omega _{d,\textrm{max}}\ll\omega _{n,\textrm{min}}$

#### Moderazione variabile di controllo $u(t)$

\
Contenimento dell'ampiezza della variabile di controllo $u$ in ingresso al sistema fisico (impianto).

#### Fisica realizzabilità del regolatore $R(s)$

\
Il regolatore dev'essere un sistema proprio, quindi il grado relativo (differeza poli-zeri) deve essere maggiore o uguale a zero (grado del denominatore maggiore o uguale al grado del numeratore).\
\
\
\
Esempio: attenuazione di $d(t)$ di $A_d=40$ dB\

> $$ A_d=40 \textrm{ dB} \quad A_d=20\log{\bar A_d} \Rightarrow \bar A_d=10^{\frac{40}{20}}=10^2 $$ $$ d(t)=D\sin{(\omega t)} \longrightarrow y_d(t)=Y_d\sin{(\omega t+\varphi)} \quad \quad \textrm{con } Y_d\le\frac{D}{\bar A_d}=\frac{D}{10^2} $$

## SPECIFICHE IN TERMINI DI GUADAGNO D'ANELLO

### STABILITÀ ROBUSTA

Stabilità robusta rispetto alle incertezze significa stabilità in presenza di errori di modello o incertezze di parametri, ad esempio: massimo ritardo temporale $\tau _{\textrm{max}}$ o massima incertezza sul guadagno statico $\Delta\mu _{\textrm{max}}$\
\
**Specifica su $L(j\omega)$**: $M_f\ge M_f^{\star}$

### PRECISTIONE STATICA

Per soddisfare tali specifiche va considerata l'analisi statica effettuata sulla funzione di sensitività $S(s)$.\
\
Un **esempio di specifica** è: 

> $|e_{\infty}|\le e^{\star}$ in risposta a un gradino $w(t)=W1(t)$, $d(t)=D1(t)$ con $W\le W^{\star}$ e $|D|\le D^{\star}$.\
Quindi $$ e_{\infty}=\frac{W}{1+\mu}+\frac{D}{1+\mu}=\frac{D+W}{1+\mu}\approx\frac{D+W}{\mu} $$ e per rispettare la specifica si necessita, quindi, di $$ \mu=L(0)\ge\frac{D^{\star}+W^{\star}}{e^{\star}} $$

Un altro **esempio di specifica** può essere:

> $e_{\infty}=0$ in risposta a $W(s)=\frac{W}{s^k}$ e/o $D(s)=\frac{D}{s^k}$ quindi $L(s)$ deve avere $k$ poli nell'origine.

Mettendo insieme i precedenti due esempi si ha un qualcosa del tipo:

> se $|e_{\infty}|\le e^{\star}$ in risposta a $W(s)=\frac{W}{s^k}$ e/o $D(s)=\frac{D}{s^k}$ allora $k-1$ poli in $L(s)$ e $\mu\ge\frac{D^{\star}+W^{\star}}{e^{\star}}$.

**N.B.** notare che la specifiche sono sulla $L(s)$ quindi se per esempio avessi $G(s)=\frac{1}{s(s+2)}$ e avessi la specifica di errore a regime nullo in risposta al gradino $w(t)=W1(t)$, il regolatore non necessiterebbe di poli nell'origine in quanto è già presente il polo necessario in $G(s)$.\
\
**N.B.** se $e_{\infty}=0$ in risposta ad un disturbo sull'attuatore $D_a(s)=\frac{D_a}{s^k}$ allora $D(s)=D_a(s)G(s)$ ed $E(s)=S(s)G(s)D_a(s)$ quindi $$ \textrm{IMPORTANTE} $$ $$ k\textrm{ poli nell'origine in } R(s) $$ 

### PRECISIONE DINAMICA

**Specifiche**: $S\%\le S^{\star}$ e $T_{\alpha,\epsilon}\le T^{\star}$.\
\
Se si progettasse $L(j\omega)$ in modo che $F(j\omega)$ abbia una coppia di poli complessi coniugati dominanti in $\omega _n\approx \omega _c$ con coefficiente di smorzamento $\xi$ allora $$ \xi\approx\frac{M_f}{100} $$ Perchè $S\%\le S^{\star}$ allora $$ \xi\ge\xi^{\star}=\frac{\left|\ln{\left(\frac{S^{\star}}{100}\right)}\right|}{\sqrt{\pi ^2+\ln^2\left(\frac{S^{\star}}{100}\right)}} $$ con $$ S^{\star}=\frac{-\pi\xi^{\star}}{\sqrt{1-(\xi^{\star})^2}} $$ e quindi $$ M_f\ge M_f^{\star}=100\xi^{\star} $$ Perchè $T_{a,1}\le T^{\star}$ allora $\xi\omega _n\ge\frac{4.6}{T^{\star}}$ e quindi $$ M_f\omega _c\ge\frac{460}{T^{\star}} $$ Volendo mettere insieme le due specifiche: $$ M_f^{\star}\omega _c\ge\frac{460}{T^{\star}} \Longrightarrow \omega _c\ge\frac{460}{M_f^{\star}T^{\star}}=\omega _c^{\star} $$ $$ \omega _c^{\star}=\omega _{c,\textrm{min}} $$ **N.B.** $L(j\omega)$ può attraversare $0$ dB solo una volta.
```{=latex}
\begin{center}
```

![](precisioneDinamica.PNG){height=230px}

```{=latex}
\end{center}
```

### ATTENUAZIONE DISTURBO IN USCITA $d(t)$

Il disturbo in uscita $d(t)$, con una banda limitata in un range di pulsazioni $[\omega _{d,\textrm{min}},\omega _{d,\textrm{max}}]$ (solitamente $\omega _{d,\textrm{min}}$ presa uguale a 0), dev'essere attenuato di $A_d$ dB ($A_d>0$).\
\
Si ricordi che se $d(t)=D\cos{(\omega t+\varphi)}$ allora $$ Y_D(s)=S(s)D(s)\Longrightarrow y(t)=|S(j\omega)|D\cos{(\omega t+\varphi+\arg{(S(j\omega))})} $$ e che $$ |S(j\omega)|_{\textrm{dB}}\approx\begin{cases} -|L(j\omega)|_{\textrm{dB}} \quad \omega\le\omega _c \\ 0 \quad \quad \quad \quad \quad \ \ \omega>\omega _c \end{cases} $$ Da specifica vogliamo $|S(j\omega)|_{\textrm{dB}}\le -A_d$ dB. Poichè $\omega _{d,\textrm{max}}\ll\omega _c$, si ha $$ |L(j\omega)|_{\textrm{dB}}\ge A_d\textrm{ dB} $$ Ad esempio se $d(t)$ dev'essere attenuato di $20$ dB allora $|L(j\omega)|_{\textrm{dB}}\ge 20\textrm{ dB}$
```{=latex}
\begin{center}
```

![](disturboUscita.PNG){height=200px}

```{=latex}
\end{center}
```

### ATTENUAZIONE DISTURBO DI MISURA $n(t)$

Il disturbo di misura $n(t)$, con banda limitata in un range di pulsazioni $[\omega _{n,\textrm{min}},\omega _{n,\textrm{max}}]$ ($\omega _{n,\textrm{max}}$ spesso considerata $+\infty$), deve essere attenuato di $A_n$ dB ($A_n>0$).\
\
Ricordando che se $n(t)=N\cos{(\omega t+\varphi)}$ allora $$ Y_N(s)=-F(s)N(s)\Longrightarrow y(t)=|F(j\omega)|N\cos{(\omega t+\varphi-\arg{(F(j\omega))})} $$ e che $$ |F(j\omega)|_{\textrm{dB}}\approx\begin{cases} 0 \quad \quad \quad \quad \quad \quad \omega\le\omega _c \\ |L(j\omega)|_{\textrm{dB}} \quad \quad \ \omega>\omega _c \end{cases} $$ Da specifica si vuole $|F(j\omega)|_{\textrm{dB}}\le -A_n$ dB. Poichè $\omega _{c,\textrm{min}}\gg\omega _c$ si ha $$ |L(j\omega)|_{\textrm{dB}}\le -A_n\textrm{ dB} $$ Ad esempio se $n(t)$ dev'essere attenuato di $20$ dB allora $|L(j\omega)|_{\textrm{dB}}\le -20$ dB.\
**N.B.** se non ho specifiche particolari su $\omega _{c,\textrm{max}}$ sostanzialmente si prende $\omega _{c,\textrm{max}}=\omega _{n,\textrm{min}}$.
```{=latex}
\begin{center}
```

![](disturboMisura.PNG){height=200px}

```{=latex}
\end{center}
```

### MODERAZIONE DELLA VARIABILE DI CONTROLLO $u(t)$

Contenimento dell'ampiezza della variabile di controllo $u$ in ingresso al sistema fisico (impianto).\
Ricordiamo che se $w(t)=W\cos{(\omega t+\varphi)}$ allora $$ U(s)=Q(s)U(s)\Longrightarrow u(t)=|Q(j\omega)|W\cos{(\omega t+\varphi+\arg{(Q(j\omega))})} $$ e che $$ |Q(j\omega)|_{\textrm{dB}}\approx\begin{cases} -|G(j\omega)|_{\textrm{dB}}  \quad \quad \omega\le\omega _c \\ |R(j\omega)|_{\textrm{dB}} \quad \quad \quad \omega>\omega _c \end{cases} $$ Poichè si vuole contenere $|Q(j\omega)|_{\textrm{dB}}$ e non abbiamo controllo su $G(j\omega)$ si deve:

* limitare $\omega _c$
* realizzare $R(j\omega)$ passa-basso

```{=latex}
\begin{center}
```

![](moderazioneControllo.PNG){height=230px}

```{=latex}
\end{center}
```
**N.B.** il limite superiore su $\omega _c$ può essere determinato dalle specifiche sulla variabile di controllo, in caso contrario si prende $\omega _{c,\textrm{max}}=\omega _{n,\textrm{min}}$.

### FISICA REALIZZABILITÀ DEL REGOLATORE $R(s)$

Il regolatore dev'essere un sistema proprio, quindi il grado relativo (differeza poli-zeri) deve essere maggiore o uguale a zero (grado del denominatore maggiore o uguale al grado del numeratore).\
A pulsazioni elevate la pendenza $-k_L$ dB/dec di $|L(j\omega)|_{\textrm{dB}}$ è determinata dalla differenza tra poli (ciascuno contribuisce con pendenza $-20$ dB/dec) e zeri (ciascuno contribuisce con pendenza $20$ dB/dec). Se a pulsazioni elevate $|G(j\omega)|_{\textrm{dB}}$ ha pendenza $-k_G$ dB/dec allora $$ -k_L\le-k_G $$ In parole povere se $$ R(s)=\frac{N(s)}{D(s)} $$ perchè il regolatore sia fisicamente realizzabile si deve avere $$ \textrm{grado di }D(s)\ge\textrm{grado di }N(s) $$
```{=latex}
\begin{center}
```

![](fisicaRealizzabilita.PNG){height=150px}

```{=latex}
\end{center}
```

### RIEPILOGO

Avendo $$ L(j\omega)=R(j\omega)G(j\omega) \quad \quad G(j\omega)\textrm{ data} $$
```{=latex}
\begin{center}
```

![](specificheGuadagnoAnello.PNG)

```{=latex}
\end{center}
```
\newpage

## SINTESI DEL REGOLATORE

### SINTESI PER TENTATVI O "LOOP SHAPING"

Consiste nel dare forma alla $L(j\omega)$ in modo che:

* il diagramma della ampiezze non attraversi le "regioni proibite" in bassa e alta frequenza
* per $\omega=\omega _c$ rispetti il vincolo sul margine di fase

procedendo per tentativi basati su opportune considerazioni.

### STRUTTURA

È conveniente dividere il progetto in 2 fasi fattorizzando $R(s)$ come $$ R(s)=R_s(s)R_d(s) $$

#### Regolatore statico

$$ R_s(s)=\frac{\mu _s}{s^k} $$ progettato per soddisfare precisione statica e attenuazione dei disturbi $d$.

#### Regolatore dinamico

$$ R_d(s)=\mu _d\frac{\prod_{i}(1+\tau _{i}s) \prod_{i}(1+\frac{2\zeta _i}{\alpha _{ni}}s + \frac{s^2}{\alpha _{ni}^2})}{s^g \prod_{i}(1+T_i s) \prod_{i} (1+\frac{2\xi _{i}}{\omega _{ni}} s +\frac{s^2}{\omega _{ni}^2})} $$ progettato per soddisfare stabilità robusta, precisione dinamica, attenuazione disturbi $n$, moderazione del controllo e fisica realizzabilità.\
\
**N.B.** $\mu _d$ può essere scelto **solo se** $\mu _s$ non è stato imposto.\
\
**N.B.** posso inserire $\frac{1}{s}$ per avere $e_{\infty}=0$ anche se la specifica è $e_{\infty}<e_{\textrm{max}}$ ma introduco uno sfasamento di $-90^{\circ}$.

### SINTESI DEL REGOLATORE STATICO

Il guadagno $\mu _s$ e il numero di poli nell'origine in $R_s(s)$ dipende dalla specifica sull'errore a regime $e_{\infty}$ in risposta a segnali canonici.\
Ad esempio: $|e_{\infty}|\le e^{\star}$ in risposta al gradino su $w$ e $d$, con $G(s)$ senza poli nell'origine.\
Progetto: si può scegliere $$ R(s)=\mu _s\ge\mu ^{\star} $$ oppure $$ R(s)=\frac{\mu _s}{s} $$ Nel secondo caso possiamo scegliere $\mu _s$ "liberamente" purchè consenta di rispettare i vincoli dell'attenuazione di $d$.

### SINTESI DEL REGOLATORE DINAMICO 

La progettazione di $R_d(s)$ mira a 

1. imporre $\omega _c$ in un certo intervallo
2. garantire un dato margine di fase $M_f$ (ovvero garantire che $\arg{L(j\omega _c)}\ge-180+M_f$, vedi criterio di Bode)
3. garantire una certa attenuazione e pendenza di $L(j\omega)$ (e $R(j\omega)$) a pulsazioni elevate

**N.B.** Per soddisfare il terzo punto basta introdurre poli del regolatore ad alte frequenze.\
\
Si procederà individuando dei possibili scenari in base al diagramma di $$ G_e(s)=R_s(s)G(s) $$ detto **sistema esteso**.

### SINTESI DEL REGOLATORE DINAMICO: SCENARIO A

Supponiamo scenario A come uno scenario in cui nell'intervallo ("centrale") di pulsazioni ammissibili per la pulsazione di attraversamento $\omega _c$ esiste un sotto-intervallo in cui la fase di $G_e(j\omega)$ rispetta il vincolo sul margine di fase.
```{=latex}
\begin{center}
```

![](scenarioA.PNG){height=300px}

```{=latex}
\end{center}
```
Gli obiettivi da raggiungere sono:

* attenuare (selettivamente) il diagramma delle ampiezze (traslarlo in basso) in modo che $\omega _c$ ricada nel sotto-intervallo in cui il vincolo sul margine di fase è rispettato
* alterare il meno possibile la fase

Le possibili azioni sono:

1. Se $\mu _d$ libero, allora scegliere $R_d(s)=\mu _d$ con $\mu _d<1$
2. Se $\mu _d$ bloccato (vincolato dalla scelta di $\mu _s$), allora attenuare mediante l'inserimento di poli e zeri in $R_d(s)$ 

#### $\mu _d$ LIBERO

```{=latex}
\begin{center}
```

![](scenarioAMuLibero.PNG){height=250px}

```{=latex}
\end{center}
```

#### $\mu_d$ VINCOLATO

\
Per attenuare solo nel range di pulsazioni selezionato si progetta una **_rete ritardatrice_** $$ R_d(s)=\frac{1+\alpha\tau s}{1+\tau s}\quad\quad 0<\alpha<1 $$ $$ s_p=-\frac{1}{\tau}\quad\quad s_z=-\frac{1}{\alpha\tau} $$

```{=latex}
\begin{center}
```

![](reteRitardatrice.PNG){height=230px}

```{=latex}
\end{center}
```
```{=latex}
\begin{center}
```

![](effettoReteRitardatrice.PNG){height=230px}

```{=latex}
\end{center}
```
```{=latex}
\begin{center}
```

![](bodeRitardatrice.PNG){height=270px}

```{=latex}
\end{center}
```
Per trovare $\omega ^{\star}$ si procede nel seguente modo 
\begin{equation*}
    \begin{aligned}
        \log{\left(\omega ^{\star}\right)}&=\frac{1}{2}\left[\log{\left(\frac{1}{\tau}\right)}+\log{\left(\frac{1}{\alpha\tau}\right)}\right] \\
        &=\frac{1}{2}\log{\left(\frac{1}{\tau}\frac{1}{\alpha\tau}\right)} \\
        &=\log{\left(\frac{1}{\alpha\tau ^2}\right)^{\frac{1}{2}}} \\
        &=\log{\frac{1}{\tau\sqrt{\alpha}}} \\
        &\Longrightarrow \omega ^{\star}=\frac{1}{\tau\sqrt{\alpha}}
    \end{aligned}
\end{equation*}
L'obiettivo è, quindi, calcolare $\alpha$ e $\tau$ in modo che $L(j\omega)$ abbia una pulsazione di attraversamento $\omega _c^{\star}$ e valga $\arg{(L(j\omega _c^{\star}))}\approx\arg{(G_e(j\omega _c^{\star}))}$.\
Si procederà:

* scegliendo $\alpha$ tale che $20\log{\alpha}\approx -|G_e(j\omega _c^{\star})|_{\textrm{dB}}$ 
* scegliendo $\tau$ tale che $\frac{1}{\alpha\tau}\le\frac{\omega _c^{\star}}{10}$

Quindi si avrà 
\begin{equation*}
    \begin{aligned}
        |R_d(j\omega _c^{\star})G_e(j\omega _c^{\star})|_{\textrm{dB}}&=0 \\
        20\log{|R_d(j\omega _c^{\star})|}+20\log{|G_e(j\omega _c^{\star})|}&=0 \\
        20\log{|R_d(j\omega _c^{\star})|}&=-20\log{|G_e(j\omega _c^{\star})|}
    \end{aligned}
\end{equation*}
Supponendo $|R_d(j\omega _c^{\star})|_{\textrm{dB}}\approx 20\log{\alpha}$ si avrà $$ 20\log{\alpha}=-|G_e(j\omega _c^{\star})|_{\textrm{dB}}\Longrightarrow\alpha=10^{-\frac{|G_e(j\omega _c^{\star})|_{\textrm{dB}}}{20}} $$

#### Rete ritardatrice: formule di inversione

\
Obiettivo 1: calcolare $\alpha$ e $\tau$ in modo che alla pulsazione $\omega _c^{\star}$ la rete ritardatrice abbia un'attenuazione di $0<M^{\star}<1$ e uno sfasamento $-\frac{\pi}{2}<\varphi ^{\star}<0$, ovvero $$ R_d(j\omega _c^{\star})=\frac{1+j\alpha\tau\omega _c^{\star}}{1+j\tau\omega _c^{\star}}=M^{\star}e^{j\varphi ^{\star}} $$ $$ M^{\star}=|R_d(j\omega _c^{\star})| \quad\quad \varphi ^{\star}=\arg{(R_d(j\omega _c^{\star}))} $$ Si pone $$ \frac{1+j\alpha\tau\omega _c^{\star}}{1+j\tau\omega _c^{\star}}=M^{\star}\left(\cos{(\varphi ^{\star})}+j\sin{(\varphi ^{\star})}\right) $$
\begin{equation*}
    \begin{aligned}
        1+j\alpha\tau\omega _c^{\star}&=M^{\star}\left(\cos{(\varphi ^{\star})}+j\sin{(\varphi ^{\star})}\right)(1+j\tau\omega _c^{\star}) \\
        &=M^{\star}\left[\cos{(\varphi ^{\star})}+j\tau\omega _c^{\star}\cos{(\varphi ^{\star})}+j\sin{(\varphi ^{\star})}-\tau\omega _c^{\star}\sin{(\varphi ^{\star})}\right] \\
        &=M^{\star}\left[\cos{(\varphi ^{\star})}-\tau\omega _c^{\star}\sin{(\varphi ^{\star})}+j\left(\tau\omega _c^{\star}\cos{(\varphi ^{\star})}+\sin{(\varphi ^{\star})}\right)\right]
    \end{aligned}
\end{equation*}
Uguagliando parte reale ed immaginaria si ottiene
\begin{equation*}
    \begin{aligned}
        1&=M^{\star}\cos{(\varphi ^{\star})}-M^{\star}\tau\omega _c^{\star}\sin{(\varphi ^{\star})} \\
        \alpha\tau\omega_c^{\star}&=M^{\star}\tau\omega _c^{\star}\cos{(\varphi ^{\star})}+M^{\star}\sin{(\varphi ^{\star})}
    \end{aligned}
\end{equation*}
Quindi le formule di inversione sono:
\begin{equation*}
    \begin{aligned}
        \tau&=\frac{\cos{(\varphi ^{\star})}-\frac{1}{M^{\star}}}{\omega_c^{\star}\sin{(\varphi ^{\star})}} \\
        \alpha\tau&=\frac{M^{\star}-\cos{(\varphi ^{\star})}}{\omega_c^{\star}\sin{(\varphi ^{\star})}}
    \end{aligned}
\end{equation*}
Si noti che per avere $\alpha >0$ occorre $M^{\star}<\cos{(\varphi ^{\star})}$.\
\
Obiettivo 2: imporre $|L(j\omega)|_{\textrm{dB}}=0$ per $\omega=\omega _c^{\star}$.\
Si procede: 

1. scegliendo $\omega _c^{\star}$ e ricavare $M_f^{\star}$ dalle specifiche
2. calcolare $M^{\star}$ e $\varphi ^{\star}$ imponendo $$ |G_e(j\omega _c^{\star})|_{\textrm{dB}}-20\log{M^{\star}} $$ $$ M_f^{\star}=180^{\circ}+\arg{(G_e(j\omega _c^{\star}))}+\varphi^{\star} $$ Ottenendo $M^{\star}$ dalla prima (o da quanto visto in precedenza): $$ M^{\star}=10^{-\frac{|G_e(j\omega _c^{\star})|_{\textrm{dB}}}{20}} $$ E per il margine di fase:  $$: $$
\begin{equation*}
    \begin{aligned}
        M_f^{\star}&=180^{\circ}+\arg{(L(j\omega _c^{\star}))} \\
        M_f^{\star}&=180^{\circ}+\arg{(G_e(j\omega _c^{\star}))}+\arg{(R_d(j\omega _c^{\star}))} \\
        M_f^{\star}&=180^{\circ}+\arg{(G_e(j\omega _c^{\star}))}+\varphi^{\star} \\
        \varphi^{\star}&=M_f^{\star}-180^{\circ}-\arg{(G_e(j\omega _c^{\star}))}
    \end{aligned}
\end{equation*}
3. si verifica che $0<M^{\star}<1$, $-\frac{\pi}{2}<\varphi ^{\star}<0$ e $M^{\star}<\cos{(\varphi ^{\star})}$
4. si calcolano $\alpha$ e $\tau$ tramite le formule inverse viste nel paragrafo precedente.

### SINTESI DEL REGOLATORE DINAMICO: SCENARIO B

Si suppone, invece, scenario B la situazione in cui nell'intervallo ("centrale") di pulsazioni ammissibili per la pulsazione di attraversamento $\omega _c$ NON esistono pulsazioni in cui la fase di $G_e(j\omega)$ rispetti il vincolo sul margine di fase.
```{=latex}
\begin{center}
```

![](scenarioB.PNG){height=300px}

```{=latex}
\end{center}
```
Gli obiettivi da raggiungere sono: 

* modificare il diagramma delle fasi (aumentare la fase) nell'intervallo in modo che il vincolo sul margine di fase sia rispettato
* amplificare il meno possibile l'ampiezza

Le possibili azioni da compiere sono:

1. aggiungere uno o più zeri (a pulsazioni precedenti quella di attraversamento desiderata) per aumentare la fase
2. aggiungere uno o più poli a pulsazioni più alte per la fisica realizzabilità e per evitare una
eccessiva amplificazione

Aggiungendo 1 solo zero si avrebbe
```{=latex}
\begin{center}
```

![](scenarioB1Zero.PNG){height=200px}

```{=latex}
\end{center}
```
Aggiungendone 2 invece
```{=latex}
\begin{center}
```

![](scenarioB2Zeri.PNG){height=200px}

```{=latex}
\end{center}
```
**N.B.** il massimo incremento di fase dato da uno zero è $90^{\circ}$ per $\omega\to\infty$ quindi il guadagno di fase per uno zero è $<90$.\
\
Tenendo conto dell'aggiunta di uno o più poli si può progettare $R_d(s)$ come segue.

#### Rete anticipatrice

$$ R_d(s)=\frac{1+\tau s}{1+\alpha\tau s} \quad \quad 0<\alpha<1 $$ Nel caso in cui si necessiti di un anticipo maggiore di fase (ad esempio 2 zeri): $$ R_d(s)=\frac{1+\tau _1 s}{1+\alpha _1\tau _1s}\frac{1+\tau _2 s}{1+\alpha _2\tau _2s} \quad \quad 0<\alpha _1<1, 0<\alpha _2<1 $$ $$ s_z=-\frac{1}{\tau} \quad\quad s_p=-\frac{1}{\alpha\tau} $$ 
\
\
Una volta realizzata la rete anticipatrice (singola o multipla) si possono verificare 2 casi:

* **_B1_**: $\omega _c$ è nell'intervallo di specifica e il vincolo sul margine di fase è rispettato. In questo caso il progetto è terminato
* **_B2_**: $\omega _c$ è fuori dall'intervallo di specifica o in un intervallo in cui il vincolo di margine di fase non è rispettato.\
In ogni caso ci si è ricondotti ad uno scenario A (esiste un sotto-intervallo in cui il vincolo sul margine di fase è rispettato).

#### Caso B2

* Se $\mu _d$ libero allora scegliamo $\mu _d<1$ per attenuare $$ R_d(s)=\mu _d\frac{1+\tau _b s}{1+\alpha _b\tau _b s} $$
* Se $\mu _d$ bloccato $$ R_d(s)=\frac{1+\alpha _a\tau _a s}{1+\tau _a s}\frac{1+\tau _b s}{1+\alpha _b\tau _b s} $$

#### Rete ritardo-anticipo

$$ R_d(s)=\frac{1+\alpha _a\tau _a s}{1+\tau _a s}\frac{1+\tau _b s}{1+\alpha _b\tau _b s} $$ 

* Rete anticipatrice: polo e zero a più alte frequenze
* Rete ritardatrice: polo e zero a più basse frequenze

```{=latex}
\begin{center}
```

![](reteRitardoAnticipo.PNG){height=250px}

```{=latex}
\end{center}
```

#### Rete anticipatrice: diagramma di Bode

```{=latex}
\begin{center}
```

![](reteAnticipatrice.PNG){height=270px}

```{=latex}
\end{center}
```

#### Rete anticipatrice: formule di inversione

\
Obiettivo 1: calcolare $\alpha$ e $\tau$ in modo che alla pulsazione $\omega _c^{\star}$ la rete ritardatrice abbia un'attenuazione di $M^{\star}>1$ e uno sfasamento $0<\varphi ^{\star}<\frac{\pi}{2}$, ovvero $$ R_d(j\omega _c^{\star})=\frac{1+j\tau\omega _c^{\star}}{1+j\alpha\tau\omega _c^{\star}}=M^{\star}e^{j\varphi ^{\star}} $$ $$ M^{\star}=|R_d(j\omega _c^{\star})| \quad\quad \varphi ^{\star}=\arg{(R_d(j\omega _c^{\star}))} $$ Si pone $$ \frac{1+j\tau\omega _c^{\star}}{1+j\alpha\tau\omega _c^{\star}}=M^{\star}\left(\cos{(\varphi ^{\star})}+j\sin{(\varphi ^{\star})}\right) $$
\begin{equation*}
    \begin{aligned}
        1+j\tau\omega _c^{\star}&=M^{\star}\left(\cos{(\varphi ^{\star})}+j\sin{(\varphi ^{\star})}\right)(1+j\alpha\tau\omega _c^{\star}) \\
        &=M^{\star}\left[\cos{(\varphi ^{\star})}+j\alpha\tau\omega _c^{\star}\cos{(\varphi ^{\star})}+j\sin{(\varphi ^{\star})}-\alpha\tau\omega _c^{\star}\sin{(\varphi ^{\star})}\right] \\
        &=M^{\star}\left[\cos{(\varphi ^{\star})}-\alpha\tau\omega _c^{\star}\sin{(\varphi ^{\star})}+j\left(\alpha\tau\omega _c^{\star}\cos{(\varphi ^{\star})}+\sin{(\varphi ^{\star})}\right)\right]
    \end{aligned}
\end{equation*}
Uguagliando parte reale ed immaginaria si ottiene
\begin{equation*}
    \begin{aligned}
        1&=M^{\star}\cos{(\varphi ^{\star})}-M^{\star}\alpha\tau\omega _c^{\star}\sin{(\varphi ^{\star})} \\
        \tau\omega_c^{\star}&=M^{\star}\alpha\tau\omega _c^{\star}\cos{(\varphi ^{\star})}+M^{\star}\sin{(\varphi ^{\star})}
    \end{aligned}
\end{equation*}
Quindi le formule di inversione sono:
\begin{equation*}
    \begin{aligned}
        \tau&=\frac{M^{\star}-\cos{(\varphi ^{\star})}}{\omega_c^{\star}\sin{(\varphi ^{\star})}} \\
        \alpha\tau&=\frac{\cos{(\varphi ^{\star})}-\frac{1}{M^{\star}}}{\omega_c^{\star}\sin{(\varphi ^{\star})}}
    \end{aligned}
\end{equation*}
Si noti che per avere $\alpha >0$ occorre $\frac{1}{M^{\star}}<\cos{(\varphi ^{\star})}$.\
\
Obiettivo 2: imporre $|L(j\omega)|_{\textrm{dB}}=0$ per $\omega=\omega _c^{\star}$.\
Si procede: 

1. scegliendo $\omega _c^{\star}$ e ricavare $M_f^{\star}$ dalle specifiche
2. calcolare $M^{\star}$ e $\varphi ^{\star}$ imponendo $$ |G_e(j\omega _c^{\star})|_{\textrm{dB}}-20\log{M^{\star}} $$ $$ M_f^{\star}=180^{\circ}+\arg{(G_e(j\omega _c^{\star}))}+\varphi^{\star} $$ Ottenendo $M^{\star}$ dalla prima (o da quanto visto in precedenza): $$ M^{\star}=10^{-\frac{|G_e(j\omega _c^{\star})|_{\textrm{dB}}}{20}} $$ E per il margine di fase:
\begin{equation*}
    \begin{aligned}
        M_f^{\star}&=180^{\circ}+\arg{(L(j\omega _c^{\star}))} \\
        M_f^{\star}&=180^{\circ}+\arg{(G_e(j\omega _c^{\star}))}+\arg{(R_d(j\omega _c^{\star}))} \\
        M_f^{\star}&=180^{\circ}+\arg{(G_e(j\omega _c^{\star}))}+\varphi^{\star} \\
        \varphi^{\star}&=M_f^{\star}-180^{\circ}-\arg{(G_e(j\omega _c^{\star}))}
    \end{aligned}
\end{equation*}
3. verificare $M^{\star}>1$, $0<\varphi ^{\star}<\frac{\pi}{2}$ e $\frac{1}{M^{\star}}<\cos{(\varphi ^{\star})}$
4. si calcolano $\alpha$ e $\tau$ tramite le formule inverse viste nel paragrafo precedente.

## CONTROLLORI PID

Un controllore PID (Proporzionale Integrale Derivativo) "ideale" è della forma $$ R(s)=K_p\left(1+\frac{1}{T_is}+T_ds\right) \quad \quad T_i=\textrm{ Tempo integrale} \quad T_d=\textrm{ Tempo derivativo} $$
```{=latex}
\begin{center}
```

![](retroazionePID.PNG){height=150px}

```{=latex}
\end{center}
```
Ingresso di controllo: 
\begin{equation*}
    \begin{aligned}
        U(s)&=R(s)E(s) \\
        &= K_pE(s)+\frac{K_p}{T_i}\frac{E(s)}{s}+K_pT_dsE(s)
    \end{aligned}
\end{equation*}
Che nel dominio del tempo risulta $$ u(t)=\mathcal{L}[U(s)]=K_pe(t)+\frac{K_p}{T_i}\int_{0}^{t}e(\tau)d\tau+K_pT_d\frac{de(t)}{dt} $$ 
Di cui:

* $K_pe(t)$ termine **P**roporzionale
* $\frac{K_p}{T_i}\int_{0}^{t}e(\tau)d\tau$ termine **I**ntegrale
* $K_pT_d\frac{de(t)}{dt}$ termine **D**erivativo (**N.B.** non causale)

ATTENZIONE!!\
Il PID ideale non è fisicamente realizzabile. Infatti, sviluppando i calcoli, si vede che la funzione di trasferimento del controllore ha un numeratore con grado più elevato del denominatore: $$ R(s)=K_p\left(1+\frac{1}{T_is}+T_ds\right)=\frac{K_pT_is+K_p+K_pT_iT_ds^2}{T_is} $$ il PID "reale" (fisicamente realizzabile) richiede di aggiungere un polo in alta frequenza $$ R^{\textrm{fr}}(s)=K_p\left(1+\frac{1}{T_is}+T_ds\right)\frac{1}{1+T_ps} $$
\
\
Raccogliendo i termini e definendo opportunamente $\tau _1$, $\tau _2$ si può vedere che il PID reale è una combinazione di una rete anticipatrice e di una ritardatrice:
\begin{equation*}
    \begin{aligned}
        R^{\textrm{fr}}(s)&=\frac{K_p}{T_i}\frac{T_is+1+T_iT_ds^2}{s}\frac{1}{1+T_ps} \\
        &=\mu\frac{(1+\tau _1s)(1+\tau _2s)}{s}\frac{1}{1+T_ps} \quad \quad \mu := \frac{K_p}{T_i}
    \end{aligned}
\end{equation*}
\
Casi particolari:

* **Regolatori P**: se $T_i\to\infty$ e $T_d=0$ (no termine integrale e derivativo), si ottiene un regolatore proporzionale $R(s)=K_p$
* **Regolatori I**: in assenza di termine proporzionale e derivativo, si ottiene un regolatore puramente integrale $R(s)=\frac{K_i}{s}$. Si può interpretare come una rete ritardatrice con il polo posto nell'origine e con lo zero all'infinito
* **Regolatori PI**: se $T_d=0$ (no termine derivativo), si ottiene un regolatore proporzionale integrale $R(s)=K_p\left(1+\frac{1}{T_is}\right)$. Possono essere visti come reti ritardatrici con polo nell'oricine e zero in $-1/T_i$.
* **Regolatori PD**: se $T_i\to\infty$ (no termine integrale), si ottiene un regolatore proporzionale derivativo $R(s)=K_p(1+T_ds)$. Possono essere visti come reti anticipatrici con zero in $-1/T_d$ e polo posto all'infinito (nel caso ideale)

# LUOGO DELLE RADICI

Considerando il seguente schema in retroazione
```{=latex}
\begin{center}
```

![](retroazioneLuogoRadici.PNG){height=150px}

```{=latex}
\end{center}
```
in cui si mette in evidenza il guadagno $k$. La funzione di trasferimento in anello chiuso è $$ F(s)=\frac{kR(s)G(s)}{1+kR(s)G(s)}=\frac{kL(s)}{1+kL(s)} $$ L'obiettivo è studiare come variano nel piano complesso i poli di $F(s)$ al variare di $k$.

#### Esempio

Prendendo in esempio un sistema del prim'ordine $L(s)=\frac{1}{s+1}$ (polo in $-1)
```{=latex}
\begin{center}
```

![](retroazioneLuogoRadiciEs1.PNG){height=100px}

```{=latex}
\end{center}
```
La funzione di trasferimento in anello chiuso è $$ F(s)=\frac{kL(s)}{1+kL(s)}=\frac{k\frac{1}{s+1}}{1+k\frac{1}{s+1}}=\frac{k}{s+1+k} \quad \quad \quad \textrm{polo in $-1-k$} $$ **_Luogo delle radici_**: posizione nel piano complesso del polo di $F(s)$ al variare di $k\ge 0$
```{=latex}
\begin{center}
```

![](luogoRadiciEs1.PNG){height=100px}

```{=latex}
\end{center}
```

## DEFINIZIONE DI LUOGO DELLE RADICI

Sia $$ L(s)=\frac{N(s)}{D(s)} $$ si ha $$ F(s)=\frac{kL(s)}{1+kL(s)}=\frac{kN(s)}{D(s)+kN(s)} $$

* Gli zeri di $F(s)$ sono le radici di $kN(s)$ e quindi sono gli zeri di $L(s)$
* I poli di $F(s)$ sono le radici di $D(s)+kN(s)$ e quindi dipendono da poli e zeri di $L(s)$

**N.B.** la retroazione non sposta gli zeri del sistema, ma solo i poli

#### Luogo diretto:

posizione dei poli di $F(s)$ al variare di $k\ge 0$ (ci si concentrerà su questo)

#### Luogo inverso:

posizione dei poli di $F(s)$ al variare di $k\le 0$

## EQUAZIONE CARATTERISTICA

```{=latex}
\begin{center}
```

![](retroazioneLuogoRadiciEs1.PNG){height=100px}

```{=latex}
\end{center}
```
I poli del sistema retroazionato sono le soluzioni dell'**equazione caratteristica** $$ D(s)+kN(s)=0 $$

* $k=0 \longrightarrow D(s)=0$ I poli di $F(s)$ coincidono con quelli di $L(s)$
* $k\to\infty \longrightarrow N(s)=0$ I poli di $F(s)$ coincidono con gli zeri di $L(s)$

**N.B.** Per sistemi propri il polinomio $D(s)$ ha grado maggiore o uguale a quello di $N(s)$, l'ordine del polinomio $D(s)+kN(s)$ è lo stesso di quello di $D(s)$\
$\Longrightarrow$ il numero di poli del sistema retroazionato è uguale a quello del sistema ad anello aperto.

### OSSERVAZIONI

Fissato un valore di $k$ le soluzioni dell'equazione caratteristica determinano $n$ punti nel piano complesso, con $n$ ordine di $L(s)$ $$ D(s)+kN(s)=0 $$

#### Esempio:

sistema del terz'ordine $$ L(s)=\frac{1}{(s+1)^3} \quad \quad \textrm{3 poli in -1} $$ Il luogo delle radici è costituito da $n$ "rami" parametrizzati nel valore di $k$. Una volta fissato, gli $n$ punti sugli $n$ rami identificano i poli del sistema retroazionato per quel $k$.\
Se i coefficienti dell'equazione caratteristica sono reali allora il luogo è simmetrico rispetto all'asse reale.
```{=latex}
\begin{center}
```

![](luogoRadiciEs2.PNG){height=100px}

```{=latex}
\end{center}
```

## REGOLE DI TRACCIAMENTO

Sia $n$ il numero di poli e $m$ il numero di zeri di $L(s)$ (con $n\ge m$).\
Le regole sono:

1. Il luogo ha tanti rami quanti sono i poli del sistema in catena aperta
2. Ogni ramo parte da un polo di $L(s)$ e termina in uno zero di $L(s)$ o all'infinito. In particolare, $m$ rami terminano negli zeri di $L(s)$ e $n-m$ rami terminano all'infinito
3. Il luogo è simmetrico rispetto all’asse reale 
4. I punti dell'asse reale che appartengono al luogo sono quelli che lasciano alla propria destra un numero dispari di singolarità (cioè poli o zeri) di $L(s)$.

Siano ora $-p_1,\ldots,-p_n$ i poli e $-z_1,\ldots,-z_m$ gli zeri di $L(s)=\frac{(s+z_1)\cdots(s+z_m)}{(s+p_1)\cdots(s+p_n)}$

5. I rami che tendono all'infinito lo fanno lungo asintoti che si intersecano sull'asse reale nel punto con ascissa pari a $$ x_a=\frac{1}{n-m}\left(\sum_{i=1}^{m}z_i-\sum_{i=1}^{n}p_i\right) $$
6. Gli asintoti dividono il piano complesso in parti uguali. In particolare l'angolo che il $j$-esimo asintoto forma con l'asse reale è $$ \theta _{a,j}=\frac{(2j+1)\pi}{n-m}, \quad \quad \quad j=0,\ldots,n-m-1 $$
7. Quando il grado relativo del sistema è maggiore di 1 (cioè $n-m\ge 2$), la somma dei poli è costante al variare di $k$, quindi il baricentro del luogo è il punto dell’asse reale con ascissa $$ x_b=-\frac{1}{n}\sum_{i=1}^{n}p_i $$ 

```{=latex}
\begin{center}
```

![](asintoti.PNG){height=250px}

```{=latex}
\end{center}
```

Le regole che si enuncieranno in seguito si applicano ai poli semplici di $L(s)$ (per i poli multipli le regole sono più complesse)

8. La tangente al ramo uscente da un polo semplice $-p_j$ forma con l'asse reale l'angolo $$ \alpha _j=180^{\circ}+\sum_{i=1}^{m}\theta _i-\sum_{i\ne j} \varphi _i $$ dove $\theta _i$ (e rispettivamente $\varphi _i$) è l'angolo formato con il semiasse reale positivo dal vettore che congiunge il polo in considerazione con lo zero $-z_i$ (rispettivamente con il polo $-p_i$)
9. La tangente del ramo entrante in uno zero semplice $-z_j$ forma con l'asse reale l'angolo $$ \beta _j=180^{\circ}-\sum_{i\ne j}\theta _i+\sum_{i=1}^{n}\varphi _i $$ dove gli angoli $\theta _i$ e $\varphi _i$ sono definiti in modo analogo alla precedente regola

Ad esempio: determinare l'angolo di uscita $\alpha _3$ del ramo che parte dal polo in $-p_3$
```{=latex}
\begin{center}
```

![](luogoRadiciEs3.PNG){height=180px}

```{=latex}
\end{center}
```
Oppure, un altro esempio: determinare l'angolo d'ingresso $\beta _2$ del ramo che entra nello zero in $-z_2$
```{=latex}
\begin{center}
```

![](luogoRadiciEs4.PNG){height=180px}

```{=latex}
\end{center}
```

10. Eventuali punti di incrocio di rami sull'asse reale si possono determinare trovando i massimi e i minimi relativi della funzione $$ \gamma (x)=-\frac{D(x)}{N(x)} $$ Nello specifico, se $\bar x$ è un punto di minimo e $s=\bar x$ appartiene al luogo, esistono due rami complessi che confluiscono sull'asse reale in $\bar x$; se $\bar x$ è, invece, un punto di massimo e $s=\bar x$ appartiene al luogo, esistono due rami reali che si incontrano in $\bar x$ e poi si semparano diventando complessi.
```{=latex}
\begin{center}
```

![](luogoRadiciReg10.PNG){height=180px}

```{=latex}
\end{center}
```

## SISTEMI DEL PRIM'ORDINE

```{=latex}
\begin{center}
```

![](luogoRadiciIordine.PNG){height=200px}

```{=latex}
\end{center}
```

## SISTEMI DEL SECOND'ORDINE 

### CON POLI REALI

```{=latex}
\begin{center}
```

![](luogoRadiciIIordineReali.PNG){height=230px}

```{=latex}
\end{center}
```

### CON POLI COMPLESSI CONIUGATI

```{=latex}
\begin{center}
```

![](luogoRadiciIIordineComplCC.PNG){height=230px}

```{=latex}
\end{center}
```

## ESEMPIO CON MATLAB

Luogo delle radici di un sistema del secondo ordine con zero $$ G(s)=\frac{s+2}{s^2+2s+2} $$
```matlab
s = tf('s');
G = zpk([-2], [-1+j,-1-j], 1);
rlocus(G);
```
```{=latex}
\begin{center}
```

![](luogoRadiciMatlab.PNG){height=200px}

```{=latex}
\end{center}
```