### Paulo Araya - Rut: 21.918.080-2
### Roger Villarroel - Rut: 21.994.625-2

##### Problema 1:
Transforme los siguientes valores en sistema decimal a base binaria, octal y hexadecimal utilizando solo el método de las divisiones sucesivas. Para la parte fraccionaria, si corresponde, obtenga mínimo 6 cifras aproximando las multiplicaciones a 4 cifras.

1. $421486_{10}$
2. $3927.67291_{10}$

**Desarrollo 1.1:**
*   **Binario (Base 2):**
    $$
    \begin{aligned}
    421486 \div 2 &= 210743, r = 0 \\
    210743 \div 2 &= 105371, r = 1 \\
    105371 \div 2 &= 52685, r = 1 \\
    52685 \div 2 &= 26342, r = 1 \\
    26342 \div 2 &= 13171, r = 0 \\
    13171 \div 2 &= 6585, r = 1 \\
    6585 \div 2 &= 3292, r = 1 \\
    3292 \div 2 &= 1646, r = 0 \\
    1646 \div 2 &= 823, r = 0 \\
    823 \div 2 &= 411, r = 1 \\
    411 \div 2 &= 205, r = 1 \\
    205 \div 2 &= 102, r = 1 \\
    102 \div 2 &= 51, r = 0 \\
    51 \div 2 &= 25, r = 1 \\
    25 \div 2 &= 12, r = 1 \\
    12 \div 2 &= 6, r = 0 \\
    6 \div 2 &= 3, r = 0 \\
    3 \div 2 &= 1, r = 1 \\
    1 \div 2 &= 0, r = 1 \\
    \text{Resultado: } & 1100110111001101110_2
    \end{aligned}
    $$
*   **Octal (Base 8):**
    $$
    \begin{aligned}
    421486 \div 8 &= 52685, r = 6 \\
    52685 \div 8 &= 6585, r = 5 \\
    6585 \div 8 &= 823, r = 1 \\
    823 \div 8 &= 102, r = 7 \\
    102 \div 8 &= 12, r = 6 \\
    12 \div 8 &= 1, r = 4 \\
    1 \div 8 &= 0, r = 1 \\
    \text{Resultado: } & 1467156_8
    \end{aligned}
    $$
*   **Hexadecimal (Base 16):**
    $$
    \begin{aligned}
    421486 \div 16 &= 26342, r = 14 \rightarrow E \\
    26342 \div 16 &= 1646, r = 6 \\
    1646 \div 16 &= 102, r = 14 \rightarrow E \\
    102 \div 16 &= 6, r = 6 \\
    6 \div 16 &= 0, r = 6 \\
    \text{Resultado: } & 66E6E_{16}
    \end{aligned}
    $$

**Desarrollo 1.2:**
*   **Conversión a Hexadecimal (Base 16):**
    *   Parte Entera ($3927$):
        $$
        \begin{aligned}
        3927 \div 16 &= 245, r = 7 \\
        245 \div 16 &= 15, r = 5 \\
        15 \div 16 &= 0, r = 15 \rightarrow F \\
        \text{Entero: } & F57_{16}
        \end{aligned}
        $$
    *   Parte Fraccionaria ($0.6729$):
        $$
        \begin{aligned}
        0.6729 \times 16 &= 10.7664 \rightarrow A \\
        0.7664 \times 16 &= 12.2624 \rightarrow C \\
        0.2624 \times 16 &= 4.1984 \rightarrow 4 \\
        0.1984 \times 16 &= 3.1744 \rightarrow 3 \\
        0.1744 \times 16 &= 2.7904 \rightarrow 2 \\
        0.7904 \times 16 &= 12.6464 \rightarrow C \\
        \text{Resultado: } & F57.AC432C_{16}
        \end{aligned}
        $$
