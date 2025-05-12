# Understanding Euler theorem

## Euler theorem

If $N$ **and *a* are [coprime](https://en.wikipedia.org/wiki/Coprime) positive integers, then 

 $a^{\phi(N)} \equiv 1 \pmod{N}$

where $\phi$  is the euler totient function, which describe how many elements is in set: 

$\{0<x<n|x\in\mathbb{Z}, gcd(x,N)=1 \}$.

To be short, why this is happening is because all positive interger $<N$ which is coprime with $N$ forms  a “group” which this group contains $\phi(N)$ elements . And we have a theorem illustrate that $|G|=N$⇒$\forall g\in G,g^n=1$. 

Here we go through the following three steps to demonstrate and prove this theorem:

1. Define “group” 
2. THM: $|G|=N$⇒$\forall g\in G,g^n=1$
3. Proof $\{0<x<n|x\in\mathbb{Z}, gcd(x,N)=1 \}$ and operation $(\cdot, \pmod{N})$ form a group  ⇒ Euler theorem

### 1. Group definition

1.1 Definition:

A **group** is an algebraic structure defined formally as follows:

Let $G$ be a set and $\cdot$  be a binary operation on $G$. Then $(G, \cdot)$ is a group if it satisfies the following axioms:

1. **Closure**: $\forall a, b \in G$, $a \cdot b \in G$
2. **Associativity**: $\forall a, b, c \in G$, $(a \cdot b) \cdot c = a \cdot (b \cdot c)$
3. **Identity Element**: $\exists e \in G$ such that $\forall a \in G$, $e \cdot a = a \cdot e = a$
4. **Inverse Element**: $\forall a \in G$,  $\exists a^{-1} \in G$ such that $a \cdot a^{-1} = a^{-1} \cdot a = e$

1.2 Example of creating a group using prime number $5$:

[Multiplicative Group Modulo 5 (Z*5)](Multiplicative%20Group%20Modulo%205%20(Z%205)%2015ffac0b993580239cd7d46be8ae1dcb.md)

### 2. THM: $|G|=N$⇒$\forall g\in G,g^N=1$

According to this theorem, we know that for all elements in $G$ with number of element $N$, we have $g^N=1$. 

[proof](https://en.wikipedia.org/wiki/Lagrange%27s_theorem_(group_theory))

### 3. Proof $\{0<x<n|x\in\mathbb{Z}, gcd(x,N)=1 \}$ and operation $(\cdot, \pmod{N})$ form a group

[Proof](Proof%2015ffac0b9935805091b0cb372f47a8ed.md)

According the derivations, we proof the Euler theorem by (2.) (3.).