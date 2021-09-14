### Pay as you go 
Private ID® uses state-of-the-art face, face+face mask, voice and fingerprint algorithms to detect and recognize human biometrics in images and audio. Capabilities include models and APIs that locate biometric geometry, validate biometrics and perform identification. 

Requests for Private ID services are billed by Product SKU under a standard pay-as-you-go pricing model. One or more Product SKUs are triggered for each request, depending on the fields that are specified in the request. 

Only valid requests containing a live person incur costs. For example, invalid an image that does not contain a face, audio that does not , or where the biometric sample is a spoof, do not incur cost.  

#### Billable Units 
**Billable Units**: Each component, model, API or service applied to a biometric is a billable unit. Using multiple components, models, APIs or services against a single biometric image or audio counts as processing multiple billable units. For example, if you apply Face Landmarks, Blur Detection and Face Identification (3 models) to the same image, you are billed for three billable units. 

**Metadata Storage**: Private ID stores a repository of anonymized metadata during enrollment against which Private ID searches for matches. Storage charges are applied monthly per enrolled subject. Metadata storage fees are prorated daily. If each day during the month a customer enrolled 1,000 subjects for a few hours and then deleted them each night, the customer would still be billed for 1,000 metadata storage each day. 

### Pricing Table - Product SKUs

Pricing is based on monthly usage for both billable units and metadata storage. The table below sets out the Private ID "pay-as-you-go" pricing in US dollars (USD). 

| SKU | Description | Each Request | 1000 Requests | Throughput |
| ---- | ----------- | ------- | :-----------: | :-----------: | 
| PRIV01 | Tier 1 (0-1M requests/month) | $0.00100 | $1.00 | Unlimited |
| PRIV02 | Tier 2 (1M-10M requests/month) | $0.00080 | $0.80 | Unlimited |
| PRIV03 | Tier 3 (10M - 100M requests/month) | $0.00060 | $0.60 | Unlimited | 
| PRIV04 | Tier 4 ( >100M requests/month) | $0.00040 | $0.40 | Unlimited |
| PRIV05 | Anonymized Metadata Storage | $0.00100 | $1.00 | |
| PRIV10 | Remote Onboarding/KYC/AML | $0.15 | $150.00 | Unlimited |

Each model, API, or service request counts as one billable unit. 
Each Product SKU includes 1000 billable units.

### Product SKU Usage Counter Details 
* Each Product SKU contains 1000 billable units.
* SKU counters reset to zero on the first day of each calendar month at 12 AM PST (UTC-8). 

### Tier Usage Counter Details 
* Tier usage counters reset to zero on the first day of each calendar month at 12 AM PST (UTC-8). 
* Tiers operate independently for each Customer ID and do not aggregate across multiple Customer IDs.
 
### Example 1
If your application made the following requests in a one-month period:
* 700 Face Enrollments, where each enrollment requested six models
  * Face Landmark DNN
  * Blur Detection DNN
  * Image Spoof Detection DNN
  * Video Spoof Detection DNN
  * Eyeglass Detection DNN
  * Face 1:n Identification DNN

Your cost would be $4.20, or $0.006/enrollment. This is calculated by multiplying 700 enrolled persons by six Tier 1 units, or (700 x 6 x $0.00100).

### Example 2
If your application made the following requests in a one-month period:
* 5000 Face Authentications, where each authentication requested five models 
  * Face Landmark DNN
  * Blur Detection DNN
  * Image Spoof Detection DNN 
  * Video Spoof Detection DNN
  * Face Identification DNN

Your cost would be $25.00, or $0.00500/prediction. This is calculated by multiplying 5000 persons times 5 Tier 1 units, or (5000 Authentications x 5 Requests x $0.00100).

### Example 3
If your application enrolled 1000 subjects on the 15th day of a month containing 30 days, the Anonymized Metadata Storage cost for those 1000 enrollments in a one-month period would be $0.50, or $0.0005/enrollment. The cost is calculated by multiplying (15 days x 1000 face enrollments x $0.00100/month), and then dividing the product by 30 days. 

Invoices are rounded up to the next penny once at the end of each billing cycle.