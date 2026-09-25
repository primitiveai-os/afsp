# AFSP: Agentic Financial Services Protocol

AFSP is an open standard for verifying AI agents before they access a regulated financial institution's open banking APIs. It defines a Pre-Credential Trust Layer (AFSP-01): before an agent reaches an institution's systems, it must show who it is, who it is acting for, and that the request has been authorized.

AFSP is a standard, not a product. It is written for financial institutions, agent platforms, and anyone building against open banking infrastructure.

## Status

**v0.1 Draft. Open for public comment for 30 days.**

<!-- TODO: add publication date and a link to the specification document. -->

## The five checks

To reach an institution's open banking API, an agent must present a cryptographically signed attestation covering five checks:

| Signal | Check | What it confirms |
|---|---|---|
| **S1** | Who is this agent? | Where the software making the request comes from |
| **S2** | Acting for whom? | That the customer authorized this session |
| **S3** | Identity verified? | That the customer's identity was confirmed beforehand |
| **S4** | Financially real? | That the customer is a genuine account holder |
| **S5** | Present right now? | That a live human is at the other end of the session |

The institution verifies all five checks in real time. If any check fails, the session stops before the agent reaches the underlying banking systems. Together, the five checks form AFSP's "Know Your Agent" (KYA) layer.

## How it works

1. **Consumer and agent.** The agent requests access. The consumer authorizes the session on their enrolled device, using biometric binding in the device's hardware trusted execution environment (TEE).
2. **AFSP platform.** Signals S1–S5 come from independent sources and are bound into a single ECDSA-signed JSON attestation (the PCAA package).
3. **Institution.** The institution's API endpoint checks the signature, the binding, and each signal against the institution's own risk-decisioning framework.
4. **Existing controls.** KYC, credit, and fraud decisions go ahead as they do today. AFSP's role ends at the clearance decision.

### Scope

AFSP does not make credit, fraud, KYC, or servicing decisions. Those controls stay with the institution; AFSP runs before them. AFSP is designed to fit existing regulatory frameworks, including Section 1033 and FFIEC guidance, and to give regulators an auditable record.

## Get involved

- **Read and comment on the spec.** The full technical specification will be published in this repository and open for comment.
- **Become a founding endorser.** This requires a letter and a commitment to join the working group. Contact [afsp@primitive.com](mailto:afsp@primitive.com).
- **Build against it.** The specification, schemas, and worked examples are open to any platform.

## Extending AFSP

Any organization may propose an extension. [Open an extension proposal](https://github.com/primitiveai-os/afsp/issues/new?template=extension-proposal.yml). See [CONTRIBUTING.md](CONTRIBUTING.md) for what to include and how proposals are reviewed.

## Governance

AFSP is maintained by the AFSP Technical Working Group. See the [charter](CHARTER.md).

**Founding partners**

- **CIDR Technologies Inc d.b.a Primitive**: founding technical author
- **MX**: founding endorser

Founding endorsers have board-level input into the standard. Founding endorsement stays open to other institutions during the comment period.

Primitive has committed to transferring governance to an independent non-profit AFSP foundation as adoption grows. The foundation's governance model is patterned on the Financial Data Exchange (FDX). Nick Thomas has agreed to serve as the foundation's interim executive director.

## License

AFSP, including the specification, schemas and example code, is published under the [Apache License 2.0](LICENSE). It is royalty-free and includes a patent grant from the authors and every contributor for their contributions.

See [NOTICE](NOTICE) and the [patent notice](PATENTS.md). Contributors must accept the [Contributor License Agreement](legal/cla/INDIVIDUAL.md).

The license does not grant rights to the AFSP name. Only versions approved by the AFSP Technical Working Group may be called AFSP or claim AFSP conformance.

## Contact

[afsp@primitive.com](mailto:afsp@primitive.com)
