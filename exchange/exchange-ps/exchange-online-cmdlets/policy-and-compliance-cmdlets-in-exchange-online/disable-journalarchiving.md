---
title: "Disable-JournalArchiving"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 1/16/2018
ms.audience: Admin
ms.topic: reference
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 4425a74d-f63e-413f-b42d-8c3ae8d53791
description: "This cmdlet is available only in the cloud-based service."
---

# Disable-JournalArchiving

This cmdlet is available only in the cloud-based service. 
  
Use the **Disable-JournalArchiving** cmdlet to disable journal archiving for specific users. Microsoft Office 365 journal archiving uses mailboxes in Exchange Online to record orjournal messages for mailboxes in on-premises organizations.
  
For information about the parameter sets in the Syntax section below, see [Exchange cmdlet syntax](https://technet.microsoft.com/library/bb123552.aspx). 
  
```
Disable-JournalArchiving -Identity <MailboxIdParameter> [-Confirm [<SwitchParameter>]] [-PreserveMailUser <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example disables the journal archiving for the user named Timothy Amaral. Timothy's journal archive mailbox in Exchange Online is named  `TimothyAmaral_Archive`.
  
```
Disable-JournalArchiving -Identity TimothyAmaral_Archive
```

## Detailed Description
<a name="DetailedDescription"> </a>

For each on-premise mailbox that's configured for journal archiving in Office 365, a mail user (also known as a mail-enabled user) and a journal archive mailbox are created in Exchange Online. The mail user routes the incoming journaled messages from the on-premises organization, and the journal archive mailbox stores the journaled messages in the cloud.
  
The **Disable-JournalArchiving** cmdlet removes the mail user and converts the journal archive mailbox into an inactive mailbox. The inactive mailbox remains fully available for In-place eDiscovery.
  
> [!NOTE]
> In hybrid organizations that use DirSync, this cmdlet doesn't remove the mail user. Removal of the mail user is handled by DirSync. 
  
You need to be assigned permissions before you can run this cmdlet. Although this topic lists all parameters for the cmdlet, you may not have access to some parameters if they're not included in the permissions assigned to you. To find the permissions required to run any cmdlet or parameter in your organization, see [Find the permissions required to run any Exchange cmdlet](https://technet.microsoft.com/library/mt432940.aspx).
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Exchange.Configuration.Tasks.MailboxIdParameter  <br/> | The _Identity_ parameter specifies the identity of the user's journal archive mailbox in Exchange Online. You can use any value that uniquely identifies the journal archive mailbox. <br/>  For example: <br/>  Name <br/>  Display name <br/>  Alias <br/>  Distinguished name (DN) <br/>  Canonical DN <br/>  _\<domain name\>_\ _\<account name\>_ <br/>  Email address <br/>  GUID <br/> **LegacyExchangeDN** <br/> **SamAccountName** <br/>  User ID or user principal name (UPN) <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
| _PreserveMailUser_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |The  _PreserveMailUser_ switch specifies that you want to keep the mail user that's associated with the archive mailbox. You don't need to specify a value with this switch. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

To see the input types that this cmdlet accepts, see [Cmdlet Input and Output Types](http://go.microsoft.com/fwlink/p/?linkId=616387). If the Input Type field for a cmdlet is blank, the cmdlet doesn't accept input data. 
  
## Return Types
<a name="ReturnTypes"> </a>

To see the return types, which are also known as output types, that this cmdlet accepts, see [Cmdlet Input and Output Types](http://go.microsoft.com/fwlink/p/?linkId=616387). If the Output Type field is blank, the cmdlet doesn't return data. 
  

