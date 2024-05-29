# **Credential Policy (CrP) and Credential Policy Statement (CrPS)** <br>
Effective Date: 20 May 2024

# Introduction

## Overview

This document outlines the Credential Policy (CrP) and serves as the Credentialing Practice Statement (CrPS) for Private ID's UltraPass® service. UltraPass® provides a secure, easy to deploy, and low-friction method for businesses, government agencies, non-governmental organizations (NGOs) or educational institutions to verify identities remotely for use online. The purpose of this document is to demonstrate that the UltraPass® service meets IAL2 and AAL2 requirements.
The UltraPass® service performs Unsupervised, Remote Proofing during enrollment. Enrollment is completed using an UltraPass® native mobile app on iOS or Android, or via a mobile web enrollment flow provided by a Relying Party (RP).
Private ID’s UltraPass® service enables Relying Parties to ensure that their End Users' identities are verified by a trusted source while also ensuring that their most sensitive data–their biometric data–is not transmitted to or stored by the service.

## Roles

### Subject/End User 
An individual who has successfully completed identity proofing and verification processes and been issued a credential.
Relying Party (RP). A partner enterprise or entity that uses Private ID's UltraPass® services to verify a Subject's identity and eligibility for services at a specific access level (AL) offered by the Relying Party. 

### Referee Organization 
Referee Organization: An entity contracted by Private ID to follow specific Referee Rules, notifying Private ID of the details of each identity proofing attempt for an IAL2 credential, as outlined in NIST SP 800-63-3 revision 3.

## Terms

### Authoritative Source 
A recognized repository known for its accuracy and current information, used to validate details provided by the applicant.

### Credential Usage 
An UltraPass® identity credential is issued to an End User for authentication by a Relying Party for transactions or exchanges. ### ### Relying Parties direct End Users to the UltraPass® platform for initial sign-up and specify the required Assurance Level (AL) for credential issuance and authentication. Relying Parties should use authentication assertions at the specified AL or lower and must not rely on assertions for services at a higher AL or beyond the assertion's valid lifetime. The terms under which credentials are issued and authenticated are determined through a contract or fixed agreement with Private Identity LLC.

## Policy Administration

### This document is administered by:
Private Identity LLC <br>
13331 Signal Tree Lane <br>
Potomac, MD USA. <br>
Email: [Support@privateid.com](mailto:Support@privateid.com)

### CrP/CrPS Review and Approval 
This CrP/CrPS is reviewed annually by Private ID’s Technology, Information Security, and Product teams to confirm changes are adequately reflected. Once reviews and updates have been addressed, the CrP/CrPS is approved by the Private ID Chief Operating Officer (COO).

### Jurisdictions 
Private ID operates in the United States, Canada, and Europe. The IAL2/AL2 flows described in this CrP/CrPS are only operable in the United States.

# Publication and Repository Responsibilities 

Private ID shall publish its CrP/CrPS regarding the UltraPass® service, and other terms of service as required to fully inform all necessary and appropriate parties, in its Terms of Use, Member Terms and Privacy Policy. These publications shall be maintained such that they are accurate per the current state of the UltraPass® service at any given time.
Private ID SHALL maintain an internal repository containing only the essential information about individual credentials, their statuses, and the Subject’s attributes and eligibility, to comply with legislative, contractual, and policy requirements
Private ID’s Member Terms and Privacy Policy govern the circumstances under which member data may be shared. Private ID SHALL require the End Users to acknowledge and authorize publication of their personal information to each RP with whom they interact.

# IdP Credential Registration and Issuance

## Overview
Private ID’s UltraPass® enrollment is a Remote, Unsupervised registration.
Multi-factor authentication is needed to prove the End User’s identity for the purpose of a registration, as outlined in section 3.3.

