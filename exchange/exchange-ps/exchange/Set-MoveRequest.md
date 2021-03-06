---
applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online
schema: 2.0.0
---

# Set-MoveRequest

## SYNOPSIS
!!! Exchange Server 2010

Use the Set-MoveRequest cmdlet to change move request options after the move request has been created. You can use the Set-MoveRequest cmdlet to recover from failed move requests.

!!! Exchange Server 2013, Exchange Server 2016, Exchange Online

This cmdlet is available in on-premises Exchange and in the cloud-based service. Some parameters and settings may be exclusive to one environment or the other.

Use the Set-MoveRequest cmdlet to change move request options after the move request has been created. You can use the Set-MoveRequest cmdlet to recover from failed move requests.

## SYNTAX

```
Set-MoveRequest [-Identity] <MoveRequestIdParameter> [-AcceptLargeDataLoss] [-BadItemLimit <Unlimited>]
 [-BatchName <String>] [-Confirm] [-DomainController <Fqdn>] [-IgnoreRuleLimitErrors <$true | $false>]
 [-Priority <Normal | High>] [-Protect <$true | $false>] [-RemoteCredential <PSCredential>]
 [-RemoteGlobalCatalog <Fqdn>] [-RemoteHostName <Fqdn>] [-SuspendWhenReadyToComplete <$true | $false>]
 [-WhatIf] [-ArchiveTargetDatabase <DatabaseIdParameter>] [-CompleteAfter <DateTime>]
 [-CompletedRequestAgeLimit <Unlimited>] [-IncrementalSyncInterval <TimeSpan>]
 [-InternalFlags <InternalMrsFlag[]>] [-LargeItemLimit <Unlimited>] [-PreventCompletion <$true | $false>]
 [-SkipMoving <SkippableMoveComponent[]>] [-StartAfter <DateTime>] [-TargetDatabase <DatabaseIdParameter>]
 [-MigrationMailbox <MailboxIdParameter>] [-MoveOptions <MultiValuedProperty>]
 [-ProxyToMailbox <MailboxIdParameter>] [-RequestExpiryInterval <Unlimited>]
 [-SourceEndpoint <MigrationEndpointIdParameter>] [<CommonParameters>]
```

## DESCRIPTION
!!! Exchange Server 2010

You can pipeline the Set-MoveRequest cmdlet from the Get-MoveRequestStatistics, Get-MoveRequest, or Get-Mailbox cmdlets.

You need to be assigned permissions before you can run this cmdlet. Although all parameters for this cmdlet are listed in this topic, you may not have access to some parameters if they're not included in the permissions assigned to you. To see what permissions you need, see the "Mailbox moves" entry in the Mailbox Permissions topic.

!!! Exchange Server 2013

You can pipeline the Set-MoveRequest cmdlet from the Get-MoveRequestStatistics, Get-MoveRequest, or Get-Mailbox cmdlets.

You need to be assigned permissions before you can run this cmdlet. Although all parameters for this cmdlet are listed in this topic, you may not have access to some parameters if they're not included in the permissions assigned to you. To see what permissions you need, see the "Mailbox moves" entry in the Recipients Permissions topic.

!!! Exchange Server 2016, Exchange Online

You can pipeline the Set-MoveRequest cmdlet from the Get-MoveRequestStatistics, Get-MoveRequest, or Get-Mailbox cmdlets.

You need to be assigned permissions before you can run this cmdlet. Although this topic lists all parameters for the cmdlet, you may not have access to some parameters if they're not included in the permissions assigned to you. To find the permissions required to run any cmdlet or parameter in your organization, see Find the permissions required to run any Exchange cmdlet (https://technet.microsoft.com/library/mt432940.aspx).

## EXAMPLES

### Example 1 -------------------------- (Exchange Server 2010)
```
Set-MoveRequest -Identity Ayla@humongousinsurance.com -BadItemLimit 5
```

This example changes the move request for Ayla to accept up to five corrupt mailbox items.

