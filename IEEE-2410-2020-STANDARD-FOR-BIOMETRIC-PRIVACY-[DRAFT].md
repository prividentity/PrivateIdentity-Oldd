# P2410-2020/D1 Draft Standard for Biometric Privacy 

## ABSTRACT 
The Standard for Biometric Privacy (SBP) provides private identity assertion. SBP enhances and extends the prior IEEE 2410-2019 Standard for Biometric Open Protocol by including formal governance for privacy and biometrics such that adherence guarantees the SBP system does not incur GDPR, CCPA, BIPA or HIPAA privacy obligations. Homomorphic encryption ensures the biometric payload is always one-way encrypted with no need for key management and guarantees privacy by ensuring plaintext biometrics are never received by the SBP server.  

The SBP implementation includes software running on a client device and on the SPB server.  Pluggable components are used to replace legacy functionality to allow rapid integration into existing operating environments. The SBP implementation allows the systems to meet security needs by using the application programming interface, whether the underlying system is a relational database management system or a search engine. The SBP implementation functionality offers a “point-and-cut” mechanism to add the appropriate security to the production systems as well as to the systems in development. The architecture is language neutral, allowing Representational State Transfer (REST), JavaScript Object Notation (JSON), and Secure Sockets Layer (SSL) or Transport Layer Security to provide the communication interface.

This document describes the essential methodology to SBP.

**Keywords**: biometrics, privacy, admin console, application, SBP admin, SBP cluster, SBP server, SBP IDS, client device IDS, Jena Rules, IDS cluster, IEEE 2410, liveness, original site admin, site admin, trusted adjudicated data, user, user device

## Important Notices and Disclaimers Concerning IEEE Standards Documents
Sponsor **Standards Development Board** of the **IEEE Communications Society**
and the **Technical Committee on COM/SDB** of the **IEEE Technical Activities Board**

**Approved:** <_Date Approved_>

**IEEE-SA Standards Board**
Copyright © 2020 by The Institute of Electrical and Electronics Engineers, Inc.
Three Park Avenue, New York, New York 10016-5997, USA.  All rights reserved.

This document is an unapproved draft of a proposed IEEE Standard. As such, this document is subject to change. USE AT YOUR OWN RISK! IEEE copyright statements SHALL NOT BE REMOVED from draft or approved IEEE Standards, or modified in any way. Because this is an unapproved draft, this document shall not be utilized for any conformance/compliance purposes. Permission is hereby granted for officers from each IEEE Standards Working Group or Committee to reproduce the draft document developed by that Working Group for purposes of international standardization consideration.  IEEE Standards Department shall be informed of the submission for consideration prior to any reproduction for international standardization consideration (stds.ipr@ieee.org). Prior to adoption of this document, in whole or in part, by another standards development organization, permission shall first be obtained from the IEEE Standards Department (stds.ipr@ieee.org). When requesting permission, IEEE Standards Department shall require a copy of the standard development organization's document highlighting the use of IEEE content. Other entities seeking permission to reproduce this document, in whole or in part, shall also obtain permission from the IEEE Standards Department.
IEEE Standards Department, 445 Hoes Lane, Piscataway, NJ 08854, USA. 

IEEE documents are made available for use subject to important notices and legal disclaimers. These notices and disclaimers, or a reference to this page, appear in all standards and may be found under the heading “Important Notice” or “Important Notices and Disclaimers Concerning IEEE Standards Documents.”

## Notice and Disclaimer of Liability Concerning the Use of IEEE Standards Documents
IEEE Standards documents (standards, recommended practices, and guides), both full-use and trial-use, are developed within IEEE Societies and the Standards Coordinating Committees of the IEEE Standards Association (“IEEE-SA”) Standards Board. IEEE (“the Institute”) develops its standards through a consensus development process, approved by the American National Standards Institute (“ANSI”), which brings together volunteers representing varied viewpoints and interests to achieve the final product. Volunteers are not necessarily members of the Institute and participate without compensation from IEEE. While IEEE administers the process and establishes rules to promote fairness in the consensus development process, IEEE does not independently evaluate, test, or verify the accuracy of any information or the soundness of any judgments contained in its standards.

IEEE does not warrant or represent the accuracy or content of the material contained in its standards, and expressly disclaims all warranties (express, implied and statutory) not included in this or any other document relating to the standard, including, but not limited to, the warranties of: merchantability; fitness for a particular purpose; non-infringement; and quality, accuracy, effectiveness, currency, or completeness of material. In addition, IEEE disclaims any and all conditions relating to: results; and workmanlike effort. IEEE Standards documents are supplied “AS IS” and “WITH ALL FAULTS.”

Use of an IEEE Standard is wholly voluntary. The existence of an IEEE Standard does not imply that there are no other ways to produce, test, measure, purchase, market, or provide other goods and services related to the scope of the IEEE Standard. Furthermore, the viewpoint expressed at the time a standard is approved and issued is subject to change brought about through developments in the state of the art and comments received from users of the standard. 
In publishing and making its standards available, IEEE is not suggesting or rendering professional or other services for, or on behalf of, any person or entity nor is IEEE undertaking to perform any duty owed by any other person or entity to another. Any person utilizing any IEEE Standards document, should rely upon his or her own independent judgment in the exercise of reasonable care in any given circumstances or, as appropriate, seek the advice of a competent professional in determining the appropriateness of a given IEEE Standard.

IN NO EVENT SHALL IEEE BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO: PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE PUBLICATION, USE OF, OR RELIANCE UPON ANY STANDARD, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE AND REGARDLESS OF WHETHER SUCH DAMAGE WAS FORESEEABLE.

**Translations**
The IEEE consensus development process involves the review of documents in English only. In the event that an IEEE Standard is translated, only the English version published by IEEE should be considered the approved IEEE Standard.

**Official statements**
A statement, written or oral, that is not processed in accordance with the IEEE-SA Standards Board Operations Manual shall not be considered or inferred to be the official position of IEEE or any of its committees and shall not be considered to be, or be relied upon as, a formal position of IEEE. At lectures, symposia, seminars, or educational courses, an individual presenting information on IEEE Standards shall make it clear that his or her views should be considered the personal views of that individual rather than the formal position of IEEE. 

**Comments on standards**
Comments for revision of IEEE Standards documents are welcome from any interested party, regardless of membership affiliation with IEEE. However, IEEE does not provide consulting information or advice pertaining to IEEE Standards documents. Suggestions for changes in documents should be in the form of a proposed change of text, together with appropriate supporting comments. Since IEEE Standards represent a consensus of concerned interests, it is important that any responses to comments and questions also receive the concurrence of a balance of interests. For this reason, IEEE and the members of its societies and Standards Coordinating Committees are not able to provide an instant response to comments or questions except in those cases where the matter has previously been addressed. For the same reason, IEEE does not respond to interpretation requests. Any person who would like to participate in revisions to an IEEE Standard is welcome to join the relevant IEEE working group.

Comments on standards should be submitted to the following address:
	Secretary, IEEE-SA Standards Board 
	445 Hoes Lane 
	Piscataway, NJ 08854 USA

**Laws and regulations**
Users of IEEE Standards documents should consult all applicable laws and regulations. Compliance with the provisions of any IEEE Standards document does not imply compliance to any applicable regulatory requirements.  Implementers of the standard are responsible for observing or referring to the applicable regulatory requirements. IEEE does not, by the publication of its standards, intend to urge action that is not in compliance with applicable laws, and these documents may not be construed as doing so.

**Copyrights**
IEEE draft and approved standards are copyrighted by IEEE under U.S. and international copyright laws. They are made available by IEEE and are adopted for a wide variety of both public and private uses.  These include both use, by reference, in laws and regulations, and use in private self-regulation, standardization, and the promotion of engineering practices and methods. By making these documents available for use and adoption by public authorities and private users, IEEE does not waive any rights in copyright to the documents.

**Photocopies** 
Subject to payment of the appropriate fee, IEEE shall grant users a limited, non-exclusive license to photocopy portions of any individual standard for company or organizational internal use or individual, non-commercial use only. To arrange for payment of licensing fees, please contact Copyright Clearance Center, Customer Service, 222 Rosewood Drive, Danvers, MA 01923 USA; +1 978 750 8400. Permission to photocopy portions of any individual standard for educational classroom use can also be obtained through the Copyright Clearance Center.

**Updating of IEEE Standards documents**
Users of IEEE Standards documents should be aware that these documents may be superseded at any time by the issuance of new editions or may be amended from time to time through the issuance of amendments, corrigenda, or errata. An official IEEE document at any point in time consists of the current edition of the document together with any amendments, corrigenda, or errata then in effect. 

Every IEEE Standard is subjected to review at least every ten years. When a document is more than ten years old and has not undergone a revision process, it is reasonable to conclude that its contents, although still of some value, do not wholly reflect the present state of the art. Users are cautioned to check to determine that they have the latest edition of any IEEE Standard.

In order to determine whether a given document is the current edition and whether it has been amended through the issuance of amendments, corrigenda, or errata, visit the IEEE-SA Website at http://ieeexplore.ieee.org/xpl/standards.jsp or contact IEEE at the address listed previously. For more information about the IEEE SA or IEEE’s standards development process, visit the IEEE-SA Website at http://standards.ieee.org.

**Errata** 
Errata, if any, for all IEEE Standards can be accessed on the IEEE-SA Website at the following URL: http://standards.ieee.org/findstds/errata/index.html. Users are encouraged to check this URL for errata periodically.

**Patents**
Attention is called to the possibility that implementation of this standard may require use of subject matter covered by patent rights. By publication of this standard, no position is taken by the IEEE with respect to the existence or validity of any patent rights in connection therewith. If a patent holder or patent applicant has filed a statement of assurance via an Accepted Letter of Assurance, then the statement is listed on the IEEE-SA Website at http://standards.ieee.org/about/sasb/patcom/patents.html. Letters of Assurance may indicate whether the Submitter is shalling or unshalling to grant licenses under patent rights without compensation or under reasonable rates, with reasonable terms and conditions that are demonstrably free of any unfair discrimination to applicants desiring to obtain such licenses.

