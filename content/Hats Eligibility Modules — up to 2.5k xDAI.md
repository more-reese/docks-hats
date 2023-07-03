**Bounty: up to 2\.5k xDAI**

# Overview

A [Hats Eligibility module](https://github.com/Hats-Protocol/hats-protocol#eligibility) is a contract that programmatically controls which addresses are eligible to wear a given Hat. It handles both up-front eligibility (who can be minted a Hat in the first place) and revocation (who should lose their Hat).

Eligibility is one of the most powerful aspects of Hats Protocol, and we expect there to be a broad ecosystem of eligibility modules covering a myriad of use cases. Many of these modules will be very niche, or serve as adapters between Hats Protocol and other reputation and governance protocols.

Some of them, however, will be nearly universal. This bounty is for two such eligibility modules, focused on the three main token standards: ERC721, ERC1155, and ERC20. The first is required, and the second two are optional. Our expectation is that all three will utilize similar internal logic, so the second two should not require as much work as the first.

Some illustrative examples of how DAOs might use these eligibility modules:

- If you have a particular Govrn contribution NFT(s) (ERC721), you qualify for a more advanced role (hat) in the DAO.

- If you have a ticket to a previous SongCamp event (ERC1155), you are eligible for the "music experts" panel in the DAO.

- If you have enough of the DAO's tokens or shares (ERC20), you are eligible for the baseline "member" Hat. Or conversely, if at any point you no longer have enough tokens, any Hat from that DAO that you are wearing would be revoked from you.

# Specifications

All eligibility modules must implement the following function:

`getWearerStatus(address wearer, uint256 hatId) external view virtual returns (bool eligible, bool standing);`

Eligibility modules can be composed together by calling other eligibility modules from within `getWearerStatus()`. For the present three modules, `standing` should always return true, on the expectation that they will be composed with other modules that handle `standing`. 

## 1\. ERC 721 Eligibility Module — 1\.5k DAI

- `standing` should always return true

- `eligible` should return true only if the `wearer` is the owner of the specified ERC721 token(s), as identified by contract address and token id

- Should be configurable to support single-token criteria as well as multiple-token criteria

## 2\. ERC1155 Eligibility Module — +0.5k DAI

- `standing` should always return true

- `eligible` should return true only if the `wearer` has at least a specified balance of the specified ERC1155 token(s), as identified by contract address and token id

- Should be configurable to support single-token criteria as well as multiple-token criteria

  - Balance requirement should be configurable for each token

## 3. ERC20 Eligibility Module — \+0.5k DAI

- `standing` should always return true

- `eligible` should return true only if the `wearer` has at least a specified balance of the specified ERC20 token(s)

- Should be configurable to support single-token criteria as well as multiple-token criteria

  - Balance requirement should be configurable for each token

# Other Requirements

- Each module should inherit from [HatsEligibilityModule](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsEligibilityModule.sol) from the [hats-module repo](https://github.com/Hats-Protocol/hats-module)

- Each module should be deployable by [HatsModuleFactory](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsModuleFactory.sol) (see the Releases for most recent version)

- Gas efficiency is key, since eligibility modules will likely be called many many times over the life of the Hat(s) they are attached to. 

  - See the hats-module repo for how the use of clones with immutable args can generate substantial gas savings.

- Utilize our standard solidity repo structure (see the [hats-module repo](https://github.com/Hats-Protocol/hats-module) for an example)

- Full test coverage

- Any contract owners with permissions to change parameters (which may or may not be necessary or beneficial) should be Hats, not addresses (see [this contract](https://github.com/Hats-Protocol/hats-baal-shamans/blob/d3a3796b678cd805d788f15f7517de6e687c392a/src/HatsOnboardingShaman.sol#LL290C1-L290C1) for an example)

- All code should be permissive and open-source, with MIT license

# What you can expect from the Hats Protocol team

- This is an opportunity to build two foundational eligibility modules that will touch a huge portion of the Hats Protocol ecosystem of users

- We will work with you to understand how the Hats Protocol, HatsEligibilityModule, and HatsModuleFactory contracts work

- We will work with you on implementation considerations, tradeoffs, and prioritization

- We will help you wrt working with Foundry (as necessary)

- We will be available for questions and support throughout the project

- If/when we see you irl, you'll get a Hats hat! 🧢