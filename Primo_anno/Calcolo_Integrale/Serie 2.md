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

*Convergenza delle rappresentazioni decimali:*
Per ogni successione di cifre c<sub>k</sub>, la serie ∑ck/10k è convergente. la sua somma l è compresa tra 0 e 1

DIM. la serie con termine 9/10<sup>k</sup> è convergente $$\sum_{k=1}^{\infty} \frac{c_k}{10^k} \leq \sum_{k=1}^{\infty} \frac{9}{10^k} = 9 \sum_{k=1}^{\infty} \left(\frac{1}{10}\right)^k = 9 \cdot \frac{\frac{1}{10}}{1 - \frac{1}{10}} = 1$$

(Abbiamo svolto la serie utilizzando la formula delle serie geometriche con x, in questo caso 1/10<1) Inoltre per la proprietà di confronto, la serie è convergente e la sua somma è compresa tra 0 e 1

*Trovare i decimali:*



*Completezza della rappresentazione decimale:*
Per ogni numero l ∈ [0, 1] esiste una successione di cifre c<sub>k</sub> tale che $$\sum_{k=1}^{∞} \frac {c_k} {10^k}=l$$
*Dim:*
Infatti, $c_k \le 9$ per ogni k, quindi:
$$\frac {c_k} {10^k} \le \frac 9 {10^k}  \space \space \forall k$$
Inoltre, la serie Daje Roma

  
