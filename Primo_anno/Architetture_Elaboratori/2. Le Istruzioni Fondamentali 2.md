##### **Organizzazione della memoria:**
![[Pasted image 20250414173758.png]]

*Stack Pointer (x2, sp):*
- Per le chiamate nidificate
- per le variabili locali delle funzioni
- Si trova nella sezione dedicata allo stack

*Global Pointer (gp):*
Per gestire i dati dinamici non-locali allocati in runtime es. in C malloc(), free(), realloc()

##### **Il set di istruzioni (cosa la CPU sa fare):**
Le fasi di esecuzione di un'istruzione sono:

1) *Fetch:* Caricamento dell'istruzione (Dalla posizione indicata dal PC)
2) *Decodifica:* Riconoscimento dell'istruzione, la CU attiva le parti funzionali necessarie
3) *Load:* Caricamento di eventuali argomenti a seconda dei modi di indirizzamento
4) Esecuzione dell'istruzione da parte dell'ALU
5) *Store:* Salvataggio del risultato in memoria o in un registro
6) Aggiornamento del Program Counter

Tipologie di istruzioni:

- LOAD/STORE: Trasferiscono dati da/verso la memoria
  Es: lb, lbu, lw, ...

- Logico/Aritmetiche: Svolgono calcoli aritmetici e logici
  Es: add, and, sub, ...

- Salti Condizionati e incondizionati: Controllano il flusso logico di esecuzione
  Es: beq, bge, bgeu, ...

- Gestione delle eccezioni/interrupt: Salvataggio dello stato e suo ripristino
- Istruzioni di trasferimento dati

##### **Codifica delle istruzioni:**
La codifica dell'istruzione deve indicare:

- Quale operazione va svolta (Opcode)
- Quali argomenti sono necessari
- Dove mettere il risultato

Quindi di seguito vediamo come codificare gli argomenti di un'istruzione, ossia i possibili modi di indirizzamento.

###### **Modi di indirizzamento standard:**
- Immediato:
  1) Valore costante modificato nell'istruzione stessa
  2) 0 accessi alla memoria, limitato dalla dimensione dell'istruzione
  
- A registro:
  1) Il registro contiene l'indirizzo di memoria
  
- A spiazzamento (con offset):
  1) Valore costante codificato nell'istruzione
  2) Registro contiene il registro con l'indirizzo base dello spiazzamento
  3) Può indicizzare un byte/mezza word/word
  
- Relativo al program counter:
  1) Valore costante codificato nell'istruzione
  2) Il valore base è il vettore attuale del PC
  3) Può indicizzare solo parole (istruzioni)

##### **L'architettura RISC-V:**
L'architettura RISC-V è caratterizzata da word da 32 bit, spazio di indirizzamento da 32 bit (4GByte) e interi in complemento a 2 su 32 bit. Quindi è possibile rappresentare interi nel range $[-2^{31},\space2^{31}-1]$. Inoltre possiede 32 indirizzi di uso generale.

- CPU: ALU e programma:
  1) 32 registri + program counter
  2) Ha accesso alla memoria
  
- CSR: trap, eccezioni, Virtual memory
  1) Registri di controllo e di stato
  2) Permette di tenere traccia delle eccezioni/interrupt del programma 
  
- FPU: per calcoli in virgola mobile:
  1) Estensione F (single) o D (double)
  2) 32 registri da 32 bit f0-f31, d0-d31
  3) Ha accesso alla memoria

Di seguito ecco i 32 registri della CPU RISC-V e il loro utilizzo specifico:

![[Pasted image 20250414190108.png]]

![[Pasted image 20250414190202.png]]

###### **Le Estensioni:**
![[Pasted image 20250414190955.png]]
Queste sono le estensioni dell'architettura RISC-V:
- L'estensione più semplice ha solo 51 istruzioni
- Tutte le istruzioni di tutte le estensioni sono 184
- L'estensione G (Non presente all'interno della tabella) include tutte le istruzioni

##### **Istruzioni Base:**
###### **Somma e sottrazione**
Sia a = (b - c) + (d - e)  con a = s0, b = s1, c = s2, d = s3, e = s4

```
addi s1, zero, 4   # variabile = 0 + costante
addi s2, zero, 3
addi s3, zero, 9
addi s4, zero, 4

sub t0, s1, s2      # (b - c)
sub t1, s3, s4      # (d - e)
add s0, t0, t1      # a = t1 + t0
```

###### **Movimentazioni di dati da/per memoria:**
Sia n una variabile il cui valore è nella locazione di memoria indicata da s6 e sia v un vettore la cui base è registrata in s5. Scrivere le istruzioni in codice RISC-V che eseguano questo comando ad alto livello: v[12] = n + v[6]

```
lw t0, 24(s5)  # prendo il contenuto v[6] e lo salvo in t0
lw t1, (s6)    # prendo il contenuto di s6 e lo salvo in t1
add t0, t1, t0 # eseguo la somma: t0 = N (contenuto in t0) + v[6]
sw t0, 48(s5)  # salvo il risultato contenuto in t0 in v[12]
```

##### **Operatori logici:**

```
sll t0, s1, 0x1    # shift left logic
srl t0, s1, 0x2    # shift right logic 
and t0, s1, s2     # and between s1 and s2 in t0
andi t0, x1, 0x3   # I type and between x1 and 0x3 in t0
or t0, s1, s2      # or between s1 and s2 in t0
ori t0, s1, 0x4    # I type or between s1 and 0x4 in t0
```

##### **Comparazione e salto condizionato:**

```
beq s1, s2, etichetta     # branch se uguali 
bne s1, s2, etichetta     # branch se non uguali
bge s1, x0, etichetta     # branch se minore uguale a 0
bge x0, s1, etichetta     # branch se maggiore uguale a 0
blt s1, x0, etichetta     # branch se minore di 0
bgt s1, x0, etichetta     # branch se maggiore di 0


# other examples
slt s0, s1, s2            # set s0 to 1 if s1 is less than s2
slti s0, s1, 10           # set s0 to 1 if s1 is less than 10
```


*Esempio:*

```
or t4, zero, t0       # faccio un or fra zero e t0 per ricavare il max 

CheckB:
	blt t4, t1, UpdateB   # se t4<t1 brancho a UpdateB
 	jal CheckC            # salto a CheckC 
	
UpdateB:
	or t4, zero, t1       # ricavo il max e lo metto in t4
	
CheckC:
	blt t4, t2, UpdateC   # se t4<t2 salto a UpdateC
	jal CheckD            # sennò salto a CheckD

UpdateC:
	or t4, zero, t2       # il max diventa t2
	
CheckD:
	blt t4, t3, UpdateD   # se t4 < t3 salto a UpdateD
	jal End               # salto a End

UpdateD:
	or t4, zero t3        # il max diventa t3

End:
	sw t4, rez, t5       # salvo la word t4 in t5[rez]

```

##### **Direttive Principali per l'assemblatore:**

- .data: Definizione dei dati statici
- .text: Definizione del programma
- .asciiz: Stringa terminata da \0
- .byte: Sequenza di byte
- .double: Sequenza di double
- .float: Sequenza di float
- -half: Sequenza di half words
- .word: Sequenza di words


