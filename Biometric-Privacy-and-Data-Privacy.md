## Biometric Privacy and Data Privacy
### BIOMETRIC PRIVACY 

Private Identity fully complies with IEEE 2410-2020 Standard for Biometric Privacy, an open standard and code of practice that focuses on end-user privacy and protection of biometric data using fully homomorphic encryption.  Private Identity also fully complies with ISO/IEC 27001:2013 Standard for Information Security Management, a code of practice that focuses on protection of data privacy. 

IEEE P2410-2020 assures consumer privacy by keeping biometric data encrypted at rest, in transit and in use and ensuring privacy by never processing, receiving or holding the plaintext biometric. The result is, “... guaranteed privacy, a complete specification without key management functions, and a simple standard implementation that consists of only 3 API endpoints.”

### DATA PRIVACY 

ISO 27001:2013 provides a comprehensive set of information security control objectives and a set of generally accepted good practice security controls.  Private Identity applies these controls appropriately in line with specific risks.  The Standard contains 12 main sections: 1. Risk assessment, 2. Security policy, 3. Organization of information security, 4. Asset management, 5. Human resources security, 6. Physical and environmental security, 7. Communications and operations management, 8. Access control, 9. Information systems acquisition, development and maintenance, 10. Information security incident management, 11. Business continuity management, 12. Compliance.  

### GDPR, CCPA AND BIPA COMPLIANCE

Private Identity allows its customers to utilize biometric security solutions without subjecting their organizations to GDPR, CCPA or BIPA obligations. 

Fully homomorphic encryption (FHE) mitigates the regulatory and legal privacy risk of biometric data by enabling mathematical operations on an encrypted dataset. The FHE transformation at the edge completely mitigates privacy risk by eliminating all requirements to store, transmit or use a plaintext biometric or template.￼

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(11).png)

Specifically, the biometric data is irreversibly anonymized using a 1-way cryptographic hash algorithm and then discarded (deleted) without the data ever leaving the local device. This anonymized data ceases to be personal data because no decrypt key exists and the loss of privacy by decryption is mathematically impossible. As a result, the FHE is not “Personal Data” under General Data Protection Regulation (EU) 2016/679 (“GDPR”) or the California Consumer Privacy Act (“CCPA”) and is not “Biometric Information” under the Biometric Information Privacy Act (“BIPA”).  As a result, the identification system is also exempt from data breach notification requirements.

#### Exempt from GDPR Obligations

Under GDPR, personal data is defined as information that can be identified by reference to “an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural or social identity of that natural person.”  No identifier is stored by the Private Identify system. The biometric data is transformed and then discarded while it is still on the local device and the only data transmitted or stored is a 1-way cryptographic hash algorithm. No identifier that can be associated with a data subject is transmitted or stored. That data has become irreversibly anonymized, is not “Personal Data,” and is therefore exempt from the GDPR. 

#### Exempt from CCPA Obligations

Similarly, this anonymized data would not be “Personal information” under the CCPA, which is data reasonably capable of being associated with a consumer.  The CCPA specifies that personal information does not include consumer information that is deidentified and the obligations imposed on businesses by the CCPA do not, “restrict a business’ ability to….collect, use, retain, sell, or disclose consumer information that is de-identified.”  “De-identified” under the CCPA is information that cannot “reasonably identify…or be linked, directly or indirectly, to a particular consumer” and that has technical safeguards and processes that prohibit reidentification.”  The data maintained by the Private Identity algorithm meet this standard. The only information transmitted or stored is an encrypted payload (1-way cryptographic vector hash) that cannot be reversed into any information that can be associated with a consumer.  Accordingly, Private Identity allows a business to utilize biometric identification without subjecting the business to the CCPA obligations.

#### Exempt from BIPA Obligations

Finally, the Private Identity recognition algorithm would not result in a business collecting data that qualifies as "Biometric information" within the BIPA. The BIPA defines biometric information as information based on an individual's “biometric identifier.”  A "biometric identifier" is a “retina or iris scan, fingerprint, voiceprint, or scan of hand or face geometry.” The Private Identity recognition algorithm does not transmit the biometric identifier from the data subject’s local device as the data is transformed into irreversible anonymous information before transmission. Accordingly, the BIPA would not be applicable to businesses utilizing this technology. 