Essential Patent Claims may exist for which a Letter of Assurance has not been received. The IEEE is not responsible for identifying Essential Patent Claims for which a license may be required, for conducting inquiries into the legal validity or scope of Patents Claims, or determining whether any licensing terms or conditions provided in connection with submission of a Letter of Assurance, if any, or in any licensing agreements are reasonable or non-discriminatory. Users of this standard are expressly advised that determination of the validity of any patent rights, and the risk of infringement of such rights, is entirely their own responsibility. Further information may be obtained from the IEEE Standards Association.

**Participants** <br>
At the time this draft standard was completed, the Biometrics Open Protocol Working Group had the following membership:<br>
Scott Streit, Chair<br>
Clayton Stewart, Vice Chair<br>
Mark Thompson<br>
Stephen Suffian<br>
Brian Streit <br>
Daniel Farinella<br>
Suleyman Muhammad<br>
Nathan Dent<br>
Steve Bailey<br>

The following members of the individual balloting committee voted on this standard. Balloters may have voted for approval, disapproval, or abstention.<br>
Susan Burgess<br>
John Callahan<br>
Keith Chow<br>
Thomas Coughlin<br>
Grazia D’Eelia<br>
Sourav Dutta<br>
Dan Friedman<br>
Randall Groves<br>
Marco Hernandez<br>
Werner Hoelzl<br>
Noriyuki Ikeuchi<br>
Akio Iso<br>
Piotr Karocki<br>
Bruce Kraemer<br>
Paul Lambert<br>
Shalliam Lumpkins<br>
Nick S. A. Nikjoo<br>
Paul Nikolich<br>
Benjamin Rolfe<br>
Osman Sakr<br>
Thomas Starai<br>
Scott Streit<br>
Walter Struppler<br>
Stephen Suffian<br>
Mitsutoshi Sugawara<br>
Michael Swearingen<br>
David Tepen<br>
John Vergis<br>
Hung-Yu Wei<br>
Forrest Wright<br>
Oren Yuen<br>
Daidi Zhong<br>

When the IEEE-SA Standards Board approved this standard on <Date Approved>, it had the following membership:<br>
John D. Kulick, Chair<br>
Jon Walter Rosdahl, Vice Chair<br>
Richard H. Hulett, Past Chair<br>
Konstantinos Karachalios, Secretary<br>
Masayuki Ariyoshi<br>
Ted Burse<br>
Stephen Dukes<br>
Jean-Philippe Faure<br>
J. Travis Griffith<br>
Gary Hoffman<br>
Dan Friedman<br>
Michael Janezic <br>
Joseph L. Koepfinger*<br>
David J. Law<br>
Hung Ling<br>
Andrew Myles<br>
T. W. Olsen<br>
Glenn Parsons<br>
Ronald C. Petersen<br>
Annette D. Reilly<br>
Stephen J. Shellhammer<br>
Adrian P. Stephens<br>
Yatin Trivedi<br>
Philip Winston<br>
Don Wright<br>
Yu Yuan<br>
Daidi Zhong<br>
*Member Emeritus<br>

## Introduction
One-way fully homomorphic encryption, the inclusion of identification as well as authentication and a greatly simplified Application Programming Interface (API) distinguish the architecture design of IEEE P2410-2020 from legacy Standard P2410-2017. The reinforced architecture of the Standard for Biometric Privacy (SBP) is well suited for implementation into enterprise systems for secure authentication via biometric modalities. 

SBP represents significant progress toward the goal of replacing passwords with non-repudiable identity and providing authentication with convenience. Biometrics include a wide range of information taken from a person, e.g., fingerprints, face, voice, iris pattern, etc. and his/her behavioral properties, e.g., gait, date, time, and location.  Recent increases in the processing power and sensor technologies allow digital signal processing (DSP) algorithms to run in the time needed for a real-time authentication (1-5 seconds, or similar to username and password login processing).  Unlike passwords, biometrics cannot be script-injected; however, biometric data is considered highly sensitive due to its personal nature and unique association with users.  Secure storage, transport and processing of biometric data is of paramount importance in the design and implementation of the SBP system.
The SBP solution itself is simple and biometric agnostic. While the old standard considered matching in the plain text space, the IEEE P2410-2020 brings a new level of consumer privacy assurance by keeping biometric data encrypted at rest, in transit and in use.  Biometric enrollment information (i.e. representation of fingerprint, voice, facial, and other biometric features) is represented by distance-measurable feature vectors.  These feature vectors allow all processing to occur in the encrypted space and ensure privacy by never processing, receiving or holding the plaintext biometric. The result is guaranteed privacy, a complete specification without key management functions, and a simple standard implementation that consists of only 3 API endpoints. 

With the increasing need to secure user access to their footprints of Personally Identifiable Information (PII) in the Internet (e.g. for financial and health records) and enterprise assets, the SBP server is designed to control communication with its clients via a two-way SSL/TLS homomorphic interface.  Users authenticate identity via the SBP platform before being granted access by an enterprise system that controls resources and assets. If authentication is successful, the user is authorized to access the resource or asset (i.e., they are "granted access").  Otherwise, they are denied access.  

## Draft Standard for Biometric Privacy
**IMPORTANT NOTICE:** IEEE Standards documents are not intended to ensure safety, security, health, or environmental protection, or ensure against interference with or from other devices or networks. Implementers of IEEE Standards documents are responsible for determining and complying with all appropriate safety, security, environmental, health, and interference protection practices and all applicable laws and regulations.

This IEEE document is made available for use subject to important notices and legal disclaimers. 
These notices and disclaimers appear in all publications containing this document and may 
be found under the heading “Important Notice” or “Important Notices and Disclaimers 
Concerning IEEE Documents.” They can also be obtained on request from IEEE or viewed at http://standards.ieee.org/IPR/disclaimers.html.

## 1. Overview

### 1.1 Scope

The Standard for Biometric Privacy (SBP) provides three API calls to support biometric identification and authentication including liveness. The SBP implementation allows the systems to meet security needs by using the application-programming interface (API). The SBP implementation need not know whether the underlying system is a machine learning model, a relational database management system (RDBMS) or a search engine. The SBP implementation functionality offers a “point-and-cut” mechanism to add the appropriate security to the production systems as well as to the systems in development.

SBP additionally includes the biometric identification which the industry frequently calls the ‘one to many’ case.  In the past, biometric identification was not considered because this requires a lookup against previously stored biometrics and this lookup required indexing and storing the biometric in plain text biometric identification.  This specification includes biometric identification by using biometric features vectors as input to the enroll endpoint, biometric feature vectors as input to the predict endpoint and either video or audio as input to the liveness endpoint.   

### 1.2  Purpose

This standard provides a biometric-agnostic security protocol for authentication, identification and liveness. 

### 1.3 Intended audience

The intended audience of this document includes security evaluators, system underwriters, developers, and systems engineers. The SBP is subject to changes and updates.

## 2.  Normative references
The following referenced documents are indispensable for the application of this document (i.e., since they shall be understood and used, each referenced document is cited in text and its relationship to this document is explained). For dated references, only the edition cited applies. For undated references, the latest edition of the referenced document (including any amendments or corrigenda) applies.

US Department of Defense (Mitre, 1985). Department of Defense Trusted Computer System Evaluation Criteria (“TCSEC”). Accessed 8 August 2020.  Available at: https://csrc.nist.gov/csrc/media/publications/conference-paper/1998/10/08/proceedings-of-the-21st-nissc-1998/documents/early-cs-papers/dod85.pdf

## 3. Definitions, acronyms, and abbreviations

### 3.1 Definitions
For the purposes of this document, the following terms and definitions apply. The IEEE Standards Dictionary Online should be consulted for terms not defined in this clause.
RESTful: Refers to Representational State Transfer (REST), which is a software architecture style.
Acronyms and abbreviations

1:M                     One-to-Many <br>
4F                      Four Fingers, a proprietary biometric technology<br>
5-tuple                 Five tuple data parameters  <br>
Account                 User account with limited privileges <br>
Admin                   Administrator<br>
AOP                     Aspect Oriented Programming<br>
API                     Application Programming Interface<br>
app                     A client application<br>
CPU                     Central Processing Unit<br>
CBV                     Current Biometric Vector<br>
CSRF                    Cross-Site Request Forgery<br>
ID                      Identifier<br>
IDS                     Intrusion Detection System<br>
IBV                     Initial Biometric Vector <br>
IP                      Internet Protocol<br>
JSON                    JavaScript object notation<br>
LDAP                    Lightweight Directory Access Protocol<br>
MAC                     Mandatory Access Control<br>
MCA                     Mobile Client Application<br>
NSA                     National Security Agency (U.S.)<br>
PII                     Personally Identifiable Information <br>
QR code                 Quick Response code<br>
RDBMS                   Relational Database Management System<br>
REST                    Representational State Transfer<br>
SBP                     Standard for Biometric Privacy <br>
SSL                     Secure Socket Layer<br>
TCSEC                   Trusted Computer System Evaluation Criteria<br>
TLS                     Transport Layer Security<br>
URL                     Uniform Resource Locator <br>
XNTP                    eXtended Network Time Protocol<br>
XOR                     “Exclusive OR” is a binary operation <br>

## 4.  Conformance
The SBP comprises the rules governing secure communication between a variety of client devices and the trusted server. This standard is based on the tested computer-based implementation of the Trusted Computer System Evaluation Criteria (TCSEC).

SBP conforms to the TCSEC, which is the U.S. Department of Defense standard that sets basic requirements for assessing the effectiveness of computer security controls built into a computer system. TCSEC was created by the National Computer Security Center, an arm of the National Security Agency (NSA) and is also frequently referred to as “Orange Book, section B1.” SBP also conforms to the US ODNI Intelligence Community Directive 503 “Protecting Sensitive Compartmented Information Within Information Systems,” and to the standards of the Multiple Independent Levels of Security/Safety (MILS) architecture.

