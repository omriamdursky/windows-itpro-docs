---
title: Information protection in Windows overview
ms.reviewer:
description: Learn about how information protection works in Windows to identify and protect sensitive information
keywords: information, protection, dlp, data, loss, prevention, protect
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
---

# Information protection in Windows overview

**Applies to:**

- [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)](https://go.microsoft.com/fwlink/p/?linkid=2069559)

[!include[Prerelease information](../../includes/prerelease.md)]

Information protection is an integral part of Microsoft 365 Enterprise suite, providing intelligent protection to keep sensitive data secure while enabling productivity in the workplace.


>[!TIP]
> Read our blog post about how [Microsoft Defender ATP integrates with Microsoft Information Protection to discover, protect, and monitor sensitive data on Windows devices](https://cloudblogs.microsoft.com/microsoftsecure/2019/01/17/windows-defender-atp-integrates-with-microsoft-information-protection-to-discover-protect-and-monitor-sensitive-data-on-windows-devices/).

Microsoft Defender ATP applies the following methods to discover, classify, and protect data:

- **Data discovery** - Identify sensitive data on Windows devices at risk
- **Data classification** - Automatically detect when content has been assigned a Sensitivity label, or it contains data that matches a Sensitive information types


## Data discovery and data classification

Microsoft Defender ATP automatically discovers files with sensitivity labels and files that contain sensitive information types.

Sensitivity labels classify and help protect sensitive content.

Sensitive information types in the Office 365 data loss prevention (DLP) implementation fall under two categories:

- Default
- Custom

Default sensitive information types include information such as bank account numbers, social security numbers, or national IDs. For more information, see [What the sensitive information type look for](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for).

Custom types are ones that you define and is designed to protect a different type of sensitive information (for example, employee IDs or project numbers). For more information see, [Create a custom sensitive information type](https://docs.microsoft.com/office365/securitycompliance/create-a-custom-sensitive-information-type).

When a file is created or edited on a  Windows device, Microsoft Defender ATP scans the content to evaluate if it contains sensitive information.

Turn on the Azure Information Protection integration so that when a file that contains sensitive information is discovered by Microsoft Defender ATP though labels or information types, it is automatically forwarded to Azure Information Protection from the device.

![Image of settings page with Azure Information Protection](images/atp-settings-aip.png)

The reported signals can be viewed on the Azure Information Protection – Data discovery dashboard.

## Azure Information Protection - Data discovery dashboard

This dashboard presents a summarized discovery information of data discovered by both Microsoft Defender ATP and Azure Information Protection. Data from Microsoft Defender ATP is marked with Location Type - Endpoint.

![Image of Azure Information Protection - Data discovery](images/azure-data-discovery.png)

Notice the Device Risk column on the right, this device risk is derived directly from Microsoft Defender ATP, indicating the risk level of the security device where the file was discovered, based on the active security threats detected by Microsoft Defender ATP.

Click on a device to view a list of files observed on this device, with their sensitivity labels and information types.

>[!NOTE]
>Please allow approximately 15-20 minutes for the Azure Information Protection Dashboard Discovery to reflect discovered files.

## Log Analytics

Data discovery based on Microsoft Defender ATP is also available in [Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview), where you can perform complex queries over the raw data.

For more information on Azure Information Protection analytics, see [Central reporting for Azure Information Protection](https://docs.microsoft.com/azure/information-protection/reports-aip).

Open Azure Log Analytics in Azure Portal and open a query builder (standard or classic).

To view Microsoft Defender ATP data, perform a query that contains:

```
InformationProtectionLogs_CL
| where Workload_s == "Windows Defender"
```

**Prerequisites:**

- Customers must have a subscription for Azure Information Protection.
- Enable Azure Information Protection integration in Microsoft Defender Security Center:
    - Go to **Settings** in Microsoft Defender Security Center, click on **Advanced Settings** under **General**.



