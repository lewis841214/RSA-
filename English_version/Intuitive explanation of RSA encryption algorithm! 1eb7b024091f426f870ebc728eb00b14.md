# Intuitive explanation of RSA encryption algorithm!

Outline:

1. [Find some regular patterns!](Intuitive%20explanation%20of%20RSA%20encryption%20algorithm!%201eb7b024091f426f870ebc728eb00b14.md)
2. [Designing an encrypt/decrypt process through the findings!](Intuitive%20explanation%20of%20RSA%20encryption%20algorithm!%201eb7b024091f426f870ebc728eb00b14.md)
3. [Why using two large primes plays a crucial role in designing this algorithm?](Intuitive%20explanation%20of%20RSA%20encryption%20algorithm!%201eb7b024091f426f870ebc728eb00b14.md)

## 1. Finding a regular pattern!

Before we get lost in complex notations, let's first look at some examples and understand why for any number $N$, there exists some integer $r$ such that $a^r\equiv1\pmod{N}$.

### 1.1 If $N$ is prime

Let $N=11$, we have:

$2^{10}\equiv1\pmod{11}$

$3^{10}\equiv1\pmod{11}$

$4^{10}\equiv1\pmod{11}$

…

$8^{10}\equiv1\pmod{11}$

$9^{10}\equiv1\pmod{11}$

$10^{10}\equiv1\pmod{11}$

and we have:

$2^{10+1}\equiv2\pmod{11}$

$3^{10+1}\equiv3\pmod{11}$

…

$10^{10+1}\equiv10\pmod{11}$

So we see that, if $N$ is a prime number, we have the following formula:

1. $m^{N-1}\equiv1\pmod{N}$

and

2. $m^{N}\equiv m\pmod{N}$

Quite magical, right?

### 1.2 If $N=p*q$ for $p, q$ both prime and unequal

We first state the formula:

1. $m^{(p-1)(q-1)}\equiv1\pmod{N}$

and

2. $m^{(p-1)(q-1) + 1}\equiv m\pmod{N}$

This formula only fails to hold when $gcd(m,N)\neq1$.

Let's see an example: $p=5, q=7$, so $N=35$ and $(5-1)(7-1)=24$

$2^{(5-1)(7-1)}\equiv1\pmod{35}$

$3^{(5-1)(7-1)}\equiv1\pmod{35}$

$4^{(5-1)(7-1)}\equiv1\pmod{35}$

$5^{(5-1)(7-1)}\neq1\pmod{35}$

$6^{(5-1)(7-1)}\equiv1\pmod{35}$

$7^{(5-1)(7-1)}\neq1\pmod{35}$

$8^{(5-1)(7-1)}\equiv1\pmod{35}$

…

$14^{(5-1)(7-1)}\neq1\pmod{35}$

…

$34^{(5-1)(7-1)}\equiv1\pmod{35}$

and 

$2^{(5-1)(7-1)+1}\equiv2\pmod{35}$

$3^{(5-1)(7-1)+1}\equiv3\pmod{35}$

…

$34^{(5-1)(7-1)+1}\equiv34\pmod{35}$

### 1.3 (Euler theorem) If $N$ is any positive integer number:

We first state the formula:

1. $m^{\phi(N)}\equiv1\pmod{N}$

and

2. $m^{\phi(N) + 1}\equiv m\pmod{N}$

where $\phi(N)$ is the number of positive integers which are smaller than and co-prime with $N$.

This is the well-known Euler theorem!

[Understanding Euler theorem](Understanding%20Euler%20theorem%2015bfac0b993580998b9bd0b19f60ecd9.md)

## 2. Designing an encryption algorithm through observed regular patterns!

After observing these regular patterns, how can we apply this regularity?

Here's what we will do: 

If we already know that "All positive integers under prime N have the property: $m^{N}\equiv m \mod{N}$", then we can design an encryption and decryption process like this:

