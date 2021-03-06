---
# required metadata

title: Create snapshot reports of Cloud Discovery cloud app use | Microsoft Docs
description: This article provides information about how to upload logs manually to create a snapshot report of your Cloud Discovery apps.
keywords:
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/07/2018
ms.topic: conceptual
ms.prod:
ms.service: cloud-app-security
ms.technology:
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: reutam
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
*Applies to: Microsoft Cloud App Security*


# Create snapshot Cloud Discovery reports
It is important to upload a log manually and let Microsoft Cloud App Security parse it before attempting to use the automatic log collector. For information on how the log collector works and the expected log format, see [Using traffic logs for Cloud Discovery](#log-format).

If you don't have a log yet and you want to see a sample of what your log should look like, follow the procedure below, and download a sample log file to see what your log is supposed to look like.


To create a snapshot report:
  
1. Collect log files from your firewall and proxy, through which users in your organization access the Internet. Make sure to gather logs during times of peak traffic that are representative of all user activity in your organization.  
  
2. In the Cloud App Security portal, click on **Discover** and then **Create new snapshot report**.  
  
   ![Create new snapshot report](./media/create-new-snapshot-report.png)
     
3. Enter a **Report name** and a **Description**
  
    ![New snapshot report](./media/new-snapshot-report.png) 

4. Select the **Data source** from which you want to upload the log files.  
  
5. Verify your log format to make sure that it is formatted properly according to the sample you can download. Click **View and verify** and then click **Download sample log**. Then compare your log with the sample provided to make sure it's compatible. 

   ![Verify your log format](./media/cloud-discovery-snapshot-verify.png)  

   > [!NOTE]
   > The FTP sample format is supported in snapshots and automated upload while syslog is supported in automated upload only.<br></br>
   Downloading a sample log will download a sample FTP log.


6. **Choose the traffic logs** that you want to upload. You can upload up to 20 files at once. Compressed and zipped files are also supported.  
  
7. Click **Create**.  

8. After upload completes, the status message will appear at the top right corner of your screen letting you know that your log was successfully uploaded.  
  
9. After you upload your log files, it will take some time for them to be parsed and analyzed.  
   After processing of your log files completes, you will receive an email to notify you that it is done. 
  
10. A notification banner will appear in the status bar at the top of the portal to update you with the processing status of your log files.  
    ![processing log file menu bar](./media/processing-log-file-menu-bar.png) 
   
11. After the logs are uploaded successfully, you should see a notification letting you know that the log file processing completed successfully. At this point, a you can view the report either by clicking the link in the status bar, or by going to the Settings cog, and selecting **Cloud Discovery settings**.   
  
     ![Discovery settings tab](./media/discovery-settings-tab.png)
12. Then selecting **Snapshot reports** and select your snapshot report.
 
![snapshot report management](./media/snapshot-report-managment.png)

  
## Using traffic logs for Cloud Discovery <a name="log-format"></a>
Cloud Discovery utilizes the data in your traffic logs. The more detailed your log, the better visibility you get. Cloud Discovery requires web-traffic data with the following attributes:
- Date of the transaction
- Source IP
- Source user - highly recommended
- Destination IP address
- Destination URL **recommended** (URLs provide higher accuracy for cloud app detection than IP addresses)
- Total amount of data (data information is highly valuable)
- Amount of uploaded or downloaded data (provides insights about the usage patterns of the cloud apps)
- Action taken (allowed/blocked)

Cloud Discovery cannot show or analyze attributes that are not included in your logs.
For example, **Cisco ASA Firewall** standard log format does not contain the **number of uploaded bytes per transaction** nor **Username**, and does not contain **Target URL** (but only target IP).
Therefore, these attributes will not be shown in Cloud Discovery data for these logs, and the visibility into the cloud apps will be limited. For Cisco ASA firewalls, it is necessary to set the information level to 6. 


In order to successfully generate a Cloud Discovery report, your traffic logs must meet the following conditions:
1.  Data source is supported (see list below).
2.  Log format matches the expected standard format (this will be checked upon upload by the Log tool).
3.  Events are not more than 90 days old.
4.  The log file is valid and includes outbound traffic information.



## Supported firewalls and proxies <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Web App Firewall (W3C)
- Blue Coat Proxy SG - Access log (W3C)
- Check Point
- Cisco ASA Firewall (For Cisco ASA firewalls, it is necessary to set the information level to 6)
- Cisco ASA with FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – URLs log
- Clavister NGFW (Syslog)
- Digital Arts i-FILTER
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Palo Alto series Firewall
- Sonicwall (formerly Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (Common)
- Squid (Native)
- Websense - Web Security Solutions - Investigative detail report (CSV)
- Websense - Web Security Solutions - Internet activity log (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery supports both IPv4 and IPv6 addresses.

If your log is not supported, select **Other** as the **Data source** and specify the appliance and log you are trying to upload. Your log will be reviewed by the Cloud App Security cloud analyst team and you will be notified if support for your log type is added. Alternatively, you can define a custom parser that matches your format. For more information, see [Use a custom log parser](custom-log-parser.md).


Data attributes (according to vendor documentation):


|                 Data source                  |    Target App URL    |    Target App IP     |       Username       |      Origin IP       |    Total traffic     |    Uploaded bytes    |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
|                  Barracuda                   | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |          No          |          No          |
|                  Blue Coat                   | <strong>Yes</strong> |          No          | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                  Checkpoint                  |          No          | <strong>Yes</strong> |          No          | <strong>Yes</strong> |          No          |          No          |
|              Cisco ASA (Syslog)              |          No          | <strong>Yes</strong> |          No          | <strong>Yes</strong> | <strong>Yes</strong> |          No          |
|           Cisco ASA with FirePOWER           | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                  Cisco FWSM                  |          No          | <strong>Yes</strong> |          No          | <strong>Yes</strong> | <strong>Yes</strong> |          No          |
|              Cisco Ironport WSA              | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                 Cisco Meraki                 | <strong>Yes</strong> | <strong>Yes</strong> |          No          | <strong>Yes</strong> |          No          |          No          |
|           Clavister NGFW (Syslog)            | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                SonicWall (formerly Dell)                | <strong>Yes</strong> | <strong>Yes</strong> |          No          | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|            Digital Arts i-FILTER             | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                  Fortigate                   |          No          | <strong>Yes</strong> |          No          | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                 Juniper SRX                  |          No          | <strong>Yes</strong> |          No          | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                 Juniper SSG                  |          No          | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                  McAfee SWG                  | <strong>Yes</strong> |          No          |          No          | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                    MS TMG                    | <strong>Yes</strong> |          No          | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|              Palo Alto Networks              |          No          | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                    Sophos                    | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |          No          |
|                Squid (Common)                | <strong>Yes</strong> |          No          | <strong>Yes</strong> | <strong>Yes</strong> |          No          | <strong>Yes</strong> |
|                Squid (Native)                | <strong>Yes</strong> |          No          | <strong>Yes</strong> | <strong>Yes</strong> |          No          | <strong>Yes</strong> |
| Websense - Investigative detail report (CSV) | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|    Websense - Internet activity log (CEF)    | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
|                   Zscaler                    | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> | <strong>Yes</strong> |
     
 
## See Also  
[Control cloud apps with policies](control-cloud-apps-with-policies.md)   

[Premier customers can also choose Cloud App Security directly from the Premier Portal.](https://premier.microsoft.com/)  
    
      
  