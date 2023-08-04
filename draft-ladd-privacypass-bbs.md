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

In 2004 Boneh-Boyen-Shacham introduced the eponymous BBS signature. The BBS signature scheme as documented in {{draft-irtf-cfrg-bbs-signatures}} lets a signer sign a sequence of strings called attributes, and provides a way for a holder of a signature to prove possession and the value of some of the attributes.

# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
