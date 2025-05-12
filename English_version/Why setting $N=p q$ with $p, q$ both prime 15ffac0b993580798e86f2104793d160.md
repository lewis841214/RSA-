# Why setting $N=p*q$ with $p, q$ both prime?

1. If we set $N$ as an arbitary large number, finding $\phi(N)$ is very hard! For example, finding $\phi(2^{1024})$ is  intracable.
2. If we set $N$ as a prime number, then $\phi(N)=N-1$ which is computable! However, 
    1. Me: We know (N,e), (N,d), $\phi(N-1)$ 
    2. Hacker: know both (N,e), $\phi(N-1)$ 
        1. when formulating $ed\equiv1 \pmod{\phi(N) = N-1}$, and given  (N, e) as a public key, (N, d) as a private key,
        2. Since $N-1$ is known,  we can set $d=e^K$ for some $K$ s.t.  $e^{K+1}\equiv1\pmod{N-1}$
        3. So private key  is found by hacker and no longer private.
3. By setting $p, q$ both prime and $p\neq q$, we have $\phi(N)=(p-1)(q-1)$ . So:
    1. Me: We know (N,e), (N,d), $\phi(N-1)$ 
    2. Hacker: only know (N, e). To know $\phi(N-1)$, he(she) should first find $p, q$ which is intractable.
        
        So Hacker can’t find $d$ through $(N, e)$.