![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Income Tax - XML Schema Definition 

All schemas for the Return Service import a [Common.v2.xsd](../../Schema%20-%20Common/Common.v2.xsd) which has some data types specific to Inland Revenue. This [Common.v2.xsd](../../Schema%20-%20Common/Common.v2.xsd) will be used in other Gateway Services outside of the `/Returns/` namespace so it must be kept up-to-date, without numerous redundant versions remaining.  
 
The [ReturnCommon.v2.xsd](../../Service%20-%20Return/Latest/ReturnCommon.v2.xsd) imports the [Common.v2.xsd](../../Schema%20-%20Common/Common.v2.xsd) and creates data types to be used 
across all tax types and return types. [ReturnCommon.v2.xsd](../../Service%20-%20Return/Latest/ReturnCommon.v2.xsd) also includes two request elements and two response elements. These requests are `retrieveFormInfoRequest` and `retrieveFilingObligationsRequest`, while the responses are `retrieveFilingObligationsResponse` and `retrieveStatusResponse`.  
 
The reason for adding root-level elements in the [ReturnCommon.v2.xsd](../../Service%20-%20Return/Latest/ReturnCommon.v2.xsd) is due to the fact that these request and response structures will never change, regardless of the tax type. This allows Inland Revenue to keep a uniform request and response structure across all current and future tax types.  
 
Importing from [ReturnCommon.v2.xsd](../../Service%20-%20Return/Latest/ReturnCommon.v2.xsd) will be schemas that require more fine grained detail. These will primarily define the request for the `File` operation, the response for `RetrieveReturn` and the response for `Prepop`.  
 
## Income Return Common XSD

The [IncomeReturnCommon.v1.xsd](IncomeReturnCommon.v1.xsd) imports the [ReturnCommon.v2.xsd](../../Service%20-%20Return/Latest/ReturnCommon.v2.xsd) and [Common.v2.xsd](../../Schema%20-%20Common/Common.v2.xsd) and creates data types used across many of the specific income tax schemas.

[IncomeReturnCommon.v1.xsd](IncomeReturnCommon.v1.xsd) also includes the `prepopResponse` element. This is because the `prepopResponse` is common between all income tax form types. 

* View and download Income Return Common [IncomeReturnCommon.v1.xsd](IncomeReturnCommon.v1.xsd)
* Download all XSDs in a bundled zip file [Bundle-IncTax-XSD.zip](Bundle-IncTax-XSD.zip)
	
## XSD Schemas	

Every minor form type represents a different return or form. These can be either a primary 
form or an attachment form. Primary forms can be submitted with multiple attachment forms 
in the same payload using the attachmentForms element. Primary forms can only be submitted 
as a primary form, and not inside the attachmentForms element. Attachment forms can be 
submitted alone under the formFields element, or as an attachment under the 
attachmentForms element.  
 
For most forms, only one is allowed to be submitted per period. Some form types, however, 
can be submitted multiple times in the same period, in which case a submissionKey is required 
to be submitted on amendment.  

### 2020 Annual Income Return XSDs 

| Entity Type | Primary Form | XSD schema | minorFormType | Form type | Forms allowed per period | Version | Years supported| Attachment Forms   |
| --- | --- | --- | :---: | :---: | :---: | :---: | :---: | --- |
| Individual   | Individual income tax return| [ReturnIR3.v1.xsd](ReturnIR3.v1.xsd)| `3` | Primary | Single | 1 | 2013+ | <ul><li>IR10</li><li>IR833</li><li>IR3F</li><li>IR3B </li><li>IR3R</li><li>IR3K</li><li>IR307</li><li>IR308</li><li>IR215</li><li>CFC</li></ul>|
|Individual   | Non-resident income tax return |[ReturnIR3NR.v1.xsd](ReturnIR3NR.v1.xsd)| `3NR` | Primary or attachment | Single | 1 | 2013+ | <ul><li>IR10</li><li>IR833</li><li>IR3F</li><li>IR3B</li><li>IR3R</li><li>IR3K</li></ul>|
|Company  | Companies income tax return |[ReturnIR4.v1.xsd](ReturnIR4.v1.xsd)| `4` | Primary | Single |1 | 2013+ | <ul><li>IR10</li><li>IR833</li><li>IR44E</li><li>IR4J</li><li>CFC</li></ul> |
| Company  | Annual imputation return |[ReturnIR4J.v1.xsd](ReturnIR4J.v1.xsd)| `4J` | Primary | Single |1 | 2013+ | |
|Trust or estate | Estate or trust income tax return| [ReturnIR6.v1.xsd](ReturnIR6.v1.xsd)| `6` | Primary | Single |1 | 2013+ | <ul><li>IR10</li><li>IR833</li><li>IR3F</li><li>IR3B</li><li>IR3R</li><li>IR44E</li></ul> |
| Partnerships and look-through companies | Partnership and LTCs income tax return| [ReturnIR7.v1.xsd](ReturnIR7.v1.xsd)| `7` | Primary | Single |1 | 2015+ |<ul><li>IR10</li><li>IR833</li><li>IR3F</li><li>IR3B</li><li>IR3R</li></ul> |
| Māori authority| Māori authorities income tax return |[ReturnIR8.v1.xsd](ReturnIR8.v1.xsd)| `8` | Primary | Single |1 | 2015+ | <ul><li>IR10</li><li>IR833</li><li>IR3F</li><li>IR3B</li><li>IR3J</li></ul>  |
| Māori authority| Māori authorities credit account return |[ReturnIR8J.v1.xsd](ReturnIR8J.v1.xsd)| `8J` | Primary or attachment | Single |1 | 2015+ | |
| Clubs and Societies | Clubs or societies income tax return| [ReturnIR9.v1.xsd](ReturnIR9.v1.xsd)| `9` | Primary | Single |1 | 2015+ | <ul><li>IR10</li><li>IR833</li></ul> |
| Group investment fund | Superannuation funds income tax return |[ReturnIR44.v1.xsd](ReturnIR44.v1.xsd)| `44` | Primary | Single |1 | 2015+ | <ul><li>IR833</li></ul>|
| Group investment fund| Group investment fund return |[ReturnIR44E.v1.xsd](ReturnIR44E.v1.xsd)| `44E` | Attachment | Single |1 | 2013+ | |
| Individual| Farming income |[ReturnIR3F.v1.xsd](ReturnIR3F.v1.xsd)| `3F` | Attachment | Single |1 | 2013+ | | 
| Individual| Schedule of business income |[ReturnIR3B.v1.xsd](ReturnIR3B.v1.xsd)| `3B` | Attachment | Single |1 | 2013+ | 
|Individual | Rental income schedule| [ReturnIR3R.v1.xsd](ReturnIR3R.v1.xsd)| `3R` | Attachment | Multiple |1 | 2013+ | |
| | Sale or disposal of financial arrangements |[ReturnIR3K.v1.xsd](ReturnIR3K.v1.xsd)| `3K` | Attachment | Multiple |1 | 2013+ | | 
| Financial | Financial statements summary |[ReturnIR10.v1.xsd](ReturnIR10.v1.xsd)| `10` | Attachment | Single |1 | 2013+ | |
| | Adjust your income |[ReturnIR215.v1.xsd](ReturnIR215.v1.xsd) | `215` | Primary or attachment | Single |1 | 2015+ | |
| | Schedule of beneficiary’s estate or trust income |[ReturnIR307.v1.xsd](ReturnIR307.v1.xsd)| `307` | Attachment | Multiple |1 | 2013+ | |
| | Branch equivalent tax account return| [ReturnIR308.v1.xsd](ReturnIR308.v1.xsd)| `308` | Attachment | Single |1 | 2013+ | |
| | Property sale information |[ReturnIR833.v1.xsd](ReturnIR833.v1.xsd)| `833` | Primary or attachment | Single |1 | 2016+ | |
| | Controlled foreign investment |[ReturnCFC.v1.xsd](ReturnCFC.v1.xsd)| `CFC ` | Attachment | Single |1 | 2013+ | |
| | Donation Tax credit claim (IR526) | [ReturnREB.v1.xsd](ReturnREB.v1.xsd) | `REB` | | 1| |  |   
| Individual | Auto-calc return | [ReturnAUTO.v1.xsd](ReturnAUTO.v1.xsd) | `CALC`  | Primary | Single | 1 | 2019+ | |



* More information of filing a Tax Return can be found [here](https://www.ird.govt.nz/activities/file-an-income-tax-return)
	
    
