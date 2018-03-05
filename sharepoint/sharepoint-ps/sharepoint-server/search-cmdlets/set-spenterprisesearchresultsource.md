---
title: "Set-SPEnterpriseSearchResultSource"
ms.author: tlarsen
author: tlarsen
manager: laurawi
ms.date: 11/29/2015
ms.audience: ITPro
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d52033b9-ea2a-4830-a766-efa0d2016a31

description: "Sets properties of a result source."
---

# Set-SPEnterpriseSearchResultSource

Sets properties of a result source.
  
```
Set-SPEnterpriseSearchResultSource -Identity <ResultSourcePipeBind> [-AssignmentCollection <SPAssignmentCollection>] [-AuthenticationType <Anonymous | LocalNTAuth | SingleAccountBasicAuth | SingleAccountFormsAuthentication | SingleAccountCookie | ApplicationPoolIdentity | Kerberos | PerUserFormsAuthentication | PerUserCookie | SSO | SingleAccountNTLM | PerUserNTLM | SingleAccountDigest | PerUserDigest | PerUserBasicAuth | Custom | PerUserCustom>] [-AutoDiscover <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-MakeDefault <$true | $false>] [-Name <String>] [-Owner <SearchObjectOwner>] [-Password <String>] [-ProviderId <Guid>] [-QueryTemplate <String>] [-RemoteUrl <String>] [-SearchApplication <SearchServiceApplicationPipeBind>] [-SsoId <String>] [-UserName <String>] [-WhatIf [<SwitchParameter>]]

```

## Example

--------EXAMPLE 1------
  
```
$ssa = Get-SPEnterpriseSearchServiceApplication -Identity "Search Service Application"
```

```
$owner = Get-SPEnterpriseSearchOwner -Level SSA
```

```
$customResultSource = New-SPEnterpriseSearchResultSource -SearchApplication $ssa -Owner $owner -ProviderId fa947043-6046-4f97-9714-40d4c113963d -Name "Custom SharePoint Result Source"
```

```
Set-SPEnterpriseSearchResultSource -Identity $customResultSource -Name "Basic SharePoint Result Source"
```

This example updates the description of the result source, and the identity of the result source is specified by name.
  
--------EXAMPLE 2------
  
```
$ssa = Get-SPEnterpriseSearchServiceApplication -Identity "Search Service Application"
```

```
$owner = Get-SPEnterpriseSearchOwner -Level SSA
```

```
$customResultSource = New-SPEnterpriseSearchResultSource -SearchApplication $ssa -Owner $owner -ProviderId fa947043-6046-4f97-9714-40d4c113963d -Name "Custom SharePoint Result Source"
```

```
Set-SPEnterpriseSearchResultSource -SearchApplication $ssa -Owner $owner -Identity "Custom SharePoint Result Source" -Description "A custom SharePoint Result Source for demonstration purposes"
```

This example updates the description of the result source, and the identity of the result source is specified by name.
  
## Detailed Description

