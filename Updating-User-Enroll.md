This page documents how to update enrolled user modalities. This document assumes a user is already enrolled by only one modality (like face or voice) and want to add another one on top of it.

The following workflow must start with the user predicting with one modality to get his subject_id. Afterwards, the user should manually go to the application interface, with the newly requested modality equaling to true.

**Example**

A certain user is enrolled with face, and can successfully predict with that. This user wants to enroll with voice, too. The URL the user should have the following parameters:

> apiKey=xxxx&voice=true&action=enroll&subject_id=x
