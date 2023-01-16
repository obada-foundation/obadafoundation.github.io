---
title: The pNFT Standard
permalink: /standard/
has_children: true 
nav_order: 4
---


# Representing Physical Assets using Non-Fungible Tokens
Text for ISO New Work Item Proposal Form 04 - approved by AHG3 Aug 31, 2022
 
<br>

## Outline

#### Foreword

#### Introduction

#### 1. Scope

#### 2. Normative References

#### 3. Terms and Definitions

#### 4. Architecture

#### 5. Physical Asset Data Model
* 5.1	Physical Asset Identifier Generation Methods 
     * 5.1.1 	Decentralized Identifier (DID) Generation Method
     * 5.1.2    The USN (Universal Serial Number) Human Readable Identifier
     * 5.1.3 	Alternate DID Generation Methods / Use of Existing Edentifiers
* 5.2  Resolving Physical Asset Data 
     * 5.2.1 	Data Storage / On-chain vs Off-chain
     * 5.2.2 	Verifiable Data - Hashing and Checksum (root hash)

#### 6. Physical Layer Verification Processes
* 6.1 Trust Anchor System 
* 6.2 Human Trust Anchor Methods
* 6.3 Machine Trust Anchor Methods

#### 7. Communication Protocol for DID Registry Interoperability
* 7.1 DID Method Scheme to Enable DID Registry Interoperability
* 7.2 Embedding the Digital Representation in a Supply-Chain Application and/or in an NFT 
* 7.3 Smart Contract
* 7.4 Cryptocurrency Interactions

#### 8.  Privacy, Encryption, Cybersecurity
* 8.1 Privacy, Confidentiality, and Anonymity
* 8.2 Compliance with Legislative, Regulatory, and Other Authorities (e.g. GDPR, Right to be Forgotten)
* 8.3 Ownership, Administration, and Control of the Digital Representation
* 8.4 Security Considerations 


<br>

## Purpose & Justification


The purpose of this proposal is to create a DLT-agnostic standard for representing physical assets as non-fungible tokens (NFTs).  Standardizing the physical NFT will enable better management and interoperability of physical assets across supply chain / enterprise systems, with verifiable digital information.  The ability to register the existence, prove the events, and transfer the ownership of physical assets has numerous environmental implications as well.  For example, in the asset disposition sector, 50 million tons of used electronics reach end-of-life each year, yet only 15% of this e-waste can currently be tracked.  Similar problems exist in many other industries.   The traceability enabled by this standard has the potential to positively impact any industrial sector dealing with identifiable assets.

This DLT agnostic architecture solves the three fundamental problems encountered when developing any  blockchain solution for physical assets:

* First, a creative approach is needed to create a Digital Representation of a physical asset.  A common “fingerprint” for a given asset is needed, given that siloed systems typically assign their own forms of ID.   So an algorithmic “formula” essentially creates a “universal ID”, that anyone can recreate, based on serial numbers and other info that can be found on the asset.  Data about the asset gets associated to the universal ID in a way that proves that the data could not have been changed or tampered with.
* Second, real-world processes that act on the physical asset need to be tied to the Digital Representation.   The asset’s existence must be proven, as must the actions of the humans and machines that process the asset.
* And last, a scheme for creating interoperable registries to store the Digital Representations.

These necessary pieces of the data puzzle enable a fundamental infrastructure component for any type of physical asset or supply chain.  It allows any ecosystem, community or organization to set up their own interoperable Digital Representations, to embed as a native component in their supply chain/enterprise systems, or to utilize as a primitive component in their own physical NFTs.

<br>

## Scope

### This document establishes a DLT agnostic architecture for physical assets using NFTs which includes:

* **An algorithmic data method**  for generating decentralized identifiers (DIDs) from physical assets with immutable unique identifiers, such as serial numbers.
* **Processes for utilizing off-chain trust anchors** to establish proof of real-world human and machine generated events and information, that tie a real-world asset to its Digital Representation.
* **A DID method scheme** to enable DID Registry interoperability, so the Digital Representation can be stored, resolved, or transfered to any compliant DID Registry.

### This document is applicable to…

* Serialized physical assets with unique immutable identifiers, such as serial numbers.
* The systems, machines, organizations, and natural persons that process them.

### This document is not applicable to...
* Fungible assets and non-serialized, non-fungible assets (unique assets without immutable identifiers).
* Digital assets and identifiable bundles of assets. 
* Any specific DID method, blockchain / DLT protocol, or NFT standard.


