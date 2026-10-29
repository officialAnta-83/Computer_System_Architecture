[Booths_Multiplication_Algorithm.docx](https://github.com/user-attachments/files/34137739/Booths_Multiplication_Algorithm.docx)


# Booth's Multiplication Algorithm Summary

This repository provides an editable, clean Markdown implementation of Booth's Multiplication Algorithm notes, complete with text-based flowcharts, step-by-step mathematical logic, and an execution trace matrix optimized for GitHub rendering.

---

## 1. Overview
**Booth’s Algorithm** is a specialized, efficient multiplication algorithm designed to find the product of **two signed binary numbers** represented in two's complement notation. It treats strings of consecutive 1s in the multiplier as a single subtraction and addition operation rather than executing multiple shifts and additions.

---

## 2. Structural Operation Flow

```text
                     [ Start ]
                         │
                         ▼
             ┌───────────────────────┐
             │       Initialize      │
             │   A   <- 0            │
             │   Q_1 <- 0            │
             │   M   <- Multiplicand │
             │   Q   <- Multiplier   │
             │  Count <- n           │
             └───────────────────────┘
                         │
      ┌──────────────────┴───◄──────────────────┐
      │                                         │
      ▼                                         │
  [ Check ] ───► ( Q_0 , Q_1 )                  │
                    │                           │
         ┌──────────┼──────────┐                │
      10 │       11 │ 00    01 │                │
         ▼          ▼          ▼                │
     ┌───────┐  ┌───────┐  ┌───────┐            │
     │ A<-A-M│  │  Do   │  │ A<-A+M│            │
     └───┬───┘  │Nothing│  └───┬───┘            │
         │      └───┬───┘      │                │
         └──────────┼──────────┘                │
                    │                           │
                    ▼                           │
       ┌─────────────────────────┐              │
       │  Arithmetic Right Shift │              │
       │      [ A, Q, Q_1 ]      │              │
       │   Count <- Count - 1    │              │
       └────────────┬────────────┘              │
                    │                           │
                    ▼                           │
             ( Count == 0? ) ───[ No ]──────────┘
                    │
                 [ Yes ]
                    │
                    ▼
                 [ Stop ]
```

---

## 3. Step-by-Step Mathematical Evaluation

### Problem Setup
Multiply $9 \times 13$ using Booth's Algorithm.

*   **Variables Declared:**
    *   $\text{Multiplicand } (M) = (13)_{10} = (01101)_2$
    *   $\text{Multiplier } (Q) = (9)_{10} = (01001)_2$
    *   $\text{Bit length } (N) = 5 \implies \text{Counter} = 5$
    *   $\text{Initial Accumulator } (A) = (00000)_2$
    *   $\text{Initial State bit } (Q_{+1}) = 0$

*   **Complement Derivation (for $-M$ subtraction):**
    *   $+M = 01101$
    *   $\text{1's Complement} = 10010$
    *   $\text{2's Complement } (-M) = 10010 + 1 = 10011$

---

## 4. Algorithmic Execution Matrix

| Cycle | Accumulator (A) | Multiplier (Q) | $Q_{+1}$ | Operation Performed | Remaining Counter |
| :---: | :---: | :---: | :---: | :--- | :---: |
| **0** | `00000` | `01001` | `0` | **Initialization** | 5 |
| **1** | `00000`<br>`+10011`<br>───────<br>`10011` | `01001` | `0` | **$Q_0 Q_{+1} = 10 \implies A \leftarrow A - M$**<br><br>*(Add 2's Complement of M)* | 5 |
| | `11001` | `10100` | `1` | **Arithmetic Right Shift (ARS)** | **4** |
| **2** | `11001`<br>`+01101`<br>───────<br>`[1]00110` | `10100` | `1` | **$Q_0 Q_{+1} = 01 \implies A \leftarrow A + M$**<br><br>*(Discard Overflow Bit)* | 4 |
| | `00011` | `10100` | `0` | **Arithmetic Right Shift (ARS)** | **3** |
| **3** | `00001` | `11010` | `0` | **Arithmetic Right Shift (ARS) ($Q_0 Q_{+1} = 00$)** | **2** |
| **4** | `00001`<br>`+10011`<br>───────<br>`10100` | `11010` | `0` | **$Q_0 Q_{+1} = 10 \implies A \leftarrow A - M$**<br><br>*(Add 2's Complement of M)* | 2 |
| | `11010` | `01101` | `0` | **Arithmetic Right Shift (ARS)** | **1** |
| **5** | `11010`<br>`+01101`<br>───────<br>`[1]00111` | `01101` | `0` | **$Q_0 Q_{+1} = 10 \implies A \leftarrow A + M$**<br><br>*(Discard Overflow Bit)* | 1 |
| | `00011` | `10101` | `1` | **Arithmetic Right Shift (ARS)** | **0** |

---

## 5. Result Extraction & Verification

*   **Final Values at Stop Condition:**
    *   $A = 00011$
    *   $Q = 10101$
    *   $\text{Combined Binary String } (AQ) = 0001110101$

*   **Base-10 Conversion:**
    *   $1110101_2 = (1 \times 2^6) + (1 \times 2^5) + (1 \times 2^4) + (0 \times 2^3) + (1 \times 2^2) + (0 \times 2^1) + (1 \times 2^0)$
    *   $= 64 + 32 + 16 + 4 + 1 = 117_{10}$

$$\therefore (9)_{10} \times (13)_{10} = (117)_{10}$$

Reference - Morris Mano