### Example 1 -------------------------- (Exchange Server 2013)
```
Set-MoveRequest -Identity Ayla@humongousinsurance.com -BadItemLimit 5
```

This example changes the move request for Ayla to accept up to five corrupt mailbox items.

### Example 1 -------------------------- (Exchange Server 2016)
```
Set-MoveRequest -Identity Ayla@humongousinsurance.com -BadItemLimit 5
```

This example changes the move request for Ayla to accept up to five corrupt mailbox items.

### Example 1 -------------------------- (Exchange Online)
```
Set-MoveRequest -Identity Ayla@humongousinsurance.com -BadItemLimit 5
```

This example changes the move request for Ayla to accept up to five corrupt mailbox items.

## PARAMETERS

### -Identity
The Identity parameter specifies the identity of the mailbox or mail user. You can use the following values:

- GUID

- Distinguished name (DN)

- Domain\\Account

- User principal name (UPN)

- LegacyExchangeDN

- SMTP address

- Alias

```yaml
Type: MoveRequestIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: True
Position: 1
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### -AcceptLargeDataLoss
!!! Exchange Server 2010

The AcceptLargeDataLoss parameter specifies that a large amount of data loss is acceptable if the BadItemLimit is set to 51 or higher. Items are considered corrupted if the item can't be read from the source database or can't be written to the target database. Corrupted items won't be available in the destination mailbox or .pst file.



!!! Exchange Server 2013, Exchange Server 2016, Exchange Online

The AcceptLargeDataLoss switch specifies the request should continue even if a large number of items in the source mailbox can't be copied to the target mailbox. You need to use this switch if you set either the BadItemLimit or LargeItemLimit parameters to a value of 51 or higher. Otherwise, the command will fail.



```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BadItemLimit
!!! Exchange Server 2010

The BadItemLimit parameter specifies the number of bad items to skip if the request encounters corruption in the mailbox. Use 0 to not skip bad items. The valid input range for this parameter is from 0 through 2147483647. The default value is 0. We recommend that you keep the default value 0 and only change the BadItemLimit parameter value if the request fails.

If you set the BadItemLimit parameter to more than 50, the command fails, and you receive a warning stating: "Please confirm your intention to accept a large amount of data loss by specifying AcceptLargeDataLoss." If you receive this warning, you need to run the command again, this time using the AcceptLargeDataLoss parameter. No further warnings appear, and any corrupted items aren't available after the process is complete.



!!! Exchange Server 2013, Exchange Server 2016, Exchange Online

The BadItemLimit parameter specifies the maximum number of bad items that are allowed before the request fails. A bad item is a corrupt item in the source mailbox that can't be copied to the target mailbox. Also included in the bad item limit are missing items. Missing items are items in the source mailbox that can't be found in the target mailbox when the request is ready to complete.

Valid input for this parameter is an integer or the value unlimited. The default value is 0, which means the request will fail if any bad items are detected. If you are OK with leaving a few bad items behind, you can set this parameter to a reasonable value (we recommend 10 or lower) so the request can proceed. If too many bad items are detected, consider using the New-MailboxRepairRequest cmdlet to attempt to fix corrupted items in the source mailbox, and try the request again.

If you set this value to 51 or higher, you also need to use the AcceptLargeDataLoss switch. Otherwise, the command will fail.



