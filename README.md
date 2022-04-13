# Semaphore

A semaphore is a gadget allowing Ethereum users to prove their membership of a set which they had previously joined without revealing their original identity.
It comprises of **smart contracts** and **zero knowledge components** working in tandem.

#### Smart Contracts:

The smart contracts handle: state, permissions, proof verification **on-chain**

#### Zero Knowledge Components:

The zero knowledge components: generate proofs **off-chain**, updates state if proofs are valid

### Basic Understanding:

  - Generate off-chain identities and add them to a merkle tree (on or off chain)
  - Anonymously broadcast signal on-chain if and only if the owner belongs to a valid merkle tree and the nullifier has not already been used.

### Understanding Circuits:

Circuits allow you to prove:

  - **Merkle tree**: that the identity commitment exists in the Merkle tree,
  - **Nullifiers**: that the signal was only broadcasted once,
  - **Signal**: that the signal was truly broadcasted by the user who generated the proof.

### Understanding the Smart Contracts

Semaphore "main" smart contracts can be grouped into two main categories: Base and Extension
Extension is essentialy the base contract implemented for a specific task ie Voting

#### Base

**SemaphoreCore.sol**: contains the functions to verify Semaphore proofs and to save the nullifier hash in order to avoid double signaling;
**SemaphoreGroups.sol**: contains the functions to create groups, add or remove members.

SemaphoreCore should be used in every implementation and is used to verify proofs with Semaphore.
SemaphoreGroups is an abstract contract and every function can be overidden
