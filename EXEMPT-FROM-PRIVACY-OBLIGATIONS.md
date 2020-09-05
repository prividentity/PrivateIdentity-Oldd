# Exempt from GDPR, CCPA, BIPA and HIPAA Privacy Obligations 

## Contents
1. [<b>`Overview`</b>](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#1overview)
   1. [Cloud Biometric MFA system processes only "anonymized data.](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#cloud-biometric-mfa-system-processes-only-anonymized-data)
   1. [Cloud Biometric MFA system is exempt from privacy law obligations](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#cloud-biometric-mfa-system-is-exempt-from-privacy-law-obligations)
1. [<b>`GDPR Analysis`</b>](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#gdpr-analysis) 
   1. [FHE Payloads Contain "Anonymized Data"](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-contain-anonymized-data)
   1. [FHE Payloads Do Not Contain "Biometric Data"](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-do-not-contain-biometric-data)
   1. [System is not subject to GDPR obligations](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#system-is-not-subject-to-gdpr-obligations)
1. [<b>`CCPA Analysis`</b>](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#ccpa-analysis)
   1. [FHE Payloads Contain "Deidentified Information"](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-contain-deidentified-information)
   1. [FHE Payloads Do Not Contain "Biometric Information"](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-do-not-contain-biometric-information)
   1. [FHE Payloads Are Not Subject to CCPA Obligations](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-are-not-subject-to-ccpa-obligations)
1. [<b>`BIPA Analysis`</b>](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#bipa-analysis)
   1.  [FHE Payloads Do Not Contain "Biometric Identifiers" or "Biometric Information"](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-do-not-contain-biometric-identifiers-or-biometric-information)
    1. [FHE Payloads Do Not Incur BIPA Obligations](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-do-not-incur-bipa-obligations)
1. [<b>`HIPAA Analysis`</b>](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#hipaa-analysis)
   1. [FHE Payloads Do Not Contain Individually Identifiable Health Information](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-do-not-contain-individually-identifiable-health-information)
   1. [https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-do-not-incur-hipaa-obligations](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-do-not-incur-hipaa-obligations)
   1. [FHE Payloads Do Not Incur HIPAA Obligations](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#fhe-payloads-do-not-incur-hipaa-obligations)
1. [<b>`Resources`</b>](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#resources)

## 1.`Overview`
* [<b>Fully homomorphic encryption</b>](https://en.wikipedia.org/wiki/Private_biometrics) (FHE) enables encrypted match and search operations on encrypted data without allowing any third party to observe the actual data. 
* [<B>IEEE 2410 Standard for Biometric Privacy</b>](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D) (SBP) <b>requires FHE for private identity assertion and authentication</b>. 
* IEEE 2410 compliance, "...<b>guarantees the SBP system does not incur </b>GDPR, CCPA, BIPA or HIPAA privacy obligations." </b>

#### `Cloud Biometric MFA system processes only "anonymized data."`
* <b>FHE payloads are anonymized data.</b> The FHE payload is a globally unique positional array that does not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait (embeddings, or vector encryptions). 

* Below is an example of a Base-64 encoded FHE payload.
> `WzAuMDUwMDcyMjk3NDUzODgwMzEsMC4wNjUwNTE0MjE1MjMwOTQxOCwwLjAxMTI1MjIyOTEwMTk1NTg5LDAuMDU5ODE1MzkxODk4MTU1MjEsLTAuMTUxMjE1NDA0MjcyMDc5NDcsLTAuMTQ5NTE4MTAyNDA3NDU1NDQsMC4wNTA2NzE3NDUwOTE2NzY3MSwtMC4wNDU3NDU4ODY4NjIyNzc5ODUsMC4xMTM2MDg2MzU5NjIwMDk0MywwLjAyOTE5MjgwNzE1Mjg2NzMxNywwLjAzOTM5MDUzNzg4NzgxMTY2LC0wLjEwMTk0ODQxNzcyMzE3ODg2LDAuMDU3MTY1MzE3MjM3Mzc3MTcsMC4wODczNTUzMjMxMzU4NTI4MSwtMC4wMDAyMTMwNzk3OTQ3NzU2OTQ2LDAuMDgyODEyODgyOTU5ODQyNjgsMC4wNDI0OTUwNDU4MTA5Mzc4OCwtMC4xMjIyNjg5NzQ3ODEwMzYzOCwtMC4xMzc3NDUwOTcyNzk1NDg2NSwwLjE2MTk5OTMyOTkyNDU4MzQ0LDAuMDcxMzQ3MzkzMDk1NDkzMzIsLTAuMD==`

* <b>UUIDs are anonymized data.</b> The Cloud Biometric MFA system generates a universally unique identifier (“UUID”) to label each end user instead of using a username, email address or other personal data. 
* Below is an example of an UUID
> `f669af15b6af1f23665e`
* UUIDs cannot be tied back to an individual/end user by Private Identity. Therefore, the UUID is also anonymized data. 
* <b>FHE payloads and UUIDs are not “personal data” or “biometric data” </b>under the GDPR, “personal information” or “biometric information” under the CCPA, “biometric identifiers” or “biometric information” under the BIPA, and are not “protected health information” under the HIPAA. 

#### Cloud Biometric MFA system is exempt from privacy law obligations
* <b>The system processes only anonymized data</b> and not personal data. This eliminates the data subject’s rights that would otherwise arise when personal data is being processed.    
* <b>The loss of any FHE payloads and UUIDs would not constitute a breach</b> of biometric data or personal data. FHE payloads do not constitute personal data.
* <b>The system fulfills the GDPR, CCPA, BIPA and HIPAA's regulatory and policy goals</b> by minimizing the need to process unnecessary categories of personal data.  This helps advance each of the data protection principles underlying data privacy laws worldwide.   

## `GDPR Analysis`
![GDPR Icon](https://github.com/openinfer/PrivateIdentity/blob/master/images/GDPR%202.png)
* The system, "<b>advance[s] the principles of the GDPR by transforming biometrics into anonymized FHE payloads.</b> This eliminates the requirement for organizations to gather personal data to support robust security and advances the integrity and confidentiality principle and the data minimization principle of the GDPR." 
[Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#95-gdpr) for full text.

#### FHE Payloads Contain "Anonymized Data"
* <b>"FHE payloads and UUIDs are not personal data under the GDPR.</b> 
* Accordingly, the <b>GDPR’s principles do not apply to the FHE payloads or UUIDs." </b>
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#951-fhe-payloads-contain-anonymized-data) for full text. 

#### FHE Payloads Do Not Contain "Biometric Data"
* <b>"The FHE payload with UUID does not qualify as biometric data.</b> In particular, the FHE payload does not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait."
* <b>"The UUID is a randomly generated, universally unique identifier </b>that cannot be tied back to an individual/end user once assigned and in the possession of an entity utilizing SBP systems."
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#952-fhe-payloads-do-not-contain-biometric-data) for full text. 

#### System is not subject to GDPR obligations
* <b>"The GDPR does not regulate the processing of anonymized information </b>[GDPR Recital 26](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32016R0679). 
* In Recital 26, the GDPR specifically refers to anonymization to exclude anonymized data from the scope of the data protection legislation, stating:

> “The principles of data protection should therefore not apply to anonymous information, namely information which does not relate to an identified or identifiable natural person or to personal data rendered anonymous in such a manner that the data subject is not or no longer identifiable. This Regulation does not therefore concern the processing of such anonymous information, including for statistical or research purposes” [GDPR Recital 26](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32016R0679).

* <b>"We conclude that the FHE payloads and UUIDs are not subject to the requirements of GDPR </b>because they constitute anonymized data and do not contain personal data or biometric data."
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS) for full text. 

## `CCPA Analysis`
![CCPA Icon](https://github.com/openinfer/PrivateIdentity/blob/master/images/CCPA%201.png)
* “The system <b>advances the CCPA’s data minimization goals </b>by transmitting, storing and using (processing) only deidentified data and deleting all personal information immediately after it is transformed into FHE payloads."
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#96-ccpa) for full text. 

#### FHE Payloads Contain "Deidentified Information"
* "The <b>CCPA defines and regulates “personal information” </b>as “information that identifies, relates to, describes, is capable of being associated with, or could reasonably be linked, directly or indirectly, with a particular consumer or household.” 
* The system <b>fully realizes the CCPA’s legislative goals</b> by, "transforming personal information into FHE payloads and UUIDs that are treated as “deidentified” data under the CCPA."
* The system <b>only transmits, stores or uses deidentified (anonymized) data</b>. 
* The system <b>does not, "transmit, store or use any other personal data or biometric data</b>, machine or device identifications, metadata, or any other identifying information."
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#961-fhe-payloads-contain-deidentified-information) for full text. 

#### FHE Payloads Do Not Contain "Biometric Information"
* The CCPA defines biometric information as follows.
> “…an individual’s physiological, biological or behavioral characteristics, including an individual’s DNA, that <b>can be used, singly or in combination with each other or with other identifying data, to establish individual identity</b>. Biometric information includes, but is not limited to, imagery of the iris, retina, fingerprint, face, hand, palm, vein patterns, and voice recordings, from which an identifier template, such as a faceprint, a minutiae template, or a voiceprint, can be extracted, and keystroke patterns or rhythms, gait patterns or rhythms, and sleep, health, or exercise data that contain identifying information.” [CCPA 1798.140(b)](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.140.).
* "The encrypted <b>FHE payloads and UUIDs created by SBP systems do not qualify as biometric data under the CCPA</b>. These FHE payloads and UUIDs contain no biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait."
* <b>"Accordingly, the encrypted FHE payloads and UUIDs should not be treated as biometric information under the CCPA."</b>
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#962-fhe-payloads-do-not-contain-biometric-information) for full text. 

#### FHE Payloads Are Not Subject to CCPA Obligations
* <b>FHE payloads and UUIDs are deidentified data</b>.
* "<b>Businesses processing deidentified data are not obligated</b> to provide or delete information in response to a consumer request or to re-identify individual data to verify a consumer request." 
> “If a business maintains consumer information that is deidentified, a business is not obligated to provide or delete this information in response to a consumer request or to re-identify individual data to verify a consumer request.”  [see California Consumer Privacy Act Regulations at § 999.323(f)](https://www.oag.ca.gov/sites/all/files/agweb/pdfs/privacy/ccpa-proposed-regs.pdf)
* The CCPA Regulations at § [1798.140(b)](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.140.) <b>further excludes deidentified information from the scope of the legislation.</b> 
> <b>“‘Deidentification’ means information that cannot reasonably identify, relate to, describe, be capable of being associated with, or be linked, directly or indirectly to a particular consumer</b>, provided that a business that uses deidentified information has implemented technical and process safeguards that prohibit reidentification of the consumer, has implemented processes to prevent inadvertent release of deidentified information, and makes no attempt to reidentify the information.” [1798.140(h)](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.140.)
* Finally, in the same section, [CCPA § 1798.145(a)(5)](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.145.) further provides that <b>nothing in the CCPA restricts a business’s ability to “collect, use, retain, sell, or disclose consumer information that is deidentified or in the aggregate.”</b>
* "Therefore, the <b>consumer rights provided under the CCPA thus fall away with respect to this deidentified information and businesses that utilize this system do not incur CCPA obligations."</b>
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#962-fhe-payloads-do-not-contain-biometric-information) for full text. 

## `BIPA Analysis`
![BIPA Icon](https://github.com/openinfer/PrivateIdentity/blob/master/images/BIPA%201.png)
* BIPA applies to both biometric identifiers and biometric information. 
* A <b>“biometric identifier”</b> includes specific types of information including fingerprint, voiceprint, retina/iris scan, scans or records of hand or face geometry." [See 740 ILCS 14/10](https://www.ilga.gov/legislation/ilcs/ilcs3.asp?ActID=3004&ChapterID=57) 
* <b>"Biometric information"</b> includes “any information, regardless of how it is captured, converted, stored, or shared, based on an individual’s biometric identifier used to identify an individual.” [See 740 ILCS 14/10](https://www.ilga.gov/legislation/ilcs/ilcs3.asp?ActID=3004&ChapterID=57) 
* Illinois courts have found “that <b>biometric templates</b> derived from user-uploaded photos qualify as “biometric information” under BIPA.”  [See Rivera v. Google, Inc., 238 F. Supp. 3d 1088 (N.D. Ill. 2017)](https://www.lexisnexis.com/community/case-opinion/b/case/posts/rivera-v-google-inc)

#### FHE Payloads Do Not Contain "Biometric Identifiers" or "Biometric Information"
* Plaintext biometric information is FHE transformed through a one-way cryptographic hash function (in our case, a mobile embedding DNN) and becomes an FHE payload. 
* FHE payloads are “globally unique positional arrays of 128 floating-point numbers that do not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral traits.”
* The system, "<b>advances the rights of Illinois residents with respect to the collection of their biometric identifiers</b> or biometric information by only transmitting, storing or using anonymized data."
* “Accordingly, the <b>system only transmit, store or use deidentified data and no biometric identifiers or biometric information</b>. 
* Under the plain language of this section and the Illinois state court interpretation, <b>we find the encrypted FHE payload should not be treated as biometric identifiers or biometric information</b>.”
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#971-fhe-payloads-do-not-contain-biometric-identifiers-or-biometric-information) to full text. 

#### FHE Payloads Do Not Incur BIPA Obligations
* <b>BIPA obligations apply only to biometric information. </b>
* As discussed in the section above, the system does not contain biometric information or biometric identifiers.
* Accordingly, an organization using Cloud Biometric MFA is, “not collecting or storing biometric information and, with respect to this system, eliminates the requirement to comply with BIPA obligations including the consent requirements and the requirement for an organization to protect and store biometric data at least to the same degree it protects other confidential or sensitive information.”
## `HIPAA Analysis`
![HIPAA icon](https://github.com/openinfer/PrivateIdentity/blob/master/images/HIPAA%201.png)
* “The Privacy Rule, or Standards for Privacy of Individually Identifiable Health Information, established a standard for the protection of certain health information in the United States.” 
* “The Security Standards for the Protection of Electronic Protected Health Information (the Security Rule) established a national set of security standards for protecting certain health information that is held or transferred in electronic form in the United States.”
* “The Security Rule operationalized the protections contained in the Privacy Rule by addressing the technical and non-technical safeguards that organizations called “covered entities” must put in place to secure individuals’ “electronic protected health information” (e-PHI).” 

#### FHE Payloads Do Not Contain Individually Identifiable Health Information
* “The HIPAA defines and protects Protected Health Information, which is individually identifiable health information. 
* The system fully realizes HIPAA’s goals by, “transforming personal information into FHE payloads and UUIDs that are “deidentified” data…” 
> FHE payloads and UUIDs contain no health information, health-related information, healthcare provider information, or healthcare event-related information
> There is no data in the system that could be combined with the FHE payloads or UUIDs to identify the individual or device to whom the data relates
> FHE payloads and UUIDs are not reversible
> FHE payloads and UUIDs cannot be linked to an individual 
* The system only “transmit[s], store[s] or use[s] deidentified (anonymized) data.”
* The system does not transmit, store or use, “any other personal data, biometric data, health data, health-related data, machine or device identifications, metadata, or any other identifying information.”
* Finally, FHE payload and UUIDs do not contain any information useful for diagnostic purposes.
#### FHE Payloads Do Not Incur HIPAA Obligations
* Therefore the system (inclusive of FHE payloads and UUIDs) is, <b>“not subject to the requirements of the Privacy Rule or the Security Rule under HIPAA </b>because [it does] not contain personal data, biometric data, or health information. Furthermore, the FHE payloads and UUIDs are universally unique and cannot be tied back to an individual/end user once assigned and in the possession of an entity utilizing SBP systems.”

> <b>IMPORTANT NOTICE:</b> THIS ANALYSIS OF DATA PRIVACY LAWS DOES NOT CONSTITUTE LEGAL ADVICE AND ALL BUSINESSES SHOULD SEEK COUNSEL CONCERNING THEIR DATA PRIVACY LEGAL AND COMPLIANCE OBLIGATIONS.

## `Resources`
**IEEE 2410-2020 Standard for Biometric Privacy**<br>
IEEE-SA Standards Board (2020). "IEEE 2410 Standard for Biometric Privacy." The Institute of Electrical and Electronics Engineers (New York, NY). [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D)

**Data Privacy and Compliance in the Age of Fully Homomorphic Encryption (FHE): GDPR, CCPA and BIPA.**<br>
Lentchner, Cassie and S. Farmer. “Data Privacy and Compliance in the Age of Fully Homomorphic Encryption (FHE): GDPR, CCPA and BIPA.” Pillsbury Winthrop Shaw Pittman LLP. August 1, 2020. 

**US Patent (2019): Systems and methods for privacy-enabled biometric processing**<br>
Streit, S. (2019).  “Systems and methods for privacy-enabled biometric processing.”  US Patent No. 10,419,221.  [Link](https://patents.google.com/patent/US10419221B1/)

**US Patent (2020): Systems and methods for privacy-enabled biometric processing**<br>
Streit, S. (2020).  "Systems and methods for privacy-enabled biometric processing." US Patent No. 10,721,070. [Link](http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.htm&r=1&f=G&l=50&s1=10,721,070.PN.&OS=PN/10,721,070&RS=PN/10,721,070)

**Paper: Privacy-Enabled Biometric Search**<br>
S. Streit, B. Streit, and S. Suffian, “Privacy-Enabled Biometric Search,” Aug. 2017. [Link](https://arxiv.org/abs/1708.04726)

**DHS:  Risks and Opportunities of Contactless Biometrics.**<br>
_IARPA launched the Homomorphic Encryption Computing Techniques with Overhead Reduction (HECTOR) R&D program in 2017 and reported that law enforcement agencies and private sector companies may, “leverage these new forms of Personal Identifying Information (PII) without encroaching on civil liberties…”_<br>
“Risks and Opportunities of Contactless Biometrics.” US Office of the Director of National Intelligence. (9/2017) Public-Private Analytic Exchange Program. Retrieved 3/20/2020 from https://www.hsdl.org/?abstract&did=809318. Page 3.

**Wikipedia:  Private Biometrics**<br>
Wikipedia contributors. (2020, February 17). Private biometrics. In Wikipedia, The Free Encyclopedia. Retrieved September 2020, from https://en.wikipedia.org/w/index.php?title=Private_biometrics&oldid=941261347

