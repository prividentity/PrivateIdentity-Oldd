Cloud Biometric API uses state-of-the-art face, face+face mask, voice and fingerprint algorithms to detect and recognize human biometrics in images and audio. Capabilities include models and APIs that locate biometric geometry, validate biometrics and perform identification. 

Requests to the Cloud Biometric API are billed by Product SKU under the pay-as-you-go pricing model. One or more Product SKUs are triggered for each request, depending on the fields that are specified in the request. 

#### There are two types of fees.
**Billable Units**: Each component, model, API or service applied to a biometric is a billable unit. Using multiple components, models, APIs or services against a single biometric image or audio counts as processing multiple billable units. For example, if you apply Face Landmarks, Blur Detection and Face Identification (3 models) to the same image, you are billed for one billable unit of Face Landmarks, one billable unit of Blur Detection and one billable unit for Face Identification. 

**Metadata Storage**: Cloud Biometric API stores a repository of anonymized face, face+mask, voice and/or fingerprint metadata during enrollment against which Cloud Biometric API can search for matches. Storage charges are applied monthly per enrolled subject. Metadata storage fees are prorated daily. If each day during the month a customer enrolled 1,000 faces for a few hours and then delete them each night, the customer would still be billed for 1,000 enrolled face metadata each day. 

### Pricing Table - General

Pricing is based on monthly usage for both billable units and metadata storage. The table below sets out the service's expected "pay-as-you-go" pricing pattern. Geolocation, retrieval of phone billing records, OCR API, and SMS messaging services do not fit this pattern. Prices are listed in US dollars (USD). 

| Usage | Description | Price/Unit| Price/1000 Units | Throughput |
| ---- | ----------- | ------- | :-----------: | :-----------: | 
| Tier 1 | 0-1M transactions/month | $0.00100 | $1.00 | Unlimited |
| Tier 2 | 1M-10M transactions/month | $0.00080 | $0.80 | Unlimited |
| Tier 3 | 10M - 100M transactions/month | $0.00060 | $0.60 | Unlimited | 
| Tier 4 | Over 100M transactions/month | $0.00040 | $0.40 | Unlimited |
| Metadata | Monthly Metadata Storage | $0.00010 | $0.10 | Unlimited | 

Each model use or API call counts as one billable unit. 

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
| **FACE RECOGNITION** | | | | | 
| [Face Landmark](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-face-wmask-and-fingerprint-geometry-detection-dnns)| LM | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Blur Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#blurry-image-detect-dnn) | BD | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Image Spoof Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#video-and-image-spoofing-detection-dnn-spoofing-prevention) | IS | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Video Spoof Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#video-and-image-spoofing-detection-dnn-spoofing-prevention) | VS | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Eyeglasses Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#active-liveness-dnn-spoofing-prevention) | ED | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Eye Blink Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#active-liveness-dnn-spoofing-prevention) | EB | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Face Identification](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns) | FR | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Face+Mask Identification](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns) | FM | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| **FINGERPRINT RECOGNITION** | | | | | 
| [Fingerprint Geometry](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-face-wmask-and-fingerprint-geometry-detection-dnns) | FG | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Fingerprint Validation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-face-with-mask--fingerprint-validation-dnns) | FV | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Fingerprint Identification](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns) | FI | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| **VOICE RECOGNITION** | | | | | 
| [Voice Validation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-validation-dnn) | VV | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Voice Data Augmentation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-data-augmentation) | VD | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Voice Fast Fourier Transformation (FFT)](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-pulse-code-modulation-pcm-transformation) | FV | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Voice Identification](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-embedding-dnn) | VI | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| **GEOLOCATION** | | | | |
| On-Device Geolocation | GEO | $0.012000 | $0.012000 | $0.012000 | $0.012000 |
| **PHOTO ID VERIFICATION** | | | | | 
| [Document Geometry](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#document-geometry-detection-dnns) | DG | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Document OCR API](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#document-ocr-api) | OCR | $0.01200 | $0.01200 | $0.01200 | $0.01200 |
| [Phone Lookup (in USA)](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#mobile-billing-record-lookup-api) | PL1 | $0.03000 | $0.03000 | $0.03000 | $0.03000 |
| [Phone Lookup](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#mobile-billing-record-lookup-api) (not in USA) | PL2 | $2.50000 | $2.50000 | $2.50000 | $2.50000 | 
| [SMS Verification Message API](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#sms-verification-message-api) | SMS | $0.02000 | $0.02000 | $0.02000 | $0.02000 | 
| **ENROLLMENT METADATA STORAGE** | | | | |
| Face Metadata Storage | FS | $0.00100 | $0.00100 | $0.00100 | $0.00100 | 
| Face+Mask Metadata Storage | FMS | $0.00100 | $0.00100 | $0.00100 | $0.00100 |
| Fingerprint Metadata Storage | FPS | $0.00100 | $0.00100 | $0.00100 | $0.00100 |
| Voice Metadata Storage | VS | $0.00100 | $0.00100 | $0.00100 | $0.00100 |

### Example 1
If your application made the following requests in a one-month period:
* 700 Face Enrollments using six components.
  * Face Landmarks
  * Blur Detection
  * Image Spoof Detection
  * Video Spoof Detection 
  * Eyeglass Detection 
  * Face+Mask Identification 

Your cost would be $4.20, or $0.00600/enrollment. This is calculated by multiplying 700 enrolled persons by six Tier_1 units, or (700 x 6 x $0.00100).

### Example 2
If your application made the following requests in a one-month period:
* 5000 Face Predicts
  * Face Landmarks
  * Blur Detection
  * Image Spoof Detection
  * Video Spoof Detection 
  * Face+Mask Identification 

Your cost would be $25.00, or $0.00500/prediction. This is calculated by multiplying 5000 persons times 5 Tier_1 units, or (5000 x 5 x $0.00100).

### Example 3
If your application enrolled 1000 faces on the 15th day of a month with 30 days, the FHE storage cost for those 1000 face enrollments in a one-month period would be $0.50, or $.0005/enrollment. The cost is calculated by multiplying (15 days x 1000 face enrollments x $0.00100/month), and then dividing the product by 30 days. 

Invoices are rounded up to the next penny once at the end of each billing cycle.