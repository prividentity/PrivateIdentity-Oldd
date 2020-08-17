# P2410-2020/D1 Draft Standard for Biometric Privacy 
Sponsor

Standards Development Board
of the
IEEE Communications Society

and the

Technical Committee on COM/SDB
of the
IEEE Technical Activities Board

Approved <Date Approved>

IEEE-SA Standards Board
Copyright © 2020 by The Institute of Electrical and Electronics Engineers, Inc.
Three Park Avenue
New York, New York 10016-5997, USA
All rights reserved.

This document is an unapproved draft of a proposed IEEE Standard. As such, this document is subject to change. USE AT YOUR OWN RISK! IEEE copyright statements SHALL NOT BE REMOVED from draft or approved IEEE Standards, or modified in any way. Because this is an unapproved draft, this document shall not be utilized for any conformance/compliance purposes. Permission is hereby granted for officers from each IEEE Standards Working Group or Committee to reproduce the draft document developed by that Working Group for purposes of international standardization consideration.  IEEE Standards Department shall be informed of the submission for consideration prior to any reproduction for international standardization consideration (stds.ipr@ieee.org). Prior to adoption of this document, in whole or in part, by another standards development organization, permission shall first be obtained from the IEEE Standards Department (stds.ipr@ieee.org). When requesting permission, IEEE Standards Department shall require a copy of the standard development organization's document highlighting the use of IEEE content. Other entities seeking permission to reproduce this document, in whole or in part, shall also obtain permission from the IEEE Standards Department.
IEEE Standards Department
445 Hoes Lane 
Piscataway, NJ 08854, USA

## Abstract
The Standard for Biometric Privacy (SBP) provides private identity assertion. SBP enhances and extends the prior IEEE 2410-2019 Standard for Biometric Open Protocol by including formal governance for privacy and biometrics such that adherence guarantees the SBP system does not incur GDPR, CCPA, BIPA or HIPAA privacy obligations. Homomorphic encryption ensures the biometric payload is always one-way encrypted with no need for key management and guarantees privacy by ensuring plaintext biometrics are never received by the SBP server.  

The SBP implementation includes software running on a client device and on the SPB server.  Pluggable components are used to replace legacy functionality to allow rapid integration into existing operating environments. The SBP implementation allows the systems to meet security needs by using the application programming interface, whether the underlying system is a relational database management system or a search engine. The SBP implementation functionality offers a “point-and-cut” mechanism to add the appropriate security to the production systems as well as to the systems in development. The architecture is language neutral, allowing Representational State Transfer (REST), JavaScript Object Notation (JSON), and Secure Sockets Layer (SSL) or Transport Layer Security to provide the communication interface.

This document describes the essential methodology to SBP.

**Keywords**: biometrics, privacy, admin console, application, SBP admin, SBP cluster, SBP server, SBP IDS, client device IDS, Jena Rules, IDS cluster, IEEE 2410, liveness, original site admin, site admin, trusted adjudicated data, user, user device

## Important Notices and Disclaimers Concerning IEEE Standards Documents
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
Laws and regulations 
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

