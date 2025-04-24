 Esistono delle serie con $a_{n}$ di segno variabile, dove i criteri di confronto visti precedentemente non possono essere applicati. In questo caso si può definire la convergenza assoluta:

*Def*
$$\sum_{n=0}^{\infty}a_{n}\space\space converge \space assolutamente\space se \space\space \sum_{n=0}^{\infty}|a_{k}|\space converge$$
##### **Criterio di Leibniz:**
Nel caso in cui ci troviamo difronte ad una serie con segno alterno (+, -, +, -, etc...), utilizzeremo per lo studio della serie il criterio di Leibniz.

Si ha $\sum_{n=0}^{\infty}(-1)^na_{n}$ con $a_{n}\ge 0$, dove se n pari è positiva e se n è dispari è negativa.

Il criterio si compone di tre fasi:
$$\begin{matrix} 1)\space a_{n}\ge 0 \\
2)\space\lim_{ n \to \infty }a_{n} =0 \\
3)\space a_{n}\space decrescente
\end{matrix}$$
Se vengono soddisfatti questi punti si ottiene che $\sum_{n=0}^{+\infty}(-1)^na_{n}$ converge.

##### **Serie di potenze:**
Fissato $x_{0}\in\mathbb{R}$ e $a_{n}$ con $n\in N$ possiamo definire la serie di potenze di centro $x_{0}$ associata alla successione $a_{n}$ come: $$\sum_{n=0}^{\infty}a_{n}{(x-x_{0})}^n=a_{0}+a_{1}(x-x_{0})+\dots$$
Per quali valori di $x\in \mathbb{R}$ converge la serie $a_{n}$? Ogni serie di potenze converge sempre nel suo centro $x_{0}$ perché $(x_{0}-x_{0})^n=0$. Quindi sappiamo che i valori fissati sono $a_{n}\space e \space x_{0}$, mentre x gioca il valore di incognita. Quindi per quali valori di x converge?

Esempio: $\sum_{n=0}^{+\infty} \frac {(x-3)^n}{\sqrt{n+4}}$, in questo caso $x_{0}=3$ e $a_{n}=\frac 1 {\sqrt{ n+4 }}$
Proveremo che converge $\forall x\in[2,4)$ e quindi sarà definita $S(x)=\sum_{n=0}^{\infty}\frac {(x-3)^n}{\sqrt{ n+4 }}$ in $[2,4)$

*Oss:* Poniamo $x-x_{0}=y$ otteniamo la serie $\sum_{n=0}^{\infty}a_{n}y^n$ di centro 0 per cui possiamo studiare sempre questo tipo di serie e poi tornare indietro a quella originale ricordando $x=x_{0}+y$ 

*Esempio:* $\sum_{n=0}^{\infty}n{(x-7)}^n \space\space(x_{0}=7, \space a_{n}=n)$
Vediamo dove converge $\sum_{n=0}^{\infty}ny^n$. Proveremo che converge $\forall y \in (-1,1)$ e quindi $\forall x \in (6, 8)$ essendo $x = x_{0}+y= 7+y$ 

*Prop:* data $\sum_{n=0}^{\infty}a_{n}x^n$ se esiste $\bar{x}\ne{0}$ tale che $\sum_{n=0}^\infty a_{n}\bar{x}^n$ converge allora la serie converge $\forall x \in (-|\bar{x}|, |\bar{x}|)$ (non sappiamo se $\bar{x}>0 \space o \space \bar{x}<0$)

###### **Raggio di convergenza:**
Come conseguenza della precedente proposizione possiamo definire:$$\delta:=sup \left\{x\ge{0}\space\space t.c.\space\space \sum_{n=0}^{+\infty}a_{n}x^n \space\space converge\right\}$$
$\delta$ è detto raggio di convergenza, può essere uguale a 0 oppure a $+\infty$. 
- Se $\delta=0$ la serie di potenze converge solo per x=0
- Se $\delta = +\infty$ la serie di potenze converge $\forall x\in \mathbb{R}$
- Se $\delta \in(0,+\infty)$ si ha:
  1) La serie converge in ($x_{0}-\delta, x_{0}+\delta$)
  2) la serie non converge se $x < x_{0}-\delta$ o $x>x_{0}+\delta$
  3) x = $\pm \space\delta$ non possiamo dire nulla, vanno studiate a parte

Come si calcola $\delta$?

Metodo 1: $$\begin{matrix}
\lim_{ n \to +\infty }\sqrt[n]{|a_{n}|}=l\in[0,\infty)\space o \space l = +\infty \\ \\

\delta = \frac{1}{l}=\begin{cases}
\frac{1}{l}\space\space se \space\space l\in(0,\infty) \\
0 \space\space\ se\space\space l=+\infty \\
+\infty \space\space se \space\space l=0
\end{cases}
\end{matrix}$$
Metodo 2:
$$\begin{matrix}
\lim_{ n \to +\infty } \left|\frac{a_{n+1}}{a_{n}} \right|=l \space\space\Rightarrow\space\space \delta=\frac{1}{l} \\
\delta = \lim_{ n \to \infty }  \left|\frac{a_{n}}{a_{n+1}} \right| 
\end{matrix}$$
