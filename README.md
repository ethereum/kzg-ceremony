## Summary

The KZG Ceremony is a coordinated public ritual which will provide a cryptographic foundation for Ethereum scaling initiatives. From the specs repo:

> The ceremony takes place between participants and the sequencer. Participants are the entities that contribute their secret randomness to the final output 𝜏 s. The role of the sequencer is to act as the common point of interaction for all participants as well as verifying participants' contribution as the ceremony progresses.

The ceremony is designed to have the following characteristics:

- wide ecosystem participation
- browser accessible
- a meaningful narrative in a simple interface
- easy to audit transcript

The best place to follow along is the KZG Ceremony channel in the Ethereum R&D Discord or the bridged telegram channel - DM one of the contributors to be added to either.

## Resources
- [KZG Ceremony FAQ](https://github.com/ethereum/kzg-ceremony/blob/main/FAQ.md)
- [How do trusted setups work?](https://vitalik.ca/general/2022/03/14/trustedsetup.html)
- [EIP-4844](https://eips.ethereum.org/EIPS/eip-4844)
- [Proto-Danksharding FAQ](https://notes.ethereum.org/@vbuterin/proto_danksharding_faq)
- [KZG polynomial commitments](https://dankradfeist.de/ethereum/2020/06/16/kate-polynomial-commitments.html)
- [KZG Ceremony Timeline](https://notes.ethereum.org/@CarlBeek/kzg_ceremony_timelines)
- [Spec Repo](https://github.com/ethereum/kzg-ceremony-specs)
- [Frontend Repo](https://github.com/zkparty/trusted-setup-frontend)

## Audits
- [SECBIT Spec + Implementation Audit](https://github.com/ethereum/kzg-ceremony/blob/main/KZG10-Ceremony-audit-report.pdf) - Aug 2022
- [Sigma Prime Sequencer Audit](https://github.com/ethereum/kzg-ceremony/blob/main/Sigma_Prime_Ethereum_Foundation_KZG_Ceremony_Security_Assessment_v3.pdf) - Jan 2023

## Client Implementations
There are a number of independent implementations interested Ceremony participants can try to run locally, will have a variety of different features. (no guarantees on the quality or completeness!)

### CLI Interfaces

| Implementation | BLS Library | Language | License| Author| Notes |
| :- | :- | :- | :- | :- | :- |
| [Chotto](https://github.com/StefanBratanov/chotto/) | blst ([jblst](https://github.com/ConsenSys/jblst)) | Java | Apache 2.0 | Stefan Bratanov (@StefanBratanov) ||
| [go-kzg-ceremony-client](https://github.com/jsign/go-kzg-ceremony-client) | gnark-crypto| Go | MIT| Ignacio Hagopian (@jsign)| Features: transcript verification, using additional external sources of entropy, eg. drand network, an arbitrary URL provided by the user. Note: double signing not supported due to lack of hash-to-curve in gnark. |
| [eth-KZG-ceremony-alt](https://github.com/arnaucube/eth-kzg-ceremony-alt) | kilic | Go | GPL-3.0| Arnaucube (@arnaucube)| 
| [Towers of Pau](https://github.com/dknopik/towers-of-pau/tree/proper-client)| blst | Go | MIT| Daniel Knopik (@dknopik), Marius van der Wijden (@MariusVanDerWijden) | Linux only, no signatures. |
| [cpp-kzg-ceremony-client](https://github.com/PatriceVignola/cpp-kzg-ceremony-client)| blst | C++ | AGPL-3.0 | Patrice Vignola (@PatriceVignola) | Features: BLS/ECDSA signing, transcript verification, Linux/Windows/MacOS support |
| [czg-keremony](https://github.com/dsrvlabs/czg-keremony)| noble-curves | JavaScript | MIT | JoonKyo Kim (@rootwarp),  HyungGi Kim (@kim201212) |  |
| [kzg-ceremony-client](https://github.com/NethermindEth/kzg-ceremony-client)| blst | C# | MIT | Alexey (@flcl42), CheeChyuan (@chee-chyuan), Michal (@mpzajac), Jorge (@jmederosalvarado), Prince (@prix0007) | |

### Browser Interfaces

| Interface| BLS Library | License | Author | IPFS| Repository| Notes|
| :- | :- | :- | :- | :- | :- | :- |
| [ZKParty Frontend](https://ceremony.ethereum.org/) | Arkworks|| [Several](https://github.com/zkparty/trusted-setup-frontend/graphs/contributors) | [latest.kzgceremony.eth](https://latest.kzgceremony.eth.limo/)| [trusted-setup-frontend](https://github.com/zkparty/trusted-setup-frontend)| References the latest version of the interface, which departs from the audited version in minor ways |
| ZKParty Frontend (Audit Commit) | Arkworks| | [Several](https://github.com/zkparty/trusted-setup-frontend/graphs/contributors) | [1] [audit.kzgceremony.eth](https://audit.kzgceremony.eth.limo/) | [trusted-setup-frontend](https://github.com/zkparty/trusted-setup-frontend/tree/40d421f16aafd93273f636e46dc8e0a39e4690b7) | The exact interface which Sigma Prime audited in November 2022. May have minor bugs or differences from the latest version above. [docker instructions](https://github.com/zkparty/trusted-setup-frontend/blob/main/README.md) |
| [Doge KZG](https://www.dogekzg.com/)| gnark | MIT | Andrew Davis (@Savid) | [2] | [dogekzg](https://github.com/Savid/dogekzg)| 🐶|

1. audit: QmevfvaP3nR5iMncWKa55B2f5mUgTAw9oDjFovD3XNrJTV
2. doge: QmRs83zAU1hEnPHeeSKBUa58kLiWiwkjG3rJCmB8ViTcSU

### BLS Libraries

| Library| Language | License | Audit |
| :- | :- | :- | :- |
| [blst](https://github.com/supranational/blst) | C & assembly | Apache 2.0| [Audit Report](https://research.nccgroup.com/wp-content/uploads/2021/01/NCC_Group_EthereumFoundation_ETHF002_Report_2021-01-20_v1.0.pdf), [[WIP] Formal Verification](https://github.com/GaloisInc/BLST-Verification)  |
| [Arkworks](https://github.com/arkworks-rs/curves) | Rust | Apache 2.0, MIT | | 
| [gnark-crypto](https://github.com/ConsenSys/gnark-crypto) | Go & assembly| Apache 2.0| [Audit Report](https://github.com/ConsenSys/gnark-crypto/blob/master/audit_oct2022.pdf) |
| [kilic](https://github.com/kilic/bls12-381) | Go | Apache 2.0| |
| [Herumi BLS](https://github.com/herumi/bls) | C++ & assembly | [modified BSD](http://opensource.org/licenses/BSD-3-Clause) | [Technical Assessment](https://blog.quarkslab.com/resources/2020-12-17-technical-assessment-of-herumi-libraries/20-07-732-REP.pdf) |
| [Constantine](https://github.com/mratsim/constantine) | Nim | Apache 2.0 | |
| [py_ecc](https://github.com/ethereum/py_ecc/) | Python | MIT | |
| [matterlabs/EIP1962](https://github.com/matter-labs/eip1962) | Rust | Apache 2.0 | |
| [noble-curves](https://github.com/paulmillr/noble-curves) | TypeScript/JS | MIT | |


## Media

| Title | Venue | Participants | Release Date |
| :- | :-- | :--| --: |
| [KZG Ceremony Duo Summons The Ethereum Road Map](https://thedefiant.io/kzg-ceremony-duo-summons-the-ethereum-road-map-2) | The Defiant | Tegan Kline, Carl Beekhuizen, Trent Van Epps | April 2023|
| [Episode 262: Ethereum’s KZG Ceremony with Trent & Carl](https://zeroknowledge.fm/262-2/) | Zero Knowledge | Anna Rose, Kobi Gurkan, Carl Beekhuizen, Trent Van Epps | Feb 2023|
| [Ethereum's KZG Ceremony](https://www.youtube.com/watch?v=nPzBMzX4pxQ) | Bankless | David Hoffman, Trent Van Epps, Carl Beekhuizen | Jan 2023 | 
| [Peep an EIP - KZG Ceremony](https://www.youtube.com/watch?v=a_gWHaaOKSo) | EthCatHerders | Pooja Ranjan, Carl Beekhuizen | Jan 2023 | 
| [Ethereum Foundation – EIP-4844 & KZG Ceremony](https://epicenter.tv/episodes/478) | Epicenter | Friederike Ernst, Trent Van Epps, Carl Beekhuizen| Jan 2023 |
| [Building the KZG Ceremony](https://www.youtube.com/watch?v=Z2jR75njZKc) | PSE Learn and Share | Nico Serrano, Geoff Lamperd | Dec 2022 |
| [The KZG Ceremony - or How I Learnt to Stop Worrying and Love Trusted Setups](https://archive.devcon.org/archive/watch/6/the-kzg-ceremony-or-how-i-learnt-to-stop-worrying-and-love-trusted-setups/?tab=YouTube) | Devcon | Carl Beekhuizen | Oct 2022 | 

## Public Calls
| Call # |Link | Date |
| -: | -: | -: |
|1 | [Agenda/Recording](https://github.com/ethereum/pm/issues/546) |June 9 2022 |
|2 | [Agenda/Recording](https://github.com/ethereum/pm/issues/558) | June 23 2022 |
|3 | [Agenda/Recording](https://github.com/ethereum/pm/issues/560) |July 7 2022 |
|4 | [Agenda/Recording](https://github.com/ethereum/pm/issues/569) | July 21 2022 |
|5 | [Agenda/Recording](https://github.com/ethereum/pm/issues/587) | Aug 4 2022 |
|6 | [Agenda/Recording](https://github.com/ethereum/pm/issues/593) |Aug 18 2022 |
|7 | [Agenda/Recording](https://github.com/ethereum/pm/issues/613) |Sept 1 2022 |
|8 | [Agenda/Recording](https://github.com/ethereum/pm/issues/623) | Sept 15 2022 |
|9 | [Agenda/Recording](https://github.com/ethereum/pm/issues/636) | Sept 29 2022 |
