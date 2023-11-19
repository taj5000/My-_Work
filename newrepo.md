# Aadhar based mandate workflow
#### Table of Content
- Authentication using eSign
- eSign creation process
- eSign E-mandate process in NACH
- Aadhaar SOP
- Seeding of Aadhaar numbers in NPCI mapper
- De-seeding
- File Format
- Reseeding


## Authentication using eSign:
- eSign electronic signature service is an innovative initiative for allowing easy, efficient, and secure 
signing of electronic documents by authenticating signer using Aadhaar eKYC services. 

- With this service, any Aadhaar holder can digitally sign an electronic document without having to obtain a physical
digital signature dongle.

- Application Service Providers (ASP) can integrate this service within their application to offer Aadhaar holders a way to 
sign electronic forms and documents. 

- Through the interface provided by the Application Service Provider (ASP), users can apply electronic signature on any
electronic content by authenticating themselves through biometric or OTP through eSign Service Provider.

## eSign creation process:

•Registration of Customer’s Aadhaar number with his/her bank (the destination
bank) is a pre-requisite for this process.

• Corporate or aggregator provides a web page for the customer to submit all the
mandate related information.

• Each mandate form should have a unique reference number assigned by the corporate
and such reference number should be made part of the mandate data.

• The customer should be prompted to fill all the mandatory fields along with Aadhaar
number in the corporate webpage.

• Corporate sends the customer mandate data in a hashed value along with Aadhaar
number in an encrypted format to ESP (eSign service provider).

• ESP request UIDAI for OTP generation to customer mobile number. Prior to that it is
mandatory ESP to get the consent from customer electronically for retrieval of eKYC
details.

• Customer to be prompted to enter the OTP in ESP portal, where ESP will then send the
same to UIDAI as per eKYC specification for retrieval of customer eKYC details.

• On successful receipt of Aadhaar details, ESP creates a new key pair (Public and Private
Key) for that specific Aadhaar holder in HSM server hosted by ESP.

• With the eKYC details received from UIDAI, ESP prepares a Digitally Signed Certificate
(DSC) application form and send it to CA (Certified Authority) along with public key.

• CA certifies the public key shared by ESP.

• CA sends the Aadhaar eKYC class end individual Digitally Signed Certificates (DSC) to
ESP.

• ESP signs the hashed value of the mandate document received from corporate using the
private key. This is call eSign signature.

• ESP sends the eSign signature and Digital Signed Certificate (DSC) to ASP.

• ASP attach both eSign signature and X509 Certificate (DSC) in the XML format desired
by NPCI.

**eSign creation process flow**

![Alt text](<eSign.png>)








**eSign E-mandate process in NACH:**
1. Sponsor bank presents the eSign mandate received from the corporate in NACH system as
per the desired format of NPCI.

2. NACH system will check and validate the file format and send the mandate inward file to
destination bank based on the debtor bank IFSC given in the mandate file.

3. Destination bank processes the eSign inward by verify using PKI validation tool.
   
4. Validation tool to ensure following points are verified.
   
a. Digital certificate integrity.

b. eSign signature tag decryption and cross check with Signed content.

c. Verification of Aadhaar number (last 4 digit) in Digital certificate (X509) and Bank
CBS.

d. Cross check mandate data with Signed content.

5. After successful validation of eSign, destination bank perform business validations.
   
6. Once verification process is completed, destination bank uploads the response file in
NACH system.

7. NACH system will send the response file for the mandates presented by the sponsor bank
based on response received from destination bank.

## Authentication using Aadhaar - Process flow.

1. Customer has initiated the request via Merchant Portal i.e., Web Browser.
   
2. Customer will be redirected to ONMAGS Platform to enter the details required for Aadhaar 
authentication.

3. Customer enters Aadhaar Number along with required details.
   
4. ONMAGS Platform will forward that request to UIDAI for Customer Authentication via OTP
generation.

5. UIDAI will generate the OTP and send it to Customer’s registered mobile number for
Authentication.

6. Customer will enter the OTP in the ONMAGS OTP page.
   
7. ONMAGS Platform will forward that OTP to UIDAI for Verification.
 
8. UIDAI sends response for OTP Verification. If the request is not authenticated by UIDAI
then the flow ends here by showing the error message in Merchant Portal.

9. Once the customer is successfully authenticated, then the ONMAGS platform will send the
mandate request to destination bank.

10. After customer successfully authenticated by UIDAI, he/she will be landed on ONMAGS
OTP page.

11. ONMAGS will send an API request to customer’s Bank to verify the customer details will
generate the Bank OTP and send it to customer for Authentication.

12. Customer will enter the Bank OTP in ONMAGS platform for Authentication.
 
