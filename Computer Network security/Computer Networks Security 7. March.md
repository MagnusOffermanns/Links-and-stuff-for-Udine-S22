# Chapter 2 Introduction to Number Theory
Is the theory of integers
## Divisibility
We say that a nonzereo b divides a if $a = mb$ for some m where a,b and m are integers

A divides b if there is no rest remaining 

The notation $b|a$ is a commonly used notation

if $a|1$ then $a=+-1$

if $a|b$ and $b|a$ $\implies$ $a=+-b$

any $b\neq0$ divides 0 

## integer division
any integer $n$
and a nonzero integer $a$
quotient $q$
remainder $r$
$a=qn+r$

## Euclidean algorithm
goal: calculate the [[Greatest common Devisor]] of two positive integers
two integers are [[realative prime]] if the greates common divisor is 1


Simple Euclidean algorithm
```python
def Euclide(a,b) #a>b a>0 b>0
	if b=0:
		return a
	else:
		Euclide(b,mod(a,b))
```

[[Extended Euclidean algorithm XGDC]]
```python
def XGDC(a,b):
	if b==0:
		return (a,1,0)
	else:
		(d',x',y')= XGDC(b,mod(a,b))
	return(d',y',x-((a/b) \times y')
```

$(d,x,y)=xdgc(a,b) imples d=xa+by$

## Modular Arithmetic

Two numbers are congruent:
when two numbers are equal towards a certain divisor i.e.
a=b mod n $implies$ $mod( a,n)=mod(b,n)$

this implies:
$$a=b mod n \implies a+c=b+c mod n$$
$$a=b mod n \implies -a=-c mod n$$
$$a=b mod n \implies a*c =b*c mod n$$

# modular arithmetics
The new algebra $Z_r$ has two definitions
- arithmetic operations on equivalence classes 
	- $[a] =\{b|a=b (mod(n))\}$ 
	- $[a]+[b]=[a+b]$
- arithmetic operations on values:
-  $a+b=a+b mod(n)$

# What holds for Modular arithmetics
- addition is [[associative], [[commutative]], 0 is the neutral element
- multiplication is [[associative]] and [[commutative]], 1 is neutral elements
- multiplication is distributive to addition, 0 is the null elements

# Prime numbers:
Prime numbers only have the divisor of 1 and itself.

Any integer a>1 can be factored in a unique way as:
$a=p_1^{x_1} \cdot p_2^{x_2}...}

[[Prime Number theorem]]:
on limit the equality holds
$\pi(n)=\frac{n}{ln(n)}$
where $\pi(n)$ denotes the number of primes less than n.

Meaning: The frequency of primes is inversely proportional to the number of digits of $n$

The frequency of prime number decreases slowly

# [[Fermat's theorem]]
If p is prime for any integer a the number $a^P-a$ is an integer multple of p:

$$a^P \eqiv a (mod(p))$$

if $p$ is prime and $a$ is a positive integer not divisible by p then 
$$a^{p-1}\equiv 1 (mod(p))$$

alternate form:

Generalization of this algorithm is [[Euler's theorem]]


# [[Euler's theorem]]
Generalization to [[Fermat's theorem]].
States that for every a and p that are relatively prime:
$a^{\emptyset(p)}=1 mod(p)$

## [[Miller-Rabin Algorithm]]
typically used to check if big numbers are Prime
1. Find integers k,q with k>0, q is odd so that $(n-1)=s^k \times q$
2. Select a random integer a, $1<a<n-1$
3. if a^q mod n

Todo complete:


## Finding prime numbers
1.  take a random odd number n
2. test n form primality
3. if not prime repeat with n+2
4. On average after ln(n) tries one finds a prime

## Deterministic Primality Algorithms
[[Miller-Rabin Algorithm]] not deterministic only works some of the Time

[[AKS algorithm]] is more calculation intensive but returns a deterministic result

[[Chinese Remainder Theorem]]
The [[Chinese Remainder Theorem|CRT]] is used in RSA because we need to work with so big numbers in [[RSA]]. It is a way to simplify and speed up the decryption of messages. The classical decryption looks like this.

$$m=c^d (\text{Mod N} )$$

The computation to recover the plaintext message $m$  from the cypher $c$ is time intensive so the [[Chinese Remainder Theorem|CRT]] helps us out to split calculation up into 3 less complex subparts.

1. $$m_p \equiv c^{d \cdot Mod(p-1)} (\text{Mod p})$$
2. $$m_q \equiv c^{d \cdot Mod(q-1)} (\text{Mod q})$$
Recombination of $m_q$ and $m_p$ into the $y$ in step 3
3. $$m \equiv m_q +q \cdot (m^{-1} (\text{Mod p})) \cdot (m_p-m_q) \text{ (mod N)}$$

# Chapter 3

Definitions:
Plaintext: an original messages
Cyphertext: the coded message
Enciphering/Encryption: the process to turn the plaintext to cyphertext 
Decryption: The inverse for Encryption

## Symmetric encryption:
sender and receiver have the same key.
The same key is used for encryption and Decryption


# Cryptographic Systems
characterized along three dimensions
- operation
	- substitution
	-  Transposition
- the number of keys used 
	- Symmetric
	- Asymmetric
- The way in which plaintext is processed
	- [[Block cypher]]
	- [[Stream cypher]]

## How to crack cyphers   
- Cryptoanalysis
	- Attack relies on the nature of the algorithm and knowledge of the Plaintext 
	- Attack tries to exploit the characteristic of the algorithm or the plaintext  
- Bruteforce
	- attacker tries every key, on average half of the keys need to be tried

## Kinds of attacks:
- Cyphertext only 
	known: Encryption algorithm, ciphertext
- Known Plaintext
	known: Encryption algorithm, cyphertext, one or more plaintext-cyphertext pairs 
- Chosen Plaintext
	known: Encryption algorithm, Ciphertext, A encryption oracle that encrypts all possible messages with the secret key
- Chosen Ciphertext 
	known: Encryption Algorithm, Ciphertext, A decryption oracle that reconstructs the plaintext from every cyphertext except the encrypted message itself
- Chosen text 
- Todo

## Security
Unconditionally secure:
No matter how much time and computingpower the attacker has, he can't decrypt the message.

Computationally secure:
- The value of the message is beyond the cost of decrypting it
- The decryption takes very long in particular the live-time of the  information