```yaml
Type: Unlimited
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BatchName
The BatchName parameter specifies a different name for a batch.

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
!!! Exchange Server 2010, Exchange Server 2013

The Confirm switch specifies whether to show or hide the confirmation prompt. How this switch affects the cmdlet depends on if the cmdlet requires confirmation before proceeding.

- Destructive cmdlets (for example, Remove-* cmdlets) have a built-in pause that forces you to acknowledge the command before proceeding. For these cmdlets, you can skip the confirmation prompt by using this exact syntax: -Confirm:$false.

- Most other cmdlets (for example, New-* and Set-* cmdlets) don't have a built-in pause. For these cmdlets, specifying the Confirm switch without a value introduces a pause that forces you acknowledge the command before proceeding.



!!! Exchange Server 2016, Exchange Online

The Confirm switch specifies whether to show or hide the confirmation prompt. How this switch affects the cmdlet depends on if the cmdlet requires confirmation before proceeding.

- Destructive cmdlets (for example, Remove-\* cmdlets) have a built-in pause that forces you to acknowledge the command before proceeding. For these cmdlets, you can skip the confirmation prompt by using this exact syntax: -Confirm:$false.

- Most other cmdlets (for example, New-\* and Set-\* cmdlets) don't have a built-in pause. For these cmdlets, specifying the Confirm switch without a value introduces a pause that forces you acknowledge the command before proceeding.



```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainController
!!! Exchange Server 2010

The DomainController parameter specifies the domain controller that's used by this cmdlet to read data from or write data to Active Directory. You identify the domain controller by its fully qualified domain name (FQDN). For example, dc01.contoso.com.



!!! Exchange Server 2013, Exchange Server 2016, Exchange Online

This parameter is available only in on-premises Exchange.

The DomainController parameter specifies the domain controller that's used by this cmdlet to read data from or write data to Active Directory. You identify the domain controller by its fully qualified domain name (FQDN). For example, dc01.contoso.com.



```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreRuleLimitErrors
The IgnoreRuleLimitErrors parameter specifies that the command won't move the user's rules to the target server running Microsoft Exchange.

```yaml
Type: $true | $false
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Priority
!!! Exchange Server 2010

The Priority parameter specifies the position in the request queue in which to put this request for processing. Requests are processed in order, based on server health, status, priority, and last update time.



!!! Exchange Server 2013

This parameter is available only in on-premises Exchange.

The Priority parameter specifies the order in which this request should be processed in the request queue. Requests are processed in order, based on server health, status, priority, and last update time.



!!! Exchange Server 2016, Exchange Online

This parameter is available only in on-premises Exchange.

The Priority parameter specifies the order in which the request should be processed in the request queue. Requests are processed in order, based on server health, status, priority, and last update time. Valid priority values are:

- Lowest

- Lower

- Low

- Normal: This is the default value.

- High

- Higher

- Highest

- Emergency



```yaml
Type: Normal | High
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protect
This parameter is reserved for internal Microsoft use.

```yaml
Type: $true | $false
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteCredential
!!! Exchange Server 2010

The RemoteCredential parameter specifies an administrator who has permission to perform the mailbox move, for example, Administrator@ humongousinsurance.com.