## Security considerations
SBP largely considers the server side component of  an end-to-end biometric solution. This solution is recorded as IEEE Standard 2410-2015, IEEE Standard 2410-2016, IEEE Standard 2410-2019  and now the greatly simplified IEEE Standard 2410-2020 which describes all the components necessary for the server side of end to end biometric security. The standard enumerates requirements for the client component to comply with the Server Side Solution. The standard describes a set of new technologies including but not limited to liveness.  “Liveness” is a term that means ensuring the biometric is from a live source, such as a human being and not from an imitation such as a wax replica, a picture or a video.  

This technology shall be implemented on any public cloud, private cloud or on premise. The specification makes no assumptions of the “how” of a solution. The specification describes the “what” and the overall goals of the solution.

Users no longer have to remember their passwords and risk having their passwords end up in the wrong hands. SBP provides a framework for safety and convenience. Biometrics are part of us, unique to us and excellent for leveraging in a secure solution. SBP is an enterprise-grade solution that handles any size user space and requirements for fault tolerance and load balancing. 

Using multiple rounds of penetration tests, the IEEE vetting process, industry and client critiques, SBP has been validated. This mature and secure framework provides an end-to-end solution without the compromise of privacy.

### 5.1 Background
Security considerations include the security policies in place and unambiguously defined levels of security. One of the SBP’s main functions is to provide authentication instead of authorization in a way that the server does not retain the client information but rather recognizes one client from another. The key components of security considerations include identification and liveness.

This standard further enhances the security model to mitigate  recently uncovered vulnerabilities.  Security itself is a constant game of “cops” and “robbers”.  The more sophisticated the adversarial robbers become, the more powerful the security model or cop needs to be.  This standard raises the bar in all areas of biometric security with a diligent focus on authentication and privacy.  Additionally, we tackle the difficult problem of biometric identification with the maintenance of privacy.  

### 5.2 Identity assertion
The SBP implementation helps provide continuous protection to resources and assurance of the placement and viability of adjudication and other key features. Accountability is the mechanism that shall help provide a service-level guarantee of security. 

The SBP  implementation identity assertion helps confirm that named users are who they claim to be. The identity assertion implies reliance on human biometrics; however, the SBP is an interoperable standard and shall incorporate any identity asserter or a number of different asserters associated with the same named user. 

## 6. SBP Interoperability
The SBP implementation allows systems to meet security needs by using the API. The SBP implementation does not need to know whether the underlying system is a machine learning model, an RDBMS or a search engine. The SBP implementation functionality offers a “point-and-cut” mechanism to add the appropriate security to the production systems as well as to the systems in development. The architecture is language neutral, allowing REST, JSON, and SSL to provide the communication interface. 

A Client Application it is responsible for:
* Creation of the biometric feature vector. 	
* Making an API call to enroll.	
* Making an API call to predict.  	
* Making an API call for liveness.

The SBP server is responsible for:
* Saving PII data during the enrollment process for subsequent predict API calls. 
* Retrieving PII data to support the predict API call.  	
* Retrieving the probability that the liveness data and result match.

We have a set of processing rules listed as follows:
* We only transmit biometric data as ciphertext. 
* Ciphertext is embeddings taken from a pre-trained model, by the client.
* Client processing provides the embeddings by calling convenience routines.   

### 6.1 Enrollment
Enrollment occurs through the enroll API endpoint.  Enrollment takes in a finite amount of PII data and any number of distance measurable feature vectors.  Enrollment establishes the identity of the individual and links the PII data.  One embodiment of Enrollment shall use one to many neural networks to provide a client mechanism to retrieve Feature Vectors as well as a mechanism to support subsequent predict API calls.  In the case of biometrics, these feature vectors are composed of a select number of anthropometric points based on the format of input data collected.

### 6.2 Homomorphic Encryption
Current biometric techniques require the use of plaintext search for matching.  This requires the biometric be visible at some point in the search process. It would be beneficial to instead conduct matching on an encrypted dataset. Encryption is typically done using one-way encryption algorithms, meaning that given the encrypted data, there is no mechanism to get to the original data. Common one-way encryption algorithms are MD5 and SHA-512. However, these algorithms are not homomorphic, meaning that there is no way to compare the closeness of two samples of encrypted data, and thus no means to compare.  The inability to compare renders any form of classifying model in machine learning untenable.   

Homomorphic encryption is a form of encryption that allows computations to be carried out on ciphertext, thus generating an encrypted match result.  Matching in the encrypted space using a one-way encryption offers the highest level of privacy. With the payload of feature vectors one-way encrypted, there is no need to decrypt and no need for key management.  

A promising method of homomorphic encryption on biometric data is the use of autonomous or machine learning models to generate feature vectors. For black-box models, such as neural networks, these vectors shall not be used to recreate the initial input data and are therefore a form of one-way encryption. However, the vectors are distance measurable, so similarity between vectors shall be calculated. This process allows for biometric data to be homomorphically encrypted.

In regards to facial recognition performed with the geometric distance, when two face images are matched using a neural network, first each face is converted to a float vector, which in the case of Google’s FaceNet, is of size 128.  The representation of this float vector is arbitrary and cannot be reverse-engineered back to the original face. The matrix multiplication, from the neural network, becomes the vector of the face.  This vector is distance measurable and yet unrecognizable and cannot map back to an image.

