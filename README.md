## Summary

The KZG Ceremony is a coordinated public ritual which will provide a cryptographic foundation for Ethereum scaling initiatives. From the specs repo:

> The ceremony takes place between participants and the sequencer. Participants are the entities that contribute their secret randomness to the final output 𝜏 s. The role of the sequencer is to act as the common point of interaction for all participants as well as verifying participants' contribution as the ceremony progresses.

The ceremony is designed to have the following characteristics:

- wide ecosystem participation
- accessible via browser
- a meaningful narrative in a simple interface
- easy to audit transcript

The best place to follow along is the KZG Ceremony channel in the Ethereum R&D Discord or the bridged telegram channel - DM one of the contributors to be added to either.

## Context
- [KZG Ceremony FAQ](https://github.com/ethereum/kzg-ceremony/blob/main/FAQ.md)
- [How do trusted setups work?](https://vitalik.ca/general/2022/03/14/trustedsetup.html)
- [EIP-4844](https://eips.ethereum.org/EIPS/eip-4844)
- [Proto-Danksharding FAQ](https://notes.ethereum.org/@vbuterin/proto_danksharding_faq)
- [KZG polynomial commitments](https://dankradfeist.de/ethereum/2020/06/16/kate-polynomial-commitments.html)
- [KZG Ceremony Timeline](https://notes.ethereum.org/@CarlBeek/kzg_ceremony_timelines) (subject to change)
- [Spec Repo](https://github.com/ethereum/kzg-ceremony-specs)

## Audits
- [SECBIT Spec + Implementation Audit](https://github.com/ethereum/kzg-ceremony/blob/main/KZG10-Ceremony-audit-report.pdf) - Aug 2022
- [Sigma Prime Sequencer Audit](https://github.com/ethereum/kzg-ceremony/blob/main/Sigma_Prime_Ethereum_Foundation_KZG_Ceremony_Security_Assessment.pdf) - Nov 2022

## Client Implementations
- [KZG ceremony sequencer implementation](https://github.com/ethereum/kzg-ceremony-sequencer) (Rust)
- [KZG Ceremony Client](https://github.com/jsign/go-kzg-ceremony-client) (Go)
  - Allows verifying the powers of tau calculation from the currently provided transcript from the verifier
  - Apart from using CSRNG for secrets entropy, it supports two opt-in external sources of entropy: the drand network, and an arbitrary URL provided by the user
- [Towers of Pau](https://github.com/dknopik/towers-of-pau/tree/proper-client) (Go)
- [KZG sequencer crypto wrapper](https://github.com/zkparty/wrapper-small-pot) (Rust)
- [Small powers of Tau](https://github.com/crate-crypto/small-powers-of-tau) (Rust)
- [Worldcoin](https://github.com/worldcoin/kzg-ceremony-client) (client - WIP)
  - [WASM contribution code](https://github.com/worldcoin/kzg-ceremony-participant) (Rust)

## IPFS Hosted Versions
- [latest version - link to be added](): references the latest version of the interface, which departs from the audited version in minor ways
- [Audit version](https://ceremony-ipfs.efprivacyscaling.org/ipfs/QmevfvaP3nR5iMncWKa55B2f5mUgTAw9oDjFovD3XNrJTV/): the interface which Sigma Prime audited in November 2022. May have bugs or differences from the latest version above

## Other Documentation
- [Trusted Setup Rationale](https://hackmd.io/@6iQDuIePQjyYBqDChYw_jg/SJ-08AoT5)
- [Contributor Identification](https://pse-team.notion.site/Contributor-Identification-bd2824138a5f446785fdd70c60684176)
- [Queue Strategy](https://pse-team.notion.site/Queue-Strategy-c75120ae0c584e6f8db7738c9aaf963a)
- [Draft Participant API](https://www.notion.so/pse-team/Participant-API-a9d82f45a7574da28e4e47bc2ffae1e1)

## Public Calls
| Call #  |              Link |  Date |
| ---: | ---:        |        ---: |
| 1 | [Agenda/Recording](https://github.com/ethereum/pm/issues/546) | June 9 2022 |
| 2 | [Agenda/Recording](https://github.com/ethereum/pm/issues/558) | June 23 2022|
| 3 | [Agenda/Recording](https://github.com/ethereum/pm/issues/560) | July 7 2022|
| 4 | [Agenda/Recording](https://github.com/ethereum/pm/issues/569) | July 21 2022|
| 5 | [Agenda/Recording](https://github.com/ethereum/pm/issues/587) | Aug 4 2022|
| 6 | [Agenda/Recording](https://github.com/ethereum/pm/issues/593) | Aug 18 2022|
| 7 | [Agenda/Recording](https://github.com/ethereum/pm/issues/613) | Sept 1 2022|
| 8 | [Agenda/Recording](https://github.com/ethereum/pm/issues/623) | Sept 15 2022|
| 9 | [Agenda/Recording](https://github.com/ethereum/pm/issues/636) | Sept 29 2022|
