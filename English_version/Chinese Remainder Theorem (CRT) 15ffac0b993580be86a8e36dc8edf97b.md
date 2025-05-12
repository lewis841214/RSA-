# Chinese Remainder Theorem (CRT)

## Formal Statement

The Chinese Remainder Theorem states that for a system of simultaneous congruences:

$x \equiv a_1 \pmod{m_1}$
$x \equiv a_2 \pmod{m_2}$
$\vdots$
$x \equiv a_k \pmod{m_k}$

Where the moduli $m_1, m_2, ..., m_k$ are pairwise coprime, there exists a unique solution modulo the product of the moduli.

## Constructive Proof

### Key Components

1. Pairwise coprime moduli
2. Unique solution modulo $M = m_1 \cdot m_2 \cdot ... \cdot m_k$

### Solution Construction

1. Compute $M = \prod m_i$
2. Compute $M_i = M / m_i$
3. Find modular multiplicative inverses $y_i$ such that:
$M_i \cdot y_i \equiv 1 \pmod{m_i}$
4. Solution: $x = \sum a_i M_i y_i \pmod{M}$

## Concrete Example

Solve:

- $x \equiv 2 \pmod{3}$
- $x \equiv 3 \pmod{5}$
- $x \equiv 2 \pmod{7}$

### Step-by-Step Solution

1. $M = 3 \cdot 5 \cdot 7 = 105$
2. $M_1 = 35, M_2 = 21, M_3 = 15$
3. Find inverses:
    - $35 \cdot y_1 \equiv 1 \pmod{3}$
    - $21 \cdot y_2 \equiv 1 \pmod{5}$
    - $15 \cdot y_3 \equiv 1 \pmod{7}$
4. Compute solution

## Practical Applications

- Cryptography
- Number theory
- Solving systems of linear congruences
- Modular arithmetic

## Computational Complexity

- Efficient solution for small numbers
- Polynomial-time algorithm