![Figure 2 Distance Measurable Vector flow](https://github.com/openinfer/PrivateIdentity/blob/master/images/FHE%20Image%201.png)
Figure 2 - Distance Measurable Vector Flow

To compare the faces, the geometric distance of the two vectors is calculated. Two faces from the same person should have similar vectors, and faces of different people should be further apart in geometric space.

## 7. SBP API Overview
### 7.1 Format
All API names are in the RESTful JSON format.  All feature vectors have a type, such as “voice”, “face”, “fingerprint”, etc.
### 7.2 Developer API_Key
Individual developers need to apply for an API_Key for their applications that shall use SBP. This shall be done in the developer center. Once individual developers have their own API_Key, all of the API calls their applications make shall insert this API_Key as one of the parameters. The identity assertion platform shall verify the API_Key at that API level.  The use of an API key is not mandatory and implementers shall use a variety of implementation strategies or no API key whatsoever.   The examples show an API_KEY through the url property of key=.

## 8. API
### 8.1 Enroll
#### 8.1.1 Overview
To enroll a user, we take as input  the PII Data which is a set of tag/value pairs and the feature vectors used for training given as input under the “PII” and “features” fields respectively. Using a Global UUID a new identity is created in the persistent engine  corresponding to the PII provided.
#### 8.1.2 Request
The format of this API call is:  <br>

POST “/mfa/v1.1/enroll?key=<API_KEY>”<br>

Parameter:  Value<br>
Features: Type, Name, Feature Array. Type is voice, face or fingerprint.<br>

An Enroll API request example is as follows:<br>
```
{
    "features": [
          {“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
          {“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
          {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},
	   …
	   {}
     ]
}
```
#### 8.1.3 Response
The response of an Enroll request returns O as Success given data validation and database storage success.

## 8.2 Predict
### 8.2.1 Overview
Once enrolled a caller shall call the Predict API to perform an attempt to use the trained system to identify the individual subject based upon images provided in the call.

#### 8.2.2 Request
The format of this API call is: 
POST “/mfa/v1.1/predict?key=<API_KEY>”

Parameter: Value
Features: Type, Name, Feature Array.  Type is voice, face or fingerprint.

A Predict API request example is as follows:
```
{
    "features": [
        {“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
        {“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
        {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},
	   …
	   {}
        ]
}
```

#### 8.2.3 Response
The response of a Predict request, if meeting confidence thresholds, returns PII data in the following format:
```
{
    "uuid": "1008023"
    "message": "OK",
    "status": 0,
    "subject_id": 4,
    ]
}
```

### 8.3 Liveness
#### 8.3.1 Overview
To recognize liveness, a mechanism to affirm interaction with a live individual, we take in audio files along with their respective expected text. The API call returns a value related to the certainty that the audio samples match what is expected. Video is used through the same API call.   All input is in .wav format.  Liveness is a local client call, typically, but is supported on the server in the format listed below.  The best practice is for a local liveness call so that plaintext is not transmitted.  

#### 8.3.2 Request

The format of this API call is: 

```
POST “/node/liveness”
{
    “files”: “base64_audio_1”,
    “text”: “text_expected_1”,
    “name”: “voice_0.wav”,
    “localeCode”: “en-US”
}
```

#### 8.3.3 Response
The response of a liveness request Returns accuracy data as a ratio from 0 to 1, with a value of .9 denoting 90% accuracy.

```
{
    "recognized_text":"text_expected_1",
    "expected_text":"text_returned_1",
    "accuracy":0.6000000000000001,
    "message":"OK",
    "status":0
}
```

### 8.4 Delete Subject
#### 8.4.1 Overview
Delete the person from database

#### 8.4.2 Request
The format of this API call is: 

Browser URL:  “?action=deleteSubject&subject_id=<subjectId>”<br>

Python POST “/mfa/v1.1/delete_subject”<br>

```
{
    “subject_id”: 1
}
```

#### 8.4.3 Response 
The status will have an error code.

```
{
   “status”: 0
}
```

```
{
   “status”: 0
   “role_id” : <role_id>
   “message” : “Role Successfully added.”
}
```

```
{
   “status”: -2
   “message” : “Role exists in database”
}
```

## 9 PRIVATE CONSIDERATIONS
### 9.1 Background
The SBP privacy considerations section introduced into this version of IEEE P2410 specifications addresses the needs of auditors and compliance officers who would like to align and assess risk management frameworks for adoption of the IEEE 2410-2020 standard.

### 9.2  SBP Data Privacy Reference
The concept of keeping data encrypted at rest was envisioned in Trusted Computer System Evaluation Criteria [B6].  The TSCEC standard describes Object Reuse as “the reassignment to some subject of a medium (e.g., page frame, disk sector, magnetic tape) that contains one or more objects”.  Further, the standard proposed some forms of credible controls that would protect sensitive private data stored on the computer systems from accidental or unauthorized access or reading and destroying it: “No information, including encrypted representations of information, produced by a prior subject's actions is to be available to any subject that obtains access to an object that has been released back to the system” [B6].

The IEEE 1619 and 1619.1 Standard for Cryptographic Protection of Data on Block-Oriented Storage Devices also proposed data at rest encryption as the most secure method for sensitive data handling [B8]. The IEEE 1619 was developed over several years incorporating the efforts of many experts.

The Open Web Application Security Project (OWASP) manifests passivated data encryption as for the best security practices in the Cryptographic Storage Cheat Sheet: “An architectural decision shall be made to determine the appropriate method to protect data at rest.”[B9].

The IEEE P2410-2020 standard maintains privacy by only processing biometric data as a one-way fully homomorphically encrypted payload. 

The biometric is encrypted on the server and on the device at all times.

### 9.3 SBP Governance and Compliance
This section describes how the IEEE 2410-2020 standard addresses some of the privacy requirements of the most notable and current normative documents that govern biometric privacy, identification and Personally Identifiable Information (PII).
* NIST SP 800-122
* ISO/IEC 27001 
* EU DIRECTIVE 95/46/EC
* EBA/DP (PSD2)
* EU-U.S. PRIVACY SHIELD
* HIPAA
* GDPR
* CCPA
* BIPA
* ETHICAL PRINCIPLES FOR SBP

#### 9.3.1 NIST SP 800-122 
The Guide to Protecting the Confidentiality of Personally Identifiable Information (PII) NIST Special Publication 800-122 [B10], section 4.3, outlines the security controls as the critical factors in data governance. The IEEE 2410-2020 standard offers an automated solution for Access Enforcement (AC-3) control; for role-based needs and encryption (AC-3) access control.  The IEEE P2410-2020 guarantees the access enforcement rule for Remote Access (AC-17), Collaboration and Information Sharing (AC-21), Least Privilege (AC-6), Access Control for Mobile Devices (AC-19).

By design, every user in SBP has a one to many assigned security roles. The SBP Analytics enables automated controls of: Auditable Events (AU-2); Audit Review, Analysis, and Reporting (AU-6); Media Access (MP-2). The SBP server also supports the blacklisting of devices.

By implementing specific safeguards in its architecture, the IEEE P2410-2020 empowers the Transmission Confidentiality (SC-9) control, Protection of Information at Rest (SC-28), and Information System Monitoring (SI-4) using a 1-way encrypted payload that implements homomorphic encryption.  All biometric information is 1-way encrypted at rest and in transit  

#### 9.3.2 ISO/IEC 27001
The “Information technology -Security techniques - Information security management systems - Requirements” document also known as ISO/IEC 27001 [B11] defines as a necessity to control privacy and protection of Personally Identifiable Information (A.18.1.4), which IEEE 2410-2020 addresses by building in controls that are ready to comply with PII  legislation.  

#### 9.3.3 EU DIRECTIVE 95/46/EC DATA PROTECTION DIRECTIVE 
The IEEE 2410-2020 standard  addresses concerns of EU Directive 95/46/EC specified in Section V, Article 12,  and Section VII, Article 17. 

Article 12 of section V speaks of the data subject’s right to access his/her data [B12]. Based on the implementation, the owner of  SBP identity shall access all data relevant to his/her corresponding profile by accessing a corresponding URL, which would require an authentication. This feature automatically guarantees every data subject the right to obtain its PII from the controller.

The Article 16, section VII,  speaks of security of private data processing and narrates that appropriate technical measures responsible for data loss prevention, alteration, and unauthorized access should be involved in the data transmission over a network [B12]. 

The IEEE 2410-2020 standard  addresses this concern described in the EU Directive document by design, which utilizes two-way SSL/TLS in a communication between the server and client or between server and server.

#### 9.3.4 EBA/DP (PSD2)
The IEEE 2410-2020 standard addresses concerns shared in the EBA/PSD2 discussion paper [B13] that speaks of ensuring appropriate levels of security for electronic payment transactions. 

#### 9.3.5 EU-U.S. PRIVACY SHIELD
The IEEE 2410-2020 standard is consistent with the principles of Security, Data Integrity and Purpose Limitation, and Access, which are described in EU-U.S. Privacy Shield Framework Principles [B14]. 
The SBP server provides high-standard accommodations to protect Privately Identifiable Information from misuse or unauthorized access by implementing safeguards throughout the entire data processing cycle during  collection, storing, sharing, and transmitting data over the networks. (See the SBP Privacy Specific Safeguards section.)

### 9.4 SBP PII
The Guide to Protecting the Confidentiality of Personally Identifiable Information (PII) NIST Special Publication 800-122 April 2010 [B10] describes the examples of Personally Identifiable Information (PII) that heavily derives from a US federal law called The Privacy Act of 1974 [B18]. We use these examples as a reference point to Personally Identifiable Information.

The SBP server shall be separated from such PII and shall enforce a strict set of rules to operate an identity management service enterprise.  PII shall be outsourced to a LDAP, Active Directory or a similar Identity and Access Management (IAM) system.   

The organization that uses Personally identifiable information (PII) internally shall do so only for the authorized purpose(s) identified in the Privacy Act and/or in public notices.  

Organizations that share Personally identifiable information (PII) externally shall do so only for the authorized purposes identified by governing law or/and mandated by court order. 

Organization shall monitor, audit, and train staff on the authorized sharing of PII with third parties and on the consequences of unauthorized use or sharing of PII.

### 9.5 GDPR
The General Data Protection Regulation (GDPR) was adopted by the European Union in April 2016, with a key aim of making it easier for EU citizens to understand how their data is being used and to exert additional control over such data usage.   The GDPR contains the six data protection principles set out below. Organizations are “accountable” to demonstrate compliance with these principles when processing “personal data.” [3]

Where the GDPR applies, the data protection principles provide that personal data must be:

1. processed lawfully, fairly and in a transparent manner in relation to the data subject (i.e. the lawfulness, fairness and transparency principle);
1. collected for specified, explicit and legitimate purposes and not further processed in a manner that is incompatible with those purposes (i.e. the purpose limitation principle);
1. adequate, relevant and limited to what is necessary in relation to the purposes for which they are processed (i.e. the data minimization principle);
1. accurate and, where necessary, kept up to date (i.e. the accuracy principle);
1. kept in a form which permits identification of data subjects for no longer than is necessary for the purposes for which the personal data are processed (i.e. the storage limitation principle); and
1. processed in a manner that ensures appropriate security of the personal data, including protection against unauthorized or unlawful processing and against accidental loss, destruction or damage, using appropriate technical or organizational measures (i.e. the integrity and confidentiality principle).[4]

These principles must lie at the heart of each organization’s approach to processing personal data.  

SBP systems enable customers to advance the principles of the GDPR by transforming biometrics into anonymized FHE payloads. This eliminates the requirement for organizations to gather personal data to support robust security and advances the integrity and confidentiality principle and the data minimization principle of the GDPR [5]. Please see the chart below to view in greater detail how SBP systems enable customers to advance each of these principles. 

#### 9.5.2 We next consider biometric data.  Biometric data is required to be treated as a special category of personal data under the GDPR and is subject to increased compliance obligations. The GDPR defines biometric data as:

> “personal data resulting from specific technical processing relating to the physical, physiological or behavioral characteristics of a natural person, which allow or confirm the unique identification of that natural person, such as facial images or dactyloscopic (fingerprint) data” [9].  

The FHE payload with UUID does not qualify as biometric data.  In particular, the FHE payload does not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait.  

The UUID is a randomly generated, universally unique identifier that cannot be tied back to an individual/end user once assigned and in the possession of an entity utilizing SBP systems.

#### 9.5.3 FHE Payloads Are Not Subject to GDPR Obligations

The GDPR does not regulate the processing of anonymized information [10]. In Recital 26, the GDPR specifically refers to anonymization to exclude anonymized data from the scope of the data protection legislation, stating:

> “The principles of data protection should therefore not apply to anonymous information, namely information which does not relate to an identified or identifiable natural person or to personal data rendered anonymous in such a manner that the data subject is not or no longer identifiable. This Regulation does not therefore concern the processing of such anonymous information, including for statistical or research purposes” [11].     

We conclude that the FHE payloads and UUIDs are not subject to the requirements of GDPR because they constitute anonymized data and do not contain personal data or biometric data.

#### 9.5.4 GDPR Principles to SBP Traceability Matrix
||GDRP PRINCIPLES | SBP System Compliance Control|
|----|-----|-----|
|1| **Lawfulness, fairness and transparency principle** <br><br>Personal data is processed lawfully, fairly and in a transparent manner in relation to the data subject.| **Processes only anonymized data.** <br><br>SBP systems process only encrypted FHE payloads. This reduces the risk of the personal or biometric data being used for any improper, concealed or illegal purpose. <br><br>**Provides strong end-user authentication.** <br><br>The GDPR requires the organization to take reasonable steps to confirm that the person requesting access to their personal data is actually the rightful data subject. SBP systems help organizations advance and respond to requests from data subjects to exercise their rights under data protection law by providing strong end-user authentication to enable each data subject to control one’s data, to no longer consent to processing, to correct significant errors within the data and to request that data be erased (forgotten).  Strong end user authentication also allows organizations to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret.|
|2| **Purpose limitation principle** <br><br>Personal data is collected for specified, explicit and legitimate purposes and not further processed in a manner that is incompatible with those purposes. | **Processes only anonymized data** <br><br>SBP systems transmit, store and use only anonymized data. This promotes and accomplishes the regulatory goal of limiting the processing of personal data to only what is necessary in relation to the purposes for which they are processed.
|3| **Data minimization principle** Personal data is adequate, relevant and limited to what is necessary in relation to the purposes for which they are processed.| **Processes only anonymized data** SBP systems transmit, store and use encrypted FHE payloads. This promotes and accomplishes the regulatory goal of limiting the processing of personal data to only what is necessary in relation to the purposes for which they are processed.<br> Discards (deletes) all personal data <br> SBP systems discard all plaintext biometric data.  Only anonymized, encrypted FHE payloads are transmitted, stored or used to support the authentication process. This helps realize the regulatory goal of limiting the processing of personal data to only what is necessary in relation to the purposes for which they are processed.|
|4| **Accuracy principle** <br><br>Personal data is accurate and, where necessary, kept up to date. | **Processes no biometric or personal data** <br><br>The GDPR requires organizations to ensure that personal data are kept accurate and up to date. The regulation further states that personal data that are inaccurate must be deleted or rectified without delay. The system ensures accuracy by storing and processing no personal data. SBP systems only transmit, store, and use the anonymized data necessary for the authentication process. **Provides strong end-user authentication** <br><br>The GDPR requires the organization ensure that personal data is kept accurate and up to date. The regulation further states that personal data that are inaccurate must be deleted or rectified without any delay. SBP systems help organizations advance and respond to requests from data subjects to exercise their rights to correct data under data protection law by providing strong end-user authentication. This allows organizations to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret. A data subject’s personal data to be quickly and easily located, updated or deleted upon request. |
|5| **Storage limitation principle** <br><br>Personal data is kept in a form which permits identification of data subjects for no longer than is necessary for the purposes for which the personal data are processed. | **Processes only anonymized data** <br><br>SBP systems transmit, store and use only anonymized, encrypted FHE payloads and do not store personal data. This promotes and accomplishes the regulatory goal of storing personal data for no longer than is necessary. |
|6| **Integrity and confidentiality principle (security)** <br><br> Personal data is processed in a manner that ensures appropriate security of the personal data, including protection against unauthorized or unlawful processing … using appropriate technical or organizational measures. | **Provides strong end-user authentication** Strong end-user authentication is a key part of the security framework anticipated by the GDPR. In addition, Strong Customer Authentication (SCA) is required by PSD2 for “customer-initiated” online payments within Europe. Finally, ensuring network and information security constitutes a legitimate interest of an organization and is a valid legal basis for processing data. <br><br> SBP systems provide strong end-user authentication to help organizations secure personal data. This allows organizations to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret.
|7| **Accountability principle** <br><br>Requires the data controllers implement appropriate measures to protect personal data and be able to show that processing activities demonstrate compliance with the above principles. | **Does not subject organization to GDPR obligations** <br><br>The GDPR does not regulate the processing of anonymized information, including for statistical or research purposes. Indeed, the GDPR specifically refers to anonymization in Recital 26 to exclude anonymized data from the scope of data protection legislation. Accordingly, since SBP systems transmit, store and use only anonymized data, the data controller is thus not subject to GDPR data subject rights or special handling requirements for personal data or biometric data and is exempt from data breach notification requirements. |

[3]  Section 9.5 is excerpted with permission. Lentchner, Cassie and S. Farmer.  “Data Privacy and Compliance in the Age of Fully Homomorphic Encryption (FHE):  GDPR, CCPA and BIPA.”  Pillsbury Winthrop Shaw Pittman LLP.  August 1, 2020.  
[4]  Art. 5 GDPR Principles relating to processing of personal data.<br>
[5]  GDPR Article 5(1)(c)<br>
[6]  Recital 26 of the GDPR.   
[7]  Opinion 05/2014 on anonymisation techniques, 10 April 2014.<br>
[8]  GDPR Article 9, Recital 51.<br>
[9]  GDPR Article 4(14).<br>
[10] GDPR Recital 26.<br>
[11] GDPR Recital 26.<br>
[12]  Recitals 65 and 66 and in Article 17 of the GDPR <br>
[13]  Recitals 65 and 66 and in Article 17 of the GDPR <br>
[14]  Commission Delegated Regulation (EU) 2018/389 of 27 November 2017 supplementing Directive (EU) 2015/2366 of the European Parliament and of the Council with regard to regulatory technical standards for strong customer authentication and common and secure open standards of communication. [[Link](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv:OJ.L_.2018.069.01.0023.01.ENG&toc=OJ:L:2018:069:TOC)] <br>
[15]  Recitals 65 and 66 and in Article 17 of the GDPR<br>
[16]  GDPR Recital 26. <br>

### 9.6 CCPA
The CCPA (California Civil Code §§ 1798.100 to 1798.199) is currently the most comprehensive privacy legislation in the United States. The CCPA is similar to the GDPR in that it grants California residents robust data privacy rights and control over their personal information, including a subset of the elements of the GDPR’s lawfulness, fairness and transparency principle, data minimization principle, and integrity and confidentiality (security) principle [17].

The CCPA grants California residents rights with respect to the collection of their personal information, including the right to be forgotten (deletion of information), the right to opt-out of the sale of their personal information, and the right to know what information a business collects about them.  SBP systems advance the individual rights of California residents with respect to: (a) the collection of their personal information by transmitting, storing and using only deidentified data, and (b) providing strong end-user authentication that allows businesses to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret.
The CCPA’s broad definition of personal information includes any plaintext data or pseudonymized data that remains capable of being associated with a particular consumer or household [18]. The CCPA does not restrict a business’s ability to collect, use, retain, sell, or disclose consumer information that is “deidentified” (anonymized). SBP systems help advance the CCPA’s data minimization goals by transmitting, storing and using (processing) only deidentified data and deleting all personal information immediately after it is transformed into FHE payloads. 

The CCPA maintains that a business has, “[a] duty to implement and maintain reasonable security procedures and practices.” This security provision includes a proportionality element providing that it is the duty of the business to maintain reasonable security procedures and practices, “appropriate to the nature of the information.” SBP systems aid a business in advancing this goal and responding to requests from subjects seeking to exercise their rights under the CCPA by providing strong end-user authentication that allows organizations to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret.  Please see the chart below to view in greater detail how SBP systems enable customers to advance each of these principles.

#### 9.6.1 FHE Payloads Contain Deidentified Information

The CCPA defines and regulates “personal information” as “information that identifies, relates to, describes, is capable of being associated with, or could reasonably be linked, directly or indirectly, with a particular consumer or household.” SBP systems fully realize the CCPA’s legislative goals by transforming personal information into FHE payloads and UUIDs that are treated as “deidentified” data under the CCPA. 

As discussed in detail above, SBP systems only transmit, store or use deidentified (anonymized) data. Additionally, SBP systems do not transmit, store or use any other personal data or biometric data, machine or device identifications, metadata, or any other identifying information. 

#### 9.6.2 FHE Payloads Do Not Contain Biometric Information
The CCPA defines biometric information as follows. 

> “…an individual’s physiological, biological or behavioral characteristics, including an individual’s DNA, that can be used, singly or in combination with each other or with other identifying data, to establish individual identity. Biometric information includes, but is not limited to, imagery of the iris, retina, fingerprint, face, hand, palm, vein patterns, and voice recordings, from which an identifier template, such as a faceprint, a minutiae template, or a voiceprint, can be extracted, and keystroke patterns or rhythms, gait patterns or rhythms, and sleep, health, or exercise data that contain identifying information.” [19]

The encrypted FHE payloads and UUIDs created by SBP systems do not qualify as biometric data under the CCPA. These FHE payloads and UUIDs contain no biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait. 

Accordingly, the encrypted FHE payloads and UUIDs should not be treated as biometric information under the CCPA. 

#### 9.6.3 FHE Payloads Are Not Subject to CCPA Obligations
The CCPA states that businesses processing deidentified data are not obligated to provide or delete information in response to a consumer request or to re-identify individual data to verify a consumer request. Specifically, the final text of the California Consumer Privacy Act Regulations at § 999.323(f) provides that, “If a business maintains consumer information that is deidentified, a business is not obligated to provide or delete this information in response to a consumer request or to re-identify individual data to verify a consumer request.”
In addition, the CCPA Regulations at § 1798.140 further excludes deidentified information from the scope of the legislation.  

> ““Deidentification” means information that cannot reasonably identify, relate to, describe, be capable of being associated with, or be linked, directly or indirectly to a particular consumer, provided that a business that uses deidentified information [has implemented technical and process safeguards that prohibit reidentification of the consumer, has implemented processes to prevent inadvertent release of deidentified information, and makes no attempt to reidentify the information.” [20]

Finally, in the same section, CCPA § 1798.145(a)(5) further provides that nothing in the CCPA restricts a business’s ability to “collect, use, retain, sell, or disclose consumer information that is deidentified or in the aggregate.” [21] 

As previously described, the FHE payloads and UUIDs contain only deidentified data. Therefore, the consumer rights provided under the CCPA thus fall away with respect to this deidentified information and businesses that utilize this system do not incur CCPA obligations. 

#### 9.6.4  CCPA Requirements to SBP Traceability Matrix
||CCPA REQUIREMENTS | SBP System Compliance Control|
|----|-----|-----|
|1| **CCPA REQUIREMENTS** <br>Right to access data<br>Right to be forgotten<br>Right to opt-out of sale of information <br> Notices to data subjects | **Processes only deidentified data** <br><br> SBP systems transmit, store and use only deidentified data.  This reduces the risk of personal information or biometric information being used for any improper purpose and allows a customer’s business to utilize biometric identification without subjecting the business to the CCPA obligations. CCPA provides that businesses processing deidentified data are not obligated to provide or delete this information in response to a consumer request or to re-identify individual data to verify a consumer request.  Specifically, Subsection 999.323(f) of the final text of the California Consumer Privacy Act Regulations (the “CCPA Regulations”), provides that, “If a business maintains consumer information that is deidentified, a business is not obligated to provide or delete this information in response to a consumer request or to re-identify individual data to verify a consumer request.” The consumer rights provided under the CCPA fall away with respect to the deidentified, encrypted FHE payload produced by SBP systems. <br><br> **Provides strong end-user authentication.** <br><br>The CCPA’s security provision requires that organizations have a, “duty to implement and maintain reasonable security procedures and practices.” The CCPA’s security provisions include a proportionality element providing that it is the duty of the business to maintain reasonable security procedures and practices, “appropriate to the nature of the information.” SBP systems help organizations advance and respond to requests from subjects seeking to exercise their rights under CCPA by providing strong end-user authentication. <br><br>Strong end-user authentication is also key to quickly providing each data subject with the ability to control and access one’s data, to opt-out of sale of information, to display notices, and to request that data be erased (forgotten).  SBP systems allow organizations to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret.|
|2| **CCPA REQUIREMENTS** <br>Pseudonymization<br>Deidentification | **Processes only deidentified data** <br><br>SBP systems transmit, store and use only deidentified data. This promotes and accomplishes the regulatory goal of limiting the processing of personal information to only what is necessary.  According to CCPA regulations, deidentification means information that cannot reasonably identify, relate to, describe, be capable of being associated with, or be linked, directly or indirectly to a particular consumer (§1798.140). <br><br>Discards (deletes) all personal data <br><br>SBP systems discard all biometric information.  Only anonymized data is transmitted, stored or used to support the authentication process. This realizes the regulatory goal of limiting the processing of personal information to only what is necessary.|
|3| **CCPA REQUIREMENTS** <br>Appropriate data security required | **Provides strong end-user authentication.** The CCPA’s security provision requires that businesses have, “[a] duty to implement and maintain reasonable security procedures and practices.” The CCPA’s security provisions include a proportionality element providing that it is the duty of the business to maintain reasonable security procedures and practices, “appropriate to the nature of the information.” SBP systems help organizations advance and respond to requests from subjects seeking to exercise their rights under CCPA by providing strong end-user authentication. <br><br>Strong end-user authentication is also key to quickly providing each data subject with the ability to control and access one’s data, to opt-out of sale of information, to display notices, and to request that data be erased (forgotten).  SBP systems allow organizations to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret. |

[17]  Section 9.6 is excerpted with permission. Lentchner, Cassie and S. Farmer.  “Data Privacy and Compliance in the Age of Fully Homomorphic Encryption (FHE):  GDPR, CCPA and BIPA.”  Pillsbury Winthrop Shaw Pittman LLP.  August 1, 2020.  
[18]  CCPA 1798.140(o)(1). <br>
[19]  CCPA 1798.140(b).<br>
[20]  CCPA 1798.140(h).<br>
[21]  CCPA § 1798.145(a)(5).<br> 

### 9.7 BIPA
The Illinois Biometric Information Privacy Act 740 ILCS 14 (“BIPA”) is the most stringent biometric privacy law in the U.S. The BIPA applies to both biometric identifiers and biometric information.  It requires covered businesses to inform consumers in writing that biometric identifiers or biometric information is collected and stored, of the purpose and length of time of biometric information storage and use, and to secure written consent from consumers. BIPA also prohibits covered businesses from profiting from biometric data, permits only a limited right to disclose the data, mandates protection obligations and retention guidelines, and creates a private right of action for any individuals harmed by violators of BIPA.[22]

BIPA applies to both biometric identifiers and biometric information. Under BIPA, a “biometric identifier” includes specific types of information including fingerprint, voiceprint, retina/iris scan, scans or records of hand or face geometry [23]. Biometric information includes “any information, regardless of how it is captured, converted, stored, or shared, based on an individual’s biometric identifier used to identify an individual.” [24] Illinois courts have specifically found that face-scan measurements (i.e. a biometric template) derived from user-uploaded photos qualify as “biometric information” under BIPA [25].  

BIPA grants residents of Illinois rights with respect to the collection of their biometric identifiers or biometric data.  Under BIPA, notices require private entities to inform consumers that: (1) biometric identifier or biometric information is being collected and stored; and (2) “[the] specific purpose and length of term for which a biometric identifier or biometric information is being collected, stored, and used.”  In addition, BIPA requires affirmative consent for virtually any data collection in all circumstances for both commercial and non-commercial purposes.  Please see the chart below to view in greater detail how SBP systems enable customers to advance these principles.

#### 9.7.1 FHE Payloads Do Not Contain Biometric Identifiers or Biometric Information 
Biometric identifiers and biometric information under the BIPA are subject to increased compliance obligations. The biometric identifier under the BIPA includes specific types of information including fingerprint, voiceprint, retina/iris scan, scans or records of hand or face geometry.[26] And, the biometric information under the BIPA includes, “any information, regardless of how it is captured, converted, stored, or shared, based on an individual’s biometric identifier used to identify an individual.” Illinois courts have further stated in Rivera v. Google, Inc. that face-scan measurements (i.e. a biometric template[27]) derived from user-uploaded photos qualify as “biometric information” under BIPA. [28]   

As discussed above in Section 9.5.1 and 9.6.1, SBP systems advance the rights of Illinois residents with respect to the collection of their biometric identifiers or biometric information by only transmitting, storing or using anonymized data. To accomplish this, the system grants each end user a license to run application software on the user’s local device. Using this application, the user collects his/her own biometric data. This data is then transformed (encrypted) by a one-way cryptographic hash function on the local device and becomes FHE payloads. FHE payloads are globally unique positional arrays of 128 floating-point numbers that do not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral traits. 

Accordingly, SBP systems only transmit, store or use deidentified data and no biometric identifiers or biometric information. Under the plain language of this section and the Illinois state court interpretation, we find the encrypted FHE payload should not be treated as biometric identifiers or biometric information. 

#### 9.7.2 FHE Payloads Do Not Incur BIPA Obligations
The BIPA obligations apply only to biometric information. As discussed immediately above in Section 5.1, SBP systems do not contain biometric information or biometric identifiers. 

Accordingly, an organization using SBP systems are not collecting or storing biometric information and, with respect to this system, eliminates the requirement to comply with BIPA obligations including the consent requirements and the requirement for an organization to protect and store biometric data at least to the same degree it protects other confidential or sensitive information. 

#### 9.7.3  BIPA Requirements to SBP Traceability Matrix
||BIPA REQUIREMENTS | SBP System Compliance Control|
|----|-----|-----|
|1| **BIPA REQUIREMENTS** <br> Prohibits private entities from profiting from biometric data. <br>Prohibits disclosure or distribute of biometric data without consent <br>The disclosure being required to complete a transaction that the customer initiated<br><br> (Lawfulness, fairness and transparency principle) | **Processes no biometric identifier or biometric data** <br><br>SBP systems transmit, store and use only encrypted FHE payloads. This reduces the risk of a biometric identifier or biometric data from being used for any improper purpose and allows a private entity to utilize biometric identification or biometric data without subjecting the entity to the BIPA obligations. BIPA provides that a “biometric identifier” [30] is “based on” a “retina or iris scan, fingerprint, voiceprint, or scan of hand or face geometry.” [31] SBP systems, on the other hand, create encrypted FHE payloads that are deidentified or anonymized data (see discussion (see above discussions at Section 3.2 and 4.2). These resulting encrypted FHE payloads are not based on any biometric feature, measurement or other physical or biological characteristic. Accordingly, the BIPA requirements are not applicable to encrypted FHE payloads and the consumer rights provided under the BIPA fall away with respect to the encrypted FHE payload produced by SBP systems.<br><br> **Provides strong end-user authentication **<br><br> The BIPA establishes an obligation for private entities to protect and store biometric identifiers or biometric data at least to the same degree as it protects other confidential or sensitive information. The BIPA (740 ILCS 14/15(e)(2)) maintains that a private entity shall protect biometric identifiers or biometric data,  “In the same (or a more protective) way that the employer stores, transmits, and protects other confidential and sensitive information.”  As such, SBP systems provide strong end-user authentication to help organizations secure personal data. Additionally, it allows organizations to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret. |
|2| **BIPA REQUIREMENTS** <br>  Inform consumers in writing that biometric identifiers or biometric information is being collected or stored. <br>Inform the consumer in writing of the purpose and length of time the biometric information will be stored or used. <br>Secure written consent from the consumer.<br><br>(Purpose limitation principle) | **Processes no biometric identifier or biometric data** <br><br>SBP systems process (transmit, store and use) only encrypted FHE payloads. This reduces the risk of a biometric identifier or biometric data from being used for any improper purpose and allows a private entity to utilize biometric identification or biometric data without subjecting the entity to the BIPA obligations. BIPA provides that a “biometric identifier” [32] is “based on” a “retina or iris scan, fingerprint, voiceprint, or scan of hand or face geometry.” [33] SBP systems, on the other hand, create encrypted FHE payloads that are deidentified or anonymized data (see discussion above at Section 9.5 and 9.6). These resulting encrypted FHE payloads are not based on any biometric feature, measurement or other physical or biological characteristic. Accordingly, the BIPA requirements are not applicable to encrypted FHE payloads and the consumer rights provided under the BIPA fall away with respect to the encrypted FHE payload produced by SBP systems.|
|3| **BIPA REQUIREMENTS** <br>Written policy that establishes a retention schedule<br>Guidelines for destroying biometric information<br>3-year limitation<br><br>(Storage limitation principle) | <br><br>SBP systems process (transmit, store and use) only encrypted FHE payloads. This reduces the risk of a biometric identifier or biometric data from being used for any improper purpose and allows a private entity to utilize biometric identification or biometric data without subjecting the entity to the BIPA obligations. BIPA provides that a “biometric identifier” [32] is “based on” a “retina or iris scan, fingerprint, voiceprint, or scan of hand or face geometry.” [34] SBP systems, on the other hand, create encrypted FHE payloads that are deidentified or anonymized data (see discussion above at Section 9.5 and 9.6). These resulting encrypted FHE payloads are not based on any biometric feature, measurement or other physical or biological characteristic. Accordingly, the BIPA requirements are not applicable to encrypted FHE payloads and the consumer rights provided under the BIPA fall away with respect to the encrypted FHE payload produced by SBP systems.|
|4| **BIPA REQUIREMENTS** <br>Mandates protection (security) obligations and retention guidelines <br><br>(Integrity and confidentiality principle) | **Provides strong end-user authentication** <br><br>The BIPA establishes an obligation for private entities to protect and store biometric identifiers or biometric data at least to the same degree as it protects other confidential or sensitive information. The BIPA (740 ILCS 14/15(e)(2)) maintains that a private entity shall protect biometric identifiers or biometric data,  “In the same (or a more protective) way that the employer stores, transmits, and protects other confidential and sensitive information.”  As such, SBP systems provide strong end-user authentication to help organizations secure personal data. Additionally, it allows organizations to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret.
|5| **BIPA REQUIREMENTS** <br> <br>Private entities are to adhere to their guidelines.<br>Creates a private right of action for individuals harmed by violators of BIPA. <br><br>(Accountability principle) | **Processes no biometric identifier or biometric data** <br><br>SBP systems process (transmit, store and use) only encrypted FHE payloads. This reduces the risk of a biometric identifier or biometric data from being used for any improper purpose and allows a private entity to utilize biometric identification or biometric data without subjecting the entity to the BIPA obligations. BIPA provides that a “biometric identifier” [32] is “based on” a “retina or iris scan, fingerprint, voiceprint, or scan of hand or face geometry.” [33] SBP systems, on the other hand, create encrypted FHE payloads that are deidentified or anonymized data (see discussion above at Section 9.5 and 9.6). These resulting encrypted FHE payloads are not based on any biometric feature, measurement or other physical or biological characteristic. Accordingly, the BIPA requirements are not applicable to encrypted FHE payloads and the consumer rights provided under the BIPA fall away with respect to the encrypted FHE payload produced by SBP systems.<br><br> **Does not subject entity to BIPA obligations** <br><br>The BIPA only regulates the processing of biometric identifiers or biometric data. Under the BIPA, a “biometric identifier” includes specific types of information including fingerprint, voiceprint, retina/iris scan, scans or records of hand or face geometry. Additionally, Illinois courts have specifically stated that face-scan measurements (i.e. a biometric template) derived from user-uploaded photos qualify as “biometric information” under IL BIPA. [38] SBP systems transmit, store and use only encrypted FHE payloads (anonymized data).  These encrypted FHE payloads are no longer based on any biometric feature, measurement or other physical or biological characteristic. Accordingly, the BIPA requirements are not applicable to FHE transformed data. |

[22] Section 9.7 is excerpted with permission. Lentchner, Cassie and S. Farmer.  “Data Privacy and Compliance in the Age of Fully Homomorphic Encryption (FHE):  GDPR, CCPA and BIPA.”  Pillsbury Winthrop Shaw Pittman LLP.  August 1, 2020.  
[23]  740 ILCS 14/10.<br>
[24]  740 ILCS 14/10.<br>
[25]  _Rivera v. Google, Inc._, 238 F. Supp. 3d 1088 (N.D. Ill. 2017).<br>
[26]  740 ILCS 14/10.<br>
[27]  Traditional biometric recognition systems involve the use and storage of plaintext biometrics through which a template or image with the features extracted from an original biometric is stored and used during subsequent authentication attempts to match features. The storage or use of plaintext biometrics presents data privacy risks through risk of loss of the biometric information.  Even where the data is stored in a decentralized fashion or divided form, it must be decrypted to plaintext to support the match operation and thus has inherent privacy risks and are covered by several privacy laws.
[28] _Rivera v. Google, Inc._, 238 F. Supp. 3d 1088 (N.D. Ill. 2017).<br>
[29]  BIPA (740 ILCS 14/15(e)(2))
[30]  BIPA, 740 ILCS 14/10. <br>
[31]  BIPA, 740 ILCS 14/10. <br>
[32]  BIPA, 740 ILCS 14/10. <br>
[33]  BIPA, 740 ILCS 14/10. <br>
[34]  BIPA, 740 ILCS 14/10. <br>
[35]  BIPA, 740 ILCS 14/10. <br>
[36]  BIPA, 740 ILCS 14/10. <br>
[37]  BIPA, 740 ILCS 14/10. <br>
[38] _Rivera v. Google, Inc._, 238 F. Supp. 3d 1088 (N.D. Ill. 2017).<br>

### 9.8 HIPAA (Public Law 104-191)
The Health Insurance Portability and Accountability Act of 1996 (HIPAA) required the Secretary of the U.S. Department of Health and Human Services (HHS) to develop regulations protecting the privacy and security of certain health information. [B28] To fulfill this requirement, HHS published what are commonly known as the HIPAA Privacy Rule and the HIPAA Security Rule. The Privacy Rule, or Standards for Privacy of Individually Identifiable Health Information, established a standard for the protection of certain health information in the United States. The Security Standards for the Protection of Electronic Protected Health Information (the Security Rule) established a national set of security standards for protecting certain health information that is held or transferred in electronic form in the United States. 

The Security Rule operationalized the protections contained in the Privacy Rule by addressing the technical and non-technical safeguards that organizations called “covered entities” must put in place to secure individuals’ “electronic protected health information” (e-PHI). Within HHS, the Office for Civil Rights (OCR) enforces the Privacy and Security Rules with voluntary compliance activities and civil money penalties.

#### 9.8.1 HIPAA Privacy Rule
The HIPAA Privacy Rule protects most “individually identifiable health information” held or transmitted by a covered entity or its business associate, in any form or medium, whether electronic, on paper, or oral. The Privacy Rule calls this information protected health information (PHI). Protected health information is information, including demographic information, which relates to:
* the individual’s past, present, or future physical or mental health or condition,
* the provision of health care to the individual, or
* the past, present, or future payment for the provision of health care to the individual, and that identifies the individual or for which there is a reasonable basis to believe can be used to identify the individual. Protected health information includes many common identifiers (e.g., name, address, birth date, Social Security Number) when they can be associated with the health information listed above. 

#### 9.8.2 HIPAA Privacy Rule General Applicability
In general, the protections of the Privacy Rule apply to information held by covered entities and their business associates.  HIPAA defines a “covered entity” as 1) a health care provider that conducts certain standard administrative and financial transactions in electronic form; 2) a health care clearinghouse; or 3) a health plan.  A “business associate” is defined as a person or entity (other than a member of the covered entity’s workforce) that performs certain functions or activities on behalf of, or provides certain services to, a covered entity that involves the use or disclosure of protected health information. A covered entity may use a business associate to de-identify PHI on its behalf only to the extent such activity is authorized by their business associate agreement.  However, persons or organizations are not considered business associates if their functions or services do not involve the use or disclosure of protected health information, and where any access to protected health information by such persons would be incidental, if at all. A covered entity can be the business associate of another covered entity. 

