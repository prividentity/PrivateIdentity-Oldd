### Pay as you go 
Private ID® uses state-of-the-art voice recognition algorithms to detect and recognize human voice biometrics in audio. Capabilities include local models and APIs that locate the biometric (Geometry DNNs), validate biometrics (Validation DNNs), fully homomorphically encrypt the biometric (Embedding DNNs) and models that run on AWS SageMaker® to return identity (encrypted search and encrypted match). 

Requests to the Private ID API are billed by Product SKU under a standard Cloud pay-as-you-go pricing model. One or more Product SKUs are triggered for each request. 

#### There are two types of fees.
**Billable Units**: Each component, model, API or service applied to a biometric is a billable unit. Using multiple components, models, APIs or services against a single biometric image or audio counts as processing multiple billable units. For example, if you apply the Validation DNN and Embedding DNN (2 models) to the same audio, you are billed for two billable units. 

**Metadata Storage**: Private ID stores a repository of anonymized voice metadata during enrollment against which to search for matches. Storage charges are applied monthly per enrolled subject. Metadata storage fees are prorated daily. If each day during the month a customer enrolled 1,000 voices for a few hours and then delete them each night, the customer will still be billed for 1,000 enrolled voice metadata each day. 

### Pricing Table - Product SKUs

Pricing is based on monthly usage for both billable units and metadata storage. The table below sets out Private ID's "Cloud pay-as-you-go" pricing in US dollars (USD). 

| SKU | Description | Each Request | 1000 Requests | Throughput |
| ---- | ----------- | ------- | :-----------: | :-----------: | 
| | **1:n VOICE RECOGNITION** | | | | 
| VR1 | Tier 1 (0-1M requests/month) | $0.00100 | $1.00 | Unlimited |
| VR2 | Tier 2 (1M-10M requests/month) | $0.00080 | $0.80 | Unlimited |
| VR3 | Tier 3 (10M - 100M requests/month) | $0.00060 | $0.60 | Unlimited | 
| VR4 | Tier 4 ( >100M requests/month) | $0.00040 | $0.40 | Unlimited |
| | **METADATA STORAGE** | | | | 
| VE1 | Voice Metadata Storage (Monthly) | $0.00010 | $0.10 | Unlimited | 

Each model, API, or service request counts as one billable unit. 
Each Product SKU includes 1000 billable units.

### Product SKU Usage Counter Details 
* Each Product SKU contains 1000 billable units.
* SKU counters reset to zero on the first day of each calendar month at 12 AM PST (UTC-8). 

### Tier Usage Counter Details 
* Tier usage counters reset to zero on the first day of each calendar month at 12 AM PST (UTC-8). 
* Tiers operate independently per Product SKU. The usage of one SKU can only affect the price of that SKU. 
* Tiers operate independently for each Customer ID and do not aggregate across multiple Customer IDs.
 
### Pricing Table - Specific
The price of each component is enumerated in the table below. 

| Component | SKU | 0-1M Units | 1M-10M Units | 10M-100M Units | >100M Units |
| ----------- | :-----: | ----------- | ----------- | ------- | ------- |
| **1:N SPEAKER IDENTIFICATION** | |  |  |  |  | 
| [Voice Validation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-validation-dnn) | VR | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Voice Augmentation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-data-augmentation) | VR | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Voice Embedding DNN](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-embedding-dnn) | VR | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Voice Encrypted Match DNN](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-embedding-dnn) | VR | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| **ENROLLMENT METADATA STORAGE** | | | | |
| FHE Metadata Storage | ST | $0.00100 | $0.00100 | $0.00100 | $0.00100 |

### Example 1
If your application made the following requests in a one-month period:
* 700 Voice Enrollments using four components.
  * Voice Validation DNN 
  * Voice Augmentation 
  * Voice Embedding DNN 
  * Voice Encrypted Match DNN 

Your cost would be $2.80, or $0.00400/enrollment. This is calculated by multiplying 700 enrolled persons by four Tier_1 units, or (700 enrollments x 4 billable units x $0.00100).

### Example 2
If your application enrolled 1000 voices on the 15th day of a month with 30 days, the FHE Metadata Storage cost for those 1000 voice enrollments in a one-month period would be $0.50, or $.0005/enrollment/month. The cost is calculated by multiplying (15 days x 1000 voice enrollments x $0.001/month), and then dividing the product by 30 days. 

Invoices are rounded up to the next penny once at the end of each billing cycle.