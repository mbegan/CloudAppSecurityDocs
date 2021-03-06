---
# required metadata

title: Deploy Cloud Discovery with Microsoft Cloud App Security | Microsoft Docs
description: This topic describes the setup procedure for getting Cloud Discovery working.
keywords:
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/7/2018
ms.topic: conceptual
ms.prod:
ms.service: cloud-app-security
ms.technology:
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080

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


# Set up Cloud Discovery
Cloud Discovery analyzes your traffic logs against Microsoft Cloud App Security's cloud app catalog of over 16,000 cloud apps that are ranked and scored based on more than 70 risk factors, to provide you with ongoing visibility into cloud use, Shadow IT, and the risk Shadow IT poses into your organization.

## Snapshot and continuous risk assessment reports 

There are two types of reports you can generate: 
- **Snapshot reports** provide ad-hoc visibility on a set on traffic logs you manually upload from your firewalls and proxies.

- **Continuous reports** analyze all logs that are forwarded from your network using Cloud App Security. They provide improved visibility over all data, and automatically identify anomalous use using either the Machine Learning anomaly detection engine or by using custom policies that you define. These reports can be created by connecting in the following ways:
  - [Windows Defender ATP integration](wdatp-integration.md): Cloud App Security integrates with Windows Defender Advanced Threat Protection (ATP) natively, to simplify roll out of Cloud Discovery, extend Cloud Discovery capabilities beyond your corporate network, and enable machine-based investigation.
  - [Log collector]( ):
  - [Zscaler integration](zscaler-integration.md): 

## Log process flow: From raw data to risk assessment  
The process of generating a risk assessment consists of the following steps and takes between a few minutes to several hours depending on the amount of data processed.  

-   **Upload** – Web traffic logs from your network are uploaded to the portal.  

-   **Parse** – Cloud App Security parses and extracts traffic data from the traffic logs with a dedicated parser for each data source.  

-   **Analyze** – Traffic data is analyzed against the Cloud App Catalog to identify more than 16,000 cloud apps and to assess their risk score. Active users and IP addresses are also identified as part of the analysis.  

-   **Generate report** - A risk assessment report of the data extracted from log files is generated.   


>[!NOTE]
>- Continuous report data is analyzed twice a day.
> 


## See also

[Create snapshot Cloud Discovery reports](create-snapshot-cloud-discovery-reports.md)

[Configure automatic log upload for continuous reports](configure-automatic-log-upload-for-continuous-reports.md)

[Working with Cloud Discovery data](working-with-cloud-discovery-data.md)