In considering the applicability of the HIPAA Privacy Rule to the SBP, we consider the aspects of the SBP alone.

#### 9.8.3 HIPAA Security Rule
Today, providers are using clinical applications such as computerized physician order entry (CPOE) systems, electronic health records (EHR), and radiology, pharmacy, and laboratory systems. Health plans are providing access to claims and care management, as well as member self-service applications. While this means that the medical workforce can be more mobile and efficient, the rise in the adoption rate of these technologies increases the potential security risks.  The Security Rule protects a subset of information covered by the Privacy Rule, which is all individually identifiable health information a covered entity creates, receives, maintains or transmits in electronic form. The Security Rule calls this information “electronic protected health information” (e-PHI). The Security Rule does not apply to PHI transmitted orally or in writing. 

#### 9.8.4 HIPAA Security Rule General Applicability
The Security Rule applies to health plans, health care clearinghouses, and to any health care provider who transmits health information in electronic form in connection with a transaction for which the Secretary of HHS has adopted standards under HIPAA (the “covered entities”) and to their business associates.  The Security Rule requires covered entities to maintain reasonable and appropriate administrative, technical, and physical safeguards for protecting e-PHI.

Specifically, covered entities must:
* Ensure the confidentiality, integrity, and availability of all e-PHI they create, receive, maintain or transmit;
* Identify and protect against reasonably anticipated threats to the security or integrity of the information;
* Protect against reasonably anticipated, impermissible uses or disclosures; and
* Ensure compliance by their workforce.

