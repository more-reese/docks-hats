**Bounty: 4k xDAI**

# Overview

[Hats Signer Gate](https://github.com/Hats-Protocol/hats-zodiac) is a [Gnosis Zodiac](https://github.com/gnosis/zodiac) module that enables a DAO to delegate signer authority on a multisig to wearers of a specified Hat (or multiple Hats, in the Multi Hats Signer Gate variant).

The signers can manage funds and execute transactions from the multisig, but they cannot add new signers, change the threshold, or make any administrative changes. If they lose their Hat, they immediately lose their ability to sign.

\
We built the HSG (and MHSG variant) contracts because our early users have been asking for it, and we've come to recognize it as an important primitive in modern DAO operations. For example, DAOs want to be able to have programmatic, revocable control over the signers on working group multisigs that execute on budget allocations for those working groups, or wherever you see "multisig signing authority" in [this Hats Template](https://app.charmverse.io/hats-protocol/page-9585564840792724).

However, while an HSG-gated Safe can be used with the Safe app just like any other, the only way to set up HSG or claim signer rights is via etherscan, which is not great UX.

This bounty is for building a front end that facilitates HSG setup, configuration, and claiming.

# Requirements & User Stories

The app should support the following user actions. They apply to both HSG and MHSG.

**\[Hat Wearers / Signers\]**

1. As a DAO contributor that is wearing the signer hat for a particular multisig, I want to **c****laim signer authority **via its HSG

2. As a DAO contributor that no longer wants signing authority on a particular multisig, I want to **r****enounce signer authority **via its HSG 

   1. (could be as simple as linking to the [Hats Protocol app](https://app.hatsprotocol.xyz) for renouncing their Hat)

**\[Deployers\]**

As a DAO governance facilitator looking to spin up a new multisig for which the DAO controls the signers, I want to...

1. Set up a new HSG with the necessary configuration parameters

   1. pre-requisite for (2) and (4)

2. Deploy a new HSG together with a new Safe

As a DAO governance facilitator looking to add DAO control over signers on one of my existing multisigs, I want to...

1. Check [whether](https://github.com/Hats-Protocol/hats-zodiac/blob/39fc6925d136fc04d6e5f60bf643b5d7f49dcaa9/src/HatsSignerGateFactory.sol#L276) that multisig can be safely connected to HSG

2. Deploy a new HSG for use alongside the multisig

3. Initiate a multisig transaction to wire up a new HSG — eg from (4) — to the multisig

**\[Owners\]**

As a DAO governance facilitator (wearing the ownerHat for a given HSG), as I learn more about how the multisig should operate I may want to revise its configuration by...

1. Changing the targetThreshold

2. Changing the minThreshold

3. Changing the ownerHat

4. Adding a new signerHat (MHSG only)

**\[All\]**

1. View configuration parameters for a given HSG

2. View validity status for each existing signer for a given HSG

3. Remove invalid signer(s)

# Other Specifications

- Apart from _Deployers-5_, all multisig transactions can be handled by the Safe app; no need to build any Safe wrapper functionality

- Supports the [latest version](https://github.com/Hats-Protocol/hats-zodiac/releases) of HSG, MHSG, and the Hats Signer Gate Factory

- Supports all networks to which the above are deployed (we will work with you to deploy where relevant)

- The app will ideally be built with the same stack used by the Hats Protocol app (we will provide access to the source code for reference)

  - Hats Protocol subgraph

  - react

  - wagmi / viem

  - rainbowkit

  - next.js

  - vercel (if desired, and you can use our team's account)

- As much as possible, the UI should have the same look and feel as the next version of the Hats Protocol app (currently in development) — we will share figma designs for that app with those working on this project

- All code should be permissive and open-source, with MIT license

# What you can expect from the Hats Protocol team

- We will work with you to understand how the HSG/MHSG contracts work

- We will work with you on implementation considerations, tradeoffs, and prioritization

- We will work with you on copywriting and other Hats-specific UX considerations

- We will provide front end code and other support for building with our stack

- We will provide figma designs for the next version of the Hats Protocol app as a UI reference

- We will be available for questions and support throughout the project

- If/when we see you irl, you'll get a Hats hat! 🧢