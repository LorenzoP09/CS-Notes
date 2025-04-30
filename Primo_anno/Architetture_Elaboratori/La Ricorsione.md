Quando si può utilizzare una funzione ricorsiva per risolvere un problema? 
- Se esiste una soluzione conosciuta per lo stesso problema, di piccole dimensioni (**<font color="#ff0000">Caso base</font>**)
- Se esiste un modo di ottenere la soluzione di un problema di dimensione maggiore <font color="#ff0000">a partire dalla soluzione dello stesso problema di dimensione minore </font>. Da questa definizione ricaviamo il <font color="#ffff00">caso ricorsivo</font> che è formato da: 
  1) <font color="#ffff00">Riduzione</font> del problema in problemi più piccoli
  2) <font color="#ffff00">Chiamata ricorsiva</font> della funzione per computare i problemi più piccoli
  3) Elaborazione delle soluzioni più piccole per ottenere la <font color="#ffff00">soluzione del problema originale</font>

*Esempio* iterativo: Fattoriale di N:

```
.data 
N: .word 10
rez: .word 0

.text
	lw a0, N 
	jal factorial

	la a6, rez
	sw a0, (a6)

	li a7, 1 
	ecall

	li a7, 10
	ecall

-funzione ausiliaria-------------------------------------------------------------------------------------
factorial:
	li a7, 1
While:
	beqz a0, EndWhile
	mul a7, a7, a0
	addi a0, a0, -1
	j While
EndWhile:
	mv a0, a7
	ret    
```


---

Implementazione ricorsiva:

```
.data 
N: .word 10
rez: .word 0

.text
	lw a0, N 
	jal factorial

	la a6, rez
	sw a0, (a6)

	li a7, 1 
	ecall

	li a7, 10
	ecall

-funzione ausiliaria-------------------------------------------------------------------------------------
factorial:
	beqz a0, baseCase

recursiveStep:
	# salvo nello stack i dati per non perderli durante le chiamate ricorsive
	addi sp, sp, -8
	sw ra, 0(sp)
	sw a0, 4(sp)

	addi a0, a0, -1
	jal factorial

	mv a1, a0 
	
	# recupero i dati sullo stack
	lw a0, 4(sp)
	lw ra, 0(sp)
	addi sp, sp, 8

	mul a0, a1, a0
	jr ra

baseCase:
	li a0, 1
	ret
```

L'esecuzione di un programma ricorsivo si svolgerà più o meno così: 

![[Pasted image 20250430181442.png]]

