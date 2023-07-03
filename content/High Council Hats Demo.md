This is a demo of how Hats Protocol can be used to support High Council, with an emphasis on how it can give Member DAOs flexibility to vote in the way that works for them. Here's what this brief document covers:

1. High Council Membership 

2. How Member DAOs can vote in High Council _(skip to this section if you just want to __see the demo)_

If you're not yet familiar with Hats Protocol, check out [this document](https://docs.google.com/document/d/1i3dJGboD9pv9DyYGzUpr4EVcMSCwdYH3yXLlejRjj-o) that we shared during the last High Council call.

Everything referenced below is live on Goerli testnet.

# 🏛️🧢🌲 High Council Hats Tree 

A couple weeks ago we shared a figma mockup of the Hats Tree we'd propose for High Council. For this week, we've put that tree onchain on Goerli. You can check it out here in [the Hats app](https://app.hatsprotocol.xyz/trees/5/87/87).

[](https://s3.amazonaws.com/charm.public/user-content/7e54e8e0-9a82-4475-ab1c-08acd345fe4b/4641a599-4cdf-461f-b2fb-5c4d85f05000/d678ce50-312b-46b8-9c40-26a5d2928940.png)

Each of these nodes (aka hats) represents a role within the High Council organization. Addresses (people/EOAs, multisigs, DAOs, and other contracts) that have these roles (aka "wear" these hats) receive erc1155 tokens in their wallet. 

A couple weeks ago we discussed some of the operational benefits conferred by the right branch of this tree. The present demo focuses on the left branch, also known as the Membership Domain:

[](https://s3.amazonaws.com/charm.public/user-content/7e54e8e0-9a82-4475-ab1c-08acd345fe4b/fde47ba6-6bc6-4077-a438-c2071597449f/49151c6d-095a-4db7-8aa4-3fd3a60103bd.png)

A couple key things to note in the Membership Domain:

- The Membership Domain is the first branch of the tree

- The High Council tree is #87 on Goerli, so the id of the Membership Domain is `87.1`

- Each Member DAO gets its own hat within the Membership Domain. In the screenshot above, there are three Member DAOs. Each has an id of `87.1.*`. This `*` will be important later.

- The first child hat of each Member DAO is its Voting Representative. The wearer of this hat can vote on the Member's behalf within High Council (see next section). The id of these hats are `87.1.*.1`. 

# 🗳️ Voting in High Council 

As described in the last bullet point above, any address that is wearing a hat with an id matching the pattern of `87.1.*.1` has `votingPower == 1` in High Council. This is achieved via a custom Hats-based voting vault ([code here](https://github.com/Hats-Protocol/highcouncil-hats-vault/blob/main/src/HatsHighCouncilVotingVault.sol)).

To demonstrate how this works, we have deployed a test instance of Council to Goerli and wired it up with this voting vault. To see it in action, take a look at the following contracts on etherscan:

- [Core Voting Contract](https://goerli.etherscan.io/address/0x5EEaE7649889561C5EA704d2234f9FfFD94AdbA9)

- [Hats High Council Voting Vault](https://goerli.etherscan.io/address/0x1ba28514444198651599e3b4aa60fab78663c264)

  - determines voting power for the Core Voting Contract via the logic described above

I (`spengrah.eth`) submitted a proposal to this instance of Council. I was able to do this because I am wear hat `87.1.2.1`, which (as you can see in the Membership Domain branch) is the Hats Team's voting representative hat. Since it matches the pattern `87.1.*.1`, I have voting power of 1, which is enough to create a proposal.

[](https://s3.amazonaws.com/charm.public/user-content/7e54e8e0-9a82-4475-ab1c-08acd345fe4b/d1101873-118c-454f-adc8-a298438c4443/3d253822-d8c2-4219-9b66-cf4024ceecf6.png)

One of the coolest implications of this setup is that the Council contracts don't need to know anything about the address submitting the votes other than that they have a valid voting rep hat. All that needs to happen is for the Member DAO to issue the hat to a representative of their choosing, which could be:

- an individual representative, eg by issuing the voting rep hat to an **EOA**,

- a representative committee, eg by issuing the voting rep hat to a **multisig**,

- a GSC, eg by issuing the voting rep hat to its **GSC**,

- the **Member DAO itself**, eg by issuing itself the voting rep hat, or

- the Member DAO's entity on another chain, eg by issuing the voting rep hat to the DAO's **cross-chain avatar** **contract** on the High Council network (see next section for more details)

### Cross-Chain Membership & Voting

A DAO -- eg DAO X -- based on other chains wanting to participate in High Council governance can create a contract (aka an "avatar") on the High Council network that is controlled via cross-chain messaging. This avatar represents DAO X on the High Council network.

To become a member of High Council governance, DAO X would request their member hat and/or the voting rep hat be minted to the avatar.

- option A: DAO X's Avatar wears both their member hat and their voting rep hat

- option B: DAO X's Avatar wears their member hat, and delegates the voting rep hat to an address of their choosing

[](https://s3.amazonaws.com/charm.public/user-content/7e54e8e0-9a82-4475-ab1c-08acd345fe4b/243a1b4c-accb-41c0-84aa-8526cf8219e5/0eeee673-b6b4-4968-86b1-3d443ccbe731.png)

Alternatively, if some sort of multi-tenant cross-chain solution emerges, DAO X would request their member hat and/or the vote rep hat be minted to that multi-tenant contract and associated with DAO X's identifier within that contract.

# 🦾 Try it yourself!

To test this out yourself, all you need is a voting rep hat. Message somebody from the Hats team (Spencer, David, or nintynick) and we'll create a Member Hat for your organization along with a Voting Rep hat for you. All we need is...

- the name of the organization you represent

- your Goerli address

You can use your hat to either submit a new proposal or vote on the existing one, via the [Core Voting contract](https://goerli.etherscan.io/address/0x5EEaE7649889561C5EA704d2234f9FfFD94AdbA9#readContract).

## Vote on the existing proposal 

Follow these steps to vote:

1. On the [Write Contract tab](https://goerli.etherscan.io/address/0x5EEaE7649889561C5EA704d2234f9FfFD94AdbA9#writeContract), find the `vote` function (#12)

2. Enter the following values for each of the parameters:

   1. `votingVaults`: `[0x1ba28514444198651599e3b4aa60fab78663c264]` \-- the Hats High Council Voting Vault address (brackets required)

   2. `extraVaultData`: `[your_hat_id]` \-- the hex-encoded id of your voting rep hat (brackets required)

      1. This value will be `0x570001000*000100000000000000000000000000000000000000000000`, where the `*` corresponds to your organization's location within the High Council hats tree. You can find this number `87.1.*.1` in the hats app.

      2. You can also get this value by converting the base10 hat id from the hats app to hex in your preferred conversion tool.

   3. `proposalId`: `0` \-- this is the 0th proposal

   4. `ballot`: `0` for Yes; `1` for No; `2` for Maybe

3. Submit your tx