In considering the applicability of the HIPAA Security Rule to the SBP, we consider the aspects of the SBP alone. 

#### 9.8.5 FHE Payloads Do Not Contain Individually Identifiable Health Information
The HIPAA defines and protects Protected Health Information, which is individually identifiable health information. SBP systems fully realize HIPAA’s goals by transforming personal information into FHE payloads and UUIDs that are “deidentified” data as we have previously established. 

To further evaluate the applicability of the HIPAA rules to the FHE payloads and UUIDs, we consider whether these are individually identifiable health information by applying the following criteria:
* Do the FHE payloads or UUIDs contain any identifiers or other data that could identify the individual or device to whom the data relates?
* Do the FHE payloads or UUIDs contain any health information, health-related information, healthcare provider information, or healthcare event-related information?
* Is there any data in the organization’s possession that could be combined with the FHE payloads or UUIDs to identify the individual or device to whom the data relates?
* Are the FHE payloads or UUIDs reversible?
* Can the FHE payloads or UUIDs be linked to an individual?
The answer is “no” to each for reasons set out previously.  

As discussed in detail in previous sections, SBP systems only transmit, store or use deidentified (anonymized) data. Additionally, SBP systems do not transmit, store or use any other personal data,  biometric data, health data, health-related data, machine or device identifications, metadata, or any other identifying information. In addition, the FHE payload or UUIDs do not contain any information useful for diagnostic purposes. 

