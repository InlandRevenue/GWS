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

## Return Status Push Notification ZIP/XML Sample Files:

* [ZIP file:](Sample%20Files/PSN_DAILY_PROVIDER_1500216000_2155445580_2155445927_201909091028315313_NZX.zip) `PSN_DAILY_PROVIDER_1500216000_2155445580_2155445927_201909091028315313_NZX.zip`
    * DAILY AGENT File `PSN_DAILY_AGENT_IRD_132349932_2155445580_2155445927_201909091028315782_NZX.xml`
	* DAILY CUSTOMER File `PSN_DAILY_CUSTOMER_2155445580_2155445927_201909091028315782_NZX.xml`
* [XML Control File](Sample%20Files/PSN_DAILY_PROVIDER_1500216000_2155445580_2155445927_201909091028316719_NZX_CONTROL.xml)  `PSN_DAILY_PROVIDER_1500216000_2155445580_2155445927_201909091028316719_NZX_CONTROL.xml`

> NOTE: The real production and non-production the XML and ZIP files will be PGP encrypted.

## Requirements: 

* Software Providers needs to provide the following:
	* IP Address and port number for a SFTP server
	* SFTP Username and Password 
	* SFTP remote directory 
	* Public PGP key - used for payload encryption (See [openpgp.org](openpgp.org) for more information)
	
* The On-boarding Team will provide a 
	* SSH Keys for SFTP Public Key Authentication 

## Products using this service:
* [Income Tax](../Product%20-%20Income%20Tax/)

## Supporting services
* Service: Intermediation – view [Schemas, WSDLs, and build pack](../Service%20-%20Intermediation/)
* Service: Software Intermediation – view [Schemas, WSDLs, and build pack](../Service%20-%20Software%20Intermediation/)


