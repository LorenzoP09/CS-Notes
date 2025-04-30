Per fare una richiesta al sistema operativo dobbiamo dare in input dei valori: 
- a7:  E' un registro che definisce l'operazione richiesta
- a0, a6: Eventuali parametri della chiamata
In output avremo: 
- a0, f0: Rappresentano un eventuale risultato della chiamata

Una possibile lista delle system calls può essere questa:
![[Pasted image 20250429161158.png]]

##### **Esempio pratico: Hello World in RISC-V:**
```
.globl main
.data 
	string: .asciz "Hello world!"   # dichiaro la variabile statica string come vettore di byte ascii
.text
main: 
	li a7, 4       # loaddo in a7 4, se a7=4 è caricata la funzione di "stampa stringa" in a7
	la a0, string  # loaddo in a0 string che sarà l'input della system call
	ecall 
```

Ecco un rapido elenco delle principali chiamate al sistema operativo:
![[Pasted image 20250429164953.png]]

##### **Funzioni:**
Una funzione è un frammento di codice che riceve degli argomenti e calcola un risultato (utile per rendere il codice riusabile e modulare). 
- Ha un indirizzo di partenza 
- Riceve uno o più argomenti 
- Svolge un calcolo
- Ritorna un risultato
- Continua la sua esecuzione dall'istruzione seguente a quella che l'ha chiamata 

##### **Funzioni, come vengono strutturate:**
==$1)$ Per chiamare la funzione:==
Per chiamare la funzione/procedura utilizzo la funzione jal, ossia jump and link: 

```
jal rd, etichetta
# j etichetta -> jal x0, etichetta
```

E' importante sottolineare l'utilità di jal perché ricorda nel registro rd l'istruzione successiva all'istruzione chiamante. (Fondamentale per la continuazione del programma) e cambia il PC per iniziare l'esecuzione del corpo della funzione.

$2)$==Per tornare e continuare l'esecuzione del programma chiamante:== 
```
jalr rd, rs1, etichetta  
# jr etichetta -> jalr x0, 0(ra)
```

Ricorda nel registro rd la posizione dell'istruzione successiva e salta all'indirizzo nel registri indicato

$3)$==Passare valori alla funzione:==
Abbiamo 8 registri, ossia i registri che vanno da a0 fino a a7, che servono per passare e restituire valori a 32 bit

$4)$==Come passare valori dalla funzione:==
Abbiamo 2 registri, ossia a0 e a1, che servono per restituire 2 valori a 2 valori a 32 bit

Ricorda che i registri temporanei, ossia t0, t1,... possono cambiare fra una chiamata e l'altra (temporary), invece i registri di tipo s0, s1,... non cambiano tra una chiamata e l'atra (saved).

##### **Preservare il contenuto dei registri:**
Conviene *preservare* il precedente contenuto dei registri usati dalla funzione e *ripristinarlo.* I vantaggi sono molteplici, inoltre:
- **<font color="#2DC26B">Meno vincoli</font>** alla funzione chiamante 
- Possiamo <font color="#ffff00">passare solo 8 argomenti</font> alla funzione, quindi risparmiamo 
- Non <font color="#c00000">rischiamo di perdere contenuti</font> quando una funzione chiama un'altra funzione

Le informazioni da preservare hanno un <u>ciclo di vita caratteristico</u>, dovuto al nidificarsi delle chiamate delle funzioni. Questo è comportamento di una **pila**, in cui aggiungere un elemento (<font color="#548dd4">push</font>) e togliere l'ultimo inserito (<font color="#548dd4">pop</font>). Viene realizzata con un vettore di cui si tiene l'indirizzo dell'ultimo elemento occupato nel registro sp (<font color="#548dd4">stack pointer</font>)

##### **Uso dello stack:**
Lo stack si trova nella parte "alta" della memoria e cresce verso il basso. Supponiamo di  voler salvare e ripristinare il registro <font color="#ff0000">ra</font>. 

**<u>Come salvare un elemento:</u>** (<font color="#548dd4">push</font>)
- Si decrementa lo sp della dimensione dell'elemento (in genere una word)
- si memorizza l'elemento nella posizione 0(sp)

```
addi sp, sp, -4
sw ra, 0(sp)
```

**<u>Come recuperare un elemento:</u>** (<font color="#548dd4">pop</font>)
- Si legge l'elemento della posizione 0(sp)
- Si incrementa lo sp della quantità allocata in precedenza

```
lw ra, 0(sp)
addi sp, sp, 4
```

 ![[Pasted image 20250429221726.png]]

##### **Uso dello stack in una funzione:**
- All'inizio della funzione: 
  1) **<font color="#e36c09">Allocare</font>** su stack abbastanza word da contenere i registri da preservare
  2) **<font color="#7030a0">Salvare</font>** su stack i registri, ad offset multipli di 4 rispetto a sp

