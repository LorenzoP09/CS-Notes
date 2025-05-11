##### **Introduzione:**
![[Pasted image 20250414160045.png]]

*Importante:*
- La memoria in RISC-V è **indicizzata al byte**
- Se sono all'indirizzo t e devo leggere la word successiva l'incremento è t+4, questo perché una word sono 4 byte, ossia 32 bit
- Il RISC-V non ha vincolo di allineamento
- Gli indirizzi sono little endian (byte meno significativo è memorizzato per primo, nella locazione con indirizzo minore)

##### **Istruzioni aritmetiche:**
![[Pasted image 20250414160857.png]]

Queste sono i comandi per effettuare operazioni aritmetiche fra valori (somma, somma immediata e sottrazione). Ne segue un esempio di applicazione:

Dobbiamo eseguire in assembly RISC-V questa espressione:
f = (g+h) - (i+j)

```
add x5, x20, x21      # x5 = g + h
add x6, x22, x23      # x6 = i + j
sub x19, x5, x6       # x19 = x5 - x6
```

Ecco ulteriori istruzioni importanti per programmare in assembly RISC-V:

![[Pasted image 20250414161314.png]]
![[Pasted image 20250414161327.png]]

##### **Rappresentazione dell'istruzione Registro (R-type):**
Ogni istruzione in assembly RISC-V di tipo R-type può essere rappresentata così:

![[Pasted image 20250414161450.png]]

- *func7:* Estensione del codice operativo, usata per disambiguare operazioni avanzate
- *rs2, rs1:* Sono i registri sorgente, ossia i registri da cui si leggono i valori da elaborare
- *funct3:* Specifica una variante dell'operazione
- *rd:* E' il registro di destinazione, ossia dove viene scritto il risultato
- *opcode:* Identifica il tipo base dell'istruzione

*Esempio:* add x9, x20, x21

| funct7  | rs2   | rs1   | funct3 | rd    | opcode  |
| ------- | ----- | ----- | ------ | ----- | ------- |
| 0       | 21    | 20    | 0      | 9     | 51      |
| 0000000 | 10101 | 10100 | 000    | 01001 | 0110011 |
$00000001010110100000010010110011_2$ = $015A04B3_{16}$ 

##### **Rappresentazione dell'istruzione Immediato (I-type):**
Ogni istruzione in assembly RISC-V di tipo I-type può essere rappresentata così:

![[Pasted image 20250414163444.png]]

- *Immediate:* E' un valore costante incorporato direttamente nell'istruzione e viene utilizzato come operando nelle istruzioni
- *rs1:* E' il registro sorgente da cui leggiamo il valore
- *funct3:* Specifica una variante dell'operazione
- *rd:* E' il registro di destinazione, ossia dove viene scritto il risultato
- *opcode:* Identifica il tipo base dell'istruzione

##### **Rappresentazione dell'istruzione Store (S-type):** 

![[Pasted image 20250414164422.png]]

- *immediate*: Campo (valore costante) diviso in due parti (imm[11:5] e imm[4:0]) per un offset a 12 bit
- *rs2, rs1:* Sono i registri sorgente, ossia i registri da cui si leggono i valori da elaborare
- *rd:* E' il registro di destinazione, ossia dove viene scritto il risultato
- *funct3:* Specifica una variante dell'operazione
- *opcode:* Identifica il tipo base dell'istruzione

##### **Piccolo Sommario istruzioni principali:**

![[Pasted image 20250414164850.png]]

**R-Type (Tipo a registro):** 
- Senza accesso a memoria 
- Istruzioni aritmetico/logiche

```
add x9, x20, x21   # x9 = x20 + x21
```

**I-type (Tipo immediato):**
- Load
- Somma immediata

```
addi x1, x2, 1   # x1 = x2 + 1
lw x9, 120(x10)  # x9 = MEM[x10+120], load word
```

**S-type (Tipo Store):**
- Salvataggio registro in memoria

```
sw x9, 120(x10)  # MEM[x10+120] = x9, save word
```

**U-type (Tipo immediato grande):**
- Per movimentare parti immediate con tanti bit (utile per salti assoluti)
- può essere usato insieme ad addi per costruire costanti a 32 bit in due istruzioni

```
lui x5, 0x12345     # load upper immediate 
addi x5, x5, 0x678  # x5 = 0x12345 + 0x678
```

**UJ-type (Variante di U):**
- Per saltare e salvare il PC + 4 in un registro (jump and link)
- Indirizzo di destinazione: PC + immediate x 2 (quindi imm[0] non serve) $\pm 2^{20}$ byte dal PC

```
jal ra, funzione    # salta a funzione e salva l'indirizzo della funzione                      # chiamante in ra
```

**SB-type:**
- Due operandi da confrontare e indirizzo di branch nella parte immediata
- Indirizzo di destinazione: PC + immediate x2 (quindi imm[0] non serve) $\pm 2^{12}$ dal PC

```
beq s1, s2, C
```