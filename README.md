[![](https://raw.githubusercontent.com/shuftipro/ShuftiProSDK/master/shufti_pro_sdk.png)](https://www.shuftipro.com/)

# What Is This?
Shufti Pro is an Identity Verification software as a service that enables enterprises and individuals to secure their KYC and AML compliance. With quick, and realtime results, it acts as a security measure for sound risk assessment by using Face Verification, Document Verification, Information Authentication, and PEP's, Criminals and Money Laundering Checks. It is the go-to option for Payment Systems, FinTECH industry, Crypto, Banks, Lending Economy & Trading platforms.

# Table of contents
* [Basic Setup](#basic-setup)
* [General Requirements](#general-requirements)
* [SDK Installation Guide](#sdk-installation-guide)
* [Permissions](#permissions)
* [Integration](#integration)
* [Verifications](#verifications)
  * [Face Verification](#Face-Verification)
  * [Documentation Verification](#Documentation-Verification)
  * [Address Verification](#Address-Verification)
  * [Consent Verification](#Consent-Verification)
* [Response Logging](#response-logging)
* [Response Status Codes](#response-status-codes)
* [Sample Project Setup](#sample-project-setup)
* [Test IDs](#test-ids)
* [Contact](#contact)
* [Copyright](#copyright)

# Basic Setup
## General Requirements
Followings are minimum requirements for SDK:
- API Level 15  and higher
- Internet connection
- Camera


## SDK Installation Guide
1. Select File → New → New Module → Import .jar/Aar package from top menu of Android Studio.
2. Select the provided 'shufti_pro.aar' file.
3. Right click on 'app module' → Select 'Module setting'.
4. Select 'Dependencies' from the right pane.
5. Select '+' icon from the top right corner → select 'module dependency' → select 'shufti_pro'.

## Permissions:
Application uses the following permissions which you may have to add in privacy policy of the app. All permissions are handled in SDK.
1. Camera
2. Internet
3. Recording Audio
4. External Storage

## Verifications:
Shufti Pro supports four modes of verification:<br />
**1. Face Verification**<br />
**2. Document Verification**<br/>
**3. Address Verification**</br>
**4. Consent Verification**

## Integration: 
See the sample project provided to learn the most common use. Make sure to build on real device.
```
import com.shufti.pro.sdk.Shuftipro;
import com.shufti.pro.sdk.interfaces.ShuftiVerifyListener;
```
Make an instance 
```
Shuftipro instance = Shuftipro(clientId: "your-clientId",
                               secretKey: "your-secretKey");
```
## Face Verification
For **Face** verification
```sh
instance.shuftiproVerification(reference: "unique reference",country: "your-country", 
				      language: "your-language", email: "your-email", callback_url: "your-callback_url",
                                      redirect_url: "your-redirect_url",
				      isToMakeFaceVerification: true,
                                      isToPerformDocumentationVerification: false, 
				      isSupportPassportType: false,
				      isSupportIdCardType: false,    				    	     					   	      isSupportDrivingLicenseType: false,
				      isSupportCreditCardType: false,
				      nameOnDocument: "", 
				      dob: "",
				      documentNumber: "",
				      expiryDate: "",
				      issueDate: "",
                                      isToPerformAddressVerification: false, 
				      fullAddress: "", 
				      name: "",
				      isUtilityBillSupportedType: false, 					      					      isIdCardSupportedType: false,
				      isBankStatementSupportedType: false,
				      isToPerformConsentVerification: false,
				      textToBeVerify: "",
				      parentActivity: "your-caller-activity",
				      ShuftiVerifyListener: new ShuftiVerifyListener(){
				 
					@Override
					public void verificationStatus(HashMap<String, String> responseSet) {
					
						String event = responseSet.get("event");
				   		if(event.equalsIgnoreCase("verification.accepted")){
						//Do anything you want.. I am showing a toast message
				       		Toast.makeText(this, "Status : Verified...", Toast.LENGTH_LONG).show();
						}
						else{
						
						//Do anything you want.. I am showing a toast message
				      		 String message = responseSet.get("message");
				      	 	Toast.makeText(this, "Status : Not Verified", Toast.LENGTH_LONG).show();
				   }});
```


#### Request Parameters 

| Parameter | Description |
| ------ | ------ |
| isToMakeFaceVerification | Set value to true. |
| email | Your email address. Example: johndoe@example.com. |
| country | Full Country name or ISO2 Code. Example: United Kingdom or GB. |
| callback_url | Your callback url. Example: http://www.example.com. |

## Documentation Verification
For **Document** verification using ID documents (Methods: "**driving_license**" or "**passport**" or "**id_card**" or "**credit_or_debit_card**")
```sh
instance.shuftiproVerification(reference: "unique reference",country: "your-country", 
				      language: "your-language", email: "your-email", callback_url: "your-callback_url",
                                      redirect_url: "your-redirect_url",
				      isToMakeFaceVerification: false,
                                      isToPerformDocumentationVerification: true, 
				      isSupportPassportType: true,
				      isSupportIdCardType: true,    				    	     					   	      isSupportDrivingLicenseType: true,
				      isSupportCreditCardType: true,
				      nameOnDocument: "John Doe", 
				      dob: "12-02-1990",
				      documentNumber: "12338800",
				      expiryDate: "12-09-2000",
				      issueDate: "12-09-1990",
                                      isToPerformAddressVerification: false, 
				      fullAddress: "", 
				      name: "",
				      isUtilityBillSupportedType: false, 					      					      isIdCardSupportedType: false,
				      isBankStatementSupportedType: false,
				      isToPerformConsentVerification: false,
				      textToBeVerify: "",
				      parentActivity: "your-caller-activity",
				      ShuftiVerifyListener: new ShuftiVerifyListener(){
				 
					@Override
					public void verificationStatus(HashMap<String, String> responseSet) {
					
						String event = responseSet.get("event");
				   		if(event.equalsIgnoreCase("verification.accepted")){
						//Do anything you want.. I am showing a toast message
				       		Toast.makeText(this, "Status : Verified...", Toast.LENGTH_LONG).show();
						}
						else{
						
						//Do anything you want.. I am showing a toast message
				      		 String message = responseSet.get("message");
				      	 	Toast.makeText(this, "Status : Not Verified", Toast.LENGTH_LONG).show();
				   }});
```
#### Request Parameters 

| Parameter | Description |
| ------ | ------ |
| isToPerformDocumentationVerification | Set value to true. |
| email | Your email address. Example: johndoe@example.com. |
| country | Full Country name or ISO2 Code. Example: United Kingdom or GB. |
| callback_url | Your callback url. Example: http://www.example.com. |
| isSupportPassportType | If you set it true user will be able to verify data using passport. |
| isSupportIdCardType | If you set it true user will be able to verify data using Id card. |
| isSupportDrivingLicenseType | If you set it true user will be able to verify data using driving lisence. |
| isSupportCreditCardType | If you set it true user will be able to verify data using credit card. |
| nameOnDocument | The nameOnDocument is required if you don't want to perform OCR of the name. Otherwise optional. |
| dob | Provide a valid date. Please note that the date should be before today. Example 1990-12-31. |
| documentNumber | Allowed Characters are numbers, alphabets, dots, dashes, spaces, underscores and commas. Examples 35201-0000000-0, ABC1234XYZ098 |
| expiryDate | Provide a valid date. Please note that the date should be after today. Example 2025-12-31 |
| issueDate | Provide a valid date. Please note that the date should be after today. Example 2025-12-31 |

## Address Verification
For **Address** verification using ID documents (Methods: "**id_card**" or "**utility_bills**" or "**bank_statement**")
```sh
instance.shuftiproVerification(reference: "unique reference",country: "your-country", 
				      language: "your-language", email: "your-email", callback_url: "your-callback_url",
                                      redirect_url: "your-redirect_url",
				      isToMakeFaceVerification: false,
                                      isToPerformDocumentationVerification: false, 
				      isSupportPassportType: false,
				      isSupportIdCardType: false,    				    	     					   	      isSupportDrivingLicenseType: false,
				      isSupportCreditCardType: false,
				      nameOnDocument: "", 
				      dob: "",
				      documentNumber: "",
				      expiryDate: "",
				      issueDate: "",
                                      isToPerformAddressVerification: true, 
				      fullAddress: "", 
				      name: "",
				      isUtilityBillSupportedType: true, 					      					      isIdCardSupportedType: true,
				      isBankStatementSupportedType: true,
				      isToPerformConsentVerification: false,
				      textToBeVerify: "",
				      parentActivity: "your-caller-activity",
				      ShuftiVerifyListener: new ShuftiVerifyListener(){
				 
					@Override
					public void verificationStatus(HashMap<String, String> responseSet) {
					
						String event = responseSet.get("event");
				   		if(event.equalsIgnoreCase("verification.accepted")){
						//Do anything you want.. I am showing a toast message
				       		Toast.makeText(this, "Status : Verified...", Toast.LENGTH_LONG).show();
						}
						else{
						
						//Do anything you want.. I am showing a toast message
				      		 String message = responseSet.get("message");
				      	 	Toast.makeText(this, "Status : Not Verified", Toast.LENGTH_LONG).show();
				   }});
```
#### Request Parameters 

| Parameter | Description |
| ------ | ------ |
| isToPerformAddressVerification | Set value to true. |
| email | Your email address. Example: johndoe@example.com. |
| country | Full Country name or ISO2 Code. Example: United Kingdom or GB. |
| callback_url | Your callback url. Example: http://www.example.com. |
| isUtilityBillSupportedType | If you set it true user will be able to verify data using utility bills. |
| isIdCardSupportedType | If you set it true user will be able to verify data using Id card. |
| isBankStatementSupportedType | If you set it true user will be able to verify data using bank statements. |
| fullAddress | Leave empty to perform data extraction from provided proofs. |
| name | Leave empty to perform data extraction from provided proofs. |

## Consent Verification
For **Consent** verification
```sh
instance.shuftiproVerification(reference: "unique reference",country: "your-country", 
				      language: "your-language", email: "your-email", callback_url: "your-callback_url",
                                      redirect_url: "your-redirect_url",
				      isToMakeFaceVerification: false,
                                      isToPerformDocumentationVerification: false, 
				      isSupportPassportType: false,
				      isSupportIdCardType: false,    				    	     					   	      isSupportDrivingLicenseType: false,
				      isSupportCreditCardType: false,
				      nameOnDocument: "", 
				      dob: "",
				      documentNumber: "",
				      expiryDate: "",
				      issueDate: "",
                                      isToPerformAddressVerification: false, 
				      fullAddress: "", 
				      name: "",
				      isUtilityBillSupportedType: false, 					      					      isIdCardSupportedType: false,
				      isBankStatementSupportedType: false,
				      isToPerformConsentVerification: true,
				      textToBeVerify: "This text is to be verified",
				      parentActivity: "your-caller-activity",
				      ShuftiVerifyListener: new ShuftiVerifyListener(){
				 
					@Override
					public void verificationStatus(HashMap<String, String> responseSet) {
					
						String event = responseSet.get("event");
				   		if(event.equalsIgnoreCase("verification.accepted")){
						//Do anything you want.. I am showing a toast message
				       		Toast.makeText(this, "Status : Verified...", Toast.LENGTH_LONG).show();
						}
						else{
						
						//Do anything you want.. I am showing a toast message
				      		 String message = responseSet.get("message");
				      	 	Toast.makeText(this, "Status : Not Verified", Toast.LENGTH_LONG).show();
				   }});
```
#### Request Parameters 

| Parameter | Description |
| ------ | ------ |
| isToPerformConsentVerification | Set value to true. |
| email | Your email address. Example: johndoe@example.com. |
| country | Full Country name or ISO2 Code. Example: United Kingdom or GB. |
| callback_url | Your callback url. Example: http://www.example.com. |
| textToBeVerify | Provide text in the string format which will be verified from a given proof. |

## Response Logging
Response of verification can be logged via the code given below. You can see this in LogCat at runtime. Write this code in Response listener of SDK:
```sh

//To view the errors of request
String error = responseSet.get("error");

Log.e("LoggingResp", error);

//To get the status of request
 String event = responseSet.get("event");
 
	if(event.equalsIgnoreCase("verification.accepted")){
	
	//Verification accepted do whatever you want to do
		Log.i("LoggingResp", event);
	}else{
	
	//Verification declined do whatever you want to do
	Log.i("LoggingResp", event);
	}

```
**Note:** Run project on a real device.

## Status Response
The Shufti Pro Verification API will send a JSON response if a status request is made.

* <h3>reference</h3>
	Your unique request reference, which you provided us at the time of request, so that you can identify the response in relation to the request made.

* <h3>event</h3>
	This is the request event which shows status of request. Event is changed in every response. Please consult
	[Status Codes](https://github.com/Saudali009/Shuftipro-SDK-Android/blob/master/status_codes.md) for more information.

<aside class="notice">
Note: <b>request.invalid</b> response with <b>HTTP status code 400</b> means the request is invalid.
</aside>

>Sample Response  

```json
{
    "reference": "17374217",
    "event": "request.invalid"
}
```

## Sample project setup
In DetailFragment.java file add your **Client ID** on line 86 and **Secret Key** on line 87, thats it!
> **Note:** Run project on a real device.

# Test IDs
Shufti Pro provides the users with a number of test documents. Customers may use these to test the demo, instead of presenting their actual information. <br><br>


[![](https://raw.githubusercontent.com/shuftipro/integration-guide/master/assets/realFace.jpg?v=1)](https://raw.githubusercontent.com/shuftipro/integration-guide/master/assets/realFace.jpg?v=1) 

[![](https://raw.githubusercontent.com/shuftipro/integration-guide/master/assets/realId.jpg)](https://raw.githubusercontent.com/shuftipro/integration-guide/master/assets/realId.jpg) <br>

## Contact
If you have any questions/queries regarding implementation of SDK please feel free to contact our [tech support](mailto:support@shuftipro.com).

## Copyright
2016-18 © Shufti Pro Ltd.