1. We divide $N$ into two positive integers $e, d$, where $d*e =(N-1)K+1$. We want to apply the rule $m^{d*e}=m^{(N-1)^K}*m\equiv m\pmod{N}$. We send out $(N,e)$ as the public key, and keep the private key $(N,d)$ private. (You can view $K=1$ for simplicity)
2. Encryption: We use $e$ to encrypt the message $m$ by computing $m^e\pmod{N}$, then we will get an encrypted message $c=m^e\pmod{N}$
3. Decryption: Then we use $d$ to decrypt the encrypted message $c$ through: $c^d\pmod{N}={m^{e}}^d\equiv m\pmod{N}$

So we will send out the $(N,e)$ to others for encryption and keep the $(N,d)$ private for decryption.

However, if a hacker intercepts the public key $(N,e)$ and knows that $N$ is a prime number, they will know $d*e = N$, so $d=N/e$. Then your private key $(N,d)$ is no longer private, and the encrypted message $c$ can be decrypted by the hacker.

Therefore, setting $N$ as a prime number isn't a good idea.

## Can we design an algorithm such that even knowing the public key can't reveal the private key?

Yes we can! 

We combine two powerful observations:

1. (1.2) If $N=p*q$ for $p,q$ both prime and unequal, then $\phi(N)=(p-1)(q-1)$
2. It's easy to compute $p*q=N$, but hard to find [$N=?*?$ when $N$ is relatively large](https://en.wikipedia.org/wiki/Integer_factorization)

So if we choose two different large primes $p, q$ and set $N=p*q$, and set two integers $e$ (encryption), $d$ (decryption) such that:

1. $e*d=\phi(N)+1$ 

or

2. $e*d\equiv1\pmod{\phi(N)}$ (i.e., $e*d=\phi(N)*K+1$ for some $K\in\mathbb{Z}$)

Then we have the property: 

$m^{e*d}=m^{\phi(N)*K+1}\equiv m\pmod{N}$

So if we generate the public/private key through this process, we will get:

1. Public key: $(N, e)$
2. Private key: $(N,d)$

and the hacker will only get:

1. Public key: $(N,e)$

To find the private key $d$, they would need to:  

1. Conduct integer factorization and find $N=p*q$. (time complexity: $O(e^{c*(log{N}^{1/3})(log{log{N}}^{2/3})}$, which is impossible to solve when $N$ is large, even with the fastest computer on earth)
2. Find $\phi(N)=(p-1)(q-1)$
3. Find $d$ such that $e*d\equiv1\pmod{\phi(N)}$

But step 1 is infeasible to solve, so knowing the public key is insufficient to crack this algorithm, amazing!

At this point, we now understand and are able to design the well-known RSA algorithm, which is formally stated below:

## RSA algorithm:

1. Choose arbitrary prime numbers $p$, $q$, and compute $N=p*q$
2. Set $r=\phi(N)=\phi(p)\phi(q)=(p-1)(q-1)$
3. Choose an $e\in\mathbb{Z}$, where $e<r$ and $gcd(e,r)=1$ and find $d\in\mathbb{Z}$ such that $ed\equiv1\pmod{r}$. 
    
    I.e., $ed = r*K+1$ for some $K\in\mathbb{Z}$
    
4. Destroy $p, q$

Then set:

$(e, N)$: public key

$(d, N)$: private key

### Encryption of a message $m$:

We use the public key $(e, N)$ to encrypt the message $m$ to $c$:

$c=m^e \pmod{N}$

### Decryption of encrypted $c$:

And decrypt the message through:

$m=c^d \pmod{N}$

### Why does this work?

We only need to show why $c^d\pmod{N}\equiv m$.

Suppose $gcd(m, N)=1$, then: 

1. $c^d\equiv m^{ed}\pmod{N}$
2. Since $ed=\phi(N)*K+1$ for some $K\in\mathbb{Z}$
    
    we have: $m^{ed}=m^{1+K*\phi(N)}=m*m^{\phi(N)^K}\equiv m\pmod{N}$
    
    Note: $m^{\phi(N)}\equiv1\mod{N}$ according to Euler's theorem.
    

[Why setting $N=p*q$ with $p, q$ both prime?](Why%20setting%20$N=p%20q$%20with%20$p,%20q$%20both%20prime%2015ffac0b993580798e86f2104793d160.md)