*   **Conversión a Octal (Base 8):**
    *   Parte Entera ($3927$):
        $$
        \begin{aligned}
        3927 \div 8 &= 490, r = 7 \\
        490 \div 8 &= 61, r = 2 \\
        61 \div 8 &= 7, r = 5 \\
        7 \div 8 &= 0, r = 7 \\
        \text{Entero: } & 7527_8
        \end{aligned}
        $$
    *   Parte Fraccionaria ($0.6729$):
        $$
        \begin{aligned}
        0.6729 \times 8 &= 5.3832 \rightarrow 5 \\
        0.3832 \times 8 &= 3.0656 \rightarrow 3 \\
        0.0656 \times 8 &= 0.5248 \rightarrow 0 \\
        0.5248 \times 8 &= 4.1984 \rightarrow 4 \\
        0.1984 \times 8 &= 1.5872 \rightarrow 1 \\
        0.5872 \times 8 &= 4.6976 \rightarrow 4 \\
        \text{Resultado: } & 7527.530414_8
        \end{aligned}
        $$
*   **Conversión a Binario (Base 2):**
    *   Parte Entera ($3927$):
        $$
        \begin{aligned}
        3927 \div 2 &= 1963, r = 1 \\
        1963 \div 2 &= 981, r = 1 \\
        981 \div 2 &= 490, r = 1 \\
        490 \div 2 &= 245, r = 0 \\
        245 \div 2 &= 122, r = 1 \\
        122 \div 2 &= 61, r = 0 \\
        61 \div 2 &= 30, r = 1 \\
        30 \div 2 &= 15, r = 0 \\
        15 \div 2 &= 7, r = 1 \\
        7 \div 2 &= 3, r = 1 \\
        3 \div 2 &= 1, r = 1 \\
        1 \div 2 &= 0, r = 1 \\
        \text{Entero: } & 111101010111_2
        \end{aligned}
        $$
    *   Parte Fraccionaria ($0.6729$):
        $$
        \begin{aligned}
        0.6729 \times 2 &= 1.3458 \rightarrow 1 \\
        0.3458 \times 2 &= 0.6916 \rightarrow 0 \\
        0.6916 \times 2 &= 1.3832 \rightarrow 1 \\
        0.3832 \times 2 &= 0.7664 \rightarrow 0 \\
        0.7664 \times 2 &= 1.5328 \rightarrow 1 \\
        0.5328 \times 2 &= 1.0656 \rightarrow 1 \\
        \text{Resultado: } & 111101010111.101011_2
        \end{aligned}
        $$

---

##### Problema 2 
Transforme los siguientes valores a base decimal con el método de la multiplicación de dígitos, y luego a binaria, octal y hexadecimal (según corresponda) utilizando el método de las agrupaciones. Aproxime el valor de las multiplicaciones a 5 cifras.

1. $1011000101010101_2$
2. $217462_8$
3. $28C3B1_{16}$

**Desarrollo 2.1:**
*   **Decimal:** $1\cdot 2^{15} + 1\cdot 2^{13} + 1\cdot 2^{12} + 1\cdot 2^8 + 1\cdot 2^6 + 1\cdot 2^4 + 1\cdot 2^2 + 1\cdot 2^0 = 32768 + 8192 + 4096 + 256 + 64 + 16 + 8 + 1 = 45401_{10}$
*   **Hexadecimal (grupos de 4):** $(1011)(0001)(0101)(0101)_2 = B155_{16}$
*   **Octal (grupos de 3):** $(001)(011)(000)(101)(010)(101)_2 = 130525_8$

**Desarrollo 2.2 ($217462_8$):**
*   **Decimal:** $2\cdot 8^5 + 1\cdot 8^4 + 7\cdot 8^3 + 4\cdot 8^2 + 6\cdot 8^1 + 2\cdot 8^0 = 65536 + 4096 + 3584 + 256 + 48 + 2 = 73522_{10}$
*   **Binario (agrupación de 3):** $2|1|7|4|6|2 \rightarrow 010|001|111|100|110|010_2$
*   **Hexadecimal (agrupación de 4):** $(0001)(0001)(1111)(0011)(0010)_2 = 11F32_{16}$

**Desarrollo 2.3 ($28C3B1_{16}$):**
*   **Decimal:** $2\cdot 16^5 + 8\cdot 16^4 + 12\cdot 16^3 + 3\cdot 16^2 + 11\cdot 16^1 + 1\cdot 16^0 = 2097152 + 524288 + 49152 + 768 + 176 + 1 = 2671537_{10}$
*   **Binario (agrupación de 4):** $2|8|C|3|B|1 \rightarrow 0010|1000|1100|0011|1011|0001_2$
*   **Octal (agrupación de 3):** $(001)(010)(001)(100)(001)(110)(110)(001)_2 = 12141661_8$

