# H&amp;T SIG Dynamic Traveler Profile

The H&amp;T SIG (Hospitality &amp; Travel Special Interest Group) is a not-for-profit voluntary
organization that has been working for the past 18 months to promote the development and
implementation of GenAI and DID/SSI (Decentralized Identifiers/Self-Sovereign Identity)
architecture within the travel industry. In collaboration with groups like TrustOverIP and DID,
the H&amp;T SIG has been focusing on creating a dynamic framework or schema for a traveler SSI
profile.
While other organizations like the Open Travel Alliance (OTA) also concentrate on traveler
profile needs, the H&amp;T SIG&#39;s suggested dynamic traveler profile schema is designed to
complement, not replace, these efforts. The H&amp;T SIG schema aims to provide a high-level
traveler profile structure containing a limited set of permanent and semi-static data types
about individuals, generated on-the-fly based on the travel provider&#39;s request and the traveler&#39;s
consent.
The dynamic H&amp;T SIG traveler profile schema seeks to facilitate commonality among schema
elements for three main purposes:
1. Enabling diverse companies serving the travel industry to utilize the schema for their
own profiles.
2. Providing a useful blueprint for major firms and new entrants addressing SSI/DID
personal data protection within the travel industry and potentially other verticals like
retail.
3. Accelerating trilateral content distribution and verification among travelers, suppliers,
and intermediaries for collectivized travel experiences via GenAI and ChatGPT travel
industry implementation.

The suggested structure of the H&amp;T SIG dynamic traveler profile comprises various categories
of traveler information, such as personal identification, contact information, travel documents,
payment information, travel preferences, and more. The profile request structure consists of
components like the traveler&#39;s DID, the issuer of the verifiable credential, the category of the
requested information, and individual claims within each category.

The dynamic traveler profile generation process involves four main steps: Traveler Profile
Request, User Consent, Traveler Profile Presentation, and Verification. This ensures that the
profile is applicable to any category of travel supplier or intermediary, including airlines, hotels,
rental cars, ground transportation providers, activity operators, and more.

By creating a high-level, standardized schema for dynamic traveler profiles, the H&amp;T SIG aims to
streamline the implementation of DID/SSI and GenAI within the travel industry. This will
ultimately enhance the security and privacy of traveler data, improve the interoperability of
systems, and enable more personalized and efficient travel experiences for travelers.

# Published Specifications

Dynamic Traveler Profile Generation Specification - 

# Template Instructions

1. Assign work item leads by their github handles in the [CODEOWNERS](./CODEOWNERS) file.
2. Tag overseeing WG with that WG's tag (i.e. #ccwg)
3. Assign orgs/teams within DIF and define openness to external PRs depending on IPR policy
4. Get to definitioning. A starter document structure can be found in `single-file-test/spec.md`. This guide can be expanded and altered but following the high level structure will make it easier for readers to get up to speed with the profile.
5. Configure GitPages!

## Spec-Up

For spec-up setup, see the [spec-up readme](https://github.com/decentralized-identity/spec-up)
TLDR run 

Update "name" value in `package.json` and `package-lock.json` with the name of the project
`npm install spec-up`

