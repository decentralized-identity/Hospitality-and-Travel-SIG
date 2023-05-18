**Dynamic Traveler Profile Generation Specification**

**Specification Status:** Published

**Latest Draft:** [identity.foundation/traveler-profile/spec](https://github.com/decentralized-identity/SIG-Hospitality-and-Tourism)

**Latest Version:** 0.1

**Previous Version:** 0.0

**Authors:**

*   Kabir Maiga
*   William Seggos

**Contributors:**

*   Gene Quinn
*   Douglas Rice
*   Bill Carroll
*   Nick Price
*   Alex Bainbridge

**Feedback**:

[GitHub H&T-SIG/traveler-profile](https://github.com/decentralized-identity/SIG-Hospitality-and-Tourism) ([pull requests](https://github.com/decentralized-identity/SIG-Hospitality-and-Tourism), [new issue](https://github.com/decentralized-identity/SIG-Hospitality-and-Tourism), [open issues](https://github.com/decentralized-identity/SIG-Hospitality-and-Tourism))

1.  **Introduction**

1.1. **Purpose**

The purpose of this specification is to define a dynamic traveler profile generation system that allows travel providers to request traveler information, which is then generated on-the-fly by the traveler's digital wallet or digital agent. This approach enables standardized traveler profile requests and presentation models, ensuring consistency and interoperability across the travel industry for all aspects of consumer information, including searching, shopping, reserving, purchasing, executing, and reviewing travel experiences, as well as managing travel interruptions. Designed to cater to both individual and group travel for leisure and business purposes, this system promotes a seamless and efficient experience for travelers and travel providers alike.

1.2. **Scope**

This specification covers the process of generating traveler profiles, including profile presentation requests, user consent, profile presentation, and verification. It also describes the structure of profile requests and the standardized composition of generated profiles.

  

2. **Overall Description**

2.1. **Dynamic Traveler Profile Generation Process**

The process consists of four main steps: Traveler Profile Request, User Consent, Traveler Profile Presentation, and Verification. In the first step, the travel provider requests the traveler's profile by specifying the required information. Next, the traveler, as the holder of the information, provides consent and sets any terms of use for their profile data. The traveler's digital wallet or digital agent then generates the profile, which is presented to the travel provider in the third step. Finally, the travel provider verifies the authenticity of the presented data by resolving issuer DIDs and checking signatures.

![](https://passivebolt.atlassian.net/wiki/download/attachments/1509359617/Screen%20Shot%202023-04-13%20at%203.14.06%20PM.png?version=1&modificationDate=1682110334857&cacheVersion=1&api=v2)2.2. **Traveler** **Profile Request**

The Traveler Profile Request is the initial step in the dynamic traveler profile generation system. It is designed to ensure that travel providers can request the necessary traveler information while maintaining high level of consumer confidentiality. By utilizing Decentralized Identifiers (DIDs), the system enables travelers to remain anonymous during the request process, effectively addressing any concerns about privacy and personal data protection.

The Traveler Profile Request structure consists of several components, including the traveler's DID, the issuer of the verifiable credential, the category of the requested information, and individual claims within each category. Each claim is further broken down into its value, format, standard, and language. The structure also indicates whether a specific claim is required and the purpose for requesting that claim. By following this standardized structure, travel providers can ensure consistency and interoperability across the industry when requesting traveler profile information.

![](https://passivebolt.atlassian.net/wiki/download/attachments/1509359617/Screen%20Shot%202023-04-13%20at%203.37.53%20PM.png?version=1&modificationDate=1682110334709&cacheVersion=1&api=v2)

The profile request structure is an essential aspect of the dynamic traveler profile generation process. It is crucial for travel providers to have a clear understanding of the function and purpose of each component within the structure. By doing so, they can effectively craft profile requests tailored to their specific needs while maintaining the standardization required for seamless interoperability across the travel industry. This part of the specification serves as a guide, ensuring that all parties involved have a clear understanding of the various components and their interrelationships within the request structure.

*   DID: Decentralized Identifier for the traveler
*   Issuer: Indicates the trusted entity issuing the verifiable credential
*   Category: Groups related profile elements together (e.g., demographic info, payment info)
*   Claims: Specific information requested within each category (e.g., name, phone number)
*   Value: The actual data for the claim
*   Format: The format in which the data is presented (e.g., text, date)
*   Standard: Any applicable standards or guidelines for the data
*   Language: The language used for presenting the data
*   Required: Indicates whether the claim is required or optional
*   Purpose: The purpose for requesting the specific claim

Example Profile Request in JSON-LD

```json

scssCopy code{
  "@context": "https://www.w3.org/ns/did/v1",
  "id": "did:example:123456789",
  "issuer": \[
    {
      "type": "VerifiableCredential",
      "category": "demographicInfo",
      "claims": \[
        {
          "name": {
            "value": "John Doe",
            "format": "text",
            "standard": "ISO 10646",
            "language": "en"
          },
          "required": true,
          "purpose": "Identification"
        },
        {
          "birthdate": {
            "value": "1990-01-01",
            "format": "date",
            "standard": "ISO 8601",
            "language": "en"
          },
          "required": false,
          "purpose": "Age Verification"
        }
      \]
    }
  \]
}
```

2.3. **Traveler** **Profile Presentation**

After the traveler's digital wallet or digital agent generates the profile based on the travel provider's request and the traveler's consent, the profile presentation is created. This presentation includes the requested information, organized by categories and claims.

Example Profile Presentation in JSON-LD:
```json
scssCopy code{
  "@context": "https://www.w3.org/ns/did/v1",
  "id": "did:example:123456789",
  "type": "VerifiablePresentation",
  "verifiableCredential": \[
    {
      "@context": "https://www.w3.org/ns/vc/v1",
      "id": "https://example.com/credentials/123",
      "type": \["VerifiableCredential"\],
      "issuer": "did:example:issuer123",
      "issuanceDate": "2023-04-13T00:00:00Z",
      "credentialSubject": {
        "id": "did:example:123456789",
        "demographicInfo": {
          "name": "John Doe",
          "birthdate": "1990-01-01"
        }
      }
    }
  \],
  "proof": {
    "type": "Ed25519Signature2018",
    "created": "2023-04-13T00:00:00Z",
    "proofPurpose": "assertionMethod",
    "verificationMethod": "did:example:123456789#key1",
    "jws": "eyJhbGciOiJFZERTQSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..l9d0YHjcFAH2H4dB9xlWFZQLUpixVCWzn8lXY7ZNFYUxujfQkzLwGhMfKYM0pGtE8bGvk5XOMJX14qkTzTWRlCw"
  }
}
```
In the example above, the profile presentation includes the verifiable credential containing the requested demographic information (name and birthdate) and a proof, which verifies the authenticity of the presented data.

2.6. **Profile Element Categories**

Profile element categories group related profile elements together, allowing for a structured and organized presentation of information. The following list provides an exhaustive collection of profile element categories that can be used within the dynamic traveler profile generation process:

*   **Personal Identification**: Includes elements such as name, date of birth, gender, and nationality.
*   **Contact Information**: Contains elements like email address, phone number, and physical address.
*   **Travel Documents**: Covers elements such as passport, visa, and other travel-related documentation.
*   **Payment Information**: Encompasses elements like credit card details, billing address, and payment preferences.
*   **Frequent Traveler Programs:** Incorporates elements related to loyalty and rewards program memberships.
*   **Travel Preferences**: Covers elements such as seating preferences, meal preferences, and special needs or accommodations.
*   **Health Information**: Contains elements like vaccination records, medical conditions, and medication requirements.
*   **Emergency Contacts**: Includes elements related to the traveler's designated emergency contact(s), such as name, relationship, and contact information.
*   **Travel History**: Covers elements related to previous travel experiences, including destinations visited and trip details.
*   **Accommodation Preferences and Requirements**: Encompasses elements like room type, bed preferences, and hotel facilities or amenities desired.
*   **Transportation Preferences and Requirements**: Contains elements such as preferred airline, car rental preferences, and ground transportation options.
*   **Activity Interests and Requirements**: Covers elements related to the traveler's interests in specific activities, attractions, or experiences during their trip.
*   **Travel Insurance**: Includes elements related to travel insurance policies, coverage details, and provider information.
*   **Communication Preferences**: Encompasses elements such as preferred language, communication channels, and marketing preferences.

These categories can be utilized and customized by travel providers to create tailored profile requests that address their specific needs and requirements.

3. **System Features**

3.1. **Generated Profile Structure**

The generated traveler profile will have a standardized structure composed of three block types:

*   **Identifiers (DIDs)**: Unique decentralized identifiers for the traveler.
*   **Verifiable Credentials (third-party issued)**: Claims issued and verified by a trusted third party.
*   **Self-Issued Verifiable Credentials (preferences and requirements)**: Claims issued by the traveler themselves, typically containing personal preferences.

![](https://passivebolt.atlassian.net/wiki/download/attachments/1509359617/Screen%20Shot%202023-04-13%20at%203.58.59%20PM.png?version=1&modificationDate=1682110334468&cacheVersion=1&api=v2)Each verifiable credential block type will contain profile elements (e.g., name, phone number, passport) grouped by profile element categories (e.g., Personal Identification, Payment Information). Standardized tagging methods will be used to provide travel context for each profile element category.

3.2. **Travel Context Tags**

Travel Context Tags are an essential component of the dynamic traveler profile generation system, serving as the key to delivering context-specific traveler information to travel providers and intermediaries. These tags facilitate a seamless user experience by enabling the traveler's digital agent or wallet to compile and present relevant data based on the unique context of each travel service request.

As the travel industry encompasses a wide range of service providers and intermediaries, including resorts, cruises, online travel companies, and travel management companies, it is crucial to tailor the presentation of traveler information to suit each distinct context. By leveraging Travel Context Tags associated with various types of travel services, the traveler's digital agent or wallet can efficiently filter and present only the most pertinent data for each specific provider or intermediary request.

This strategic use of tags as shorthands not only enhances the overall travel experience but also streamlines the traveler's interaction with different travel services. With the help of Travel Context Tags, both travelers and travel providers can effortlessly navigate the dynamic traveler profile system, ensuring that the provided data is always aligned with the context of each unique travel situation.

*   **Accommodations**: Relevant for hotels, hostels, and other lodging providers.
*   Examples: room type preference, smoking preference, loyalty program membership
*   **Transportation**: Relevant for airlines, trains, buses, taxis, and other mobility sectors.
*   Examples: seat preference, frequent flyer program membership, luggage requirements
*   **Dining**: Relevant for restaurants, food service providers in hotels, trains, and airplanes.
*   Examples: dietary restrictions, allergies, meal preferences, favorite cuisines, medical / religious reasons
*   **Activities**: Relevant for tour operators, event providers, and other activity organizers.
*   Examples: interests, preferred activity types, accessibility requirements
*   **Communication**: Relevant for contact information and communication preferences.
*   Examples: email address, phone number, preferred contact method, language preference
*   **Payment**: Relevant for payment information and financial transactions.
*   Examples: credit card details, billing address, preferred currency, loyalty rewards

4. **Future Scope**

This section outlines potential areas for future development and enhancement of the dynamic traveler profile generation system:

4.1. **Enhanced User Consent Management**

Improvements in user consent management, allowing travelers to define more granular consent levels and terms of use for their profile information.

4.2. **Interoperability with Non-Travel Industries**

Expanding the system to support interoperability with non-travel industries, allowing users to leverage their profiles across various sectors.

5. **Applicability and Customization**

5.1. **Travel Provider Implementation**

Travel providers should implement the dynamic traveler profile generation system according to their specific needs and requirements. They should use the standardized profile request structure and generated profile composition to ensure consistency and interoperability.

5.2. **Customization**

The system is designed to be adaptable and customizable to accommodate the specific needs of different travel industry players. Customization should be done in a way that maintains consistency and interoperability across the industry.

6. **Conformance**

6.1. **Compliance Criteria**

Travel providers and digital wallet or digital agent developers must adhere to the specification to ensure the proper functioning and interoperability of the system. Compliance criteria include:

*   Implementing the profile request structure as defined in Section 2.2
*   Generating traveler profiles using the structure outlined in Section 3.1
*   Using the standardized travel context tags as described in Section 3.2

6.2. **Test Cases**

Test cases should be developed to validate the implementation of the specification by travel providers and digital wallet or digital agent developers. These test cases should cover:

*   Correct generation of traveler profiles based on profile presentation requests
*   Proper handling of user consent and terms of use
*   Verification of issuer DIDs and signatures
*   Consistency in the use of travel context tags

7. **References**

*   W3C. (2021). Decentralized Identifiers (DIDs) v1.0. Retrieved from [https://www.w3.org/TR/did-core/](https://www.w3.org/TR/did-core/)
*   W3C. (2019). Verifiable Credentials Data Model 1.0. Retrieved from [https://www.w3.org/TR/vc-data-model/](https://www.w3.org/TR/vc-data-model/)
*   ISO. (2014). ISO 8601:2014 - Date and time format. Retrieved from [https://www.iso.org/standard/40874.html](https://www.iso.org/standard/40874.html)
*   ISO. (2017). ISO 10646:2017 - Universal Coded Character Set (UCS). Retrieved from [https://www.iso.org/standard/67909.html](https://www.iso.org/standard/67909.html)
*   W3C. (2018). JSON-LD 1.1 - A JSON-based Serialization for Linked Data. Retrieved from [https://www.w3.org/TR/json-ld11/](https://www.w3.org/TR/json-ld11/)

**8\. Glossary**

DID: Decentralized Identifier - A globally unique identifier for a digital identity, associated with a person, organization, or other entity.

Digital Wallet: A software application that stores, manages, and secures a user's digital identity, credentials, and other personal information.

Digital Agent: A software application that automates processes on behalf of a user, such as managing their digital identity and performing tasks like generating traveler profiles.

JSON-LD: JSON for Linked Data - A lightweight syntax to express structured data in JSON, used for serializing Linked Data.

Verifiable Credential: A digital document containing claims made by an issuer about a subject, which can be verified by a third party.

Verifiable Presentation: A digital document containing one or more verifiable credentials, presented by a subject to a verifier.

Issuer: An entity that creates and issues a verifiable credential to a subject.

Subject: An entity, such as a person or organization, that is the topic of a verifiable credential or presentation.

Verifier: An entity that checks the validity and authenticity of a verifiable credential or presentation.
