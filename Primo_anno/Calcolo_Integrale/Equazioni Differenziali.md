Un'equazione differenziale è un'equazione in cui l'incognita è una funzione y(t) definita in un intervallo $\mathbb{I}$. In questo tipo di equazioni entrano in gioco le derivate di y(t), l'ordine dell'equazione corrisponde al grado massimo della derivata

*Esempio:* $y^{III}(t)+y^I+sin(t\space y(t))=e^t$ è un equazione di grado 3

##### **Equazione in forma normale:**
Un'equazione è in forma normale quando essa è di grado n, allora si scrive:

>$$y^{(n)}=f(t,\space y(t),\space y^I(t),\space\dots,\space y^{(n-1)}(t))$$

*Esempio:* $y^I(t)=\cos(y(t))+y(t)e^t$, questa equazione è di ordine 1 in forma normale

##### **Equazioni Differenziali di primo ordine:**

###### **Equazioni differenziali "elementari" e problemi di Cauchy:**

Tipologia 1: $$y'=f(x)\space\space\Longrightarrow\space\space\int f(x)dx=F(x)+c$$
*Esempio:*$$\begin{matrix}y'=3e^{2x} \\
y = \int3e^{2x}dx=3\int \frac{1}{2}\cdot2e^{2x}=\frac{3}{2}e^{2x}+c
\end{matrix}$$
Le soluzioni sono infinite, per trovarne solo 1 si impone una condizione iniziale: 
$$\begin{cases}
y^I=f(t,\space y(t))  \\
 \\y(t_0)=y_0\space\space\space\space\space t_0\in\mathbb{I}
\end{cases}$$
Quando ci troviamo in questo caso siamo davanti ad un problema di Cauchy, dove abbiamo un'equazione differenziale e delle condizioni iniziali. Risolvendo il problema di Cauchy significa trovare tra le infinite soluzioni dell'equazione differenziale quella che soddisfa le condizioni iniziali.

*Esempio:*
$$\begin{matrix}
\begin{cases} y'=-e^{-x}\space\space\space\rightarrow\space\space\space y=\int (-e^{-x})dx=e^{-x}+c\\
 \\ y(0) = 3\space\space\space\rightarrow\space\space\space 3 = e^{-0}+c\space\space\space\rightarrow\space\space\space c=2
\end{cases} \\
 \\ \mbox{La soluzione dell'equazione è } y(x)=e^{-x}+2
\end{matrix}$$
###### **Equazioni differenziali a variabili separabili:**
Sono equazioni differenziali del 1°ordine che si possono ricondurre alla forma:

>$$y'=f(x)\cdot g(y)$$

*Esempi:* $y'=y\ln x$, $y'=e^xy\ln y$. Per risolverle devo.
1) Separare le variabili x e y
2) Integrare ciascun membro rispetto alla variabile da cui dipende
3) Ricavare y(x)

*Esempio di risoluzione 1:* $y'=y^2ln(x)$
$$\begin{matrix} 
\mbox{1) Separo le variabili} \space\space\rightarrow\space\space \frac {dy}{dx}=y^2ln(x)\space\space\rightarrow\space\space \frac {dy}{y^2}=ln(x)dx \\
\mbox{2) Integro ciascun membro}\space\space\rightarrow\space\space \int \frac {dy}{y^2}=\int ln(x)dx \\ \\

\mbox{Calcolo gli integrali} \\
\mbox{-}\int y^{-2}dy\space\rightarrow\space\frac {y^{-2+1}}{-2+1}+c\space\rightarrow\space-\frac{1}{y}+c \\
\mbox{-}\int ln(x)dx \space\rightarrow\space  \int1\cdot ln(x)dx \space\rightarrow\space x\cdot ln(x)-\int\frac{1}{x}\cdot x dx \space\rightarrow\space x\cdot ln(x)-x+c
 \\ \\
\mbox{3) y(x)} = -\frac {1}{xln(x)-x+c} 
\end{matrix}$$

###### **Equazioni differenziali lineari del 1°ordine:**
Le equazioni differenziali lineari del 1°ordine sono tutte quelle equazioni differenziali che sono rappresentabili in questo modo:

>$$y'(x)+a(x)y(x)=f(x)$$

Notiamo subito due cose:
1) Se a(x)=0 allora l'equazione è di tipo "elementare"
2) Se f(x)=0 allora l'equazione diventa un equazione a variabili separabili

*Esempi:* y'-xy = 2x, $y'+ \frac{1}{x}\cdot y=4x^2$

Come si risolve questo tipo di equazione? Tramite il metodo del fattore integrante:
1) Trovo una primitiva di a(x), cioè una funzione A(x) tale che A'(x)=a(x)
2) Moltiplico entrambi i membri per $e^{A(x)}$: $y'(x)e^{A(x)}+a(x)e^{A(x)}=f(x)e^{A(x)}$ e notiamo che il primo membro è uguale a $[y(x)e^{A(x)}]'$
3) Integro entrambi i membri: $y(x)e^{A(x)}=\int f(x)e^{A(x)}dx$ +c
4) Ricavo y(x) moltiplicando entrambi i membri per $e^{-A(x)}$: $y(x) = e^{-A(x)}\int f(x)e^{A(x)}dx\space +ce^{-A(x)}$

*Esempio: $y'(x)-xy(x)=2x$*
$$\begin{matrix} 
\mbox{1) Trovo una primitiva di a(x), ossia A(x): } \int -xdx = -\frac {x^2}{2} \\
\mbox{2) Moltiplico entrambi i membri per  $e^{A(x)}$: } \space y'(x)e^{A(x)}-xe^{A(x)}y(x)=2x\space e^{A(x)} \\
\mbox{3) Integro i membri: }\space y(x)e^{-\frac{x^2}{2}}=\int 2xe^{-\frac{x^2}{2}}dx+c=-2e^{-\frac{x^2}{2}}+c \\
\mbox{4) Ricavo y(x) moltiplicando per $e^{-A(x)}$ e semplificando ho che:} y(x)=-2+ce^{\frac{x^2}{2}} 
\end{matrix}$$
**Quindi la soluzione dell'equazione differenziale è: $-2+ce^{-\frac {x^2}{2}}$**

