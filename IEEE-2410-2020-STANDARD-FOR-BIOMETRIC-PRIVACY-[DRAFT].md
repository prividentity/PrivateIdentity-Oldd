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

**Official statements **
A statement, written or oral, that is not processed in accordance with the IEEE-SA Standards Board Operations Manual shall not be considered or inferred to be the official position of IEEE or any of its committees and shall not be considered to be, or be relied upon as, a formal position of IEEE. At lectures, symposia, seminars, or educational courses, an individual presenting information on IEEE Standards shall make it clear that his or her views should be considered the personal views of that individual rather than the formal position of IEEE. 

**Comments on standards**
Comments for revision of IEEE Standards documents are welcome from any interested party, regardless of membership affiliation with IEEE. However, IEEE does not provide consulting information or advice pertaining to IEEE Standards documents. Suggestions for changes in documents should be in the form of a proposed change of text, together with appropriate supporting comments. Since IEEE Standards represent a consensus of concerned interests, it is important that any responses to comments and questions also receive the concurrence of a balance of interests. For this reason, IEEE and the members of its societies and Standards Coordinating Committees are not able to provide an instant response to comments or questions except in those cases where the matter has previously been addressed. For the same reason, IEEE does not respond to interpretation requests. Any person who would like to participate in revisions to an IEEE Standard is welcome to join the relevant IEEE working group.

Comments on standards should be submitted to the following address:
	Secretary, IEEE-SA Standards Board 
	445 Hoes Lane 
	Piscataway, NJ 08854 USA

**Laws and regulations **
Users of IEEE Standards documents should consult all applicable laws and regulations. Compliance with the provisions of any IEEE Standards document does not imply compliance to any applicable regulatory requirements.  Implementers of the standard are responsible for observing or referring to the applicable regulatory requirements. IEEE does not, by the publication of its standards, intend to urge action that is not in compliance with applicable laws, and these documents may not be construed as doing so.

**Copyrights**
IEEE draft and approved standards are copyrighted by IEEE under U.S. and international copyright laws. They are made available by IEEE and are adopted for a wide variety of both public and private uses.  These include both use, by reference, in laws and regulations, and use in private self-regulation, standardization, and the promotion of engineering practices and methods. By making these documents available for use and adoption by public authorities and private users, IEEE does not waive any rights in copyright to the documents.

**Photocopies** 
Subject to payment of the appropriate fee, IEEE shall grant users a limited, non-exclusive license to photocopy portions of any individual standard for company or organizational internal use or individual, non-commercial use only. To arrange for payment of licensing fees, please contact Copyright Clearance Center, Customer Service, 222 Rosewood Drive, Danvers, MA 01923 USA; +1 978 750 8400. Permission to photocopy portions of any individual standard for educational classroom use can also be obtained through the Copyright Clearance Center.

**Updating of IEEE Standards documents **
Users of IEEE Standards documents should be aware that these documents may be superseded at any time by the issuance of new editions or may be amended from time to time through the issuance of amendments, corrigenda, or errata. An official IEEE document at any point in time consists of the current edition of the document together with any amendments, corrigenda, or errata then in effect. 

Every IEEE Standard is subjected to review at least every ten years. When a document is more than ten years old and has not undergone a revision process, it is reasonable to conclude that its contents, although still of some value, do not wholly reflect the present state of the art. Users are cautioned to check to determine that they have the latest edition of any IEEE Standard.

In order to determine whether a given document is the current edition and whether it has been amended through the issuance of amendments, corrigenda, or errata, visit the IEEE-SA Website at http://ieeexplore.ieee.org/xpl/standards.jsp or contact IEEE at the address listed previously. For more information about the IEEE SA or IEEE’s standards development process, visit the IEEE-SA Website at http://standards.ieee.org.

**Errata** 
Errata, if any, for all IEEE Standards can be accessed on the IEEE-SA Website at the following URL: http://standards.ieee.org/findstds/errata/index.html. Users are encouraged to check this URL for errata periodically.

**Patents**
Attention is called to the possibility that implementation of this standard may require use of subject matter covered by patent rights. By publication of this standard, no position is taken by the IEEE with respect to the existence or validity of any patent rights in connection therewith. If a patent holder or patent applicant has filed a statement of assurance via an Accepted Letter of Assurance, then the statement is listed on the IEEE-SA Website at http://standards.ieee.org/about/sasb/patcom/patents.html. Letters of Assurance may indicate whether the Submitter is shalling or unshalling to grant licenses under patent rights without compensation or under reasonable rates, with reasonable terms and conditions that are demonstrably free of any unfair discrimination to applicants desiring to obtain such licenses.