13. ONMAGS platform will forward that OTP to destination bank for Verification.
  
14. If OTP verification is successful only Bank needs to mark the mandate as accepted at their

end.
15. Until OTP validation is passed the mandate would be in non-accepted state at the Bank end.

16. ONMAGS Platform in turn redirects the response to Merchant Web Page where customer
can view the response.




## Aadhaar SOP
Aadhaar Payments Bridge System facilitates end-to-end processing of bulk electronic payment
instructions primarily facilitating the government departments to disburse the social security
benefits under different schemes by Direct Benefit Transfers (DBT) to the bank account of the
beneficiaries.

In APB system, the subsidy/benefit can be disbursed to the account of the
beneficiary based on the mapping of Aadhaar number to the IIN of a bank in NPCI mapper.

Given below is the document list that defines the standard
operating procedure to be followed by the member banks for the following activities:

• Join the APB system as a participant

• Seeding the Aadhaar number

• De-seeding the Aadhaar number

• Marking/unmarking OD flag

• Reconciliation between Aadhaar numbers in banks’ CBS with NPCI mapper

• Processing the transactions as a sponsor bank

• Processing the transactions as a destination bank

### Seeding of Aadhaar numbers in NPCI mapper:

**Seeding of Aadhaar numbers in NPCI mapper involves two steps:**

**1. Verification of Aadhaar numbers as per banks’ internal policy and linking the same to the
customer’s account in core banking system of the bank.**

**2. Seeding the Aadhaar number in NPCI mapper.**

~~~
What is NPCI mapper?
NPCI mapper is a repository of Aadhaar numbers linked with particular bank and used for the purpose of routing the Aadhaar based payment transactions to the destination banks. The NPCI mapper contains Aadhaar number along with IIN (Issuer Identification Number) of the bank that has seeded the Aadhaar number.
~~~

Banks should take utmost care in linking the Aadhaar number to an account and seeding
in NPCI mapper.** Once the Aadhaar number is seeded, then that account shall become
eligible to receive Direct Benefit Transfers (DBT) credits from the government** or any
other agency Incorrect linking in CBS will lead to wrong credits, the bank will be liable
to make good such wrong credits to the originating department/s or agency/s.

**The following steps should be followed by the bank for seeding an Aadhaar number:**

a. The bank should define a clear process, listing the documents to be submitted by
the customer for verification and seeding of Aadhaar numbers.

b. Bank should obtain any of the following document and written consent of the
customer as per the format provided in Annexure II. Any other document as may
be required by the banks depending on their internal policy may also be obtained.

c. Under no circumstance the Aadhaar seeding should be done without an informed
consent of the customer.

d. If the documentary proof submitted is not in line with the internal policy of the
bank, then such request for Aadhaar seeding should be rejected with advice to
the customer for deficiencies to be rectified.

e. Bank should verify the Aadhaar credentials of the customer through demographic
authentication as mandated by UIDAI vide their circular with the details as per
their records. The bank should match the name and ensure the account belongs
to the person who has submitted the Aadhaar consent form for seeding.

f. On being satisfied with the documentary proof the bank should first issue an
acknowledgement for the seeding request and then proceed to link the Aadhaar
number to the customer’s account in their core banking system (CBS).

g. After linking is completed the bank should proceed for seeding the Aadhaar
number in NPCI mapper.

h. As a first step of seeding, verification should be done whether the account is
eligible to receive the credits pertaining to the direct benefit transfers. If the
account is not eligible to receive the credits, then the seeding request should be
returned to the customer with appropriate reason. Few examples

**1. NRE account**

**2. Loan account**

**3. PPF account/FD account**

**4. Blocked/frozen account**

**5. Inoperative/Dormant account**

**6. (The list is only indicative. Any account that is not eligible to
receive credits, Aadhaar numbers pertaining to such accounts
should not be seeded with NPCI. Such seeding request should be
rejected, with the reason for such rejection)**

**i. Bank should have distinct fields in their CBS for updating the Aadhaar number
submitted for KYC purpose and/or for Aadhaar seeding purpose.**

**j. Under no circumstances the Aadhaar number submitted as a part of KYC be seeded
in NPCI mapper. The seeding should only be subject to explicit consent from
customer for receiving the Aadhaar based payments and also subject to submission
of written consent (mandate) by the customer.**

**k. Based on the purpose for which Aadhaar number is submitted by the customer,
the bank official should update the number in the relevant field in core banking.**

**l. Banks should implement the verhoeff algorithm for checking the validity of the
Aadhaar numbers.**

**m. Bank should have automated process with a minimum of one time download of all
Aadhaar numbers submitted for seeding purpose to be uploaded into NPCI mapper.
It is recommended that banks should have process for multiple download and
upload into NPCI mapper during the day.**