This cmdlet updates properties of a user-created result source. This cmdlet supports the same update operations as are supported through the "Manage Result Sources" page in the SharePoint Central Administration website. The result source cannot be a built-in source (a built-in source has the BuiltIn property set to true) for any update operation other than changing the default result source using the MakeDefault parameter.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Office.Server.Search.Cmdlet.ResultSourcePipeBind  <br/> |Specifies the result source to update. The type must be a valid GUID string, in the form 12345678-90ab-cdef-1234-567890bcdefgh; a valid name of a result source (for example, "Custom SharePoint Result Source"); or an instance of a valid ****Source object.  <br/> |
| _AssignmentCollection_ <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> |Manages objects for the purpose of proper disposal. Use of objects, such as **SPWeb** or **SPSite**, can use large amounts of memory and use of these objects in Windows PowerShell scripts requires proper memory management. Using the **SPAssignment** object, you can assign objects to a variable and dispose of the objects after they are needed to free up memory. When **SPWeb**, **SPSite**, or **SPSiteAdministration** objects are used, the objects are automatically disposed of if an assignment collection or the **Global** parameter is not used.  <br/> > [!NOTE]> When the **Global** parameter is used, all objects are contained in the global store. If objects are not immediately used, or disposed of by using the **Stop-SPAssignment** command, an out-of-memory scenario can occur.           |
| _AuthenticationType_ <br/> |Optional  <br/> |Microsoft.Office.Server.Search.Administration.FederationAuthType  <br/> |Specifies an authentication type for the result source. If parameter is not changed, the value is unchanged.A specific set of authentication types are supported for each search provider type and, if parameter is not specified, the authentication type will default based on search provider type. This cmdlet supports the following set of authentication mechanisms and corresponding types: Default SharePoint Authentication ( **FederationAuthType.LocalNTAuth**), Basic Authentication ( **FederationAuthType.SingleAccountBasicAuth** - specify UserName and Password), Default Remote SharePoint Authentication ( **FederationAuthType.PerUserBasicAuth**), Single Sign On ( **FederationAuthType.SSO** - requires SsoId to be specified), Anonymous ( **FederationAuthType.Anonymous**), Digest Authentication ( **FederationAuthType.SingleAccountDigest** - specify UserName and Password), NTLM Application Pool Identity ( **FederationAuthType.ApplicationPoolIdentity**), NTLM User Name and Password ( **FederationAuthType.SingleAccountNTLM** - specify UserName and Password). When using a Local SharePoint Search/Local SharePoint People Search provider, then **FederationAuthType.LocalNTAuth** (default) and **FederationAuthType.SingleAccountBasicAuth** are supported. When using a Remote SharePoint Search/Remote SharePoint People Search provider, then **FederationAuthType.PerUserBasicAuth** (default) and **FederationAuthType.SSO** are supported. When using OpenSearch 1.0/1.1 search provider, then the following authentication types are supported: **FederationAuthType.Anonymous** (default), **FederationAuthType.SingleAccountBasicAuth**, **FederationAuthType.SingleAccountDigest**, **FederationAuthType.SingleAccountNTLM**, and **FederationAuthType.ApplicationPoolIdentity**.  <br/> |
| _AutoDiscover_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether to use automatic discovery of the Exchange Server endpoint for the result source provider. Setting value to true ($true) states that automatic discovery should be used. If the parameter is not specified, the value is unchanged. Only applicable when using an Exchange search provider.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Specifies a description for the result source. If the parameter is not specified, the value is unchanged.  <br/> |
| _MakeDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether the result source should be set as default result source or not, for the scope specified by the **Owner** parameter. If parameter is not specified, the default result source will not change. Setting value to true ($true) states that the result source should be set as default. Setting value to false ($false) states that the result source should not be set as default and, in this case, if the result source to update is currently the default, the original default result source ("Local SharePoint Results") will be set as default again.Tip: Use instance, not name or GUID string Id, as **Identity** when using **Makedefault**, to clearly specify that **Owner** is only to be used for specifying the level where the result source should be set as default (if value is true) or where the default should be reset to original (if value is false).  <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Specifies a name for the result source. If parameter is not specified, the value is unchanged. Names must be unique at each administrative level. For example, two result sources in a site cannot share a name, but one in a site and one provided by the site collection can.  <br/> |
| _Owner_ <br/> |Optional  <br/> |Microsoft.Office.Server.Search.Administration.SearchObjectOwner  <br/> |Specifies the search object owner that defines the scope at which the corresponding result source is available.  <br/> |
| _Password_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the password of the user credentials to use to connect to the result source. If parameter is not specified, the value is unchanged. Used when authentication type (AuthenticationType) is set to a type that consumes user credentials ( **FederationAuthType.SingleAccountBasicAuth**, **FederationAuthType.SingleAccountDigest** or **FederationAuthType.SingleAccountNTLM**).  <br/> |
| _ProviderId_ <br/> |Optional  <br/> |System.Guid  <br/> |Specifies a search provider to be used by the result source. If parameter is not specified, the value is unchanged. Is specified as a Guid or GUID string, which must be one of the following: **FA947043-6046-4F97-9714-40D4C113963D** (Local SharePoint Search), **E4BCC058-F133-4425-8FFC-1D70596FFD33** (Local SharePoint People Search), **1E0C8601-2E5D-4CCB-9561-53743B5DBDE7** (Remote SharePoint Search), **E377CAAA-FCAF-4a1b-B7A1-E69A506A07AA** (Remote SharePoint People Search), **3A17E140-1574-4093-BAD6-E19CDF1C0122** (Exchange Search), **3A17E140-1574-4093-BAD6-E19CDF1C0121** (OpenSearch 1.0/1.1). **FA947043-6046-4F97-9714-40D4C113963D** (Local SharePoint Search), **E4BCC058-F133-4425-8FFC-1D70596FFD33** (Local SharePoint People Search), **1E0C8601-2E5D-4CCB-9561-53743B5DBDE7** (Remote SharePoint Search), **E377CAAA-FCAF-4a1b-B7A1-E69A506A07AA** (Remote SharePoint People Search), **3A17E140-1574-4093-BAD6-E19CDF1C0122** (Exchange Search), **3A17E140-1574-4093-BAD6-E19CDF1C0121** (OpenSearch 1.0/1.1).  <br/> |
| _QueryTemplate_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the query transformation template of the result source. If parameter is not specified, the value is unchanged. Incoming queries are changed according to the template, to use this new query text instead. Include the incoming query in the new text by using the query variable "{searchTerms}". Use this to scope results. For example, to only return OneNote items, set the new text to "{searchTerms} fileextension=one". Then, an incoming query "sharepoint" becomes "sharepoint fileextension=one". Default value is {searchTerms}.  <br/> |
| _RemoteUrl_ <br/> |Optional  <br/> |System.String  <br/> |Specifies a connection URL template for the result source. If parameter is not specified, the value is unchanged. Must be set when using a search provider that consumes it: Remote SharePoint Search, Remote SharePoint People Search, OpenSearch 1.0/1.1, and Exchange (if AutoDiscover is not turned on). When using other search providers the parameter is ignored. For Remote SharePoint Search/Remote SharePoint People Search, specify the address of the root site collection of the remote SharePoint farm. For OpenSearch 1.0/1.1, specify the URL of the OpenSearch source. Include the query in the URL by using the query variable "{searchTerms}", which will be automatically replaced with the query. For Exchange, specify the Exchange EWS URL from which to retrieve results.  <br/> |
| _SearchApplication_ <br/> |Optional  <br/> |Microsoft.Office.Server.Search.Cmdlet.SearchServiceApplicationPipeBind  <br/> |Specifies the search application. The type must be a valid GUID, in the form 12345678-90ab-cdef-1234-567890bcdefgh; a valid search application name (for example, SearchApp1); or an instance of a valid **SearchServiceApplication** object.  <br/> |
| _SsoId_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the reverse proxy certificate Secure Store Id to use to connect to the result source. If parameter is not specified, the value is unchanged. Must be specified if authentication type ( **AuthenticationType**) is set to **FederationAuthType.SSO** (Single Sign On). If you are connecting to your intranet through a reverse proxy, enter the SSO Id of the Single Sign On entry which stores the certificate used to authenticate against the reverse proxy.  <br/> |
| _UserName_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the user name of the user credentials to use to connect to the result source. If parameter is not specified, the value is unchanged. Used when authentication type ( **AuthenticationType**) is set to a type that consumes user credentials ( **FederationAuthType.SingleAccountBasicAuth**, **FederationAuthType.SingleAccountDigest** or **FederationAuthType.SingleAccountNTLM**).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
   