Essential Patent Claims may exist for which a Letter of Assurance has not been received. The IEEE is not responsible for identifying Essential Patent Claims for which a license may be required, for conducting inquiries into the legal validity or scope of Patents Claims, or determining whether any licensing terms or conditions provided in connection with submission of a Letter of Assurance, if any, or in any licensing agreements are reasonable or non-discriminatory. Users of this standard are expressly advised that determination of the validity of any patent rights, and the risk of infringement of such rights, is entirely their own responsibility. Further information may be obtained from the IEEE Standards Association.

**Participants**
At the time this draft standard was completed, the Biometrics Open Protocol Working Group had the following membership:
Scott Streit, Chair
Clayton Stewart, Vice Chair
Mark Thompson
Stephen Suffian
Brian Streit 
Daniel Farinella
Suleyman Muhammad
Nathan Dent
Steve Bailey

The following members of the individual balloting committee voted on this standard. Balloters may have voted for approval, disapproval, or abstention.
Susan Burgess
John Callahan
Keith Chow
Thomas Coughlin
Grazia D’Eelia
Sourav Dutta
Dan Friedman
Randall Groves
Marco Hernandez
Werner Hoelzl
Noriyuki Ikeuchi
Akio Iso
Piotr Karocki
Bruce Kraemer
Paul Lambert
Shalliam Lumpkins
Nick S. A. Nikjoo
Paul Nikolich
Benjamin Rolfe
Osman Sakr
Thomas Starai
Scott Streit
Walter Struppler
Stephen Suffian
Mitsutoshi Sugawara
Michael Swearingen
David Tepen
John Vergis
Hung-Yu Wei
Forrest Wright
Oren Yuen
Daidi Zhong

When the IEEE-SA Standards Board approved this standard on <Date Approved>, it had the following membership:
John D. Kulick, Chair
Jon Walter Rosdahl, Vice Chair
Richard H. Hulett, Past Chair
Konstantinos Karachalios, Secretary
Masayuki Ariyoshi
Ted Burse
Stephen Dukes
Jean-Philippe Faure
J. Travis Griffith
Gary Hoffman
Dan Friedman
Michael Janezic 
Joseph L. Koepfinger*
David J. Law
Hung Ling
Andrew Myles
T. W. Olsen
Glenn Parsons
Ronald C. Petersen
Annette D. Reilly
Stephen J. Shellhammer
Adrian P. Stephens
Yatin Trivedi
Philip Winston
Don Wright
Yu Yuan
Daidi Zhong
*Member Emeritus

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

1:M          		One-to-Many 
4F             		Four Fingers, a proprietary biometric technology
5-tuple	 		Five tuple data parameters  
Account  		User account with limited privileges 
Admin			Administrator
AOP			Aspect Oriented Programming
API			Application Programming Interface
app			A client application
CPU			Central Processing Unit
CBV			Current Biometric Vector
CSRF			Cross-Site Request Forgery
ID			Identifier
IDS			Intrusion Detection System
IBV       			Initial Biometric Vector 
IP			Internet Protocol                    
JSON			JavaScript object notation
LDAP			Lightweight Directory Access Protocol
MAC			Mandatory Access Control
MCA			Mobile Client Application
NSA			National Security Agency (U.S.)
PII			Personally Identifiable Information 
QR code	 		Quick Response code
RDBMS	 		Relational Database Management System
REST			Representational State Transfer
SBP 			Standard for Biometric Privacy 
SSL			Secure Socket Layer
TCSEC			Trusted Computer System Evaluation Criteria
TLS			Transport Layer Security
URL			Uniform Resource Locator 
XNTP			eXtended Network Time Protocol
XOR        		“Exclusive OR” is a binary operation 

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
The format of this API call is:  

POST “/mfa/v1.1/enroll?key=<API_KEY>”

Parameter:  Value
Features: Type, Name, Feature Array. Type is voice, face or fingerprint.

