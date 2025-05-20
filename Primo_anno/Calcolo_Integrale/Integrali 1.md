Sia f(x) una funzione detta **funzione integranda** e un certo intervallo $[a,b]$ chiamato **zona di integrazione**, l'integrale della funzione è l'area (**con segno**) di piano compresa tra il grafico di f(x), l'asse x e le rette verticali x = a e x = b. 

>$$\int_{a}^{b}f(x)dx$$

##### **Definizione di Riemann:**
$$
sup \left\{\int_{a}^{b}g(x)dx: 
\begin{matrix}  
g(x)\mbox{ a scala e} \\
g(x)\le f(x) \space \forall x\in [a,b]
\end{matrix}\right\}
\le A\le
inf \left\{\int_{a}^{b}h(x)dx: 
\begin{matrix}  
h(x)\mbox{ a scala e} \\
h(x)\le f(x) \space \forall x\in [a,b]
\end{matrix}\right\}

$$
Se coincidono si dice che f è Riemann integrabile su $[a,b]$ ed il valore comune e $\int_{a}^{b}f(x)dx$

##### **Calcolo di $\int_{a}^{b}f(x)dx$ :** 
1) Trovare una funzione che, nell'intervallo $[a,b]$, abbia f(x) come derivata, (ovvero primitiva di f)
2) Una volta trovata, la calcolo negli estremi della zona di integrazione (calcolo F(b) e F(a))
3) Sottraggo i due valori $\int_{a}^{b}f(x)dx=F(b)-F(a)$

*Es:* $\int_{0}^{5}3x^2dx$
1) $\int_{0}^{5}3x^2dx$ = $[x^3]_{0}^{5}$ 
2) $F(0)=0$, $F(5)=125$
3) $F(5)-F(0)=125$

##### **Primitive elementari e proprietà degli integrali:**
Abbiamo discusso di come le primitive di una funzione siano di importanza elevata nel calcolo di un integrale in $[a,b]$. Si dice che F(x) è una primitiva di f(x) se è derivabile e $F'(x) = f(x)\space \forall x \in(a,b)$.

>$\rightarrow$ Ogni funzione $f:[a,b]\rightarrow \mathbb{R}$ continua ammette delle primitive 
>$\rightarrow$ La primitiva non è mai unica: Infatti se F(x) è una primitiva, allora lo è anche F(x)+c, con $c\in\mathbb{R}$ 
>    se $F(x)_1 \space e \space F(x)_2$ sono due primitive di f(x) in uno stesso intervallo, allora $F(x)_1 - F(x)_2$ è una funzione costante
 
<u>Primitive Elementari:</u>

| $f(x)$             | $F(x)$                 |
| ------------------ | ---------------------- |
| cos(x)             | sin(x)                 |
| sin(x)             | -cos(x)                |
| $e^x$              | $e^x$                  |
| $a^x$              | $\frac {a^x}{\ln(a)}$  |
| $x^m$              | $\frac {x^{m+1}}{n+1}$ |
| $\frac 1 x$        | $ln\|x\|$              |
| $\frac {1}{1+x^2}$ | atctan(x)              |

<u>Primitive elementari generalizzate:</u>

| $\int cos(x)dx$      | $sin[f(x)]+c$               |
| -------------------- | --------------------------- |
| $\int sin(x)dx$      | $-cos[f(x)]+c$              |
| $\int e^xdx$         | $e^{f(x)}+c$                |
| $\int x^mdx$         | $\frac {f(x)^{n+1}}{n+1}+c$ |
| $\int \frac{1}{x}dx$ | $\ln\|f(x)\|+c$             |

<u>Forme "Speciali":</u>

| $\int \frac {dx}{(\alpha-x)^2}$   | $-\frac {1}{x-\alpha}$                    |
| --------------------------------- | ----------------------------------------- |
| $\int \frac {dx}{(x-\alpha)^2}$   | $-\frac {1}{x-\alpha}$                    |
| $\int \frac {dx}{\alpha x-\beta}$ | $\frac {\ln(\|\alpha x-\beta\|)}{\alpha}$ |


*Esempio:* $\int_{0}^{\frac {\pi}{2}}sin(x)dx$
$\int_{0}^{\frac {\pi}{2}}sin(x)dx = [-cos(x)]_{0}^{\frac {\pi}{2}}=-cos(\frac {\pi}{2}) - cos(0)$ = 0+1 = 1  

*Esempio:* $\int_{1}^{2}x^3dx$
$\int_{1}^{2}x^3dx = \left[ \frac {x^4}{4} \right]_1^2=\frac {2^4}{4}-\frac {1^4}{4}=\frac{16}{4}-\frac{1}{4}=\frac{15}{4}$ 

<u>Proprietà dell'integrale:</u>
1) $\int f(x)\pm g(x)dx = \int f(x)dx \space\pm\space\int g(x)dx$
2) $\int kf(x)dx = k\int f(x)dx$ 
3) $\int_a^bf(x)dx = \int_a^cdx+\int_c^bf(x)dx$ 
4) $|\int_a^bf(x)dx|\le\int_a^b|f(x)|dx$  

##### **Teorema Fondamentale del Calcolo Integrale:**

> Sia $f:[a;b]\rightarrow \mathbb{R}$ continua, poniamo$$F(t) = \int_{a}^tf(x)dx$$
> Allora $\space \space \space \Longrightarrow \begin{matrix}1)\mbox{ F è derivabile} \\ 2)\mbox{F'(t) = f(t) }\space \forall t \in [a,b]\end{matrix}$

