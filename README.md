# EtherGov

## Background
DAOs present a new phenomenon native to the web3 space. For the first time throughout history, people are able to assemble and collectively preside over a pool of funds meant for a certain cause that they’re aligned with. DAOs are inherently borderless — internet-native organizations that arise out of a similar set of beliefs of its members.

Imagine a shared bank account that lives over the internet governed by multiple idea-aligned parties, and that unlike your bank account (where your funds are beholden to the bank), nobody can tell you what to do with your funds besides the DAO’s members itself.

## Problem
There exist huge technical barriers for prospective evangelists to launch a DAO in the first place. Depending on the nature of the DAO (and the scope of its treasury’s potential actions), it will require the DAO’s evangelists to have a deep understanding of different governance primitives, let alone the complexity of having to independently fork (or integrate with) a separate set of contracts, where every distinct set is commissioned by different projects.

In addition, once launched, the DAO’s operations will forever be heavily restricted to a specific chain (aka vendor lock-in). This is because DAOs are not chain-agnostic by nature: it is currently not possible for a DAO to engage in any arbitrary transaction on a chain that is external to where their treasury is based (unless DAO members are willing to subject their bridged treasury funds to additional trust assumptions, effectively foregoing decentralization and autonomy).

It is travesty to expect DAOs to concern themselves as to which chain to base their treasury on, let alone managing their own set of contracts, whether through forks / integrations or even building from scratch. The only thing that DAOs should concern themselves with, are aspects relating to the community: establishing a vision or ideology, attracting likeminded people from all over the internet, ideating on proposals (and the passing requirements of each), etc.

## Solution
EtherGov is a DAO-as-a-Service (DaaS) platform, lifting the heavy operational burden of DAOs while also enabling their treasury to be “chainless” for the very first time. DAOs no longer need to concern themselves with infra-setting: EtherGov abstracts away infra management complexities of DAOs, allowing them to solely focus on what matters most — the community.

EtherGov is a chain-agnostic treasury account for DAOs, with fully customizable payload to enable the execution of any arbitrary transaction on any chain, and extensible plug-and-play governance primitives to allow for composable voting logic on a per-proposal basis. With EtherGov, anyone regardless of web3 experience, can launch their own fully-fledged DAO. 

**Currently, EtherGov is equipped with the following governance primitives out-of-the-box:**
- NFTs as the principal identity for a DAO voter: anyone who wants to participate in a proposal needs to own and lock an NFT associated with the DAO (defined within its treasury params);
- ERC20 as voting power: when enabled on a proposal, instead of “one-NFT-one-vote” system, voters of that proposal would be under a veToken-esque mechanism (where the amount and remaining duration of the ERC20 that is timelocked determines a voter’s voting power);
- Sismo Connect for reputation-based services: proposal participation can be further gated by any data group within Sismo Factory (if not available, one of the council members can always create a new Sismo data group that would better serve the needs of the DAO);
- Governing Council (inspired by Polkadot’s OpenGov): only people that is part of the council will be allowed to initiate proposals and remove fellow council members — anyone can make their case and submit a council candidacy (alongside an arbitrary self-bond amount), and if the candidacy proposal collects enough votes, the candidate is admitted to the council list.

DAOs have historically struggled to garner participation, due to the inherently high friction that is present in typical web3 applications. **EtherGov has enabled the following abstractions in a bid to ease user onboarding and voting experience for a non web3-native DAO participant:**
- Biometric wallets: instead of using seed phrases, Cometh Connect allows voters to vote on proposals via biometric authentication in a gasless manner (voters do not need to pay anything to vote — gas fees are abstracted and sponsored by the DAO’s gas tank);
- DAO gas tank: while every DAO will use EtherGov’s gas tank during initial deployment, they reserve the option to deploy their own gas tank and update the gas tank address within its treasury params (the change will get reflected once the DAO’s proposal passes);
- Payload abstraction: instead of mandating non-technical council members to define complex payload inputs pertaining to a transaction, EtherGov has provided a list of commonly-used transaction presets for the proposal initiator to simulate the transaction as if it’s conducted via the front-end of the protocol itself (the payload will be automatically generated based on selection of the proposal initiator via the EtherGov widget, representing the transaction).

Every EtherGov deployment fundamentally consist of safeAA, govContract, and chainModule: safeAA for account abstraction (e.g., gasless voting, etc.) and to hold treasury funds, govContract encapsulates the primary voting logic governing the safeAA, while chainModule is a generic “pass-through” (built on top of Hyperlane) handling payload generation and transmission (so that it is securely relayed and is executable upon arrival on the target chain’s chainModule).
![EtherGov basic transaction flow](https://github.com/EtherGov/EtherGov-README/assets/93366176/1115a268-2be2-4e13-be78-a59500c897dc)

## Future Improvements

The current iteration of EtherGov is the bare minimum MVP that is necessary to serve as a PoC for [ETHOnline 2023](https://ethglobal.com/events/ethonline2023). **Potential features yet-to-be-implemented are as follows:**
- Multiple NFTs to represent voter identities: a DAO may want to have multiple NFTs under its wing (e.g., BAYC and CryptoPunks, Azuki and Elementals, etc.) — EtherGov will enable DAOs to set multiple NFTs within its params, allowing for even more composable voting logic (e.g., a proposal may mandate users to lock both BAYC and CryptoPunks in order to vote, etc.);
- Multiple ERC20s as voting power: a DAO may want to have multiple ERC20s under its wing (e.g., YugaLabs in the future might launch $PUNKS as a complement to $APE, etc.) — EtherGov will enable DAOs to set multiple ERC20s within its params, allowing for versatile per-proposal voting power arrangements (e.g., a proposal may have $APE lockers to be given 2x more voting power over $PUNKS for a BAYC-centric initiative, etc.);
- Email / social login as another web2 alternative to Cometh’s biometric authentication;
- Community-sourced transaction presets: anyone will be able to contribute transaction presets to EtherGov’s library for DAOs to use, in exchange for fees (one-time / per-usage).
- Enshrined NFT / ERC20: prospective DAOs can mint NFTs / ERC20 through EtherGov, by which they will be natively enshrined within its treasury params (instead of having to mint NFTs / ERC20 separately, and then pasting their addresses into the DAO’s treasury params)
- Generative mint-and-auction contract plugin: a separate contract emulating NounsDAO’s [noun auction mechanism](https://nouns.center/intro), automatically relaying proceeds to the DAO’s EtherGov treasury.
- etc.

### Video Demo
_paste link here_
