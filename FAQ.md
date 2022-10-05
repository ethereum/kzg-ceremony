### How do I contribute randomness to the Ceremony?

The Ethereum Foundation is hosting an interface at ceremony.ethereum.org during the Public contribution period from X date to Y date. Alternatively, you are welcome to contribute via a [CLI](link). After this, we will accept special contributions from bespoke [implementations]() or unique randomness generation. Funding is available

### What does KZG stand for?

KZG comes from Kate, Zaverucha, and Goldberg. These are the author surnames from the paper ["Constant-Size Commitments to Polynomials and
Their Applications"](https://www.iacr.org/archive/asiacrypt2010/6477178/6477178.pdf), which outlines the underlying cryptographic mechanism that the Ethereum ceremony plans to utilize.

### Why does EIP-4844 need this Ceremony?

Learn more about EIP-4844 here. From the [Cryptography Rationale](https://hackmd.io/@6iQDuIePQjyYBqDChYw_jg/SJ-08AoT5):

> For EIP-4844, Ethereum needs four different Structured Reference Strings (SRS) each of different sizes. Each SRS has a secret associated with it. For security, the SRS’s must be computed in such a way that no single person knows the secret associated with them. The solution is to have multiple people contribute to the secret. If all of these people collude, then they can recover the secret. If even one person does not collude, then the secret is unrecoverable.
> 
> The process of multiple people contributing to the secret is known as a ceremony. This document will outline the assumptions and decisions made when designing the ceremony.

### Couldn’t another commitment scheme without a trusted setup be used?

Using anything other than KZG (eg. IPA or SHA256) would make the sharding roadmap much more difficult. Learn more from Vitalik's [Proto-Danksharding FAQ](https://notes.ethereum.org/@vbuterin/proto_danksharding_faq#Couldn%E2%80%99t-we-use-some-other-commitment-scheme-without-a-trusted-setup).

### Why should I trust the Sequencer?

### How can the Ceremony be compromised? What attacks are possible in this situation?

### How long does it take to contribute?

### How can I verify the final Ceremony output?

By reading the transcript.

### Why can't I contribute on a mobile device?

The Ceremony isn't optimized for the mobile environment.
