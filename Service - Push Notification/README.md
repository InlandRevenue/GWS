![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Return Status Push Notifications Service 

The Return Status Push Notification file is intended to be used by software providers where 
large quantities of return status data is required. 

The Return Status Push Notification is based around a file transfer solution, where Inland 
Revenue will send information via SFTP to the software provider on a daily (overnight) basis in 
the evening of each business day.  

## Key Features:
* View and download [build packs for Push Notifications](Gateway%20Services%20Build%20Pack%20-%20Push%20Notifications.pdf)

## Sample Notification XML Files
* File Transfer Zip File `PSN_DAILY_PROVIDER_1500131086_3456933072_3456625734_201904151848065112_NZD.zip`:
    * Child Files:
        *  [Customer File](Sample%20Files/PSN_DAILY_CUSTOMER_3456933072_3456625734_201904151848067017_NZD.xml) `PSN_DAILY_CUSTOMER_3456933072_3456625734_201904151848067017_NZD.xml`
        * [Intermediation File](Sample%20Files/PSN_DAILY_PROVIDER_1500131086_3456933072_3456625734_201904151848065112_NZD_INTERMEDIATION.xml)	`PSN_DAILY_PROVIDER_1500131086_3456933072_3456625734_201904151848065112_NZD_INTERMEDIATION.xml` __To Be Confirmed__
        * [Software Intermediation File](Sample%20Files/PSN_DAILY_PROVIDER_1500131086_3456612467_3456822335_201904151034148527_SOFTWARE_INTERMEDIATION.xml) `PSN_DAILY_PROVIDER_1500131086_3456612467_3456822335_201904151034148527_SOFTWARE_INTERMEDIATION.xml` __To Be Confirmed__ 
* Complimenting (Sibling) [Control File](Sample%20Files/PSN_DAILY_PROVIDER_1500131086_3456933072_3456625734_201904151848072877_NZD_CONTROL.xml) `PSN_DAILY_PROVIDER_1500131086_3456933072_3456625734_201904151848072877_NZD_CONTROL.xml`


## Products using this service:
* [Income Tax](../Product%20-%20Income%20Tax/)

## Supporting services
* [Service - Identity and Access](../Service%20-%20Identity%20and%20Access/Latest/)



