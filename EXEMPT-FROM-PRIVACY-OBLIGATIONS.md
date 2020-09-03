# Exempt from GDPR, CCPA, BIPA and HIPAA Privacy Obligations 

## Overview
* [<b>Fully homomorphic encryption</b>](https://en.wikipedia.org/wiki/Private_biometrics) (FHE) enables encrypted match and search operations on encrypted data without allowing any third party to observe the actual data. 
* [<B>IEEE 2410 Standard for Biometric Privacy</b>](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D) (SBP) requires FHE for private identity assertion and authentication. 
* IEEE 2410 compliance, "...<b>guarantees the SBP system does not incur </b>GDPR, CCPA, BIPA or HIPAA privacy obligations." </b>
## System processes only "anonymized data."
* <b>FHE payloads are anonymized data.</b> The FHE payload is a globally unique positional array that does not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait (embeddings, or vector encryptions). 
* <b>UUIDs are anonymized data.</b> The Cloud Biometric MFA system generates a universally unique identifier (“UUID”) to label each end user instead of using a username, email address or other personal data. This UUID cannot be tied back to an individual/end user by Private Identity. Therefore, this UUID is also anonymized data. 
* <b>FHE payloads and UUIDs are not “personal data” or “biometric data” </b>under the GDPR, “personal information” or “biometric information” under the CCPA, “biometric identifiers” or “biometric information” under the BIPA, and are not “protected health information” under the HIPAA. 

## System is exempt from privacy law obligations
* <b>The system processes only anonymized data</b> and not personal data. This eliminates the data subject’s rights that would otherwise arise when personal data is being processed.    
* <b>The loss of any FHE payloads and UUIDs would not constitute a breach</b> of biometric data or personal data. FHE payloads do not constitute personal data.
* <b>The system fulfills the GDPR, CCPA, BIPA and HIPAA's regulatory and policy goals</b> by minimizing the need to process unnecessary categories of personal data.  This helps advance each of the data protection principles underlying data privacy laws worldwide.   

## GDPR Analysis
Cloud Biometric MFA systems enable customers to, "advance the principles of the GDPR by transforming biometrics into anonymized FHE payloads. This eliminates the requirement for organizations to gather personal data to support robust security and advances the integrity and confidentiality principle and the data minimization principle of the GDPR." 
See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#95-gdpr) for full discussion.
### FHE Payloads Contain "Anonymized Data"
* "FHE payloads and UUIDs are not personal data under the GDPR. Accordingly, the GDPR’s principles do not apply to the FHE payloads or UUIDs."  
* See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#951-fhe-payloads-contain-anonymized-data) for full discussion. 
### FHE Payloads Do Not Contain "Biometric Data"
* "The FHE payload with UUID does not qualify as biometric data. In particular, the FHE payload does not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait."
* "The UUID is a randomly generated, universally unique identifier that cannot be tied back to an individual/end user once assigned and in the possession of an entity utilizing SBP systems."
* See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#952-fhe-payloads-do-not-contain-biometric-data) for full discussion. 
### System is not subject to GDPR obligations
* "The GDPR does not regulate the processing of anonymized information [GDPR Recital 26](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32016R0679). 
* In Recital 26, the GDPR specifically refers to anonymization to exclude anonymized data from the scope of the data protection legislation, stating:

> “The principles of data protection should therefore not apply to anonymous information, namely information which does not relate to an identified or identifiable natural person or to personal data rendered anonymous in such a manner that the data subject is not or no longer identifiable. This Regulation does not therefore concern the processing of such anonymous information, including for statistical or research purposes” [GDPR Recital 26](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32016R0679).

* "We conclude that the FHE payloads and UUIDs are not subject to the requirements of GDPR because they constitute anonymized data and do not contain personal data or biometric data."
* See [link](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS) for full discussion. 

## CCPA Analysis
* The system helps, "advance the CCPA’s data minimization goals by transmitting, storing and using (processing) only deidentified data and deleting all personal information immediately after it is transformed into FHE payloads."
* See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#96-ccpa) for full discussion. 

### FHE Payloads Contain "Deidentified Information"
* "The CCPA defines and regulates “personal information” as “information that identifies, relates to, describes, is capable of being associated with, or could reasonably be linked, directly or indirectly, with a particular consumer or household.” 
* The system fully realizes the CCPA’s legislative goals by, "transforming personal information into FHE payloads and UUIDs that are treated as “deidentified” data under the CCPA."
* The system only transmits, stores or uses deidentified (anonymized) data. 
* The system does not, "transmit, store or use any other personal data or biometric data, machine or device identifications, metadata, or any other identifying information."
* See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#961-fhe-payloads-contain-deidentified-information) for full discussion. 

### FHE Payloads Do Not Contain "Biometric Information"
* The CCPA defines biometric information as follows.
> “…an individual’s physiological, biological or behavioral characteristics, including an individual’s DNA, that can be used, singly or in combination with each other or with other identifying data, to establish individual identity. Biometric information includes, but is not limited to, imagery of the iris, retina, fingerprint, face, hand, palm, vein patterns, and voice recordings, from which an identifier template, such as a faceprint, a minutiae template, or a voiceprint, can be extracted, and keystroke patterns or rhythms, gait patterns or rhythms, and sleep, health, or exercise data that contain identifying information.” [CCPA 1798.140(b)](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.140.).
* "The encrypted FHE payloads and UUIDs created by SBP systems do not qualify as biometric data under the CCPA. These FHE payloads and UUIDs contain no biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait."
* "Accordingly, the encrypted FHE payloads and UUIDs should not be treated as biometric information under the CCPA."
* See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#962-fhe-payloads-do-not-contain-biometric-information) for full discussion. 

### FHE Payloads Are Not Subject to CCPA Obligations
* "<b>Businesses processing deidentified data are not obligated</b> to provide or delete information in response to a consumer request or to re-identify individual data to verify a consumer request." 
> “If a business maintains consumer information that is deidentified, a business is not obligated to provide or delete this information in response to a consumer request or to re-identify individual data to verify a consumer request.”  [see California Consumer Privacy Act Regulations at § 999.323(f)](https://www.oag.ca.gov/sites/all/files/agweb/pdfs/privacy/ccpa-proposed-regs.pdf)
* The CCPA Regulations at § [1798.140(b)](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.140.)further excludes deidentified information from the scope of the legislation. 
* “ “Deidentification” means information that cannot reasonably identify, relate to, describe, be capable of being associated with, or be linked, directly or indirectly to a particular consumer, provided that a business that uses deidentified information [has implemented technical and process safeguards that prohibit reidentification of the consumer, has implemented processes to prevent inadvertent release of deidentified information, and makes no attempt to reidentify the information.” [20]
* Finally, in the same section, [CCPA § 1798.145(a)(5)](https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.145.) further provides that nothing in the CCPA restricts a business’s ability to “collect, use, retain, sell, or disclose consumer information that is deidentified or in the aggregate.”
* "FHE payloads and UUIDs contain only deidentified data." 
* "Therefore, the consumer rights provided under the CCPA thus fall away with respect to this deidentified information and businesses that utilize this system do not incur CCPA obligations."
* See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#962-fhe-payloads-do-not-contain-biometric-information) for full discussion. 

## BIPA Analysis 
* BIPA applies to both biometric identifiers and biometric information. 
* Under BIPA, a “biometric identifier” includes specific types of information including fingerprint, voiceprint, retina/iris scan, scans or records of hand or face geometry." [See 740 ILCS 14/10](https://www.ilga.gov/legislation/ilcs/ilcs3.asp?ActID=3004&ChapterID=57) 
* "Biometric information" includes “any information, regardless of how it is captured, converted, stored, or shared, based on an individual’s biometric identifier used to identify an individual.” [See 740 ILCS 14/10](https://www.ilga.gov/legislation/ilcs/ilcs3.asp?ActID=3004&ChapterID=57) 
* Illinois courts have found that biometric templates derived from user-uploaded photos qualify as “biometric information” under BIPA.  [See Rivera v. Google, Inc., 238 F. Supp. 3d 1088 (N.D. Ill. 2017)](https://www.lexisnexis.com/community/case-opinion/b/case/posts/rivera-v-google-inc)

### FHE Payloads Do Not Contain "Biometric Identifiers" or "Biometric Information"
* The system, "advance the rights of Illinois residents with respect to the collection of their biometric identifiers or biometric information by only transmitting, storing or using anonymized data."
* the system grants each end user a license to run application software on the user’s local device. Using this application, the user collects his/her own biometric data.
data is then transformed (encrypted) by a one-way cryptographic hash function on the local device and becomes FHE payloads. FHE payloads are globally unique positional arrays of 128 floating-point numbers that do not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral traits.




* <b>IMPORTANT:</b> _This analysis of data privacy laws does not constitute legal advice and all businesses should seek counsel concerning their data privacy legal and compliance obligations._


## Resources
**IEEE 2410-2020 Standard for Biometric Privacy**<br>
IEEE-SA Standards Board (2020). "IEEE 2410 Standard for Biometric Privacy." The Institute of Electrical and Electronics Engineers (New York, NY). [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D)

**Data Privacy and Compliance in the Age of Fully Homomorphic Encryption (FHE): GDPR, CCPA and BIPA.**<br>
Lentchner, Cassie and S. Farmer. “Data Privacy and Compliance in the Age of Fully Homomorphic Encryption (FHE): GDPR, CCPA and BIPA.” Pillsbury Winthrop Shaw Pittman LLP. August 1, 2020. [Link](https://github.com/openinfer/PrivateIdentity/blob/master/images/Private%20Id%20FHE%20Privacy%20Memo%20(Pillsbury).pdf)

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