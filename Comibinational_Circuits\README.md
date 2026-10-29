[Combinational_Circuits.docx](https://github.com/user-attachments/files/34137240/Combinational_Circuits.docx)


# Digital Electronics Notes Summary: Combinational Circuits

This repository provides a clean, comprehensive summary of fundamental combinational circuits, complete with Markdown tables and plain-text layout diagrams optimized for GitHub readability.

---

## 1. Arithmetic Circuits

### 1.1 Half Adder (HA)
Adds two 1-bit binary inputs (X, Y) to produce **SUM** (S) and **CARRY** (C).

*   **Boolean Expressions:**
    *   \(S = \overline{X}Y + X\overline{Y} = X \oplus Y\)
    *   C = XY

#### Truth Table

| X | Y | SUM (S) | CARRY (C) |
|---|---|---------|-----------|
| 0 | 0 |    0    |     0     |
| 0 | 1 |    1    |     0     |
| 1 | 0 |    1    |     0     |
| 1 | 1 |    0    |     1     |

#### Logic Diagram
```text
X ──┬─────────┬──┐__
    │         │  |  \
    │   __    └──|   )─── SUM (X ⊕ Y)
Y ──┼──┼  \      |__/
    │  │   )─────┴──┐
    └──│__/         │    __
       │            ├───|  \
       └────────────┴───|   )── CARRY (XY)
                        |__/
```

---

### 1.2 Full Adder (FA)
Adds three 1-bit binary inputs (X, Y, Z) to produce **SUM** (S) and **CARRY** (C).

*   **Boolean Expressions:**
    *   \(S = X \oplus Y \oplus Z\)
    *   \(C = (X \oplus Y)Z + XY\)

#### Truth Table

| X | Y | Z | SUM (S) | CARRY (C) |
|---|---|---|---------|-----------|
| 0 | 0 | 0 |    0    |     0     |
| 0 | 0 | 1 |    1    |     0     |
| 0 | 1 | 0 |    1    |     0     |
| 1 | 0 | 0 |    1    |     0     |
| 0 | 1 | 1 |    0    |     1     |
| 1 | 0 | 1 |    0    |     1     |
| 1 | 1 | 0 |    0    |     1     |
| 1 | 1 | 1 |    1    |     1     |

#### Logic Diagram
```text
X ──┬─────────────────┐__
    │                 |  \
Y ──┼──┬──────────────|   )───┬─────────────┐__
    │  │   __         |__/    │             |  \
    └──┼──|  \                │   __        |   )── SUM (X ⊕ Y ⊕ Z)
       └──|   )──┐            └───|  \      |__/

          |__/   │                |   )─────┼────┐
                 │  Z ────────────|__/      │    │
                 │                          │    │   __
                 └──────────────────────────┼──┐ ├──|  \
                                            │  └─|   )───┐
                                            │    |__/    │   __
                                            │            ├──|  \
                                            └────────────|   )── CARRY
                                                         |__/
```

---

### 1.3 Half Subtractor (HS)
Subtracts a 1-bit input (Y) from another (X) to produce **DIFFERENCE** (D) and **BORROW** (B).

*   **Boolean Expressions:**
    *   \(D = X \oplus Y\)
    *   \(B = \overline{X}Y\)

#### Truth Table

| X | Y | DIFFERENCE (D) | BORROW (B) |
|---|---|----------------|------------|
| 0 | 0 |        0       |      0     |
| 0 | 1 |        1       |      1     |
| 1 | 0 |        1       |      0     |
| 1 | 1 |        0       |      0     |

#### Logic Diagram
```text
X ──┬───────────┐__
    │  o─┐      |  \
    │    │      |   )─── DIFFERENCE (X ⊕ Y)
Y ──┼────┼──────|__/
    │    │      │    __
    │    └──────┼───|  \
    └───────────┴───|   )── BORROW (X'Y)
                    |__/
```

---

### 1.4 Full Subtractor (FS)
Subtracts two 1-bit inputs (Y, Z) from a 1-bit input (X) to yield **DIFFERENCE** (D) and **BORROW** (B).

*   **Boolean Expressions:**
    *   \(D = X \oplus Y \oplus Z\)
    *   \(B = \overline{X}(Y \oplus Z) + YZ\)

#### Truth Table

| X | Y | Z | DIFFERENCE (D) | BORROW (B) |
|---|---|---|----------------|------------|
| 0 | 0 | 0 |        0       |      0     |
| 0 | 0 | 1 |        1       |      1     |
| 0 | 1 | 0 |        1       |      1     |
| 0 | 1 | 1 |        0       |      1     |
| 1 | 0 | 0 |        1       |      0     |
| 1 | 0 | 1 |        0       |      0     |
| 1 | 1 | 0 |        0       |      0     |
| 1 | 1 | 1 |        1       |      1     |

---

## 2. Data Routing Circuits

### 2.1 Multiplexer (MUX)
Data Selector that routes one out of \(2^n\) inputs to a single output line using n select lines.

```text
       8-to-1 MUX Selection                   16-to-1 MUX Selection
      ┌───┬───┬───┬───────┐              ┌───┬───┬───┬───┬───────┐

      | A | B | C | Output|              | A | B | C | D | Output|
      ├───┼───┼───┼───────┤              ├───┼───┼───┼───┼───────┤

      | 0 | 0 | 0 |   I₀  |              | 0 | 0 | 0 | 0 |   I₀  |
      | 0 | 0 | 1 |   I₁  |              | 0 | 0 | 0 | 1 |   I₁  |
      | 0 | 1 | 0 |   I₂  |              | 0 | 0 | 1 | 0 |   I₂  |
      | 0 | 1 | 1 |   I₃  |              |...|...|...|...|  ...  |
      | 1 | 0 | 0 |   I₄  |              | 1 | 1 | 1 | 1 |  I₁₅  |
      | 1 | 0 | 1 |   I₅  |              └───┴───┴───┴───┴───────┘
      | 1 | 1 | 0 |   I₆  |
      | 1 | 1 | 1 |   I₇  |
      └───┴───┴───┴───────┘
```

### 2.2 De-Multiplexer (DEMUX)
Data Distributor that operates inversely to a MUX, mapping a single data input to one of $2^n$ output destination rails based on $n$ control lines.

---

## 3. Code Conversion Circuits

### 3.1 3-to-8 Encoder (Octal-to-Binary)
Encodes 8 distinct input active-high lines ($Y_0 - Y_7$) down to a compressed 3-bit binary output ($A, B, C$).

*   **Boolean Functions:**
    *   $A = Y_4 + Y_5 + Y_6 + Y_7$
    *   $B = Y_2 + Y_3 + Y_6 + Y_7$
    *   $C = Y_1 + Y_3 + Y_5 + Y_7$

#### Truth Table

| $Y_0$ | $Y_1$ | $Y_2$ | $Y_3$ | $Y_4$ | $Y_5$ | $Y_6$ | $Y_7$ | A | B | C |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|  1  |  0  |  0  |  0  |  0  |  0  |  0  |  0  | 0 | 0 | 0 |
|  0  |  1  |  0  |  0  |  0  |  0  |  0  |  0  | 0 | 0 | 1 |
|  0  |  0  |  1  |  0  |  0  |  0  |  0  |  0  | 0 | 1 | 0 |
|  0  |  0  |  0  |  1  |  0  |  0  |  0  |  0  | 0 | 1 | 1 |
|  0  |  0  |  0  |  0  |  1  |  0  |  0  |  0  | 1 | 0 | 0 |
|  0  |  0  |  0  |  0  |  0  |  1  |  0  |  0  | 1 | 0 | 1 |
|  0  |  0  |  0  |  0  |  0  |  0  |  1  |  0  | 1 | 1 | 0 |
|  0  |  0  |  0  |  0  |  0  |  0  |  0  |  1  | 1 | 1 | 1 |

---

### 3.2 3-to-8 Decoder
Accepts a 3-bit input data sequence ($A, B, C$) to selectively drive exactly one out of 8 output targets ($Y_0 - Y_7$).

#### Truth Table

| A | B | C | $Y_0$ | $Y_1$ | $Y_2$ | $Y_3$ | $Y_4$ | $Y_5$ | $Y_6$ | $Y_7$ |
|---|---|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 0 | 0 | 0 |  1  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
| 0 | 0 | 1 |  0  |  1  |  0  |  0  |  0  |  0  |  0  |  0  |
| 0 | 1 | 0 |  0  |  0  |  1  |  0  |  0  |  0  |  0  |  0  |
| 0 | 1 | 1 |  0  |  0  |  0  |  1  |  0  |  0  |  0  |  0  |
| 1 | 0 | 0 |  0  |  0  |  0  |  0  |  1  |  0  |  0  |  0  |
| 1 | 0 | 1 |  0  |  0  |  0  |  0  |  0  |  1  |  0  |  0  |
| 1 | 1 | 0 |  0  |  0  |  0  |  0  |  0  |  0  |  1  |  0  |
| 1 | 1 | 1 |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  1  |

Reference - Morris Mano
