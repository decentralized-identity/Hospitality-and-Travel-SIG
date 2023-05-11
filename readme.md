# H&amp;T SIG Dynamic Traveler Profile

The DIF H&T SIG (Hospitality & Travel Special Interest Group) is a not-for-profit voluntary organization working to promote the development and implementation of DID/SSI (Decentralized Identifiers/Self-Sovereign Identity) architecture within the travel industry. An important part of the DIF H&T SIG activity is the creation of a dynamic framework or schema for a traveler SSI profile. While the Open Travel Alliance (OTA) and other travel-related organisations also address traveler profile needs, the DIF H&T SIG's suggested dynamic traveler profile schema is designed to complement, not replace, these efforts. The DIF H&T SIG schema provides a high-level traveler profile structure containing a limited set of permanent and semi-static data types for individual travelers generated on-the-fly based on the travel provider's request and the traveler's consent. The dynamic DIF H&T SIG traveler profile schema targets commonality among schema elements for three main purposes:
Enabling diverse companies serving the travel industry to utilize the schema for their own traveler profile development.
To provide a useful blueprint for firms and new entrants addressing SSI/DID personal data protection within the travel industry and from adjacent sectors such as retail.
Accelerating trilateral content distribution and verification among travelers, suppliers, and intermediaries for collectivized travel experiences via, for example, new capabilities brought about by GenAI / ChatGPT.

The suggested structure of the DIF H&T SIG dynamic traveler profile comprises various categories of traveler information: personal identification, contact information, travel documents, payment information, travel preferences, and more. 

The profile request structure consists of:  traveler DID, the issuer of the verifiable credential, the category of the requested information, and individual claims within each category.

The dynamic traveler profile generation process involves four main steps: 
Traveler Profile Request
User Consent
Traveler Profile Presentation
Verification
These steps ensure that the profile is applicable to any category of travel supplier or intermediary, including airlines, hotels, rental cars, ground transportation providers, activity operators, and is extensible to other travel sectors.

By creating a high-level, standardized schema for dynamic traveler profiles, the DIF H&T SIG seeks to support and encourage the adoption of DID/SSI within the travel industry. Broad adoption of a standardized schema will enhance the security and privacy of traveler data, improve the interoperability of systems, and enable more personalized and efficient travel experiences.

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

