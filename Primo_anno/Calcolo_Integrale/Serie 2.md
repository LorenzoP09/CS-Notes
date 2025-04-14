##### **Serie a Termini non negativi:**
Una serie numerica è ==a termini non negativi==, quindi se a<sub>k</sub> ≥ 0 per ogni k. Terminologia analoga per serie a termini positivi esistono le serie a termini
1) Non positivi, quindi con a<sub>k</sub> ≤ 0
2) Negativi, quindi cona<sub>k</sub> < 0

*Esempi.* Serie a termini non negativi
$$\sum_{k=1}^{∞} \frac 1 {k(k+1)}, \mbox{ }\mbox{ }\mbox{ }\sum_{k=1}^{∞}sin^2(k\pi/2)$$
*Esempi.* Serie a termini di segno generico
$$\sum_{k=i}^{∞} \frac {2k-1} {k^2}, \mbox{ }\mbox{ }\mbox{ }\sum_{k=1}^{∞}sin(k)$$
##### **Successioni monotone:**
==Teorema della Regolarità delle successioni monotone:==
Se la successione s<sub>n</sub> è non decrescente, allora
$$\lim_{n→+∞}s_n = l ∈ R \mbox{ }\mbox{ }oppure\mbox{ }\mbox{ }\lim_{n→+∞}s_n=+∞$$
*Principio:* L’assenza di oscillazioni permette di classificare in maniera “semplice” i possibili comportamenti del limite.

s<sub>n</sub> monotona ⇒ s<sub>n</sub> convergente o divergente

La stessa conclusione se s<sub>n</sub> è definitivamente non decrescente, cioè tale che esiste n<sub>0</sub> tale che S<sub>n+1</sub> ≥ S<sub>n</sub> per n ≥ n<sub>0</sub>

*Monotonia delle somme parziali:*
Se la serie ∑a<sub>k</sub> è a termini non negativi, la successione s<sub>n</sub> delle somme parziali è non decrescente.
**Dim**
$$S_{n+1}-S_n = \sum_{k=1}^{n+1}a_k-\sum_{k=1}^{n}a_k=a_{n+1}≥0$$

==Dicotomia delle serie a termini non negativi==
Se la serie ∑a<sub>k</sub> è a termini non negativi per ogni k, allora 
$$\sum_{k=1}^{∞}a_k\mbox{ }<+∞\mbox{ }\mbox{ }\mbox{ }\mbox{ }oppure\mbox{ }\mbox{ }\mbox{ }\sum_{k=1}^{∞}a_k=+∞$$
(Se una serie non diverge allora converge)

==Criterio di Confronto:==
siano ∑a<sub>k</sub> e ∑b<sub>k</sub> due serie a termini non negativi. Allora $$
a_k≤b_k \mbox{ }\mbox{ }e\mbox{ }\mbox{ }\sum_{k=1}^{∞}b_k<+∞ ⇒ \sum_{k=1}^{∞}a_k≤\sum_{k=1}^{∞}b_k<+∞$$
*Uso concreto del confronto*
Consideriamo la serie a termini positivi $$\sum_{k=1}^{∞}\frac 1 {(k+1)^2}$$
dato che 1/k+1 ≤ 1/k, si ha che $$a_k = \frac 1 {(k+1)^2}≤ \frac 1 {k(k+1)}=b_k\mbox{ }\mbox{ }\mbox{ }∀k = 1,2,...$$
La serie ∑b<sub>k</sub> è convergente. Di conseguenza $$\sum_{k=1}^{∞}\frac 1 {(k+1)^2}<+∞$$
*Proposizione Criterio di confronto*
Siano ∑ ak e ∑ bk due serie a termini non negativi. Allora $$
a_k≥b_k \mbox{ }\mbox{ }e\mbox{ }\mbox{ }\sum_{k=1}^{∞}b_k=+∞\mbox{ }\mbox{ }⇒\sum_{k=1}^{∞}a_k=+∞$$
##### **Serie armonica generalizzata:**
Facciamo prima chiarezza su cosa è una serie armonica e su cosa è una serie armonica *generalizzata*: $$\begin{matrix}Serie \mbox{ }armonica = \sum_{k=1}^{∞}\frac 1 k\\Serie \mbox{ } armonica \mbox{ } generalizzata = \sum_{k=1}^{∞}\frac 1 {k^a} \mbox{ }\mbox{ }(a>0)\end{matrix}$$
Per quanto visto:
- La serie armonica è divergente
- La serie armonica generalizzata con a = 2 è convergente
In generale si dimostra che
$$\sum_{k=1}^{∞}\frac 1 {k^a}\mbox{ }converge\mbox{ }⇐⇒\mbox{ }\mbox{ }a>1$$