Therefore the SBP systems (inclusive of FHE payloads and UUIDs) are not subject to the requirements of the Privacy Rule or the Security Rule under HIPAA because they do not contain personal data, biometric data, or health information.  Furthermore, the FHE payloads and UUIDs are universally unique and cannot be tied back to an individual/end user once assigned and in the possession of an entity utilizing SBP systems.

### 9.9 Compliance, Auditing & Record Keeping
Data controllers and data processors must be able to prove that their organization is up to speed on how to comply with the various regulations covered in Section 9. To do this, data controllers should regularly audit their own privacy protection practices and keep stringent records of all data that is held, the processing of that data, details of the transfer of data to other countries, and details of activities relating to personal data using Identity and Access Management (IAM).  This is a procedural requirement that technology helps occur.  Protected audit trails, logs and the like should be made available to aid compliance.  

## 10 ETHICAL PRINCIPLES 

SBP recognizes privacy as a fundamental human right and requires adherence with the ethical principles enumerated below. SBP recognizes local privacy laws and requires every individual person to be able to control his/her privacy with easy-to-use tools and clear choices. SBP forbids sale of identity data and use of identity to target ads without consent. SBP forbids participation or support of surveillance and similar activities that risk loss of privacy.  [39]

### 10.1 FAIRNESS 

