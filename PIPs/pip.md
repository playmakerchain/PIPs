---
pip: 1
title: PIP Purpose and Guidelines
author: Fabian Vogelsteller <fabian@lukso.network>, Martin Becze <mb@ethereum.org>, Hudson Jameson <hudson@ethereum.org>, and others
status: Active
type: Meta
created: 2015-10-27
updated: 2015-12-07, 2016-02-01, 2018-03-21, 2018-05-29, 2018-10-17, 2019-04-09
---

## What is an PIP?

PIP stands for LUKSO Improvement Proposal. An PIP is a design document providing information to the LUKSO and Ethereum community, or describing a new feature for LUKSO or its processes or environment. The PIP should provide a concise technical specification of the feature and a rationale for the feature. The PIP author is responsible for building consensus within the community and documenting dissenting opinions.

We are also referencing EIPs (Ethereum Improvement Proposals) and ERCs (Ethereum Request for Comment), which can be found here at (https://github.com/ethereum/EIPs/tree/master/EIPS)[https://github.com/ethereum/EIPs/tree/master/EIPS]

## PIP Rationale

We intend LIPs to be the primary mechanisms for proposing new features, for collecting community technical input on an issue, and for documenting the design decisions that have gone into LUKSO. Because the LIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

For LUKSO implementers, LIPs are a convenient way to track the progress of their implementation. Ideally each implementation maintainer would list the LIPs that they have implemented. This will give end users a convenient way to know the current status of a given implementation or library.

## PIP Types

There are three types of PIP:

- A **Standard Track PIP** describes any change that affects most or all LUKSO implementations, such as a change to the the network protocol, a change in block or transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using LUKSO. Furthermore Standard LIPs can be broken down into the following categories. Standards Track LIPs consist of three parts, a design document, implementation, and finally if warranted an update to the [formal specification].
  - **Core** - improvements requiring a consensus fork, as well as changes that are not necessarily consensus critical but may be relevant.
  - **Interface** - includes improvements around client [API/RPC] specifications and standards, and also certain language-level standards like method names ([EIP6]) and [contract ABIs]. The label “interface” aligns with the [interfaces repo] and discussion should primarily occur in that repository before an PIP is submitted to the LIPs repository.
  - **LSP** - LUKSO standard proposal. Application-level standards and conventions, including smart contract standards such as token standards ([ERC20]), name registries ([ERC26], [ERC137]), URI schemes ([ERC67]), library/package formats ([EIP82]), and wallet formats ([EIP75], [EIP85]).
- An **Informational PIP** describes an LUKSO design issue, or provides general guidelines or information to the LUKSO community, but does not propose a new feature. Informational LIPs do not necessarily represent LUKSO community consensus or a recommendation, so users and implementers are free to ignore Informational LIPs or follow their advice.
- A **Meta PIP** describes a process surrounding LUKSO or proposes a change to (or an event in) a process. Process LIPs are like Standards Track LIPs but apply to areas other than the LUKSO protocol itself. They may propose an implementation, but not to LUKSO's codebase; they often require community consensus; unlike Informational LIPs, they are more than recommendations, and users are typically not free to ignore them. Examples include procedures, guidelines, changes to the decision-making process, and changes to the tools or environment used in LUKSO development. Any meta-PIP is also considered a Process PIP.

It is highly recommended that a single PIP contain a single key proposal or new idea. The more focused the PIP, the more successful it tends to be. A change to one client doesn't require an PIP; a change that affects multiple clients, or defines a standard for multiple apps to use, does.

An PIP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement. The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.

## PIP Work Flow

Parties involved in the process are you, the champion or *PIP author*, the [*PIP editors*](#eip-editors).

:warning: Before you begin, vet your idea, this will save you time. Ask the LUKSO and Ethereum community first if an idea is original to avoid wasting time on something that will be be rejected based on prior research (searching the Internet does not always do the trick). It also helps to make sure the idea is applicable to the entire community and not just the author. Just because an idea sounds good to the author does not mean it will work for most people in most areas where LUKSO is used. Examples of appropriate public forums to gauge interest around your PIP include [the LUKSO subreddit], [the Issues section of this repository], and [one of the LUKSO Gitter chat rooms]. In particular, [the Issues section of this repository] is an excellent place to discuss your proposal with the community and start creating more formalized language around your PIP.

Your role as the champion is to write the PIP using the style and format described below, shepherd the discussions in the appropriate forums, and build community consensus around the idea. Following is the process that a successful PIP will move along:

```
[ WIP ] -> [ DRAFT ] -> [ LAST CALL ] -> [ ACCEPTED ] -> [ FINAL ]
```

Each status change is requested by the PIP author and reviewed by the PIP editors. Use a pull request to update the status. Please include a link to where people should continue discussing your PIP. The PIP editors will process these requests as per the conditions below.

* **Active** -- Some Informational and Process LIPs may also have a status of “Active” if they are never meant to be completed. E.g. PIP 1 (this PIP).
* **Work in progress (WIP)** -- Once the champion has asked the LUKSO community whether an idea has any chance of support, they will write a draft PIP as a [pull request]. Consider including an implementation if this will aid people in studying the PIP.
  * :arrow_right: Draft -- If agreeable, PIP editor will assign the PIP a number (generally the issue or PR number related to the PIP) and merge your pull request. The PIP editor will not unreasonably deny an PIP.
  * :x: Draft -- Reasons for denying draft status include being too unfocused, too broad, duplication of effort, being technically unsound, not providing proper motivation or addressing backwards compatibility, or not in keeping with the [LUKSO philosophy](https://github.com/ethereum/wiki/wiki/White-Paper#philosophy).
* **Draft** -- Once the first draft has been merged, you may submit follow-up pull requests with further changes to your draft until such point as you believe the PIP to be mature and ready to proceed to the next status. An PIP in draft status must be implemented to be considered for promotion to the next status (ignore this requirement for core LIPs).
  * :arrow_right: Last Call -- If agreeable, the PIP editor will assign Last Call status and set a review end date (`review-period-end`), normally 14 days later.
  * :x: Last Call -- A request for Last Call status will be denied if material changes are still expected to be made to the draft. We hope that LIPs only enter Last Call once, so as to avoid unnecessary noise on the RSS feed.
* **Last Call** -- This PIP will listed prominently on the https://eips.ethereum.org/ website (subscribe via RSS at [last-call.xml](/last-call.xml)).
  * :x: -- A Last Call which results in material changes or substantial unaddressed technical complaints will cause the PIP to revert to Draft.
  * :arrow_right: Accepted (Core LIPs only) -- A successful Last Call without material changes or unaddressed technical complaints will become Accepted.
  * :arrow_right: Final (Not core LIPs) -- A successful Last Call without material changes or unaddressed technical complaints will become Final.
* **Accepted (Core LIPs only)** -- This PIP is in the hands of the LUKSO client developers.  Their process for deciding whether to encode it into their clients as part of a hard fork is not part of the PIP process.
  * :arrow_right: Final -- Standards Track Core LIPs must be implemented in at least three viable LUKSO clients before it can be considered Final. When the implementation is complete and adopted by the community, the status will be changed to “Final”.
* **Final** -- This PIP represents the current state-of-the-art. A Final PIP should only be updated to correct errata.

Other exceptional statuses include:

* **Deferred** -- This is for core LIPs that have been put off for a future hard fork.
* **Rejected** -- An PIP that is fundamentally broken or a Core PIP that was rejected by the Core Devs and will not be implemented.
* **Active** -- This is similar to Final, but denotes an PIP which may be updated without changing its PIP number.
* **Superseded** -- An PIP which was previously final but is no longer considered state-of-the-art. Another PIP will be in Final status and reference the Superseded PIP.

## What belongs in a successful PIP?

Each PIP should have the following parts:

- Preamble - RFC 822 style headers containing metadata about the PIP, including the PIP number, a short descriptive title (limited to a maximum of 44 characters), and the author details. See [below](https://github.com/ethereum/LIPs/blob/master/LIPS/eip-1.md#eip-header-preamble) for details.
- Simple Summary - “If you can’t explain it simply, you don’t understand it well enough.” Provide a simplified and layman-accessible explanation of the PIP.
- Abstract - a short (~200 word) description of the technical issue being addressed.
- Motivation (*optional) - The motivation is critical for LIPs that want to change the LUKSO protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the PIP solves. PIP submissions without sufficient motivation may be rejected outright.
- Specification - The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current LUKSO platforms (cpp-ethereum, go-ethereum, parity, ethereumJ, ethereumjs-lib, [and others](https://github.com/ethereum/wiki/wiki/Clients).
- Rationale - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.
- Backwards Compatibility - All LIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The PIP must explain how the author proposes to deal with these incompatibilities. PIP submissions without a sufficient backwards compatibility treatise may be rejected outright.
- Test Cases - Test cases for an implementation are mandatory for LIPs that are affecting consensus changes. Other LIPs can choose to include links to test cases if applicable.
- Implementations - The implementations must be completed before any PIP is given status “Final”, but it need not be completed before the PIP is merged as draft. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of “rough consensus and running code” is still useful when it comes to resolving many discussions of API details.
- Copyright Waiver - All LIPs must be in the public domain. See the bottom of this PIP for an example copyright waiver.

## PIP Formats and Templates

LIPs should be written in [markdown] format.
Image files should be included in a subdirectory of the `assets` folder for that PIP as follow: `assets/eip-X` (for eip **X**). When linking to an image in the PIP, use relative links such as `../assets/eip-X/image.png`.

## PIP Header Preamble

Each PIP must begin with an RFC 822 style header preamble, preceded and followed by three hyphens (`---`). The headers must appear in the following order. Headers marked with "*" are optional and are described below. All other headers are required.


` lip:` <PIP number> (this is determined by the PIP editor)

` title:` <PIP title>

` author:` <a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.>

` * discussions-to:` \<a url pointing to the official discussion thread\>

` status:` <Draft | Last Call | Accepted | Final | Active | Deferred | Rejected | Superseded>

`* review-period-end:` <date review period ends>

` type:` <Standards Track (Core, Interface, LSP)  | Informational | Meta>

` * category:` <Core | Interface | LSP>

` created:` <date created on>

` * updated:` <comma separated list of dates>

` * requires:` <PIP number(s)>

` * replaces:` <PIP number(s)>

` * superseded-by:` <PIP number(s)>

` * resolution:` \<a url pointing to the resolution of this PIP\>

Headers that permit lists must separate elements with commas.

Headers requiring dates will always do so in the format of ISO 8601 (yyyy-mm-dd).

#### `author` header

The `author` header optionally lists the names, email addresses or usernames of the authors/owners of the PIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

> Random J. User &lt;address@dom.ain&gt;

or

> Random J. User (@username)

if the email address or GitHub username is included, and

> Random J. User

if the email address is not given.

#### `resolution` header

The `resolution` header is required for Standards Track LIPs only. It contains a URL that should point to an email message or other web resource where the pronouncement about the PIP is made.

#### `discussions-to` header

While an PIP is a draft, a `discussions-to` header will indicate the mailing list or URL where the PIP is being discussed. As mentioned above, examples for places to discuss your PIP include [LUKSO topics on Gitter](https://gitter.im/ethereum/topics), an issue in this repo or in a fork of this repo, [LUKSO Magicians](https://ethereum-magicians.org/) (this is suitable for LIPs that may be contentious or have a strong governance aspect), and [Reddit r/ethereum](https://www.reddit.com/r/ethereum/).

No `discussions-to` header is necessary if the PIP is being discussed privately with the author.

As a single exception, `discussions-to` cannot point to GitHub pull requests.

#### `type` header

The `type` header specifies the type of PIP: Standards Track, Meta, or Informational. If the track is Standards please include the subcategory (core, networking, interface, or ERC).

#### `category` header

The `category` header specifies the PIP's category. This is required for standards-track LIPs only.

#### `created` header

The `created` header records the date that the PIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

#### `updated` header

The `updated` header records the date(s) when the PIP was updated with "substantional" changes. This header is only valid for LIPs of Draft and Active status.

#### `requires` header

LIPs may have a `requires` header, indicating the PIP numbers that this PIP depends on.

#### `superseded-by` and `replaces` headers

LIPs may also have a `superseded-by` header indicating that an PIP has been rendered obsolete by a later document; the value is the number of the PIP that replaces the current document. The newer PIP must have a `replaces` header containing the number of the PIP that it rendered obsolete.

## Auxiliary Files

LIPs may include auxiliary files such as diagrams. Such files must be named PIP-XXXX-Y.ext, where “XXXX” is the PIP number, “Y” is a serial number (starting at 1), and “ext” is replaced by the actual file extension (e.g. “png”).

## Transferring PIP Ownership

It occasionally becomes necessary to transfer ownership of LIPs to a new champion. In general, we'd like to retain the original author as a co-author of the transferred PIP, but that's really up to the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the PIP process, or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email). A bad reason to transfer ownership is because you don't agree with the direction of the PIP. We try to build consensus around an PIP, but if that's not possible, you can always submit a competing PIP.

If you are interested in assuming ownership of an PIP, send a message asking to take over, addressed to both the original author and the PIP editor. If the original author doesn't respond to email in a timely manner, the PIP editor will make a unilateral decision (it's not like such decisions can't be reversed :)).


## PIP Editors

The current PIP editors are

` * Fabian Vogelsteller (@frozeman)`

` * Leonard Schellenberg Detrio (@Leondroids)`

## PIP Editor Responsibilities

For each new PIP that comes in, an editor does the following:

- Read the PIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the PIP for language (spelling, grammar, sentence structure, etc.), markup (Github flavored Markdown), code style

If the PIP isn't ready, the editor will send it back to the author for revision, with specific instructions.

Once the PIP is ready for the repository, the PIP editor will:

- Assign an PIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this PIP)

- Merge the corresponding pull request

- Send a message back to the PIP author with the next step.

Many LIPs are written and maintained by developers with write access to the LUKSO codebase. The PIP editors monitor PIP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don't pass judgment on LIPs. We merely do the administrative & editorial part.

## History

This document was derived heavily from [Ethereum's EIP-1] and [Bitcoin's BIP-0001] written by Amir Taaki which in turn was derived from [Python's PEP-0001]. In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the LUKSO Improvement Process, and should not be bothered with technical questions specific to LUKSO or the PIP. Please direct all comments to the PIP editors.

See [the revision history for further details](https://github.com/ethereum/LIPs/commits/master/LIPS/lip-1.md), which is also available by clicking on the History button in the top right of the PIP.

### Bibliography

[EIP5]: https://github.com/ethereum/EIPs/blob/master/LIPS/eip-5.md
[EIP101]: https://github.com/ethereum/EIPs/issues/28
[EIP90]: https://github.com/ethereum/EIPs/issues/90
[EIP86]: https://github.com/ethereum/EIPs/issues/86#issue-145324865
[EIP8]: https://github.com/ethereum/EIPs/blob/master/LIPS/eip-8.md
[Light Ethereum Subprotocol]: https://github.com/ethereum/wiki/wiki/Light-client-protocol
[whisper]: https://github.com/ethereum/go-ethereum/wiki/Whisper-Overview
[swarm]: https://github.com/ethereum/go-ethereum/pull/2959
[API/RPC]: https://github.com/ethereum/wiki/wiki/JSON-RPC
[EIP6]: https://github.com/ethereum/EIPs/blob/master/LIPS/eip-6.md
[contract ABIs]: https://github.com/ethereum/wiki/wiki/LUKSO-Contract-ABI
[interfaces repo]: https://github.com/ethereum/interfaces
[ERC20]: https://github.com/ethereum/EIPs/issues/20
[ERC26]: https://github.com/ethereum/EIPs/issues/26
[ERC137]: https://github.com/ethereum/EIPs/issues/137
[ERC67]: https://github.com/ethereum/EIPs/issues/67
[EIP82]: https://github.com/ethereum/EIPs/issues/82
[EIP75]: https://github.com/ethereum/EIPs/issues/75
[EIP85]: https://github.com/ethereum/EIPs/issues/85
[the LUKSO subreddit]: https://www.reddit.com/r/lukso/
[one of the LUKSO Gitter chat rooms]: https://gitter.im/lukso/
[pull request]: https://github.com/lukso-network/LIPs/pulls
[formal specification]: https://github.com/ethereum/yellowpaper
[the Issues section of this repository]: https://github.com/lukso-network/LIPs/issues
[markdown]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[Ethereums's EIP-1]: https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1.md
[Bitcoin's BIP-0001]: https://github.com/bitcoin/bips/
[Python's PEP-0001]: https://www.python.org/dev/peps/

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
