## Summary

The KZG Ceremony is an Ethereum project which will provide a cryptographic foundation for scaling initiatives like EIP-4844: Proto-Danksharding. The Ceremony is a coordinated public ritual (aka trusted setup, "Parameter Generation Event" in Zcash) which is expected to have the following characteristics:

- wide ecosystem participation
- accessible: possible to participate via browser
- a meaningful narrative in a simple interface 
- easy to audit transcript

From the specs repo:

> The ceremony takes place between participants and the coordinator. Participants are the entities that contribute their secret randomness to the final output 𝜏 s. The roll of the coordinator it to act as the common point of interaction for all participants as well as verifying participants' contribution as the ceremony progresses.

The best place to follow along is the KZG Ceremony channel in the Ethereum R&D Discord: [join here](https://discord.gg/bZrptf6Est).

## Useful Links
- [EIP-4844](https://eips.ethereum.org/EIPS/eip-4844)
- [Proto-Danksharding FAQ](https://notes.ethereum.org/@vbuterin/proto_danksharding_faq)
- [KZG polynomial commitments](https://dankradfeist.de/ethereum/2020/06/16/kate-polynomial-commitments.html)
- [KZG Ceremony Timeline](https://notes.ethereum.org/@CarlBeek/kzg_ceremony_timelines) (subject to change)
- [Spec Repo](https://github.com/ethereum/kzg-ceremony-specs) 
- [Primary implementation](https://github.com/crate-crypto/small-powers-of-tau) (Rust)
- [Trusted Setup Rationale](https://hackmd.io/@6iQDuIePQjyYBqDChYw_jg/SJ-08AoT5)

## Other Implementations
- [Towers of Pau](https://dknopik.de/)

## Latest work on other Ceremony Infra
- [Contributor Identification](https://pse-team.notion.site/Contributor-Identification-bd2824138a5f446785fdd70c60684176)
- [Queue Strategy](https://pse-team.notion.site/Queue-Strategy-c75120ae0c584e6f8db7738c9aaf963a)
- [Draft Participant API](https://www.notion.so/pse-team/Participant-API-a9d82f45a7574da28e4e47bc2ffae1e1)

## Public Calls
- #1 [Agenda/Recording](https://github.com/ethereum/pm/issues/546) - June 9 2022
- #2 [Agenda/Recording](https://github.com/ethereum/pm/issues/558) - June 23 2022
- #3 [Agenda/Recording](https://github.com/ethereum/pm/issues/560) - July 7 2022
- #4 [Agenda/Recording](https://github.com/ethereum/pm/issues/569) - July 21 2022
- #5 [Agenda/Recording](https://github.com/ethereum/pm/issues/587) - Aug 4 2022
- #6 [Agenda/Recording](https://github.com/ethereum/pm/issues/593) - Aug 18 2022
- #7 [Agenda/Recording](https://github.com/ethereum/pm/issues/613) - Sept 1 2022
- #8 [Agenda/Recording](https://github.com/ethereum/pm/issues/623) - Sept 15 2022