An Enroll API request example is as follows:
{
    "features": [
          {“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
          {“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
          {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},
	   …
	   {}
     ]
}

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
{
    "features": [
        {“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
        {“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
        {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},
	   …
	   {}
        ]
}

#### 8.2.3 Response
The response of a Predict request, if meeting confidence thresholds, returns PII data in the following format:
{
    "uuid": "1008023"
    "message": "OK",
    "status": 0,
    "subject_id": 4,
    ]
}

### 8.3 Liveness
#### 8.3.1 Overview
To recognize liveness, a mechanism to affirm interaction with a live individual, we take in audio files along with their respective expected text. The API call returns a value related to the certainty that the audio samples match what is expected. Video is used through the same API call.   All input is in .wav format.  Liveness is a local client call, typically, but is supported on the server in the format listed below.  The best practice is for a local liveness call so that plaintext is not transmitted.  

#### 8.3.2 Request

The format of this API call is: 

POST “/node/liveness”
{
    “files”: “base64_audio_1”,
    “text”: “text_expected_1”,
    “name”: “voice_0.wav”,
    “localeCode”: “en-US”
}

#### 8.3.3 Response
The response of a liveness request Returns accuracy data as a ratio from 0 to 1, with a value of .9 denoting 90% accuracy.

{
    "recognized_text":"text_expected_1",
    "expected_text":"text_returned_1",
    "accuracy":0.6000000000000001,
    "message":"OK",
    "status":0
}

### 8.4 Delete Subject
#### 8.4.1 Overview
Delete the person from database

#### 8.4.2 Request
The format of this API call is: 

Browser URL:  “?action=deleteSubject&subject_id=<subjectId>”

Python POST “/mfa/v1.1/delete_subject”

{
    “subject_id”: 1
}

#### 8.4.3 Response 
The status will have an error code.

{
   “status”: 0
}
{
   “status”: 0
   “role_id” : <role_id>
   “message” : “Role Successfully added.”
}

{
   “status”: -2
   “message” : “Role exists in database”
}

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

#### GDPR Principles to SBP Traceability Matrix
||GDRP PRINCIPLES | SBP System Compliance Control|
|------|-----------------------------------------------------|---------------------------------------|
|1|**Lawfulness, fairness and transparency principle** <br><br>Personal data is processed lawfully, fairly and in a transparent manner in relation to the data subject.| **Processes only anonymized data.** <br><br>SBP systems process only encrypted FHE payloads. This reduces the risk of the personal or biometric data being used for any improper, concealed or illegal purpose. <br><br>**Provides strong end-user authentication.** <br><br>The GDPR requires the organization to take reasonable steps to confirm that the person requesting access to their personal data is actually the rightful data subject. SBP systems help organizations advance and respond to requests from data subjects to exercise their rights under data protection law by providing strong end-user authentication to enable each data subject to control one’s data, to no longer consent to processing, to correct significant errors within the data and to request that data be erased (forgotten).  Strong end user authentication also allows organizations to accurately identify each data subject without requiring the subject to remember a username, password, token or shared secret.|
|2|**Purpose limitation principle** Personal data is collected for specified, explicit and legitimate purposes and not further processed in a manner that is incompatible with those purposes.|**Processes only anonymized data **SBP systems transmit, store and use only anonymized data. This promotes and accomplishes the regulatory goal of limiting the processing of personal data to only what is necessary in relation to the purposes for which they are processed.|
|3|**Data minimization principle** Personal data is adequate, relevant and limited to what is necessary in relation to the purposes for which they are processed.|**Processes only anonymized data** SBP systems transmit, store and use encrypted FHE payloads. This promotes and accomplishes the regulatory goal of limiting the processing of personal data to only what is necessary in relation to the purposes for which they are processed.<br> Discards (deletes) all personal data <br> SBP systems discard all plaintext biometric data.  Only anonymized, encrypted FHE payloads are transmitted, stored or used to support the authentication process. This helps realize the regulatory goal of limiting the processing of personal data to only what is necessary in relation to the purposes for which they are processed.|








[3]  Section 9.5 is excerpted with permission. Lentchner, Cassie and S. Farmer.  “Data Privacy and Compliance in the Age of Fully Homomorphic Encryption (FHE):  GDPR, CCPA and BIPA.”  Pillsbury Winthrop Shaw Pittman LLP.  August 1, 2020.  
[4]  Art. 5 GDPR Principles relating to processing of personal data.
[5]  GDPR Article 5(1)(c)
[6]  Recital 26 of the GDPR.   
[7]  Opinion 05/2014 on anonymisation techniques, 10 April 2014.
[8]  GDPR Article 9, Recital 51.
[9]  GDPR Article 4(14).
[10] GDPR Recital 26.
[11] GDPR Recital 26.
