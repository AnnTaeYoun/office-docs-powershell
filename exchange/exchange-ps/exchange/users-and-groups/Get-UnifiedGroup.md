---
applicable: Exchange Online
schema: 2.0.0
---

# Get-UnifiedGroup

## SYNOPSIS
이 cmdlet은 클라우드 기반 서비스에서만 사용할 수 있습니다.

Get-UnifiedGroup cmdlet을 사용하면 클라우드 기반 조직에서 Office 365 그룹을 볼 수 있습니다. 
Office 365 그룹의 구성원, 소유자 및 구독자를 보려면 Get-UnifiedGroupLinks cmdlet을 사용하십시오.

아래 구문 섹션의 매개 변수 집합에 대한 자세한 내용은 Exchange cmdlet 구문을 참조하십시오. (https://technet.microsoft.com/library/bb123552.aspx).

## SYNTAX

### Set2
```
Get-UnifiedGroup [-Anr <String>] [-Filter <String>] [-IncludeSoftDeletedGroups] [-ResultSize <Unlimited>]
 [-SortBy <String>] [<CommonParameters>]
```

### Set1
```
Get-UnifiedGroup [[-Identity] <UnifiedGroupIdParameter>] [-Filter <String>] [-IncludeSoftDeletedGroups]
 [-ResultSize <Unlimited>] [-SortBy <String>] [<CommonParameters>]
```

## DESCRIPTION
Office 365 그룹은 Office 365 서비스에서 사용할 수있는 그룹 개체입니다.

이 cmdlet을 실행하려면 먼저 사용 권한을 할당 받아야합니다. 이 항목에서는 cmdlet의 모든 매개 변수를 나열하지만 할당 된 사용 권한에 포함되지 않은 경우 일부 매개 변수에 액세스하지 못할 수도 있습니다. 조직에서 cmdlet 또는 매개 변수를 실행하는 데 필요한 사용 권한을 확인하려면 모든 Exchange cmdlet을 실행하는 데 필요한 사용 권한 찾기를 참조하십시오.
 (https://technet.microsoft.com/library/mt432940.aspx).

## EXAMPLES

### Example 1
```
Get-UnifiedGroup
```

이 예에서는 모든 Office 365 그룹의 요약 목록을 반환합니다.

### Example 2
```
Get-UnifiedGroup | Format-List DisplayName,EmailAddresses,Notes,ManagedBy,AccessType
```

이 예에서는 아래 필드에 대한 모든 Office 365 그룹의 요약 목록을 반환합니다:


Display name

Email address

Description

Owners

Privacy

### Example 3
```
Get-UnifiedGroup -Identity "Marketing Department" | Format-List
```

이 예에서는 Marketing Department라는 Office 365 그룹에 대한 자세한 정보를 반환합니다.

## PARAMETERS

### -Anr
이 매개 변수는 Microsoft 내부에서 사용하도록 예약되어 있습니다.

```yaml
Type: String
Parameter Sets: Set2
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter
Filter 매개 변수는 OPATH 필터 구문을 사용하여 지정된 속성 및 값으로 결과를 필터링합니다. 검색 기준은 구문을 사용합니다.{\<Property\> -\<Comparison operator\> '\<Value\>'}.

- \<Property\> is a filterable property.

- -\<Comparison Operator\> is an OPATH comparison operator. For example -eq for equals and -like for string comparison. For more information about comparison operators, see about\_Comparison\_Operators (https://go.microsoft.com/fwlink/p/?LinkId=620712).

- \<Value\> is the property value. Text values with or without spaces need to be enclosed in quotation marks ('\<Value\>'). Don't use quotation marks with integers or the system values $true, $false, or $null.

You can chain multiple search criteria together using the logical operators -and and -or. For example, {\<Criteria1\>) -and \<Criteria2\>} or {(\<Criteria1\> -and \<Criteria2\>) -or \<Criteria3\>}.

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Identity
The Identity parameter specifies the Office 365 Group that you want to view. You can use any value that uniquely identifies the Office 365 Group.

For example:

- Name

- Display name

- Alias

- Distinguished name (DN)

- Canonical DN

- Email address

- GUID

```yaml
Type: UnifiedGroupIdParameter
Parameter Sets: Set1
Aliases:
Applicable: Exchange Online

Required: False
Position: 1
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### -IncludeAllProperties
The IncludeAllProperties switch specifies whether to include the values of all properties in the results. You don't need to specify a value with this switch.

If you don't use this switch, the values of some properties (for example, CalendarMemeberReadOnly, CalendarUrl, InboxUrl, PeopleUrl, and PhotoUrl) might appear blank.

### -IncludeSoftDeletedGroups
The IncludeSoftDeletedGroups switch specifies whether to include soft-deleted Office 365 groups in the results. You don't need to specify a value with this switch.

This switch is required to return soft-deleted Office 365 groups.

Soft-deleted Office 365 groups are deleted groups that are still recoverable.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultSize
The ResultSize parameter specifies the maximum number of results to return. If you want to return all requests that match the query, use unlimited for the value of this parameter. The default value is 1000.

```yaml
Type: Unlimited
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SortBy
The SortBy parameter specifies the property to sort the results by. You can sort by only one property at a time. The results are sorted in ascending order.

If the default view doesn't include the property you're sorting by, you can append the command with | Format-Table -Auto \<Property1\>,\<Property2\>... to create a new view that contains all of the properties that you want to see. Wildcards (\*) in the property names are supported.

You can sort by the following properties:

- Name

- DisplayName

- Alias

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/p/?LinkID=113216).

## INPUTS

###  
To see the input types that this cmdlet accepts, see Cmdlet Input and Output Types (https://go.microsoft.com/fwlink/p/?linkId=616387). If the Input Type field for a cmdlet is blank, the cmdlet doesn't accept input data.

## OUTPUTS

###  
To see the return types, which are also known as output types, that this cmdlet accepts, see Cmdlet Input and Output Types (https://go.microsoft.com/fwlink/p/?linkId=616387). If the Output Type field is blank, the cmdlet doesn't return data.

## NOTES

## RELATED LINKS

[Online Version](https://technet.microsoft.com/library/9ff9204a-cc18-4e39-9159-1d16314217cd.aspx)

