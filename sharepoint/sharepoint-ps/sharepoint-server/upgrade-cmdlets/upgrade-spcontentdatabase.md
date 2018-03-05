---
title: "Upgrade-SPContentDatabase"
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 11/23/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9c7f1a52-02a7-452d-9746-a4e89aa54874

description: "Resumes a failed database upgrade or begins a build-to-build database upgrade."
---

# Upgrade-SPContentDatabase

Resumes a failed database upgrade or begins a build-to-build database upgrade.
  
```
Upgrade-SPContentDatabase -Identity <SPContentDatabasePipeBind> <COMMON PARAMETERS>

```

## Example

--------------------------EXAMPLE 1------------------------------ 
  
```
Upgrade-SPContentDatabase WSS_Content
```

This example upgrades the existing WSS_Content content database schema and then performs only build-to-build upgrade actions on existing site collections if required. This operation does not changed the CompatibilityLevel for existing site collections in this database.
  
--------------------------EXAMPLE 2------------------------------ 
  
```
Upgrade-SPContentDatabase WSS_Content -SkipSiteUpgrade
```

This example upgrades the existing WSS_Content content database schema only. No build-to-build upgrade actions are performed on any site collections. This operation does not change The CompatibilityLevel for existing site collections in this database.
  
--------------------------EXAMPLE 3------------------------------ 
  
```
Upgrade-SPContentDatabase WSS_Content -SkipSiteUpgrade -UseSnapshot
```

This example upgrades the existing WSS_Content content database schema only while using a snapshot of the database to retain read-only access to the content during the upgrade. No build-to-build upgrade actions are performed on any site collections. This operation does not change the CompatibilityLevel for existing site collections in this database.
  
## Detailed Description

This cmdlet contains more than one parameter set. You may only use parameters from one parameter set, and you may not combine parameters from different parameter sets. For more information about how to use parameter sets, see [Cmdlet Parameter Sets](https://go.microsoft.com/fwlink/?LinkID=187810). 
  
Use the **Upgrade-SPContentDatabase** cmdlet to resume a failed database upgrade or begin a build-to-build database upgrade against a SharePoint content database. The **Upgrade-SPContentDatabase** cmdlet initiates an upgrade of an existing content database that is attached to the current farm. This cmdlet begins a new upgrade session, which can be used either to resume a failed version-to-version or build-to-build upgrade of a content database or to begin a build-to-build upgrade of a content database. 
  
If the database is hosted on a version of SQL Server that supports creation and use of snapshots of the database, this cmdlet can use a database snapshot for build-to-build upgrades. During upgrade, users see a ready-only version of the database, which is the snapshot. After upgrade users see upgraded content.
  
The default behavior of this cmdlet causes an upgrade of the schema of the database and initiates build-to-build upgrades for all site collections within the specified content database if required. To prevent build-to-build upgrades of site collections, use the **SkipSiteUpgrade** parameter. This cmdlet does not trigger version-to-version upgrade of any site collections. 
  
For permissions and the most current information about Windows PowerShell for SharePoint Products, see the online documentation at [Windows PowerShell for SharePoint Server 2016 reference](https://go.microsoft.com/fwlink/p/?LinkId=671715).
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.SharePoint.PowerShell.SPContentDatabasePipeBind  <br/> |Specifies the content database to upgrade.  <br/> The value must be a valid GUID, in the form 12345678-90ab-cdef-1234-567890bcdefgh or an instance of a valid **SPContentDatabase** object.  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Specifies the name of attached content database.  <br/> |
| _WebApplication_ <br/> |Required  <br/> |Microsoft.SharePoint.PowerShell.SPWebApplicationPipeBind  <br/> |Specifies the web application that hosts the attached content database.  <br/> |
| _AllowUnattached_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Lets the upgrade process to proceed on a content database which is not currently attached to a SharePoint farm.  <br/> |
| _AssignmentCollection_ <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> |Manages objects for the purpose of proper disposal. Use of objects, such as **SPWeb** or **SPSite**, can use large amounts of memory and use of these objects in Windows PowerShell scripts requires proper memory management. Using the **SPAssignment** object, you can assign objects to a variable and dispose of the objects after they are needed to free up memory. When **SPWeb**, **SPSite**, or **SPSiteAdministration** objects are used, the objects are automatically disposed of if an assignment collection or the **Global** parameter is not used.  <br/> > [!NOTE]> When the **Global** parameter is used, all objects are contained in the global store. If objects are not immediately used, or disposed of by using the **Stop-SPAssignment** command, an out-of-memory scenario can occur.           |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
| _ForceDeleteLock_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Forces deletion of locks on the database before the upgrade starts.  <br/> |
| _ServerInstance_ <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPDatabaseServiceInstancePipeBind  <br/> |The SQL Server instance that hosts the attached content database.  <br/> |
| _SkipIntegrityChecks_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Specifies the upgrade process not to run the internal integrity checks such as missing templates, and orphan detection as part of the upgrade process.  <br/> |
| _SkipSiteUpgrade_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Specifies to not upgrade databases and their child objects when performing upgrade.  <br/> |
| _UseSnapshot_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Specifies to use the snapshot method to perform unattached upgrade. This will make a snapshot of the current database and then perform all upgrade operations that apply to the database, and optionally to its contents.  <br/> The existing connections to the content database will be set to use the snapshot for the duration of the upgrade, and then switched back after successful completion of upgrade. A failed upgrade reverts the database to its state when the snapshot was taken.  <br/> This parameter only works for versions of SQL Server that support creation and use of snapshots, for example, SQL Server Enterprise edition.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
   
## See also

#### 

[Dismount-SPContentDatabase](../../../docs-conceptual/sharepoint-server/microsoft-powershell-for-sharepoint-server-reference/database-cmdlets/dismount-spcontentdatabase.md)
  
[Get-SPContentDatabase](../../../docs-conceptual/sharepoint-server/microsoft-powershell-for-sharepoint-server-reference/database-cmdlets/get-spcontentdatabase.md)
  
[Mount-SPContentDatabase](../../../docs-conceptual/sharepoint-server/microsoft-powershell-for-sharepoint-server-reference/database-cmdlets/mount-spcontentdatabase.md)
  
[Set-SPContentDatabase](../../../docs-conceptual/sharepoint-server/microsoft-powershell-for-sharepoint-server-reference/database-cmdlets/set-spcontentdatabase.md)
  
[Test-SPContentDatabase](../../../docs-conceptual/sharepoint-server/microsoft-powershell-for-sharepoint-server-reference/database-cmdlets/test-spcontentdatabase.md)
#### 

[New-SPContentDatabase](http://technet.microsoft.com/library/18cf18cd-8fb7-4561-be71-41c767f27b51.aspx)
  
[Remove-SPContentDatabase](http://technet.microsoft.com/library/e8c337b6-37af-4fdd-8469-a32f4d45c040.aspx)

