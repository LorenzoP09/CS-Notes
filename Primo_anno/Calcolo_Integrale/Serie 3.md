##### **Modificare un numero finito di valori:**
Le proprietà di convergenza di una serie $\sum a_{k}$ dipendono dall'andamento della "coda" della successione $a_{k}$.  Cambiare il valore di un numero finito di elementi di una serie non modifica la convergenza/divergenza della serie stessa.

*Osservazione*
Siano $\sum a_{k}\space e \space \sum b_{k}$ due serie tali che, per qualche $N \in \mathbb{N}$, $b_{k}=a_{k}$ $\forall k\ge N$ allora

> $\sum a_{k}$  è convergente   $\Longleftrightarrow$   $\sum b_{k}$  è convergente

##### **Proprietà del confronto**
Siano $\sum a_{k}\space e \space \sum b_{k}$ due serie a termini non negativi. Se, per qualche $N \in \mathbb{N}$, vale che           $a_{k}\le b_{k}$   $\forall k\ge N$, allora:

>$$\sum_{k=1}^{\infty}b_{k}<+\infty \space\space\space\Rightarrow\space\space\space \sum_{k=1}^{\infty}a_{k}<+\infty$$

##### **Confronto e Rapporto:**
Se $b_{k}\ne {0}$:
$$a_{k}\le b_{k}\space\space\space\Longleftrightarrow\space\space\space \frac{a_{k}}{a_{k}}\le {1}$$
Se $a_{k}\ge 0$ e $b_{k}>0$, allora:
$$\lim_{k \to \infty} \frac {a_{k}}{b_{k}}=l<1\space\space\Rightarrow \space Esiste\space N\in\mathbb{N}\space tale\space che\space a_{k}\le b_{k},\space\forall k\ge N.$$
 Euristicamente, se $a_{k}\ge 0$ e $b_{k}\ge 0$:
$$\lim_{ n \to \infty } \frac{a_{k}}{b_{k}}=l\space\space\space\Rightarrow\space\space\space a_{k}\approx l \cdot b_{k}\space\space per\space k\space\rightarrow\space +\infty$$
In questo caso, è ragionevole aspettarsi un legame tra la convergenza della serie $\sum a_{k}$ e quella della serie $\sum b_{k}$.

##### **Criterio del confronto asintotico:**
Siano $\sum a_{k}$ e $\sum b_{k}$ tali che $a_{k}\ge 0$ e $b_{k}>0$ tali che:
$$\lim_{ k \to \infty } \frac{a_{k}}{b_{k}}=l$$
Se l > 0, allora:
$$\sum_{k=1}^{\infty}a_{k}<+\infty\space\space\space\Longleftrightarrow\space\space\space \sum_{k=1}^{\infty}b_{k}<+\infty$$
Di conseguenza, nelle stesse condizioni, si ha:
$$\sum_{k=1}^{\infty}a_{k}=+\infty\space\space\space\Longleftrightarrow\space\space\space \sum_{k=1}^{\infty}b_{k}=+\infty$$


