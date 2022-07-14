# W3F Open Grant Proposal

* **Project Name:** halo2_wasm
* **Team Name:** annoymous
* **Payment Address:** TBD

## Project Overview :page_facing_up:

Zero-knowledge proofs are a powerful cryptographic tool to enable may important applications such as zk-rollups, private transactions, and more. Popular ZKP protocols, such as Groth16 and Plonk, suffer from performance issues when the proofs are verified via WASM. This is due to fact that the underlying elliptic curve operations and pairings that are prohibitively slow in wasm, making them useless for real world applications. Efforts have been spend in optimizing wasm performance for plonk ZKP. In comparison, plonk proofs can be verified with Solidity with a couple million of Gas on Ethereum.

Instead of trying to improve pairing performance, which may also require a set of pre-compiles for bls12-381 curve, we propose an alternative route - to build a halo2 verifier in wasm. Halo2's verification algorithm consists of a multi-scalar-multiplication over the so-called pasta curves. 


### Overview

This project is meant to be a research project to analyze the feasibility of halo2 verifier in WASM, 
and compare it with a plonk verifier, with potentially a larger, follow-up project to deploy entire halo2 in product. 

### Project Details

The halo2 verification code base will mostly be borrowed from the Halo2 library, with necessary modifications for optimization and wasm compatibility.

The halo2 verification pallet will be a host of the verification algorithm. We will provide a demo to properly config the pallet. 

For comparison and benchmark purpose, we will also build a PoC for plonk verifier from the Jellyfish library. We will set a same number of constraints for both systems, tentatively 2^16, which reflects a typical z-cash circuit size, and report the efficiency difference between the proof systems.

In summary, the deliverables in this project consists of 
- a PoC pallet for Pasta Curves which may be of independent interest.
- a PoC pallet for Halo2 verifier, which is capable of verifying zero-knowledge proofs with a given verification key.
- a PoC pallet for Jellyfish Plonk verifier, which is capable of verifying zero-knowledge proofs with a given verification key.
- a tech report to summarize the performance differences.

### Ecosystem Fit
Zero knowledge proof systems is one of the hottest topic in the domain. It will enable many applications, such as private transactions, zk-rollups, zk-EVMs, cross-chain proofs and more. This project is one step further in searching for wasm friendly prove systems, and hopefully, it will report Halo2 being the right choice.

A side product of this project is the pallet for Pasta curves, a pair of cyclic curves, which is likely to be useful beyond Halo2.


## Team :busts_in_silhouette:

### Team members

* Anonymous. The member choose to be anonymous at the current stage. 

### Contact

* **Contact Name:** 
* **Contact Email:** iwritecryptocodes@gmail.com


### Legal Structure

* Individual

### Team's experience

We have extensive experience in the ZKP domain:
- we have build a privacy oriented pallet for Substrate before
- we have publications at Crypto on the topic around zero knowledge proofs
- we have discovered efficient curves for ZKP systems
- we have implemented UltraPlonk in Rust at the production level from scratch
- we have implemented Plonk verifier in Solidity smart contract
- we have hand optimized Plonk circuits and R1CS circuits for various applications

### Team Code Repos

* https://github.com/annoymous2022

### Team LinkedIn Profiles

* Anonymous

## Development Roadmap :nut_and_bolt:

### Summary
We plan to provide the following pallets:
- Pasta Curves
- Halo2 Verifier
- Plonk Verifier
We will also write a tech report about our findings, and an instruction for developers to invoke the verifiers.

### Overview

* **Total Estimated Duration:** 6 months
* **Full-Time Equivalent (FTE):**  0.5 FTE
* **Total Costs:** 30000 USDC

### Milestone 1 Example — Implement Pasta Curves Pallet

* **Estimated Duration:** 1.5 months
* **FTE:**  1
* **Costs:** 5000 USDC

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 1a. | License | Apache 2.0 / MIT / Unlicense |
| 1b. | Documentation | We will provide both inline documentation of the code and a basic tutorial that explains how a developer may use those curve operations |
| 1c. | Testing Guide | Core functions will be fully covered by unit tests and audit to ensure functionality and robustness. In the guide, we will describe how to run these tests. |

### Milestone 2 Example — Implement Halo2 Verifier Pallet

* **Estimated Duration:** 1.5 months
* **FTE:**  0.5
* **Costs:** 10000 USDC

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 2a. | License | Apache 2.0 / MIT / Unlicense |
| 2b. | Documentation | We will provide both inline documentation of the code and a basic tutorial that explains how a developer may use those curve operations |
| 2c. | Testing Guide | Core functions will be fully covered by unit tests and audit to ensure functionality and robustness. In the guide, we will describe how to run these tests. |
| 2d. | Demo | A demo to verify some rust-natively generated prove with this pallet |

### Milestone 3 Example — Implement Pasta Curves Pallet
* **Estimated Duration:** 2 months
* **FTE:**  0.5
* **Costs:** 10000 USDC

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 3a. | License | Apache 2.0 / MIT / Unlicense |
| 3b. | Documentation | We will provide both inline documentation of the code and a basic tutorial that explains how a developer may use those curve operations |
| 3c. | Testing Guide | Core functions will be fully covered by unit tests and audit to ensure functionality and robustness. In the guide, we will describe how to run these tests. |
| 3d. | Demo | A demo to verify some rust-natively generated prove with this pallet |

### Milestone 4 Example — Final report
* **Estimated Duration:** 1 months
* **FTE:**  0.5
* **Costs:** 5000 DAI

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 4a. | License | Apache 2.0 / MIT / Unlicense |
| 4b. | Report | We will provide a report on the technique details for comparison, and instructions for developers to follow |

## Future Plans

* If Halo2 verifier turns out to be significantly better than Plonk verifier, we may proceed with a  Halo2 provers in warm project.

## Additional Information :heavy_plus_sign:
