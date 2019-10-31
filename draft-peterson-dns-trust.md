---
title: "DNS Trust Considerations"
abbrev: "DNS Trust Considerations"
docname: draft-peterson-dns-trust-latest
date: {DATE}

author:
    -
      ins: T. Peterson
      name: Thomas Peterson

ipr: trust200902
category: info
area: int
workgroup: dprive
keyword: Internet-Draft
stand_alone: yes
pi: [toc, sortrefs, symrefs]

normative:
    RFC2119:
    RFC7218:
    RFC8174:

informative:
    RFC2131:
    RFC7858:
    RFC8106:
    RFC8145:

--- abstract

This document defines considerations for trust anchors where DNS protocols using
encryption are used.

--- middle

# Introduction



# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 {{RFC2119}} {{RFC8174}}
when, and only when, they appear in all capitals, as shown here.

"Classic DNS", "DoH", "DoT", and other related acronyms follow the definitions
as defined in {{?I-D.ietf-dnsop-terminology-ter}}. "Secure DNS Protocols"
refers to any DNS protocol that offers encryption in transport - this includes
but is not limited to DoH, DoT, and DNS over DTLS.

TLSA Selector, Certificate Usage, and Matching Types are defined under
{{RFC7218}}.

# Threat models

Both DoH and DoT consider resolvers provided by the local network operator as a
potential threat for both observing DNS queries, and also modifying the answers,
for example overwriting `NXDOMAIN` responses to return a successful answer
directing the client to an endpoint to serve advertising. These threats may also
use query information for statistics collection, and sell that data onto third
parties, being a privacy concern for users.

# Security Considerations

DoH or DoT services may not be available via known IP address(s) and only via
host names. Thus DNS clients may have to make requests to a Classic DNS server
either provided by the local network advertised through DHCP ({{RFC2131}},
{{RFC8145}}) or IPv6 Router Advertisements ({{RFC8106}}), or through manual
configuration in order to bootstrap future queries with a DoH or DoT service.
These DNS requests subsequently are sent un-encrypted and the validity of the
answer provided may not be accurate.

TODO: Cover impersonation scenarios

TODO: How does host verification play into this?

## Trust anchors

TODO:
* TLS providing anchorage via existing PKI infrastructure
* DNSSEC using IANA-signed root zone, as well as other islands of trust

### DANE

TODO: This should cover in detail relevant parts of RFC 7673, specifically
PKIX-TA and DANE-TA within TLSA certificate usage

# IANA Considerations

There are no IANA considerations for this document.

--- back

# Acknowledgments
{:numbered="false"}

TODO