---

##### Problema 3 
Transforme el siguiente número al formato de coma flotante (IEEE 754) de 32 bits.
$(127493.879381)_{10}$

**Desarrollo 3:**
1.  **Binario:** $11111001000000101.11100001..._2$
2.  **Normalización:** $1.11110010000001011110000... \times 2^{16}$
3.  **Exponente:** $E = 16 + 127 = 143 = 10001111_2$
4.  **Signo:** $0$ (Positivo)
5.  **Mantisa (23 bits):** $11110010000001011110000$
6.  **Resultado Hex:** $48F902F0_{16}$

---

##### Problema 4 
Codifique las siguientes palabras binarias con Hamming utilizando paridad Par.

1. $0010$
2. $0101010011$

**Desarrollo 4.1 ($0010$):**
*   Ubicación de bits: $P_1 P_2 d_3 P_4 d_5 d_6 d_7$
*   Bits de datos ($k=4$): $d_3=0, d_5=0, d_6=1, d_7=0$
*   Cálculo de paridad (Par):
    $$
    \begin{aligned}
    P_1 &= d_3 \oplus d_5 \oplus d_7 = 0 \oplus 0 \oplus 0 = 0 \\
    P_2 &= d_3 \oplus d_6 \oplus d_7 = 0 \oplus 1 \oplus 0 = 1 \\
    P_4 &= d_5 \oplus d_6 \oplus d_7 = 0 \oplus 1 \oplus 0 = 1 \\
    \end{aligned}
    $$
*   **Código:** $0101010$

**Desarrollo 4.2 ($0101010011$):**
*   10 bits -> $2^k \geq 10 + 1 + k$: requiere 4 bits de paridad ($P_1, P_2, P_4, P_8$), total 14 bits.
*   Bits de datos: $d_3=0, d_5=1, d_6=0, d_7=1, d_9=0, d_{10}=1, d_{11}=0, d_{12}=0, d_{13}=1, d_{14}=1$
*   Cálculo de paridad (Par):
    $$
    \begin{aligned}
    P_1 &= d_3 \oplus d_5 \oplus d_7 \oplus d_9 \oplus d_{11} \oplus d_{13} = 0 \oplus 1 \oplus 1 \oplus 0 \oplus 0 \oplus 1 = 1 \\
    P_2 &= d_3 \oplus d_6 \oplus d_7 \oplus d_{10} \oplus d_{11} \oplus d_{14} = 0 \oplus 0 \oplus 1 \oplus 1 \oplus 0 \oplus 1 = 1 \\
    P_4 &= d_5 \oplus d_6 \oplus d_7 \oplus d_{12} \oplus d_{13} \oplus d_{14} = 1 \oplus 0 \oplus 1 \oplus 0 \oplus 1 \oplus 1 = 0 \\
    P_8 &= d_9 \oplus d_{10} \oplus d_{11} \oplus d_{12} \oplus d_{13} \oplus d_{14} = 0 \oplus 1 \oplus 0 \oplus 0 \oplus 1 \oplus 1 = 1 \\
    \end{aligned}
    $$
*   **Código ($P_1 P_2 d_3 P_4 d_5 d_6 d_7 P_8 d_9 d_{10} d_{11} d_{12} d_{13} d_{14}$):** $11001011010011$

---

##### Problema 5 
Compruebe si las siguientes palabras en código Hamming se encuentran correctas o no. Se utiliza paridad Par.
1. $1001010$
2. $100111001101$

5.1:
*   Ubicación: $P_1(1), P_2(0), d_3(0), P_4(1), d_5(0), d_6(1), d_7(0)$
*   $C_1 = P_1 \oplus d_3 \oplus d_5 \oplus d_7 = 1 \oplus 0 \oplus 0 \oplus 0 = 1$
*   $C_2 = P_2 \oplus d_3 \oplus d_6 \oplus d_7 = 0 \oplus 0 \oplus 1 \oplus 0 = 1$
*   $C_4 = P_4 \oplus d_5 \oplus d_6 \oplus d_7 = 1 \oplus 0 \oplus 1 \oplus 0 = 0$
*   Error: $C_4 C_2 C_1 = 011_2 = 3$. Error en posición 3. El bit correcto es 1.
*   Arreglado: $1011010$

 5.2:
