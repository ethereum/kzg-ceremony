### How do I contribute randomness to the Ceremony?

The Ethereum Foundation is hosting an interface at [ceremony.ethereum.org](https://ceremony.ethereum.org/) during the public contribution period from X date to Y date. If you'd like an alternative to the hosted interface, you are welcome to contribute via a [CLI](https://github.com/crate-crypto/kzg-ceremony-cli.git). After this public contribution period, we will accept special contributions from bespoke [implementations](https://github.com/ethereum/kzg-ceremony#client-implementations) or unique randomness generation. Funding is available for both of these, more information will be shared in the coming weeks.

### What does KZG stand for?

KZG comes from Kate, Zaverucha, and Goldberg. These are the author surnames from the paper ["Constant-Size Commitments to Polynomials and Their Applications"](https://www.iacr.org/archive/asiacrypt2010/6477178/6477178.pdf), which outlines the underlying cryptographic mechanism that the Ethereum ceremony plans to utilize.

### What happens during a Ceremony?

1. A Summoner runs a computation using three random inputs (aka secrets) they provide. Three different kinds of secrets are required in this Ceremony: text, cursor movements, and browser generated.
2. The output of that computation is then passed to the Sequencer - a coordinating server which orchestrates transfers between participants.
3. The Sequencer passes the computation from step two to the next summoner, who is waiting to start. This participant computes an output using their secret inputs, and combines it with the work from Summoner 1. At this point the cycle starts again.

While it’s important that summoners discard the random secrets they use, the Ceremony only requires one honest participant to do so. As long as one person does this, observers can be sure that the final output can never be fully reverse engineered or corrupted.

Here's another framing from the [Cryptography Rationale](https://hackmd.io/@6iQDuIePQjyYBqDChYw_jg/SJ-08AoT5):
> For EIP-4844, Ethereum needs four different Structured Reference Strings (SRS) each of different sizes. Each SRS has a secret associated with it. For security, the SRS’s must be computed in such a way that no single person knows the secret associated with them. The solution is to have multiple people contribute to the secret. If all of these people collude, then they can recover the secret. If even one person does not collude, then the secret is unrecoverable. The process of multiple people contributing to the secret is known as a ceremony.

### Couldn’t another commitment scheme without a "trusted setup" be used?

Using anything other than KZG (eg. IPA or SHA256) would make the sharding roadmap much more difficult. Learn more from Vitalik's [Proto-Danksharding FAQ](https://notes.ethereum.org/@vbuterin/proto_danksharding_faq#Couldn%E2%80%99t-we-use-some-other-commitment-scheme-without-a-trusted-setup).

### What is the Sequencer and what does it do?

The Sequencer is a server hosted by the Ethereum Foundation which coordinates contributions. It keeps track of who is trying to contribute, serves them the necessary data to download, and takes each contribution.

You don't have to trust the Sequencer to produce a biased or invalid final output. The [transcript](link) provides a verifiable record of all randomness contributions. As long as there is one honest participant who doesn't record their randomness, the secret cannot be reconstructed.

### How can the Ceremony be compromised? What attacks are possible in this situation?

### How long does it take to contribute?

It should only take a few minutes to complete the contribution on a standard laptop and internet connection.

### How can I verify the final Ceremony output?

By reading the [transcript](link).

### Why can't I contribute on a mobile device?

The Ceremony isn't optimized for the mobile environment.
