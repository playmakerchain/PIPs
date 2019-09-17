# PowerPlay Improvement Proposals
This repository for the Powerplay Improvement Proposals (PIPs) and PowerPlay Standards Process (PSP) describes the  standards for the network, including core protocol specifications, client APIs, and smart contract standards.

## PIP Status Terms
* **Draft** - a PIP that is undergoing rapid iteration and changes.
* **Last Call** - a PIP that is done with its initial iteration and ready for review by a wide audience.
* **Accepted** - a core PIP that has been in Last Call for at least 2 weeks and any technical changes that were requested have been addressed by the author. The process for Core Devs to decide whether to encode a PIP into their clients as part of a hard fork is not part of the PIP process. If such a decision is made, the PIP wil move to final.
* **Final (non-Core)** - a PIP that has been in Last Call for at least 2 weeks and any technical changes that were requested have been addressed by the author.
* **Final (Core)** - a PIP that the Core Devs have decided to implement and release in a future hard fork or has already been released in a hard fork. 
* **Deferred** - a PIP that is not being considered for immediate adoption. May be reconsidered in the future for a subsequent hard fork.

## Contributing Guide

We welcome all contributions to the PowerPlay Network. Our core-devs are always reviewing all improvement proposals and to submit a new proposal just follow these steps:

 1. Review [PIP](PIPs/PIP1.md).
 2. Fork the repository by clicking "Fork" in the top right.
 3. Add your PIP to your fork of the repository. There is a [template PIP here](pip-template.md).
 4. Submit a Pull Request the PowerPlay [PIPs repository](https://github.com/playmakerchain/PIPs).

Your first PR should be a first draft of the final PIP - open a PR changing the state of your PIP to 'Final'. Once submitted, the draft will be reviewed by an editor and if is no rough consensus - for instance, because contributors point out significant issues with the IP - they may close the PR and request that you fix the issues in the draft before trying again.
