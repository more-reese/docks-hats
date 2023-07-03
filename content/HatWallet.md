
**Script**

One of the biggest challenges for DAOs today is the lack of accountability for paid contributors. It is an easy trap for a DAO to fall into, where contributor compensation is set up via DAO proposal, and some contributors are receiving large or recurring grants, but after some time, stop delivering work that is commensurate with that compensation. Right now, DAOs don't have a good way of holding those contributors accountable to following through on their responsibilities, and stopping compensation when appropriate.

Our project builds on top of Hats Protocol, an open-source repo that enables DAOs to grant their contributors roles represented by ERC1155 tokens.

We implemented a Hat-specific version of Mech from Gnosis Guild to give every Hat its own smart contract wallet, then attached the Superfluid compensation streams to those wallets. This is HatWallet. HatWallets are wallets that are controlled by the DAO but can be delegated to specific individuals and tied to specific accountabilities.

This unlocks three key capabilities:

1. HatWallet gives the DAO control over specific wallets as opposed to relying on individuals personal EOAs. This improves security.

2. HatWallet introduces role-based rewards, tying streamed rewards and compensation with a given role rather than specific addresses. This ensures good stewardship of the DAOs resources, and enables a more programmable and permissionless contribution-based reward structure.

3. HatWallet connects rewards and signing authority associated with a wallet to specific accountabilities. For example, if a facilitator role comes with control of a given HatWallet, and a specific requirement for keeping that roles is maintaining at least a 75% approval rating from their colleagues, the moment they fall below that threshold they will lose access to the rewards and authorities associated with that HatWallet. 

Here’s how it works…

(Show how it works)

Conclusion