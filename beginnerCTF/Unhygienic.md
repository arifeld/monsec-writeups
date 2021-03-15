**Name:** Unhygienic

**Type:** Crypto

**Difficulty:** Moderate

### Challenge Notes:
>My friend kept some notes about how he chooses his passwords, but he encrypted them with a one time pad, which is unbreakable. However, I think he had poor crypto hygiene and reused the same key...

>Flag is the key. Hint: All uppercase.

>`02036109340314070d131510141c06077a0b646d7f671a0b0d151403120463050b761b3241282f41312d20282f35243935412e2f412c38412524322a352e2d`

>`0b0d0a025b0775001b08166211017f1e711c1d0409711c1d7f1875011777641d64630a24323241233435412420323841352e4133242c242c2324334040405c`

### File(s) Attached:
N/A

### Solution:
This is a two-time pad (where the same key is used to encrypt two seperate strings) that was done via XOR, which as a result is vulnerable to the technique known as crib-dragging.

Recall the properties of XOR:

Commutative : A ⊕ B = B ⊕ A

Associative : A ⊕ ( B ⊕ C ) = ( A ⊕ B ) ⊕ C

Identity element : A ⊕ 0 = A

Self-inverse : A ⊕ A = 0

Both plain-text strings (`A` and `B`) were XOR'ed with key `k`, like so:

`A ^ k = A'` and `B ^ k = B'`

Using the above properties, we can get rid of the `k`:

`A' ^ B'` = `(A ^ k) ^ (B ^ k)` = `(A ^ B) ^ (k ^ k)` = `(A ^ B) ^ 0` = `A ^ B`

Now, if we can can guess parts of either `A` or `B`, we can do `A ^ B ^ (part of A or B)` to find part of the other plaintext. From there we can attempt to find the entirity of one string.

Once we have one string, we can evaluate `A' ^ A` which will give us the encryption key (and the flag).