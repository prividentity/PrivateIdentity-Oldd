# The Cloud Biometric MFA System is Exempt from GDPR, CCPA, BIPA and HIPAA Privacy Obligations 

## Overview
* [<b>Fully homomorphic encryption</b>](https://en.wikipedia.org/wiki/Private_biometrics) (FHE) enables encrypted match and search operations on encrypted data without allowing any third party to observe the actual data. 
* [<B>IEEE 2410 Standard for Biometric Privacy</b>](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D) (SBP) requires FHE for private identity assertion and authentication. 
* IEEE 2410 compliance, "...<b>guarantees the SBP system does not incur </b>GDPR, CCPA, BIPA or HIPAA privacy obligations." </b>
## Cloud Biometric MFA processes only "anonymized data."
* <b>FHE payloads are anonymized data.</b> The FHE payload is a globally unique positional array that does not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait (embeddings, or vector encryptions). 
* <b>UUIDs are anonymized data.</b> The Cloud Biometric MFA system generates a universally unique identifier (“UUID”) to label each end user instead of using a username, email address or other personal data. This UUID cannot be tied back to an individual/end user by Private Identity. Therefore, this UUID is also anonymized data. 
* <b>FHE payloads and UUIDs are not “personal data” or “biometric data” </b>under the GDPR, “personal information” or “biometric information” under the CCPA, “biometric identifiers” or “biometric information” under the BIPA, and are not “protected health information” under the HIPAA. 

### Cloud Biometric MFA is exempt from privacy law obligations
* <b>The system processes only anonymized data</b> and not personal data. This eliminates the data subject’s rights that would otherwise arise when personal data is being processed.    
* <b>The loss of any FHE payloads and UUIDs would not constitute a breach</b> of biometric data or personal data. FHE payloads do not constitute personal data.
* <b>The system fulfills the GDPR, CCPA, BIPA and HIPAA's regulatory and policy goals</b> by minimizing the need to process unnecessary categories of personal data.  This helps advance each of the data protection principles underlying data privacy laws worldwide.   

## GDPR
Cloud Biometric MFA systems enable customers to, "advance the principles of the GDPR by transforming biometrics into anonymized FHE payloads. This eliminates the requirement for organizations to gather personal data to support robust security and advances the integrity and confidentiality principle and the data minimization principle of the GDPR." 
See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#95-gdpr) for full discussion.
### FHE Payloads Contain "Anonymized Data"
* "FHE payloads and UUIDs are not personal data under the GDPR. Accordingly, the GDPR’s principles do not apply to the FHE payloads or UUIDs."  
* See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#951-fhe-payloads-contain-anonymized-data) for full discussion. 
### FHE Payloads Do Not Contain "Biometric Data"
* "The FHE payload with UUID does not qualify as biometric data. In particular, the FHE payload does not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait."
* "The UUID is a randomly generated, universally unique identifier that cannot be tied back to an individual/end user once assigned and in the possession of an entity utilizing SBP systems."
* See [link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#952-fhe-payloads-do-not-contain-biometric-data) for full discussion. 



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