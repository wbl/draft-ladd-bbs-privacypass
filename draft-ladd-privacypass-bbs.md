---
title: "BBS for PrivacyPass"
abbrev: "BBS PPAS"
category: info

docname: draft-ladd-privacypass-bbs-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Security"
workgroup: "Privacy Pass"
keyword:
 - anonymous credentials
venue:
  group: "Privacy Pass"
  type: "Working Group"
  mail: "privacy-pass@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/privacy-pass/"
  github: "wbl/draft-ladd-bbs-privacypass"
  latest: "https://wbl.github.io/draft-ladd-bbs-privacypass/draft-ladd-privacypass-bbs.html"

author:
 -
    fullname: Watson Ladd
    organization: Akamai Technologies
    email: "watsonbladd@gmail.com"

normative:

informative:


--- abstract

Existing token types in privacy pass conflate attribution with rate limiting. This document describes a token type where the issuer attests to a set of properties of the client, which the client can then selectively prove to the origin. Repeated showings of the same credential are unlinkable, unlike other token types in privacy pass.

--- middle

# Introduction

In 2004 Boneh-Boyen-Shacham introduced the eponymous BBS signature. The BBS signature scheme as documented in {{draft-irtf-cfrg-bbs-signatures}} lets a signer sign a sequence of strings called attributes, and provides a way for a holder of a signature to prove possession and the value of some of the attributes. This document explains how to use this technology with privacy pass.

# Conventions and Definitions

{::boilerplate bcp14-tagged}
# Protcol Overview
To run this protocol the Issuer must have a public key and an issuance URL, as well as a common understanding of the meaning of each attribute string (sequence of octets). E.g an age might be encoded as a single octet, or in ASCII numeric base 10 represnetation, or a fixed field, and could be the first attribute in the list.

## Issuance
The Client begins by forming a sequence of strings corresponding to the attributes they wish signed. They engage in the Attestation protocol with the Attestor, and then send the serialized array of strings as JSON array of base64 encoded strings to the Issuer. The Issuer returns the signature, again encoded in base64. The Client MUST verify the returned signature.

The Attestor interaction and validation of the attributes is not specified here. In a split instantiation as per {{draft-ietf-privacypass-architecture}}, Attestors and Issuers MUST ensure that the claims by the Client are not changeable between attestation and signing.

## Redemption
For a client to show a set of attributes they execute the ProofGen operation of {{draft-irtf-cfrg-bbs-signatures}} with the header set to a specified channel binding or origin identifer. For HTTP applications it is RECOMMENDED that the origin be used. The set of attributes they wish to show is communicated by means outside this draft. They then transmit the signature to the origin as a token.

# Privacy Pass integration
In {{draft-ietf-privacypass-architecture}} parameters are provided that any instantiation must amend. 

# Security Considerations

The position of a revealed attribute, as well as the number of unrevealed attributes, is revealed to the origin. Applications MUST ensure all clients recieve the same set of attributes in the same positions. As the redeemed tokens are not single use, instantiations MUST specify a channel binding to use or origin identifier.

# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