**n. The downloaded data should be as per the format specified by NPCI for mapper
upload (Annexure III). After the seeding file is uploaded, the NPCI mapper will
provide a response file indicating whether all the records are updated in the
mapper or some records are rejected.**

**o. Banks should have monitoring mechanism to verify the response files received
from Aadhaar mapper and take corrective action at their end.**

**p. The list of reasons for rejection in Aadhaar mapper is provided in Annexure IV.
138.**

**q. There should be a provision in CBS to update the status of seeding in NPCI mapper.
If the Aadhaar number is rejected by the mapper during the seeding process, the
reason for the reject should be updated in CBS.**

**r. Bank should send a communication to the customer, either through a mail or SMS,
on seeding of Aadhaar number with seeding date in case of successful seeding. In
case of unsuccessful seeding the communication should be sent along with the
reason for rejection. It is preferable to send SMS wherever customer has registered
his mobile number.**

**Customer's written consent format**


![Alt text](<Annexure 1 .png>)

**Aadhaar seeding declaration**

![Alt text](<Annexure VII.png>)

Banks should submit the declaration for having implemented Aadhaar consent
format designed by IBA to NPCI with regard to seeding of Aadhaar number based on
the customer consent. Banks will not have access to Aadhaar mapper until the
declaration is submitted to NPCI as per Annexure VII

**Annexure-VII AADHAAR SEEDING DECLARATION**

**Customer consent Mandatory**
It is mandatory for the banks to obtain the consent of the customer either through
physical form or electronic mode before updating in NPCI mapper. Banks are advised
to preserve the consent form received from the customer either in physical or
electronic form. In the event of any customer query or complaint, bank must
produce the documentary proof of consent given by the customer for Aadhaar
seeding.

Banks are advised to obtain the consent form from customer as per the format given
in Annexure II. 

**Annexure II – Format for normal seeding of Aadhaar number with bank**

![Alt text](<Annexure II.png>)

**Facility to check the Aadhaar seeding status**

Banks should make necessary arrangements to enable the staff as well as the
customer to check the Aadhaar mapping status. Either one or all the methods given
below can be used to facilitate this

i) The Aadhaar mapper status should be updated in CBS and the staff should be
able to view the status.

ii) The facility may be extended to the customer through internet banking or
ATM network or any other alternate channels.

iii) The API facility provided by NPCI should be implemented to provide online
status to the staff.

iv) Banks staff having access to NACH system can view the mapping status using
MIS tab.

v) Aadhaar look up facility can be availed from NPCI to ascertain mapping
status of a batch of Aadhaar numbers.

vi) Aadhaar seeding status enquiry must be made available to the customers
through AEPS (refer circular no 12 dated February 22, 2019).

**De-seeding**
In the event of an account, where Aadhaar number is seeded in NPCI for receiving the
benefits becoming ineligible to receive the credits, the bank should take immediate steps to
de-seed such an Aadhaar numbers from NPCI mapper. The following are the events that
should trigger deseeding

**1. Account closed**

**2. Account holder expired**

**3. Customer insolvent/ Account holder became insane.**

**4. Account Under Litigation.**

**5. Account blocked or frozen.**

## XML & Text file format

- NPCI can generate either XML / text (TXT) files for member banks. 
- By default the text file format will be enabled and files will be pushed to banks in TXT format only.
- In case, banks requires XML format then a request has to be submitted to NPCI for activation of XML files. XML format can be enabled only for ACH 306 format. APB & NACH Debit (156 format) files will be provided in TXT format only.

## Reseeding

a. If a customer whose Aadhaar number is deseeded from NPCI mapper approaches
the same bank again for seeding his Aadhaar number, the bank should have
provision for such reseeding.

b. The front desk staff/official should be trained to handle reseeding.
(Note: Normally the front desk officials verify their CBS and if the Aadhaar
number is linked to the account of the customer they confirm that the
Aadhaar is already seeded in NPCI mapper, this may not be a correct)

c. Even if the Aadhaar number is appearing in the CBS, it may be possible that the
bank has not removed the Aadhaar number from CBS despite deseeding the same
from NPCI or the Aadhaar number having moved out to another bank.

d. When a request for reseeding is received, the bank should make a provision in the
CBS to enable the staff to trigger re-seeding process, even though the Aadhaar
number is already available in the CBS.

e. The process will ensure that the Aadhaar numbers will be downloaded as a part
of the data files that are sent to NPCI mapper at periodic intervals for seeding.

f. The process detailed in the section ‘seeding’ should be diligently followed for
reseeding as well.

g. There should be a field to indicate the first seeding and subsequent reseeding
dates.



