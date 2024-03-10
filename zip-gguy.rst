::

  ZIP: 
  Title: Ensuring Flexibility and Sustainability of the Zcash Development Fund
  Owners: Matthew Green (@gguy)
  Original-Authors: Matthew Green (@gguy)
  Status: Draft
  Category: Consensus Process
  Created: 2024-03-04
  License: MIT
  Discussions-To: ...
  Pull-Request: ...


Terminology
===========

The key words "MUST", "MUST NOT", "SHALL", "SHALL NOT", "SHOULD", and "MAY" in
this document are to be interpreted as described in RFC 2119. [#RFC2119]_

The term "network upgrade" in this document is to be interpreted as described in
ZIP 200 [#zip-0200]_ and the Zcash Trademark Donation and License Agreement
([#trademark]_ or successor agreement).

The terms "block subsidy" and "halving" in this document are to be interpreted
as described in sections 3.10 and 7.8 of the Zcash Protocol Specification.
[#protocol]_

"Electric Coin Company", also called "ECC", refers to the Zerocoin Electric Coin
Company, LLC.

"Bootstrap Project", also called "BP", refers to the 501(c)(3) nonprofit
corporation of that name.

"Zcash Foundation", also called "ZF", refers to the 501(c)(3) nonprofit
corporation of that name.

"Section 501(c)(3)" refers to that section of the U.S. Internal Revenue Code
(Title 26 of the U.S. Code). [#section501c3]_

"Community Advisory Panel" refers to the panel of community members assembled by
the Zcash Foundation and described at [#zf-community]_.

The terms "Testnet" and "Mainnet" are to be interpreted as described in section
3.12 of the Zcash Protocol Specification [#protocol-networks]_.


Abstract
========

This proposal describes a structure for the Zcash {focus}, to be enacted in
Network Upgrade 6 with a declining schedule for the Development Fund allocation,
ensuring sustainability. This Dev Fund would total {percent} of the block
subsidies with gradually reduce by ~2% every 35064blocks (~1month) and split
into 4 slices:

* {percent} Unissued Reserve/Zcash Sustainability Fund (denoted **UR slice**);
* {percent} for the Bootstrap Project (denoted **BP slice**);
* {percent} for the Zcash Foundation, for general use (denoted **ZF slice**);
* {percent} for additional "Zcash Community Grants" for large-scale long-term
  projects (denoted **ZCG slice**).

Governance and accountability are based on existing entities and legal
mechanisms, and increasingly decentralized governance is encouraged.

Motivation
==========

Starting at Zcash's second halving in November 2024, by default 100% of the
block subsidies will be allocated to miners, and no further funds will be
automatically allocated to any other entities. Consequently, no substantial new
funding may be available to existing teams dedicated to furthering charitable,
educational, or scientific purposes, such as research, development, and
outreach: the Electric Coin Company (ECC), the Zcash Foundation (ZF), and the
many entities funded by the ZF grant program.

There is a need to strike a balance between incentivizing the security of the
consensus protocol (i.e., mining) versus crucial charitable, educational, and/or
scientific aspects, such as research, development, outreach, and the future
funding needs of the network.

Furthermore, there is a need to balance the sustenance of ongoing work by the
current teams dedicated to Zcash, with encouraging decentralization and growth
of independent development teams.

For these reasons, the Zcash Community desires to allocate and contribute a
slice of the block subsidies otherwise allocated to miners as a donation to
support charitable, educational, and scientific activities within the meaning of
Section 501(c)(3).

Requirements
============

The Dev Fund should encourage decentralization of the work and funding, by
supporting new teams dedicated to Zcash. The Zcash Community should implement a
continuous governance and fund adjustment mechanism, introducing a flexible
governance structure for adapting the Development Fund allocation based on the
ecosystem's evolving needs. There should not be any single entity which is a
single point of failure, i.e., whose capture or failure will effectively prevent
effective use of the funds.

The Dev Fund should maintain the existing teams and capabilities in the Zcash
ecosystem, unless and until concrete opportunities arise to create even greater
value for the Zcash ecosystem.

There should not be any single entity which is a single point of failure, i.e.,
whose capture or failure will effectively prevent effective use of the funds.

Major funding decisions should be based, to the extent feasible, on inputs from
domain experts and pertinent stakeholders.

The Dev Fund mechanism should not modify the monetary emission curve (and in
particular, should not irrevocably burn coins).

In case the value of ZEC jumps, the Dev Fund recipients should not wastefully
use excessive amounts of funds. Conversely, given market volatility and eventual
halvings, it is desirable to create rainy-day reserves.

The Dev Fund mechanism should not reduce users' financial privacy or security.
In particular, it should not cause them to expose their coin holdings, nor cause
them to maintain access to secret keys for much longer than they would
otherwise. (This rules out some forms of voting, and of disbursing coins to
past/future miners.)

The new Dev Fund system should be simple to understand and realistic to
implement. In particular, it should not assume the creation of new mechanisms
(e.g., election systems) or entities (for governance or development) for its
execution; but it should strive to support and use these once they are built.

Comply with legal, regulatory, and taxation constraints in pertinent
jurisdictions.

Non-requirements
================

General on-chain governance is outside the scope of this proposal.

Rigorous voting mechanisms (whether coin-weighted, holding-time-weighted or
one-person-one-vote) are outside the scope of this proposal, though there is
prescribed room for integrating them once available.


New Governance Body
-------------------

Following the second halving, the Zcash-Ecosystem is committed to establishing a
new community-elected governance body. This entity will be tasked with
overseeing adjustments to the fund and making pivotal governance decisions. To
foster heightened accountability and transparency, the governance body will
oversee both the deployment of the Development Fund and any future policy
adjustments. Furthermore, to ensure responsible use of funds, the Development
Fund will follow a declining schedule for allocations, naturally reducing
funding over time and encouraging efficient and judicious use by recipients. For
any additional funding requests beyond this schedule, recipients must propose a
Dev Fund amendment to the new governing body. Significantly, this governing body
will employ a polling mechanism to capture community consensus, ensuring that
major amendments to the fund or policies are ratified in alignment with the
ecosystem's evolving needs and priorities. This approach ensures a dynamic and
responsive funding model that is deeply rooted in community input and consensus.


Specification
=============

Consensus changes implied by this specification are applicable to the Zcash
Mainnet. Similar (but not necessarily identical) consensus changes SHOULD be
applied to the Zcash Testnet for testing purposes.


Dev Fund allocation
-------------------

To ensure the sustainable financing of Zcash {focus}, {percent} of the block
reward will be allocated to the Development Fund. This allocation, aimed at
funding the Bootstrap Project, Zcash Foundation, and Zcash Community Grants, is
designed to decrease by approximately 2% every 35064 blocks (~1 month). This
reduction is calculated by multiplying the denominator, starting at 1000, by
1.03^(blocks_since_halving % 35064) and rounding down the result. The Unissued
Reserve's calculation is an estimate and should be calculated as the leftover
unallocated rewards. Beginning with the second Zcash halving in 2024, the
development fund's allocation for the ensuing 35064 blocks will be as follows:

* {UR slice}/1000 ({percent}) Unissued Reserve/Zcash Sustainability Fund
  (denoted **UR slice**);
* {BP slice}/1000 ({percent}) for the Bootstrap Project (denoted **BP slice**);
* {ZF slice}/1000 ({percent}) for the Zcash Foundation, for general use
  (denoted **ZF slice**);
* {ZCG slice}/1000 ({percent}) for additional "Major Grants" for large-scale
  long-term projects (denoted **ZCG slice**).

After 35064blocks the Dev Fund SHALL continue for another 35064blocks and be
allocated as follows:

* {UR slice}/1020 (~{percent}) Unissued Reserve/Zcash Sustainability Fund
  (denoted **UR slice**);
* {BP slice}/1020 (~{percent}) for the Bootstrap Project (denoted **BP slice**);
* {ZF slice}/1020 (~{percent}) for the Zcash Foundation, for general use
  (denoted **ZF slice**);
* {ZCG slice}/1020 (~{percent}) for additional "Major Grants" for large-scale
  long-term projects (denoted **ZCG slice**).

This calculation will continue until the dev fund allocation effectively reaches
0. Implementations of this development fund SHALL use the numerators and
denominators above to calculate the slice.

The slices are described in more detail below. The fund flow will be implemented
at the consensus-rule layer, by sending the corresponding ZEC to the designated
address(es) for each block. This Dev Fund will extend indefinitly (unless
extended/modified by a future ZIP).


UR/ZSF slice (Unissued Reserve)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Unissued Reserve (UR) slice represents a portion of the Development Fund
that is not immediately allocated to any specific entity or project. Instead, it
serves as a strategic reserve to provide flexibility and ensure the long-term
sustainability of the Zcash ecosystem. The UR slice can be deployed in the
future for unforeseen circumstances, additional funding opportunities, or to
support the ecosystem in the event of economic downturns or declines in the
market price of ZEC.

The management and use of the UR slice will be determined through community
governance processes and the oversight of a designated committee or equivalent
body. This committee will be responsible for proposing and gathering community
concensus regarding the allocation of the UR slice based on the strategic needs
of the Zcash ecosystem. The committee's decisions must align with the overall
mission of supporting financial privacy and the Zcash platform, and they must
comply with the legal and regulatory requirements applicable to the Zcash
Development Fund.

The UR slice will be reserved in a transparent and accountable manner, with
regular reporting on its status and any allocations made from it. The goal is to
ensure that the UR slice is a reliable and effective tool for the long-term
resilience and prosperity of the Zcash ecosystem.


BP slice (Bootstrap Project)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This slice of the Dev Fund will flow as charitable contributions from the Zcash
Community to the Bootstrap Project, the newly formed parent organization to the
Electric Coin Company. The Bootstrap Project is organized for exempt
educational, charitable, and scientific purposes in compliance with
Section 501(c)(3), including but not limited to furthering education,
information, resources, advocacy, support, community, and research relating to
cryptocurrency and privacy, including Zcash. This slice will be used at the
discretion of the Bootstrap Project for any purpose within its mandate to
support financial privacy and the Zcash platform as permitted under
Section 501(c)(3). The BP slice will be treated as a charitable contribution
from the Community to support these educational, charitable, and scientific
purposes.


ZF slice (Zcash Foundation's general use)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This slice of the Dev Fund will flow as charitable contributions from the Zcash
Community to ZF, to be used at its discretion for any purpose within its mandate
to support financial privacy and the Zcash platform, including: development,
education, supporting community communication online and via events, gathering
community sentiment, and awarding external grants for all of the above, subject
to the requirements of Section 501(c)(3). The ZF slice will be treated as a
charitable contribution from the Community to support these educational,
charitable, and scientific purposes.


Zcash Community Grants (ZCG)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This slice of the Dev Fund is intended to fund independent teams entering the
Zcash ecosystem, to perform major ongoing development (or other work) that
benefits the public good within the Zcash ecosystem, to the extent that such
teams are available and effective. The Zcash Community Grants (ZCG) Committee is
given the discretion to allocate funds not only to major grants, but also to a
diverse range of projects that advance the usability, security, privacy, and
adoption of Zcash, including community programs, dedicated resources, and other
projects of varying sizes.

The funds SHALL be received and administered by ZF. ZF MUST disburse them for
"Major Grants" and expenses reasonably related to the administration of Major
Grants, but subject to the following additional constraints:

1. These funds MUST primarily be used to issue Major Grants to external parties
that are independent of ZF. They can also be used to fund other initiatives such
as community support personnel and public goods projects that benefit Zcash, and
to pay for expenses reasonably related to the administration of Major Grants.
They MUST NOT be used by ZF for its internal operations and direct expenses not
related to administration of Major Grants. Additionally, BP, ECC, and ZF are
ineligible to receive Major Grants.

2. Major Grants SHOULD support well-specified work proposed by the grantee, at
reasonable market-rate costs. They can be of any duration or ongoing without a
duration limit. Grants of indefinite duration SHOULD have semiannual review
points for continuation of funding.

3. Priority SHOULD be given to Major Grants that bolster teams with substantial
(current or prospective) continual existence, and set them up for long-term
success, subject to the usual grant award considerations (impact, ability,
risks, team, cost-effectiveness, etc.). Priority SHOULD be given to Major Grants
that support ecosystem growth, for example through mentorship, coaching,
technical resources, creating entrepreneurial opportunities, etc. If one
proposal substantially duplicates another's plans, priority SHOULD be given to
the originator of the plans.

4. Major Grants SHOULD be restricted to furthering the Zcash cryptocurrency and
its ecosystem (which is more specific than furthering financial privacy in
general) as permitted under Section 501(c)(3).

5. Major Grants awards are subject to approval by a five-seat Major Grant Review
Committee. The Major Grant Review Committee SHALL be selected by the ZF's
Community Advisory Panel or successor process. Elections SHALL be staggered to
ensure continuity within the Committee.

6. The Major Grant Review Committee's funding decisions will be final, requiring
no approval from the ZF Board, but are subject to veto if the Foundation judges
them to violate U.S. law or the ZF's reporting requirements and other (current
or future) obligations under U.S. IRS 501(c)(3).

7. Major Grant Review Committee members SHALL have a one-year term and MAY sit
for reelection. The Major Grant Review Committee is subject to the same conflict
of interest policy that governs the ZF Board of Directors (i.e. they MUST recuse
themselves when voting on proposals where they have a financial interest). At
most one person with association with the BP/ECC, and at most one person with
association with the ZF, are allowed to sit on the Major Grant Review Committee.
"Association" here means: having a financial interest, full-time employment,
being an officer, being a director, or having an immediate family relationship
with any of the above. The ZF SHALL continue to operate the Community Advisory
Panel and SHOULD work toward making it more representative and independent (more
on that below).
   
   Major Grant Review Committee members are expected to work approximately 35
   hours per month and will be compensated accordingly from the Major Grants
   budget. The total compensation for the committee, paid from the Major Grants
   budget, should be equivalent to a full-time position.
   
8. From 1st January 2022, a portion of the ZCG Slice shall be allocated to a
Discretionary Budget, which may be disbursed for expenses reasonably related to
the administration of Major Grants. The amount of funds allocated to the
Discretionary Budget SHALL be decided by the ZF's Community Advisory Panel or
successor process. Any disbursement of funds from the Discretionary Budget MUST
be approved by the Major Grant Review Committee. Expenses related to the
administration of Major Grants include, without limitation the following:
   
   * Paying third party vendors for services related to domain name
     registration, or the design, website hosting and administration of websites
     for the Major Grant Review Committee.
   * Paying independent consultants to develop requests for proposals that align
     with the Major Grants program.
   * Paying independent consultants for expert review of grant applications.
   * Paying for sales and marketing services to promote the Major Grants
     program.
   * Paying third party consultants to undertake activities that support the
     purpose of the Major Grants program. 
   * Reimbursement to members of the Major Grant Review Committee for reasonable
     travel expenses, including transportation, hotel and meals allowance.

9. A portion of the Discretionary Budget MAY be allocated to provide reasonable
compensation to members of the ZCG Committee. Committee member compensation
SHALL be limited to the hours needed to successfully perform their positions and
MUST align with the scope and responsibilities of their roles. The allocation
and distribution of compensation to committee members SHALL be administered by
the ZF. The compensation rate and hours for committee members SHALL be
determined by the ZF’s Community Advisory Panel or successor process.

10. The Major Grant Review Committee's decisions relating to the allocation and
disbursement of funds from the Discretionary Budget will be final, requiring no
approval from the ZF Board, but are subject to veto if the Foundation judges
them to violate U.S. law or the ZF's reporting requirements and other (current
or future) obligations under U.S. IRS 501(c)(3).

ZF SHALL recognize the ZCG slice of the Dev Fund as a Restricted Fund donation
under the above constraints (suitably formalized), and keep separate accounting
of its balance and usage under its `Transparency and Accountability`_
obligations defined below.

ZF SHALL strive to define target metrics and key performance indicators, and the
Major Grant Review Committee SHOULD utilize these in its funding decisions.


Direct-grant option
~~~~~~~~~~~~~~~~~~~

It may be deemed better, operationally or legally, if the Major Grant funds are
not accepted and disbursed by ZF, but rather directly assigned to the grantees.
Thus, the following mechanism MAY be used in perpetuity for some or all
grantees, if agreed upon by both ECC and ZF before Network Upgrade 4 (Canopy)
activation:

Prior to each network upgrade, based on the ZCG Committee’s recommendation, the
Foundation SHALL publish a list of grantees' addresses and the total number of
Dev Fund ZEC per block they should receive. ECC and ZF SHALL implement this list
in any implementations of the Zcash consensus rules they maintain. This decision
will then be, effectively, ratified by the miners as the network upgrade
activates.


Furthering Zcash Decentralization
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

BP/ECC and ZF SHALL conduct periodic (e.g. semiannual or annual) reviews of the
organizational structure, performance, and effectiveness of the ZCG program and
committee, taking into consideration the input and recommendations of the ZCG
Committee. As part of these periodic reviews, ECC and ZF MUST commit to
exploring the possibility of transitioning ZCG into an independent organization
if it is economically viable and it aligns with the interests of the Zcash
ecosystem and prevailing community sentiment.

In any transition toward independence, priority SHALL be given to maintaining or
enhancing the decentralization of the Zcash ecosystem. The newly formed
independent organization MUST ensure that decision-making processes remain
community-driven, transparent, and responsive to the evolving needs of the Zcash
community and ecosystem. In order to promote geographic decentralization, the
new organization SHOULD establish its domicile outside of the United States.


Transparency and Accountability
-------------------------------

Obligations
~~~~~~~~~~~

BP, ECC, ZF, and Major Grant recipients (during and leading to their award
period) SHALL all accept the obligations in this section.

Ongoing public reporting requirements:

* Quarterly reports, detailing future plans, execution on previous plans, and
  finances (balances, and spending broken down by major categories).
* Monthly developer calls, or a brief report, on recent and forthcoming tasks.
  (Developer calls may be shared.)
* Annual detailed review of the organization performance and future plans.
* Annual financial report (IRS Form 990, or substantially similar information).

These reports may be either organization-wide, or restricted to the income,
expenses, and work associated with the receipt of Dev Fund. As BP is the parent
organization of ECC it is expected they may publish joint reports.

It is expected that ECC, ZF, and Major Grant recipients will be focused
primarily (in their attention and resources) on Zcash. Thus, they MUST promptly
disclose:

* Any major activity they perform (even if not supported by the Dev Fund) that
  is not in the interest of the general Zcash ecosystem.
* Any conflict of interest with the general success of the Zcash ecosystem.

BP, ECC, ZF, and grant recipients MUST promptly disclose any security or privacy
risks that may affect users of Zcash (by responsible disclosure under confidence
to the pertinent developers, where applicable).

BP's reports, ECC's reports, and ZF's annual report on its non-grant operations,
SHOULD be at least as detailed as grant proposals/reports submitted by other
funded parties, and satisfy similar levels of public scrutiny.

All substantial software whose development was funded by the Dev Fund SHOULD be
released under an Open Source license (as defined by the Open Source Initiative
[#osd]_), preferably the MIT license.


Enforcement
~~~~~~~~~~~

For grant recipients, these conditions SHOULD be included in their contract with
ZF, such that substantial violation, not promptly remedied, will cause
forfeiture of their grant funds and their return to ZF.

BP, ECC, and ZF MUST contractually commit to each other to fulfill these
conditions, and the prescribed use of funds, such that substantial violation,
not promptly remedied, will permit the other party to issue a modified version
of Zcash node software that removes the violating party's Dev Fund slice, and
use the Zcash trademark for this modified version. The slice's funds will be
reassigned to ZCG (whose integrity is legally protected by the Restricted Fund
treatment).


ZF Board Composition
--------------------

Members of ZF's Board of Directors MUST NOT hold equity in ECC or have current
business or employment relationships with ECC, except as provided for by the
grace period described below.

Grace period: members of the ZF board who hold ECC equity (but do not have other
current relationships to ECC) may dispose of their equity, or quit the Board, by
1 November 2021. (The grace period is to allow for orderly replacement, and also
to allow time for ECC corporate reorganization related to Dev Fund receipt,
which may affect how disposition of equity would be executed.)

The Zcash Foundation SHOULD endeavor to use the Community Advisory Panel (or
successor mechanism) as advisory input for future board elections.


Acknowledgements
================

This proposal is a modification of Zooko Wilcox and Andrew Miller's ZIP 1014
[#zip-1012]_ with feedback from the community.

The authors are grateful to all of the above for their excellent ideas and any
insightful discussions.

.. _Zcash Community Forum: https://forum.zcashcommunity.com/


References
==========

.. [#RFC2119] `RFC 2119: Key words for use in RFCs to Indicate Requirement Levels <https://www.rfc-editor.org/rfc/rfc2119.html>`_
.. [#protocol] `Zcash Protocol Specification, Version 2021.2.16 or later <protocol/protocol.pdf>`_
.. [#protocol-networks] `Zcash Protocol Specification, Version 2021.2.16. Section 3.12: Mainnet and Testnet <protocol/protocol.pdf#networks>`_
.. [#trademark] `Zcash Trademark Donation and License Agreement <https://electriccoin.co/wp-content/uploads/2019/11/Final-Consolidated-Version-ECC-Zcash-Trademark-Transfer-Documents-1.pdf>`_
.. [#osd] `The Open Source Definition <https://opensource.org/osd>`_
.. [#zip-0200] `ZIP 200: Network Upgrade Mechanism <zip-0200.rst>`_
.. [#zip-1014] `ZIP 1014: Establishing a Dev Fund for ECC, ZF, and Major Grants <zip-1014.rst>`_
.. [#zf-community] `ZF Community Advisory Panel <https://www.zfnd.org/governance/community-advisory-panel/>`_
.. [#section501c3] `U.S. Code, Title 26, Section 501(c)(3) <https://www.law.cornell.edu/uscode/text/26/501>`_