*   Ubicación: $P_1(1), P_2(0), d_3(0), P_4(1), d_5(1), d_6(1), d_7(0), P_8(0), d_9(1), d_{10}(1), d_{11}(0), d_{12}(1)$
*   $C_1 = P_1 \oplus d_3 \oplus d_5 \oplus d_7 \oplus d_9 \oplus d_{11} = 1 \oplus 0 \oplus 1 \oplus 0 \oplus 1 \oplus 0 = 1$
*   $C_2 = P_2 \oplus d_3 \oplus d_6 \oplus d_7 \oplus d_{10} \oplus d_{11} = 0 \oplus 0 \oplus 1 \oplus 0 \oplus 1 \oplus 0 = 0$
*   $C_4 = P_4 \oplus d_5 \oplus d_6 \oplus d_7 \oplus d_{12} = 1 \oplus 1 \oplus 1 \oplus 0 \oplus 1 = 0$
*   $C_8 = P_8 \oplus d_9 \oplus d_{10} \oplus d_{11} \oplus d_{12} = 0 \oplus 1 \oplus 1 \oplus 0 \oplus 1 = 1$
*   Error: $C_8 C_4 C_2 C_1 = 1001_2 = 9$. Error en posición 9. El bit correcto es 0.
*   Arreglado: $100111000101$

---
##### Problema 6:
**Salidas:**
*   **S1 S0 = 00:** No cargar.
*   **S1 S0 = 01:** Carga común (2W).
*   **S1 S0 = 10:** Carga rápida (15W).
*   **S1 S0 = 11:** Carga súper rápida (30W).

**Entradas:**
*   **A (Temperatura):** 0: Baja, 1: Alta.
*   **B C (Conexión):** 01: PC, 10: Transformador, 11: Inalámbrica. (00 NO EMITIDA).
*   **D E (Procesamiento):** 00: Stand by, 01: Eficacia, 10: Equilibrio, 11: Máxima.

**Reglas**
1.  **R1:** Si `DE = 11`, $\rightarrow$ `S1 S0 = 00`.
2.  **R2:** Si `BC = 01`, $\rightarrow$ `S1 S0 = 01`.
3.  **R3 (Si A = 1 y no es PC):**
    *   Si `DE = 10`  $\rightarrow$ `00`.
    *   Si `DE = 01` o `DE = 00`  $\rightarrow$ `01`.
    *   Excepción: Si `BC = 10` y `DE = 00` $\rightarrow$ `10`.
4.  **R4 (Si BC = 10 y A = 0):**
    *   Si `DE = 10`  $\rightarrow$ `10`.
    *   Demás modos (excepto `DE = 11`) $\rightarrow$ `11`.
5.  **R5 (Si BC = 11 y A = 0):**
    *   Si `DE = 00` $\rightarrow$ `11`.
    *   Si `DE = 01` $\rightarrow$ `10`.
    *   Si `DE = 10` $\rightarrow$ `01`.

**Tabla de Verdad :**