This parameter requires the creation and passing of a credential object. This credential object is created by using the Get-Credential cmdlet. For more information, see Get-Credential (https://go.microsoft.com/fwlink/p/?linkid=142122).



!!! Exchange Server 2013

The RemoteCredential parameter specifies an administrator who has permission to perform the mailbox move, for example, Administrator@ humongousinsurance.com.

This parameter requires the creation and passing of a credential object. This credential object is created by using the Get-Credential cmdlet. For more information, see Get-Credential (https://go.microsoft.com/fwlink/p/?linkId=142122).



!!! Exchange Server 2016, Exchange Online

The RemoteCredential parameter specifies an administrator who has permission to perform the mailbox move, for example, Administrator@ humongousinsurance.com.

This parameter requires you to create a credentials object by using the Get-Credential cmdlet. For more information, see Get-Credential (https://go.microsoft.com/fwlink/p/?linkId=142122).



```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteGlobalCatalog
!!! Exchange Server 2010

The RemoteGlobalCatalog parameter specifies the FQDN global catalog server for the remote forest.



!!! Exchange Server 2013, Exchange Server 2016, Exchange Online

The RemoteGlobalCatalog parameter specifies the FQDN of the global catalog server for the remote forest.



```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteHostName
The RemoteHostName parameter specifies the FQDN of the cross-forest organization from which you're moving the mailbox.

```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SuspendWhenReadyToComplete
!!! Exchange Server 2010

The SuspendWhenReadyToComplete parameter specifies whether to suspend the move request before it reaches the status of CompletionInProgress. The move request then has a status of AutoSuspended. You can manually complete the move by using the Resume-MoveRequest command.



!!! Exchange Server 2013, Exchange Server 2016, Exchange Online

The SuspendWhenReadyToComplete parameter specifies whether to suspend the move request before it reaches the status of CompletionInProgress. Instead of this parameter, we recommend using CompleteAfter parameter.



```yaml
Type: $true | $false
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
The WhatIf switch simulates the actions of the command. You can use this switch to view the changes that would occur without actually applying those changes. You don't need to specify a value with this switch.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ArchiveTargetDatabase
This parameter is available only in on-premises Exchange.

The ArchiveTargetDatabase parameter specifies the Exchange target database to which you're moving the personal archive. You can use this parameter to change the target database only if the move request has a MoveStatus value of Queued.

You can use the following values to specify the target database:

- GUID of the database

- Database name

```yaml
Type: DatabaseIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompleteAfter
!!! Exchange Server 2013

The CompleteAfter parameter specifies a delay before the request is completed. The request is started, but not completed until the date/time you specify with this parameter.

Use the short date format defined in the Regional Options settings for the computer on which the command is run. For example, if the computer is configured to use the short date format mm/dd/yyyy, enter 03/01/2010 to specify March 1, 2010. You can enter the date only, or you can enter the date and time of day. If you enter the date and time of day, you must enclose the argument in quotation marks ("), for example, "10/05/2010 5:00 PM".



!!! Exchange Server 2016, Exchange Online

The CompleteAfter parameter specifies a delay before the request is completed. The request is started, but not completed until the date/time you specify with this parameter.

Use the short date format that's defined in the Regional Options settings on the computer where you're running the command. For example, if the computer is configured to use the short date format mm/dd/yyyy, enter 09/01/2015 to specify September 1, 2015. You can enter the date only, or you can enter the date and time of day. If you enter the date and time of day, enclose the value in quotation marks ("), for example, "09/01/2015 5:00 PM".

In Exchange Online, if you specify a date/time value without a time zone, the value is in Coordinated Universal Time (UTC).

To specify a date/time value for this parameter, use either of the following options:

- Specify the date/time value in UTC: For example, "2016-05-06 14:30:00z".

- Specify the date/time value as a formula that converts the date/time in your local time zone to UTC: For example, (Get-Date "5/6/2016 9:30 AM").ToUniversalTime(). For more information, see Get-Date (https://go.microsoft.com/fwlink/p/?LinkID=113313).



```yaml
Type: DateTime
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompletedRequestAgeLimit
The CompletedRequestAgeLimit parameter specifies how long the request is kept after it has completed before being automatically removed. The default CompletedRequestAgeLimit parameter value is 30 days.

```yaml
Type: Unlimited
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncrementalSyncInterval
!!! Exchange Server 2013

The IncrementalSyncInterval parameter specifies the wait time between incremental syncs. This parameter is used together with the CompleteAfter parameter to create a move request that will do periodic incremental syncs after the initial sync is complete.

To specify a value, enter it as a time span: dd.hh:mm:ss where d = days, h = hours, m = minutes, and s = seconds.

Valid values are from 00:00:00 to 120.00:00:00 (120 days). The default value is 24 hours.



!!! Exchange Server 2016, Exchange Online

The IncrementalSyncInterval parameter specifies the wait time between incremental syncs. This parameter is used together with the CompleteAfter parameter to create a move request that will do periodic incremental syncs after the initial sync is complete.

To specify a value, enter it as a time span: dd.hh:mm:ss where dd = days, hh = hours, mm = minutes, and ss = seconds.

Valid values are from 00:00:00 to 120.00:00:00 (120 days). The default value is 24 hours.



```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InternalFlags
This parameter is available only in on-premises Exchange.

The InternalFlags parameter specifies the optional steps in the request. This parameter is used primarily for debugging purposes.

```yaml
Type: InternalMrsFlag[]
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LargeItemLimit
!!! Exchange Server 2013

The LargeItemLimit parameter specifies the maximum number of large items that are allowed before the request fails. A large item is a message in the source mailbox that exceeds the maximum message size that's allowed in the target mailbox. If the target mailbox doesn't have a specifically configured maximum message size value, the organization-wide value is used.

For more information about maximum message size values, see the following topics:

- Exchange 2013 Message size limits

- Exchange Online Exchange Online Limits (https://go.microsoft.com/fwlink/p/?LinkId=524926)

Valid input for this parameter is an integer or the value unlimited. The default value is 0, which means the request will fail if any large items are detected. If you are OK with leaving a few large items behind, you can set this parameter to a reasonable value (we recommend 10 or lower) so the request can proceed.

If you set this value to 51 or higher, you also need to use the AcceptLargeDataLoss switch. Otherwise, the command will fail.



!!! Exchange Server 2016, Exchange Online

The LargeItemLimit parameter specifies the maximum number of large items that are allowed before the request fails. A large item is a message in the source mailbox that exceeds the maximum message size that's allowed in the target mailbox. If the target mailbox doesn't have a specifically configured maximum message size value, the organization-wide value is used.

For more information about maximum message size values, see the following topics:

- Exchange 2016: Message size limits in Exchange 2016 (https://technet.microsoft.com/library/bb124345.aspx)

- Exchange Online: Exchange Online Limits (https://go.microsoft.com/fwlink/p/?LinkId=524926)

Valid input for this parameter is an integer or the value unlimited. The default value is 0, which means the request will fail if any large items are detected. If you are OK with leaving a few large items behind, you can set this parameter to a reasonable value (we recommend 10 or lower) so the request can proceed.

If you set this value to 51 or higher, you also need to use the AcceptLargeDataLoss switch. Otherwise, the command will fail.



```yaml
Type: Unlimited
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PreventCompletion
!!! Exchange Server 2013

The PreventCompletion parameter specifies whether to run the move request, but not allow it to complete. Valid values are:

- $true The move request is run, but is not allowed to complete. Instead of this value, we recommend using the CompleteAfter parameter.

- $false This is the default value. The move request is run and allowed to complete. If you created the move request with the SuspendWhenReadyToComplete or PreventCompletion switches, set this parameter to $false before you run the Resume-MoveRequest cmdlet to complete the move request.



!!! Exchange Server 2016, Exchange Online

The PreventCompletion parameter specifies whether to run the move request, but not allow it to complete. Valid values are:

- $true: The move request is run, but is not allowed to complete. Instead of this value, we recommend using the CompleteAfter parameter.

- $false: This is the default value. The move request is run and allowed to complete. If you created the move request with the SuspendWhenReadyToComplete or PreventCompletion switches, set this parameter to $false before you run the Resume-MoveRequest cmdlet to complete the move request.



```yaml
Type: $true | $false
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipMoving
!!! Exchange Server 2013

The SkipMoving parameter allows certain stages of a mailbox move to be skipped for debugging purposes. Do not use this parameter unless directed to do so by a support professional or specific documentation.



!!! Exchange Server 2016, Exchange Online

This parameter has been replaced by the MoveOptions parameter.

The SkipMoving parameter specifies the stages of the move that you want to skip for debugging purposes. Don't use this parameter unless you're directed to do so by Microsoft Customer Service and Support or specific documentation.



```yaml
Type: SkippableMoveComponent[]
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartAfter
!!! Exchange Server 2013

The StartAfter parameter specifies a delay before the request is started. The request isn't started until the date/time you specify with this parameter.

Use the short date format defined in the Regional Options settings for the computer on which the command is run. For example, if the computer is configured to use the short date format mm/dd/yyyy, enter 03/01/2010 to specify March 1, 2010. You can enter the date only, or you can enter the date and time of day. If you enter the date and time of day, you must enclose the argument in quotation marks ("), for example, "10/05/2010 5:00 PM".



!!! Exchange Server 2016, Exchange Online

The StartAfter parameter specifies a delay before the request is started. The request isn't started until the date/time you specify with this parameter.

Use the short date format that's defined in the Regional Options settings on the computer where you're running the command. For example, if the computer is configured to use the short date format mm/dd/yyyy, enter 09/01/2015 to specify September 1, 2015. You can enter the date only, or you can enter the date and time of day. If you enter the date and time of day, enclose the value in quotation marks ("), for example, "09/01/2015 5:00 PM".

In Exchange Online, if you specify a date/time value without a time zone, the value is in Coordinated Universal Time (UTC).

To specify a date/time value for this parameter, use either of the following options:

- Specify the date/time value in UTC: For example, "2016-05-06 14:30:00z".

- Specify the date/time value as a formula that converts the date/time in your local time zone to UTC: For example, (Get-Date "5/6/2016 9:30 AM").ToUniversalTime(). For more information, see Get-Date (https://go.microsoft.com/fwlink/p/?LinkID=113313).



```yaml
Type: DateTime
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetDatabase
This parameter is available only in on-premises Exchange.

The TargetDatabase parameter specifies the identity of the database that you're moving the mailbox to. You can use this parameter to change the target database only if the move request has a MoveStatus value of Queued.

You can use the following values:

- GUID of the database

- Database name

```yaml
Type: DatabaseIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2013, Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MigrationMailbox
This parameter is reserved for internal Microsoft use.

```yaml
Type: MailboxIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MoveOptions
The MoveOptions parameter specifies the stages of the move that you want to skip for debugging purposes. Don't use this parameter unless you're directed to do so by Microsoft Customer Service and Support or specific documentation.

Don't use this parameter with the SkipMoving parameter.

```yaml
Type: MultiValuedProperty
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyToMailbox
This parameter is available only in the cloud-based service.

The ProxyToMailbox parameter specifies the move destination by the location of the specified mailbox (also known as proxying). You can use any value that uniquely identifies the mailbox.

For example:

- Name

- Display name

- Alias

- Distinguished name (DN)

- Canonical DN

- \<domain name\>\\\<account name\>

- Email address

- GUID

- LegacyExchangeDN

- SamAccountName

- User ID or user principal name (UPN)

```yaml
Type: MailboxIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequestExpiryInterval
The RequestExpiryInterval parameter specifies an age limit for a completed or failed request. When you use this parameter, the completed or failed request is automatically removed after the specified interval expires. If you don't use this parameter:

- The completed request is automatically removed based on the CompletedRequestAgeLimit parameter value.

- If the request fails, you need to manually remove it by using the corresponding Remove-\*Request cmdlet.

To specify a value, enter it as a time span: dd.hh:mm:ss where dd = days, hh = hours, mm = minutes, and ss = seconds.

When you use the value Unlimited, the completed request isn't automatically removed.

```yaml
Type: Unlimited
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2016, Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceEndpoint
This parameter is reserved for internal Microsoft use.

```yaml
Type: MigrationEndpointIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2016, Exchange Online

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
To see the input types that this cmdlet accepts, see Cmdlet Input and Output Types (https://go.microsoft.com/fwlink/p/?LinkId=616387). If the Input Type field for a cmdlet is blank, the cmdlet doesn't accept input data.

## OUTPUTS

###  
To see the return types, which are also known as output types, that this cmdlet accepts, see Cmdlet Input and Output Types (https://go.microsoft.com/fwlink/p/?LinkId=616387). If the Output Type field is blank, the cmdlet doesn't return data.

## NOTES

## RELATED LINKS

[Online Version](https://technet.microsoft.com/library/1a668f96-e924-4698-9387-ee71f8d9b136.aspx)

