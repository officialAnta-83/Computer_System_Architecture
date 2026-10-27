[Simplification_of_Boolean_Expressions.docx](https://github.com/user-attachments/files/34026435/Simplification_of_Boolean_Expressions.docx)

# SUMMARY: BOOLEAN ALGEBRA & LOGIC GATES

### 1. Basic Boolean Identities
These core rules are used to simplify complex logical expressions:
* **Annihilation & Identity:** 
  * `x + 0 = x` and `x · 1 = x`
  * `x + 1 = 1` and `x · 0 = 0`
* **Idempotent Laws:** `x + x = x` and `x · x = x`
* **Complementarity Laws:** `x + x' = 1` and `x · x' = 0` *(where x' represents x-bar)*
* **Commutative Laws:** `x + y = y + x` and `x · y = y · x`
* **Associative Laws:** 
  * `x + (y + z) = (x + y) + z`
  * `x · (y · z) = (x · y) · z`
* **Distributive Laws:** 
  * `x · (y + z) = x·y + x·z`
  * `x + (y · z) = (x + y) · (x + z)`
* **De Morgan's Laws:** `(x + y)' = x' · y'` and `(x · y)' = x' + y'`
* **Double Negation:** `(x')' = x`

---

### 2. Core Logic Gates & Truth Tables
The 8 standard types of logic gates process boolean inputs to yield specific binary outputs:
* **AND Gate (`C = A · B`):** Output is high (`1`) only if **all** inputs are `1`.
* **OR Gate (`C = A + B`):** Output is high (`1`) if **at least one** input is `1`.
* **NOT Gate / Inverter (`C = A'`):** Flips the input state (`0` to `1`, or `1` to `0`).
* **Buffer (`C = A`):** Passes the input value directly to the output without altering it.
* **NAND Gate (`C = (A · B)'`):** Inverted AND gate; output is `0` only when all inputs are `1`.
* **NOR Gate (`C = (A + B)'`):** Inverted OR gate; output is `1` only when all inputs are `0`.
* **XOR Gate (`C = A ⊕ B = A'B + AB'`):** High output if the inputs are **different**.
* **XNOR Gate (`C = A ⊙ B = AB + A'B'`):** High output if the inputs are the **same**.

---

### 3. Function Complementation (De Morgan's Theorem)
To find the complement of an entire function, you invert all operations (AND becomes OR, OR becomes AND) and invert each individual variable.
* **Example Function:** `F(A, B, C, D) = A·B + C'·D'`
* **Applying De Morgan's:** `F' = (A·B + C'·D')' = (A' + B') · (C + D)`
* **Expanded Algebraic Form:** `F' = A'·C + A'·D + B'·C + B'·D`

---

### 4. Universal Gate Realizations
Both NAND and NOR gates are considered **universal gates** because any of the basic operations (NOT, OR, AND) can be built using only them.

#### A. Realization Using NAND Gates Only
* **NOT:** Combine inputs together → `(A · A)' = A'`
* **OR:** Pass inputs through two separate NOT-configured NAND gates first, then pass both outputs through a third NAND gate → `(A' · B')' = A + B`
* **AND:** Pass inputs through a standard NAND gate first, then invert the resulting signal using a NOT-configured NAND gate → `((A · B)' · (A · B)')' = A · B`

#### B. Realization Using NOR Gates Only
* **NOT:** Combine inputs together → `(A + A)' = A'`
* **OR:** Pass inputs through a standard NOR gate first, then invert that output using a NOT-configured NOR gate → `((A + B)' + (A + B)')' = A + B`
* **AND:** Pass inputs through two separate NOT-configured NOR gates first, then pass both inverted streams through a third NOR gate → `(A' + B')' = A · B`

Reference- Morris Mano

(I am extremely sorry for the bad images of the gates)