|  #  |  A  |  B  |  C  |  D  |  E  | S1  | S0  | Observación / Regla                  |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :----------------------------------- |
|  0  |  0  |  0  |  0  |  0  |  0  |  X  |  X  | XX             |
|  1  |  0  |  0  |  0  |  0  |  1  |  X  |  X  | XX  |
|  2  |  0  |  0  |  0  |  1  |  0  |  X  |  X  | XX             |
|  3  |  0  |  0  |  0  |  1  |  1  |  X  |  X  | XX             |
|  4  |  0  |  0  |  1  |  0  |  0  |  0  |  1  | R2                               |
|  5  |  0  |  0  |  1  |  0  |  1  |  0  |  1  | R2                               |
|  6  |  0  |  0  |  1  |  1  |  0  |  0  |  1  | R2                               |
|  7  |  0  |  0  |  1  |  1  |  1  |  0  |  0  | R1                           |
|  8  |  0  |  1  |  0  |  0  |  0  |  1  |  1  | R4               |
|  9  |  0  |  1  |  0  |  0  |  1  |  1  |  1  | R4               |
| 10  |  0  |  1  |  0  |  1  |  0  |  1  |  0  | R4                 |
| 11  |  0  |  1  |  0  |  1  |  1  |  0  |  0  | R1                           |
| 12  |  0  |  1  |  1  |  0  |  0  |  1  |  1  | R5               |
| 13  |  0  |  1  |  1  |  0  |  1  |  1  |  0  | R5               |
| 14  |  0  |  1  |  1  |  1  |  0  |  0  |  1  | R5                 |
| 15  |  0  |  1  |  1  |  1  |  1  |  0  |  0  | R1                           |
| 16  |  1  |  0  |  0  |  0  |  0  |  X  |  X  | XX             |
| 17  |  1  |  0  |  0  |  0  |  1  |  X  |  X  | XX             |
| 18  |  1  |  0  |  0  |  1  |  0  |  X  |  X  | XX             |
| 19  |  1  |  0  |  0  |  1  |  1  |  X  |  X  | XX |
| 20  |  1  |  0  |  1  |  0  |  0  |  0  |  1  | R2                               |
| 21  |  1  |  0  |  1  |  0  |  1  |  0  |  1  | R2                               |
| 22  |  1  |  0  |  1  |  1  |  0  |  0  |  1  | R2                               |
| 23  |  1  |  0  |  1  |  1  |  1  |  0  |  0  | R1                           |
| 24  |  1  |  1  |  0  |  0  |  0  |  1  |  0  | R3  |
| 25  |  1  |  1  |  0  |  0  |  1  |  0  |  1  | R3            |
| 26  |  1  |  1  |  0  |  1  |  0  |  0  |  0  | R3              |
| 27  |  1  |  1  |  0  |  1  |  1  |  0  |  0  | R1                           |
| 28  |  1  |  1  |  1  |  0  |  0  |  0  |  1  | R3            |
| 29  |  1  |  1  |  1  |  0  |  1  |  0  |  1  | R3            |
| 30  |  1  |  1  |  1  |  1  |  0  |  0  |  0  | R3              |
| 31  |  1  |  1  |  1  |  1  |  1  |  0  |  0  | R1                           |

**Mapas de Karnaugh (DE \ BC):**

**Salida S1 (A=0):**

| DE \ BC | 00  | 01  | 11  | 10  |
| :-----: | :-: | :-: | :-: | :-: |
| **00**  |  X  |  0  |  1  |  1  |
| **01**  |  X  |  0  |  1  |  1  |
| **11**  |  X  |  0  |  0  |  0  |
| **10**  |  X  |  0  |  0  |  1  |
**Salida S1 (A=1):**

| DE \ BC | 00  | 01  | 11  | 10  |
| :-----: | :-: | :-: | :-: | :-: |
| **00**  |  X  |  0  |  0  |  1  |
| **01**  |  X  |  0  |  0  |  0  |
| **11**  |  X  |  0  |  0  |  0  |
| **10**  |  X  |  0  |  0  |  0  |

**Salida S0 (A=0):**

| DE \ BC | 00  | 01  | 11  | 10  |
| :-----: | :-: | :-: | :-: | :-: |
| **00**  |  X  |  1  |  1  |  1  |
| **01**  |  X  |  1  |  0  |  1  |
| **11**  |  X  |  0  |  0  |  0  |
| **10**  |  X  |  1  |  1  |  0  |

**Salida S0 (A=1):**

| DE \ BC | 00  | 01  | 11  | 10  |
| :-----: | :-: | :-: | :-: | :-: |
| **00**  |  X  |  1  |  1  |  0  |
| **01**  |  X  |  1  |  1  |  1  |
| **11**  |  X  |  0  |  0  |  0  |
| **10**  |  X  |  1  |  0  |  0  |

**Funciones Booleanas Simplificadas:**
$$
\begin{aligned}
S1 = 
&\overline{A} \cdot B \cdot \overline{D} + 
B \cdot \overline{C} \cdot \overline{D} \cdot \overline{E} +
\overline{A} \cdot B\cdot \overline{C}  \cdot \overline{E} \\
\end{aligned}
$$
$$
S0 = \overline{D} \cdot \overline{E} + C \cdot \overline{D} + \overline{B} \cdot C + A \cdot C \cdot \overline{D} + A \cdot B \cdot E
$$

---