## Private ID UltraPass® Registration
End Users SHALL be permitted to register a credential directly via Relying Party websites/applications utilizing UltraPass®. Only unsupervised, remote proofing is supported by this policy. To obtain an UltraPass® credential under this policy, End Users SHALL be directed to the UltraPass® identity authentication services by a Relying Party (RP). Under this policy, the RP decides if the end user should be directed to the UltraPass® portal for unsupervised proofing, which is the primary method for user registration.
During the registration process, users SHALL have access to the Terms of Service, Privacy Policy, Credential Policy, and any other relevant policies. Additionally, the user must accept all applicable terms before providing any sign-up information. Records of their acceptance and the date SHALL be retained.
Registration SHALL require End Users to provide a mobile phone number owned by the End User. A text message containing a unique enrollment code SHALL be sent to the End User requiring them to confirm the possession of the provided phone number before the identity proofing is performed.
Registration SHALL require End Users to perform a biometric scan (Face “selfie”). Our  UltraPass® service is powered by proprietary, patented Homomorphic Identity Tokens (HITs) that utilize deep homomorphic hashing techniques. This innovative technology allows for specific computations on tokenized biometric data without the need for decryption, thereby preserving both privacy and security. The original biometric capture (face “selfie(s)” are deleted on-device approximately 20 milliseconds after you capture them. Your biometric information will not leave the device you used for registration. Only the anonymized Homomorphic Identity Tokens (HITs) will be processed by the UltraPass® service. The enrollment flow will permit multiple attempts to properly capture the biometric scan (Face “selfie”). If the capture fails for any reason, the flow will give the user the option to quit the enrollment and restart later when conditions improve.
A FIDO2 Passkey unique to the End User will be generated and stored on the enrollment device. This process will differ slightly based on the operating system running on the enrollment device, but will follow published FIDO2 standards.
Identity Proofing and Verification
Minimal Collection of PII. Information collected in Private ID’s identity proofing process is the minimum required to complete the necessary identity checks for the UltraPass® service.  After completing the identity proofing process (successful or failed), the End User information is retained based on the Data Retention Policy set by the RP, until the End User requests deletion of their data (or as required by applicable law). The results of the validation checks on the information described below are also retained. <br>
<br>
This information may include: <br>
Name <br>
Date of birth <br>
Address <br>
Mobile phone number <br>
Email address <br>
Identity document details (ID type, ID number, expiry) and images 

## Facial image for biometrics
Evidence Collected from the End User. Private ID utilizes the following pieces of evidence, provided by the End User, to establish user identity for the UltraPass® service: (Strength of Evidence is indicated, per NIST 800-63A)
Passport that is confirmed to be authentic and confirmed against the authoritative and/or issuing sources (SUPERIOR). <br>
Government issued ID that is confirmed to be authentic and confirmed against authoritative and/or issuing sources (STRONG) <br>
Validated phone number which is corroborated against carrier data and publicly available data (FAIR) <br>
The government-issued ID is validated by one or more third party vendor services that evaluate the document’s authenticity, check for security features, review for signs of tampering, and confirm that it is unexpired. <br>
<br>
Government-issued IDs that Private ID accepts for UltraPass® are: <br>
US Passport <br>
US Passport Cards <br>
US State IDs (Includes drivers licenses) <br>
US Permanent Resident Card <br>
All International Passports (except for OFAC-sanctioned countries)

## Biometric Checks
A biometric check is performed to compare the user's image on the ID document with the original biometric scan (Face “selfie”) captured during the enrollment.

## Liveness Checks
A liveness check confirms that the applicant enrolling is physically present.

## Document Validation by Type
Passports: Extracted biographic data is checked against consumer records databases as an authoritative source. <br>
Drivers Licenses and State IDs: Extracted biographic data is checked against Department of Motor Vehicle (DMV) records as an issuing source or credit bureaus as an authoritative source. <br>
Phone number corroboration is used to check the applicant’s information against customer records from mobile phone carriers and consumer reporting agencies to provide additional proof of validity of the information.

## Data Extraction 
The applicant’s name, DOB and physical address are extracted from their ID document. In cases where the address is not available on the government-issued ID (e.g. passport), the applicant address will be requested of the user via a form for input and confirmation. The data from the document, plus the address, is validated using biographic data corroboration. All of these checks must confirm the veracity of the information for the enrollment to be successfully completed. 

## Logging
Private ID retains logs with unique identifiers for each of these pieces of evidence received back from the biographic data and phone number corroboration processes that include all details related to the attempted enrollment for the UltraPass® Enrollment service.

## Enrollment Code Address of Record 
Private ID uses the applicant's phone number as their address of record for submitting a mandatory enrollment code. Applicants will receive a text message with a unique one-time-use link containing the enrollment code that they must click on and follow to the PrivateID UltraPass® portal to continue their enrollment on that mobile device. This enrollment code is valid for up to 10 minutes when sent to a telephone number of record via SMS. Enrollment codes are not reusable after the first use nor after they expire. This phone number is confirmed to belong to the applicant during identity proofing. This validation assures that the applicant whose identity document has been supplied owns the phone number that was submitted to receive the enrollment link. If identity proofing does not confirm the information the applicant has submitted, this check will fail and they will be unable to successfully enroll at the UltraPass® IAL2.

##Errors and Redress <br>
PrivateID’s UltraPass® enrollment interface provides user guidance to assist End Users during the process. If an enrollment attempt is ultimately unsuccessful, the notification screen at the end of the process will inform the End User of the reason. This will inform the End User if a reattempt is recommended, or if other actions, like using a different enrollment document, are recommended. Specific Relying Parties (RPs) may also provide additional instructions or provide a direct means to contact customer service in-line as part of the enrollment flow for applicants who have problems with identity proofing. <br>
Additional information can be found by going to Private ID’s [FAQs](https://github.com/openinfer/PrivateIdentity/wiki/FAQs).