<u>NOTA:</u> conviene allocare tutto lo spazio assieme per avere offset costanti durante tutta l'esecuzione della funzione

- Alla fine della funzione: 
  1) **<font color="#ffff00">Ripristinare</font>** da stack i registri salvati, agli stessi offset usati precedentemente
  2) **<font color="#953734">Disallocare</font>** da stack lo stesso spazio allocato in precedenza
  3) **<font color="#00b050">Tornare</font>** alla funzione chiamante

Di seguito il codice standard per effettuare ciò di cui abbiamo discusso in questo paragrafo:

```
	addi sp, sp, -12    # allochiamo dello spazio per 3 word nello stack sottraendo 12
	sw ra, 8(sp)        # salvo ra nello stack (return address, il punto dove ritornare finita la fun)
	sw a0, 4(sp)        # salvo a0 nello stack con offset 4
	sw a1, 0(sp)        # salvo a1 nello stack con offset 0

	# corpo della funzione
	# posso chiamare jal
	# tranquillamente perché
	# salvo ra

	lw a1, 0(sp)        # ripristino i contenuti salvati nello stack nei loro registri
	lw a0, 4(sp)
	lw ra, 8(sp)
	addi sp, sp, 12     # disalloco dallo stack lo stesso spazio allocato in precedenza
	jr ra               # salto alla funzione chiamante
```

##### **Record di attivazione (Stack frame/activation record):**
Lo stack è usato anche in svariate applicazioni, tra cui: 
- Comunicare <font color="#00b050">ulteriori argomenti</font> oltre a0, ..., a7
- Comunicare <font color="#ffff00">ulteriori risultati</font> oltre a0 e a1
- Allocare <font color="#7030a0">variabili locali</font> alla procedura
Questo blocco prende il nome di **<font color="#ff0000">stack frame o activation record</font>**, ossia una parte della memoria che contiene i dati necessari alla funzione attualmente in esecuzione.
- E' allocato su stack <u>prima</u> della chiamata della funzione e rilasciato subito dopo
- Lo sp (stack pointer) si usa per puntare alla fine del record di attivazione (o stack frame) e varia allocando dati dinamicamente
- Il fp (frame pointer) si usa per puntare all'inizio del record di attivazione, resta fisso durante l'esecuzione della funzione

![[Pasted image 20250430154332.png]]

Ecco una schema di una chiamata, utile per memorizzare bene il procedimento: 
![[Pasted image 20250430154424.png]]

Esempio: calcola avgOfSquareAbsSub = $\frac {(|x|-|y|)^2+(|w|-|z|)^2}{2}$, squareAbsSub = $(|x|-|y|)^2$

```
.globl main
.data
A: .word 5 
B: .word 7 
C: .word 12
D: .word -8
.text
main: 
	lw a0, A
	lw a1, B
	lw a2, C
	lw a3, D
    
    jal avgOfSquareAbsSub

	li a7, 1               # system call = print
	ecall

	li a7, 10              # system call = exit
	ecall


avgOfSquareAbsSub:
	addi sp, sp, -28       # alloco nello stack lo spazio per 7 word
	sw ra, 0(sp)           # salvo ra nello stack per non perderlo nella chiamata annidata
	sw fp, 4(sp)           # salvo il frame pointer nello stack
	sw a0, 8(sp)           # salvo i contenuti dei registri nello stack per non perderli 
	sw a1, 12(sp)
	sw a2, 16(sp)
	sw a3, 20(sp)
	sw s1, 24(sp)

	jal squareAbsSub       # chiamo la funzione ausiliaria 
	mv s1, a0              # salvo a0 in s1

	# seconda chiamata con a2 e a3 togliendo dallo stack questi ultimi e inserendoli in a0 e a1
	lw a0, 16(sp)
	lw a1, 20(sp)

	jal squareAbsSub      # chiamo la funzione squareAbsSub
	add a0, s1, a0        # finisco di calcolare il numeratore
	srai a0, a0, 1        # shift logico a destra di 1, a0/2

	# ristoro lo stack modificato
	lw s1, 24(sp)
	lw fp, 4(sp)          # recupero il frame pointer
	lw ra, 0(sp)          # recupero il return address
	addi sp, sp, 28       # disalloco 28 unità di memoria
	ret                   # ritorno a0 

#-funzione ausiliaria--------------------------------------------------------------------------------------------
squareAbsSub: 
	addi sp, sp, -4 
	sw fp,(sp)

	bge a0, zero, pos_a0     # se a0 >= 0 salto a
	neg a0, a0         # faccio il valore assoluto di a0
	
pos_a0:
	bge a1, zero, pos_a1
	neg a1, a1

pos_a1:
	sub a0, a0, a1     # a0 = a0-a1
	mul a0, a0, a0     # a0^2

# ristoro lo stack modificato a inizio funzione senza modificare il parametro di ritorno (a0)
	lw fp, 0(sp)
	add sp, sp, 4
	ret     # ritorno a0 
```