##### **Convergenza delle rappresentazioni decimali:**
Data una successione c<sub>k</sub> di cifre, consideriamo la serie$$\sum_{k=1}^{∞}\frac {c^k} {10^k}$$

***Convergenza delle rappresentazioni decimali:***
Per ogni successione di cifre c<sub>k</sub>, la serie ∑ck/10k è convergente. la sua somma l è compresa tra 0 e 

Dimostrazione
Infatti, $c_k \le 9$ per ogni k, quindi: $$\frac {c_k} {10^k} \le \frac 9 {10^k}  \space \space \forall k$$ 
Inoltre la serie con termine $\frac{1}{10^k}$ è convergente:

$$\sum_{k=1}^{\infty} \frac{c_k}{10^k} \leq \sum_{k=1}^{\infty} \frac{9}{10^k} = 9 \sum_{k=1}^{\infty} \left(\frac{1}{10}\right)^k = 9 \cdot \frac{\frac{1}{10}}{1 - \frac{1}{10}} = 1$$

(Abbiamo svolto la serie utilizzando la formula delle serie geometriche con x, in questo caso 1/10<1) Inoltre per la proprietà di confronto, la serie è convergente e la sua somma è compresa tra 0 e 1

***Trovare i decimali:***
Consideriamo $\frac 1 4$:
1) Per trovare la cifra $c_1$, cerchiamo il più grande intero N tale che
   $$\frac N {10}\le\frac 1 4 \space \space \Rightarrow \space\space N\le\frac {10} 4 = 2 + \frac 2 4 \space\space\Rightarrow\space\space c_1 = 2$$

2) Per trovare la cifra $c_{2}$, cerchiamo il più grande intero N tale che
$$\frac N {10^2}\le\frac 1 4 - \frac {c_{1}} {10} =\frac 1 {20} \space\space\Rightarrow\space\space N \le\frac {10^2} {20} = 5\space\space\Rightarrow\space\space c_{2} = 5$$

Dato che il resto è nullo, $c_{k}$=0 $\forall k\ge{2}$ e quindi:
$$\frac 1 4=\frac {c_{1}} {10}+\frac {c_{2}} {10^2} = \frac 2 {10} + \frac 5 {10^2}=0,25$$


***Completezza della rappresentazione decimale:***
Per ogni numero l ∈ [0, 1] esiste una successione di cifre c<sub>k</sub> tale che $$\sum_{k=1}^{∞} \frac {c_k} {10^k}=l$$
Scelto $l \in[0,1]$, usiamo lo stesso procedimento di prima.
1) La cifra $c_{1}$ è il più grande intero N tale che $N\le{10l}$
2) Poniamo $r_{1}:=\frac{c_{1}}{10}$. La cifra $c_{2}$ è il più grande intero tale che $N\le 10^2r_{1}$

L’iterazione fornisce l’approssimazione $\frac{c_{1}}{10}+\dots+\frac{c_{n}}{10^2}$. Passando al limite $n \to\infty$, la successione converge a l

***Rappresentazione p-adica:***
La scelta decimale nella rappresentazione in serie dei numeri reali è puramente convenzionale. Si possono fare altre scelte.

Proposizione:

>Dato $p\in\mathbb{N}, p\le2.$ Per ogni numero $l\in[0,1]$ esiste una successione di interi $c_{k}\in\left\{0,1,\dots,p-1\right\}$ tale che $$\sum_{k=1}^{\infty} \frac{c^k}{p^k}=l$$

La procedura di calcolo è la stessa di prima. Ad esempio:
$$p=2: \space\space\space\space\space \frac 1 4=0,01 \space\space\space\space\space \frac{1}{3}=0,01010101\dots$$