## AutoGenParams

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Identity** <br/> |Required  <br/> |Microsoft.Office.Server.Search.Cmdlet.ResultSourcePipeBind  <br/> ||
|**AssignmentCollection** <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> ||
|**AuthenticationType** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**AutoDiscover** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Description** <br/> |Optional  <br/> |System.String  <br/> ||
|**MakeDefault** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**Name** <br/> |Optional  <br/> |System.String  <br/> ||
|**Owner** <br/> |Optional  <br/> |Microsoft.Office.Server.Search.Administration.SearchObjectOwner  <br/> ||
|**Password** <br/> |Optional  <br/> |System.String  <br/> ||
|**ProviderId** <br/> |Optional  <br/> |System.Guid  <br/> ||
|**QueryTemplate** <br/> |Optional  <br/> |System.String  <br/> ||
|**RemoteUrl** <br/> |Optional  <br/> |System.String  <br/> ||
|**SearchApplication** <br/> |Optional  <br/> |Microsoft.Office.Server.Search.Cmdlet.SearchServiceApplicationPipeBind  <br/> ||
|**SsoId** <br/> |Optional  <br/> |System.String  <br/> ||
|**UserName** <br/> |Optional  <br/> |System.String  <br/> ||
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   
## See also

#### 

[New-SPEnterpriseSearchResultSource](new-spenterprisesearchresultsource.md)
  
[Get-SPEnterpriseSearchResultSource](get-spenterprisesearchresultsource.md)
  
[Remove-SPEnterpriseSearchResultSource](remove-spenterprisesearchresultsource.md)