Fairness in biometric recognition is an important problem with significant potential for societal impact. Entities shall minimize misidentification and treat all individuals fairly  through software quality and engineering  

#### 10.1.1 ASSESS DATA & TOOLS 

Entities shall develop and use processes and tools to systematically assess the data used for training, testing and benchmarking recognition technology to ensure appropriate representativeness and quality. Entities shall create appropriate bias assessment tools to analyze the operation of recognition technology, and use the output of those tools to improve models over time.

#### 10.1.2 ACTIONS TO MINIMIZE BIAS 

Entities must assess the potential for bias that may arise in each specific scenario by testing recognition technology and determining how to minimize the potential for unfair bias in scenarios in which they are intended for use prior to deploying. 

### 10.2 TRANSPARENCY 
Entities must document and clearly communicate illustrative examples of appropriate as well as inappropriate or premature uses of its recognition technology in order to help balance security and civil rights concerns.  

Entity’s systems available as an online service shall include an API or other technical capability to enable third parties that are legitimately engaged in independent testing to conduct reasonable evaluations of the SBP recognition technology for accuracy and unfair bias.

### 10.3 ACCOUNTABILITY AND MEANINGFUL HUMAN REVIEW
Full biometric privacy through homomorphic encryption makes the current in-band human review practice (also known as “humans-in-the-loop” or meaningful human review) of automated recognition results using plaintext images obsolete.  Indeed, the plaintext images required for human review are always encrypted and now unavailable for human or machine inspection.  

When making decisions for what the law deems to be “consequential use cases” that affect consumers, entities must therefore make meaningful out-of-band human review of recognition results available to users by establishing communication and remediation channel(s) to ensure that individuals impacted by the recognition technology can surface their concerns and have them addressed. Examples of out-of-band human review include appeals process(es) or committee(s).

Examples of “consequential use cases” include systems where decisions may create a risk of bodily or emotional harm to a user, a user’s employment prospects or ability to access financial services may be adversely affected, there may be implications on human or fundamental rights, a user’s personal freedom or privacy may be impinged, or the potential risk of harm or adverse consequences associated with errors are sufficiently high.

### 10.4 NON-DISCRIMINATION
Entities shall not use recognition algorithms to engage in unlawful discrimination based on actual or perceived race, ethnicity, religion, political views, national origin, disability, gender, gender identity, sexual orientation or any other characteristic protected by applicable anti-discrimination laws. 

### 10.5 USER CONSENT 
Entities shall provide conspicuous notice to, and secure consent from, individuals before capturing data for use with facial recognition technology.

### 10.6 LAWFUL SURVEILLANCE
Entities shall safeguard democratic freedoms in surveillance scenarios and not deploy recognition technologies  in scenarios that put these freedoms at risk. Entities shall not deploy recognition technology in surveillance scenarios where there are inadequate safeguards to protect individual freedoms and human rights. 

Law enforcement entities shall seek an appropriate balance between the legitimate interests of government to protect public safety and the preservation of individual civil liberties and privacy rights. No entity, including law enforcement, shall use recognition technology to engage in ongoing surveillance of specified individuals in public spaces except in the following scenarios:  (a) where laws are enacted in jurisdictions that respect the rule of law and specifically regulate and define the parameters for the use of facial recognition technology in public spaces; (b) if a court order is issued in a jurisdiction that maintains a fair and independent judiciary that authorizes the use of facial recognition technology by law enforcement for ongoing surveillance of a specified individual in a public space; or (c) in an emergency involving imminent danger or risk of death or serious physical injury to a person. 

## Annex A
** Informative Glossary** 
**admin console:** An online portal that facilitates the registration and enrollment with the Standard for Biometric Privacy (SBP).
**application:** A unique software/system, which is created using the SBP application programming interface (API) key.
**Distance Measure:**  A distance function or computation that offers class separation between 
embeddings.  Typically a cosine distance or Euclidean distance function.
**SBP admin:** A SBP administrator, who sets up an environment and creates an original site admin based on the enrollment information input during the registration.
**SBP server:** An instance of the server, such as in the client/server paradigm, that supports SBP  architecture.
**liveness:** An aspect of an algorithm that defines an animated object in computer vision.
**user:** A unique user, whose identity is being asserted by SBP and who shall have one or many  devices.
**user device:** A single device that has biometric-driven client software.

## Annex B
** Informative Bibliography **

Bibliographical references are resources that provide additional or helpful material but do not need to be understood or used to implement this standard. Reference to these resources is made for informational use only. 

[B1] Bonneau, J., C. Herley, P. C. van Oorschot, and F. Stajano, “The quest to replace passwords: A framework for comparative evaluation of Web authentication schemes,” Proceedings 2012 IEEE Symposium on Security and Privacy, S&P 2012, San Francisco, CA, pp. 553–567, May 2012. 
[B2] Chan, S. W., and R. Mordani, Java™ Servlet Specification, Version 3.1. Redwood Shores, CA: Oracle America, Inc., 2013. 
[B3] Handley, M., JAX-RS: Java™ API for RESTful Web Services, Version 1.0. Santa Clara: CA: Sun Microsystems, Inc., 2008.
[B4] Ross, Arun, Othman, Asem, IEEE Transactions on Information Forensics and Security, Volume 6, Issue 1, March 2011,  Visual Cryptography for Privacy. 
[B5] Derakhshani, Reza Patent No US 8,369.595 B1, Texture Features for Biometric Authentication, February, 2013 
[B6] U.S. Department of Defense, DoD 5200.28-STD, “Department of Defense Trusted Computer System Evaluation Criteria,” December 1985.
[B7] Convolutional Neural Network https://en.wikipedia.org/wiki/Convolutional_neural_network 
[B8] Institute for Electrical and Electronics Engineers (IEEE),  IEEE 1619 Standard for Cryptographic Protection of Data on Block-Oriented Storage, 2007. 
[B9] Open Web Application Security Project (OWASP), The Cryptographic Storage Cheat Sheet, 2016.
[B10] National Institute of Standards and Technology (NIST), NIST Special Publication 800-122, April 2010. 
[B11] The International Organization for Standardization (ISO) and the International Electrotechnical Commission (IEC), ISO/IEC 27001, “Information technology -Security techniques - Information security management systems - Requirements”, Second edition, November 2013.
[B12] The Directive 95/46/EC of the European Parliament and of the Council, EU Directive 95/46/EC, October 1995.
[B13]European Banking Authority (EBA) Discussion Paper on future Draft Regulatory Technical Standards on strong customer  authentication and secure communication under the revised Payment Services Directive (PSD2), (EBA/PSD2), December 2015.
[B14] The U.S. Department Of Commerce, EU-U.S. Privacy Shield Framework Principles Issued By The U.S. Department Of Commerce, February 2013.
[B15] Public Law 104-191, The Health Insurance Portability and Accountability Act of 1996 (HIPAA), 1996.
[B16] Open Web Application Security Project (OWASP), “OWASP Top 10”, June 2013.
[B17] National Institute of Standards and Technology (NIST), NIST Special Publication 800-53 Revision 4 Security and Privacy Controls for Federal Information Systems and Organizations, April 2013.
[B18] Public Law 93-579. The Privacy Act of 1974, 5 U.S.C. § 552a, 1974.
[B19] 740 ILCS 14/ Biometric Information Privacy Act (“BIPA”).  Available at: https://www.ilga.gov/legislation/ilcs/ilcs3.asp?ActID=3004&ChapterID=57 (Accessed 8 August 2020). 
[B20] AB375, Title 1.81.5, The California Consumer Privacy Act of 2018, CCPA.  Available at: https://oag.ca.gov/privacy/ccpa (Accessed 8 August 2020). 
[B21] EURO-MILS, “Secure European Virtualisation for Trustworthy Applications in Critical Domains, Used Formal Methods”, 2015.  Accessed 8 August 2020.  Available from https://zenodo.org/record/45164#.XzSVQOhKj-g
[B22] European Parliament and Council of European Union (2016) Regulation (EU) 2016/679 (“GDPR”). Available at:  https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32016R0679&from=EN (Accessed: 8 August 2020).
[B23] Lentchner, Cassie and S. Farmer.  “Data Privacy and Compliance in the Age of Fully Homomorphic Encryption (FHE):  GDPR, CCPA and BIPA.”  Pillsbury Winthrop Shaw Pittman LLP.  August 1, 2020.  
[B24] Microsoft. (2018). Six principles for developing and deploying facial recognition technology. Accessed 8 August 2020.  Available at https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2018/12/MSFT-Principleson-Facial-Recognition.pdf. 
[B25] Office of the Director of National Intelligence (2008). “US ODNI Intelligence Community Directive 503.” Intelligence Community Information Technology Systems:  Security Risk Management, Certification And Accreditation. Accessed 8 August 2020.  Available from https://www.dni.gov/files/documents/ICD/ICD_503.pdf. 
[B26] Punke, Michael. “Some Thoughts on Facial Recognition Legislation,” AWS Machine Learning Blog, February 7, 2019.  Accessed 8 August 2020.  Available at https://aws.amazon.com/blogs/machine-learning/some-thoughts-on-facial-recognition-legislation.
[B27] US Department of Defense (Mitre, 1985). Department of Defense Trusted Computer System Evaluation Criteria (“TCSEC”). Accessed 8 August 2020.  Available at: https://csrc.nist.gov/csrc/media/publications/conference-paper/1998/10/08/proceedings-of-the-21st-nissc-1998/documents/early-cs-papers/dod85.pdf
[B28] United States. 2004. The Health Insurance Portability and Accountability Act (“HIPAA”). [Washington, D.C.]: U.S. Dept. of Labor, Employee Benefits Security Administration. Available at: http://purl.fdlp.gov/GPO/gpo10291 (Accessed 8 August 2020). 


Copyright © 2020 IEEE. All rights reserved.
This is an unapproved IEEE Standards Draft, subject to change.



