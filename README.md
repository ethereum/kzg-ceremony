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

## Special Contributions

April 1-16 2023 was the Special Contribution Period for the KZG Ceremony. This allowed participants to contribute in ways that may not have been possible in the Open Contribution period.

While the Ceremony only needs a single honest participant to provide a secure output, Special Contributions provide additional assurances beyond a standard entropy contribution:

- computing over the entropy in an isolated environment (eg. on an airgapped machine, wiping and physically destroying hardware) means it's unlikely for a malicious entity to have extracted the entropy at any point
- detailed documentation (explore links below) attached to real reputations are unlikely to all have been coopted or faked by a malicious coordinating entity. The records are available for future observers to explore.
- different hardware and software limits correlated risk
- differentiated entropy generation (eg. measuring an explosion) prevents the Ceremony output being compromised by some failure in the regular entropy generation (eg. the hosted interface)
- contributions involving large groups of people are harder to fake than those with only one person

This post is a public record of the Special Contributions with information on methodology, where to find them in the transcript, and links to documenting media. 

- [00 - Cryptosat](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#00---cryptosat)
- [01 - The KZG Marble Machine](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#01---the-kzg-marble-machine)
- [02 - Mr. Moloch's Ephemeral Album II](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#02---mr-molochs-ephemeral-album-ii)
- [03 - Dog Dinner Dance Dynamics](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#03---dog-dinner-dance-dynamics)
- [04 - CZG-Keremony - a pure JS KZG ceremony client](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#04---czg-keremony---a-pure-js-kzg-ceremony-client)
- [05 - Improvised Theatre](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#05---improvised-theatre)
- [06 - A Calculating Car](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#06---a-calculating-car)
- [07 - A noisy city](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#07---a-noisy-city)
- [08 - Exothermic Entropy](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#08---exothermic-entropy)
- [09 - The Sferic Project](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#09---the-sferic-project)
- [10 - The Great Belgian Beer Entropy Caper](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#10---the-great-belgian-beer-entropy-caper)
- [11 - KZGamer - summoning Dankshard with a dice-tower](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#11---kzgamer---summoning-dankshard-with-a-dice-tower)
- [12 - Catropy](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#12---catropy)
- [13 - srsly - an iOS KZG Ceremony client](https://github.com/ethereum/kzg-ceremony/blob/main/special_contributions.md#13---srsly---an-ios-kzg-ceremony-client)

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
