##### **Regola generali:**
Se $\sum_{n=0}^{\infty}a_{n}$ converge e $\sum_{n=0}^{\infty}b_{n}$ diverge allora $\sum_{n=0}^{\infty}a_{n}+b_{n}$ diverge

##### **Serie Geometriche:**
La serie geometrica ha la seguente forma: $\sum x^k$, la serie geometrica di ragione x:
- Se -1 < x < 1: La serie è convergente
  - Se si parte da indice 0: $\frac{1}{1-x}$
  - Se si parte da un indice p: $\frac{x^p}{1-x}$

- Se x > 1 : La serie è divergente:
- Se la successione ha ragione x > 1 ed è una somma parziale si ha che: $$\sum_{k=0}^n x^k=\frac{{1-x^{n+1}}}{1-x}$$
##### **Serie Telescopica:**
Una ==serie telescopica== è tale che a<sub>k</sub> = b<sub>k+1</sub> - b<sub>k</sub>. La successione delle somme parziali di una telescopica è s<sub>n</sub> = b<sub>n+1</sub> - b<sub>1</sub>. Una serie telescopica è convergente se la sua $S_n$ è convergente:
$$\lim_{n \to +\infty}b_{n+1}-b_1$$

##### **Tabella riassuntiva degli sviluppi di Taylor:**

| Funzione        | Sviluppo in serie di Taylor (centro x = 0)          | Raggio di convergenza |
| --------------- | --------------------------------------------------- | --------------------- |
| $\frac{1}{1-x}$ | $\sum_{n=0}^{\infty}x^n$                            | $p=1$                 |
| $e^x$           | $\sum_{n=0}^{\infty}\frac {x^n} {n!}$               | p = $+\infty$         |
| sin x           | $\sum_{n=0}^{\infty}(-1)^n\frac{x^{2n+1}}{(2n+1)!}$ | p = $+\infty$         |
| cos x           | $\sum_{n=0}^{\infty}(-1)^n \frac{x^{2n}}{2n!}$      | p = $+\infty$         |
| $ln(1+x)$       | $\sum_{n=1}^{\infty}(-1)^{n+1}\frac{x^n}{n}$        | p = 1                 |
