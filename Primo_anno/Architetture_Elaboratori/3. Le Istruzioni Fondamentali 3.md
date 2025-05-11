##### **If Then Else:**
Codifica di if (i == j) f = g + h; else f = g - h 

```
bne s3, s4, Else    # Vai a Else se i ≠ j 
add s0, s1, s2      # f = g + h (saltata se i ≠ j)
j Esci              # vai a Esci

Else: 
	sub s0, s1, s2
Esci
```

##### **Switch case:**

```
.data
	dest: .word caso0, caso1, ..., casoN
	A: .byte

.text
	lbu t0, A     # selezioniamo caso A
	slli t0, t0, 2     # t0 * 4
	la t1, dest   # indirizzo primo case
	add t1, t0, t1  # indirizzzo selezionato
	lw t1, (t1)   # carico indirizzo
	jr t1      # salto al registro

caso0:
	# codice caso
	j endSwitch

caso1:
	# codice caso
	j endSwitch

casoN:
	# codice caso
	j endSwitch

endSwitch:
	# codice seguente
	
```

##### **Realizzare iterazioni:**

###### **While Do:** 

```
.text        # inizializzazione del programma 

while: 
	 beqz t0, endWhile    # salta a endWhile se t0 == 0

     # codice da ripetere

	 j while    # ritorno a while (fulcro del loop)

endWhile:
	 # codice seguente
```

###### **For loop**

```
.text

xor t0, t0, t0      # azzero i, t0 lo utilizzo come indice del for loop, xor                        # tra tre elt uguali = 0
li t1, N            # loaddo un immediate in t1, t1 fungerà da limite del for

cicloFor: 
	bge t0, t1, endFor   # salto ad endFor se t0 (i) >= t1 (N) 
	# codice da ripetere
	addi t0, t0, 1    # t0 (i) += 1
	j cicloFor        # salto a cicloFor (loop)

endFor:
	# codice seguente
 
```


##### **ESEMPIO:**
Trova il max di un vettore

```
.data 
	vettore: .word 11, 35, 2, 17, 29, 95
	N: .word 6
.text
	la s0, vettore    # carico l'indirizzo del vettore in s0
	lw t0, (s0)       # carico il primo elt in t0 che fungerà da max
	la t1, N          # carico l'indirizzo di N in s1
	li t2, 1          # carico in t2 1. t2 fungerà da indice

for:
	bge t2, s1, endFor  # salto a endFor se t2 >= t1
	slli t3, t2, 2      # t3 = i*4 ci serve per calcolare l'offset ad ogni iter.
	add t3, t3, s0      # t3 = indirizzo vettore + i
	lw t4, (t3)         # metto in t4 vettore[i]
	ble t4, t0, else    # se elt <= max salto ad else 
	mv t0, t4           # altrimenti sposto in t0 (max) t4 (v[i])

else:
	addi t2, t2, 1     # i++
	j for              # salto a for 

endFor:
	# codice seguente
```
