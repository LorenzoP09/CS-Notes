Cosa è un vettore? Un vettore è una sequenza di N elementi di dimensioni uguali, consecutivi in memoria, indirizzabili per indice (da 0 a N-1). La dimensione totale del vettore si può calcolare moltiplicando la dimensione del vettore per la dimensione di un elemento. Si possono definire nella sezione *[[Le Istruzioni Fondamentali 2|.data]]* utilizzando un'etichetta per indicare l'indirizzo del primo elemento del vettore (quindi dove inizia in memoria). Per ottenere l'i-esimo elemento bisogna fare indirizzo per dimensione dell'elemento.

##### **Vettore di Word e Vettore di Half Word:**
Inizializzazione del vettore di word (con indice di partenzza 0x00001004):
```
vect: .word 3, -1    # Dichiaro un vettore di tipo word di 2 elementi

# 0x00001004 -> 0x3
# 0x00001008 -> 0xffffffff
```

In memoria si mostra così:
![[Pasted image 20250429101016.png]]

Inizializzazione del vettore di half word (con indice di partenza 0x00001000):
```
vect: .half 3, -1
# 0x00001000 -> 0x3
# 0x00001002 -> 0xffffffff
```

In memoria si mostra così:
![[Pasted image 20250429101016.png]]

##### **Vettori di byte in memoria:**
Un vettore di byte può essere inizializzato così: 
```
label1: .byte 1,2,3,4,5,6,7,8,9
```

![[Pasted image 20250429101735.png]]

Grazie ai vettori di byte possiamo creare delle "stringhe" tramite la codifica ascii, infatti possono essere inizializzate così:
```
label2: .asciiz "Sopra la panca"
```

![[Pasted image 20250429101833.png]]

##### **Endianess:**
Il concetto di Endianess (se un dato sistema è little endian o big endian) ha a che fare con:
- Indirizzamento in memoria - ogni indirizzo specifica il singolo byte
- Come i byte di una word sono ordinati in memoria

L'architettura RISC-V permette l'ordinamento dei byte di una word in due modi:
- **Big endian:** I byte della word sono memorizzati dal most significant byte al least significant byte
- **Little endian:** I byte della word sono memorizzati dal least significant byte al most significant byte

Esempi:
```
.text
word1: .word 0x1020304
word2: .word 0x4321
```

In Big Endian:
- word1: 01 02 03 04
- word2: 00 00 43 21

In Little Endian:
- word1: 04 03 02 01
- word2: 21 43 00 00 

##### **Accesso agli elementi per indice:**
*Esempio:* frammento che calcola l'indirizzo di un elemento in un vettore di word
```
# t0 = indice elemento
# t1 = indirizzo del vettore
# in t2 si ottiene indirizzo dell'elemento 

# la t1, vect    necessaria se il vettore è allocato staticamente (nella sezione .data)

slli t2, t0, 2   # moltiplicazione per 4 -> 4 byte shiftati di 2 
add t2, t2, t1   # indirizzo del vettore (t1) + offset (t2)
lw s0, (t2)      # carico la word in vect[t2] in s0
```

##### **Scansione di un vettore:**
Nei cicli si possono usare due stili di scansione di un vettore:
- *Scansione per indice:* 
  - Pro:
    1) Si lavora direttamente su indirizzi di memoria
    2) Ci sono meno calcoli nel ciclo
  - Contro:
     1) Bisogna convertire ogni volta l'indice nel corrispondente offset in byte

- Scansione per puntare (ovvero manipolando direttamente dalla dimensione degli elementi)
  - Pro: 
     1) Si lavora direttamente su indirizzi di memoria
     2) Ci sono meno calcoli nel ciclo
  - Contro: 
     1) Non si ha a disposizione l'indice dell'elemento
     2) L'incremento del puntatore dipende dalla dimensione degli elementi
     3) Bisogna calcolare l'indirizzo successivo all'ultimo elemento

*Esempio con indice:* somma degli elt di un vettore di word a posizione divisibile per 3
```
.data 
	vettore: .word 1,2,3,4,5,6,7,8,9  # vettore da sommare 
	N: .word 9   # lunghezza array
	Somma: .word 0     # risultato

.text
	main:
		li t0, 0       # loaddo immediate: i = 0
		lw t1, N       # carico in t1 N
		li t2, 0       # inizializzo t2 (che userò per la somma) a 0
	loop:
		bge t0, t1, fine    # il ciclo finisce se t0>=t1
		slli t3, t0, 2      # offset = i*4
		la t4, vettore      # ricavo l'indirizzo di memoria del vettore
		add t3, t3, t4      # t3 = indirizzo del vettore + offset
		lw t3, (t3)         # lettura di vettore[i]
		add t2, t2, t3      # somma += vettore[i]
		addi t0, t0, 3      # i += 3
		j loop
	fine: 
		la t0, Somma        # carica l'indirizzo di Somma
		sw t2, (t0)         # memorizzo il risultato
		
```

*Esempio con puntatori:* stesso esercizio di prima
```
.data 
	vettore: .word 1,2,3,4,5,6,7,8,9  # vettore da sommare 
	N: .word 9   # lunghezza array
	Somma: .word 0     # risultato

.text
	main: 
		lw t1, N      # lettura di N 
		la t0, vettore   # carico l'indirizzo del vettore in t0
		slli t1, t1, 2   # dimensione = N * 4
		add t1, t1, t0   # fine = ind.vettore + dim
		li t2, 0         # somma = 0
	loop: 
		bge t0, t1, fine   # se t0>=t1 salto a fine
		lw t3, (t0)        # lettura di vettore[i]
		add t2, t2, t3     # somma += vettore[i]
		addi t0, t0, 12    # i+=3*dim_elemento (9)
		j loop             # salto a loop
	fine:
		la t0, Somma       # carica l'indirizzo di Somma
		sw t2, (t0)        # memorizzo il risultato
```

##### **Matrici, Vettori di vettori:**
Una matrice MxN è una successione di M vettori, ciascuno di N elementi: 
- Il numero di elementi totali è: ==MxN==
- La dimensione totale in byte è: ==M x N x dimensione_elemento==
- La si definisce staticamente come un vettore contenente M x N elementi uguali

```

```