# KZG Ceremony FAQs

### What is EIP-4844, a.k.a. Proto-Danksharding, and how does it relate to scaling Ethereum

The Ethereum community is scaling to global accessibility through [Layer-2s](https://ethereum.org/en/layer-2/).  L2s increase the total block-space available to users while still maintaining the security offered by the Ethereum Layer 1 (L1).

L2s need to publish a lot of data on Ethereum, and the network currently charges high fees for doing so. To fix this, Ethereum will create a new data layer, often referred to as *sharding*. This provides what is called "data availability" guarantees to L2 users. The L1 only holds the data for a limited time, which means we can scale the chain without sacrificing decentralization for smaller L1 node operators.


The current leading design for this is called Danksharding. The rollout for this will happen in several steps, with the first one being [EIP-4844](https://www.eip4844.com/), also known as ProtoDanksharding. 

### What is a Summoning Ceremony?

Ceremonies use secret inputs to produce an output in a way that makes it impossible to reverse-engineer and discover the initial secrets. 

Here's a very brief summary of how they work: 

1. Participant 1 chooses a random number (eg 5.) and then runs a computation on it.
2. The output from that computation is passed to Participant 2, where they repeat Step 1 with their own secret input (e.g. 3) and mix it with the output from the 1st Participant (eg. 5x3=15).
3.  This repeats until there is a sufficient number of participants, at which point the last output in the sequence becomes the final output.

Ceremonies have also been called "Trusted Setups," most famously used by Zcash to bootstrap their privacy features. However, it can also be used to add scalability mechanisms, as Ethereum is doing.

[Carl Beekhuizen's Devcon Talk](https://archive.devcon.org/archive/watch/6/the-kzg-ceremony-or-how-i-learnt-to-stop-worrying-and-love-trusted-setups/) on this Ceremony explains both simply and in-depth how and why this ceremony works. Or, you can explore the [ceremony specs](https://github.com/ethereum/kzg-ceremony-specs/) to really dig into the nitty-gritty, and potentially write your own implementation.

### Why does (Proto)-Danksharding need a Ceremony?

(Proto)-Danksharding requires a commitment scheme for the underlying data that is fast to prove and verify (including inside SNARKS for SNARK-based L2s) while having a small commitment size. The polynomial commitment scheme that best meets the criteria is KZG commitments.

The KZG scheme commits to a polynomial by evaluating it at a secret value (specifically, a elliptic curve point). The point of this ceremony is to construct this secret value in a way that no single person knows what this secret is and to do so in a way where many people are convinced that no-one knows it even in many years time.

### How do I contribute to the Ceremony?

The easiest option is [ceremony.ethereum.org](https://ceremony.ethereum.org), it should take less than 5 minutes of your time.

If you'd like an alternative to this interface, there are several other CLIs and webpages available (links + IPFS). After this public contribution period, we will accept special contributions from bespoke [implementations](https://github.com/ethereum/kzg-ceremony#client-implementations) or unique randomness generation. Funding is available for both of these, more information will be shared in the coming weeks.

### What does KZG stand for?

KZG comes from Kate, Zaverucha, and Goldberg. These are the author surnames from the paper ["Constant-Size Commitments to Polynomials and Their Applications"](https://www.iacr.org/archive/asiacrypt2010/6477178/6477178.pdf), which outlines the underlying cryptographic mechanism that EIP-4844 plans to utilize.

To dive deep into the cryptography of KZG commitments, [Dankrad Feist's blog post](https://dankradfeist.de/ethereum/2020/06/16/kate-polynomial-commitments.html) is a good starting point.

### What happens during this Ceremony?

The interface you choose to participate with will walk you through the following steps:

1. Log in with Ethereum or Github to prevent spam.
2. Collect randomness.
3. Ask the Sequencer if you may participate. When it's your turn, the Sequencer will send you the "Powers of Tau" data.
4. Your computer will mix your randomness into the Powers of Tau and when completed, send it back to the Sequencer.
5. The Sequencer will verify that your computer did everything correctly and pass the Powers of Tau on to the next participant.

After the ceremony is completed, you should return to verify that your contribution was indeed included in the final transcript.

### What are the Powers of Tau?

The name "Powers of Tau" comes from the cryptography literature on trusted setups and SRSs.

"Tau" comes from the Greek letter $\tau$ which is the short-hand for the "secret" referred to in this documentation.

"Powers" refers to the fact that we need not only the secret, but also the consecutive powers of the secret. (ie. $[1, \tau, \tau^2, \tau^3,\dots, \tau^{2^{12}-1}]$)

It is worth noting that the Powers of Tau are not raw numbers, but they are encoded as elliptic curve points which "encrypts" and therefore hides them.

### What is the Sequencer and what does it do?

The Sequencer is a server hosted by the Ethereum Foundation which coordinates contributions. It keeps track of who is trying to contribute, serves them the necessary data to download, and verifies each contribution before sending the data to the next participant.

You don't have to trust the Sequencer to produce a biased or invalid final output. The [transcript](https://seq.ceremony.ethereum.org/info/current_state) provides a verifiable record of all randomness contributions that you can verify for yourself.

### Couldn’t another commitment scheme without a "trusted setup" be used?

Using anything other than KZG (eg. IPA or SHA256) would make the sharding roadmap much more difficult. Learn more from Vitalik's [Proto-Danksharding FAQ](https://notes.ethereum.org/@vbuterin/proto_danksharding_faq#Couldn%E2%80%99t-we-use-some-other-commitment-scheme-without-a-trusted-setup).

### What needs to go wrong for the safety of the ceremony to break?

The ceremony has a "1-of-N" trust assumption, which means that only a single participant in the entire ceremony needs to have not revealed their secret input for everything to be secure.

This means that every participant would have to strip apart the software that they are using to contribute, get that software to give them the secret, and then collude with every single other participant to reconstruct the final secret.

A more realistic failure mode is a common bug which leaks the randomness. To combat this, this site has been audited and there are alternative implementations of the contribution software built on entirely different software stacks.

This is why there will be thousands of participants using different pieces of software on different operating systems to help prevent single points of failure both in the people and hardware/software.

### What attacks are possible in this situation?

Should the secret somehow be extracted from the Powers of Tau, an attacker would be able to make arbitrary claims about the data in EIP-4844. This effectively would break all services & applications dependent on EIP-4844 blob data.

### How long does it take to contribute?

Depending on how many others are trying to contribute at the same time, you could end up waiting a while for your turn to come up to contribute. Once it is your turn, it should only take less than 3 minutes to complete the contribution with a standard laptop and internet connection.

### Why do I need to sign in with Ethereum or GitHub?

In order to reduce Sybil attacks against the Ceremony, the Sequencer needs to verify that you are a (somewhat) unique human otherwise one person could submit many different contributions preventing others from getting a turn to contribute.

- Sign in with Ethereum - This is the preferred choice as it something that all Ethereum community members should already have and it allows signatures for later verification of the transcript. Each account is required to have sent at least 3 transactions to prevent spinning up new accounts just for this ceremony.
- Sign in with GitHub - This option is offered as an alternative for those who are more distant to the community but who'd still like to participate.

### How do I know my contribution was included?

When this ceremony is over, you should review the ceremony transcript (which will be hosted on this site as well as being widely available on the internet). This transcript will contain all the necessary data to verify who participated.

If you used your Ethereum address to sign-in, then there will be cryptographic proof that you participated via a signed message from your account.

### How can I verify the final Ceremony output?

After this ceremony is over it is important for the community to verify that the ceremony ran correctly, this comprises two components:

- Verifying that either you or enough people you trust actually participated, by checking their identities appear in the transcript.
- Verifying that the transcript was constructed correctly including all the witnesses (proofs of correct contribution) and that the Powers of Tau are indeed powers.
