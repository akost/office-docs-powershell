---
applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016
schema: 2.0.0
---

# Disable-MailContact

## SYNOPSIS
!!! Exchange Server 2010

Use the Disable-MailContact cmdlet to remove the Exchange attributes of an existing mail-enabled contact in Active Directory. The contact object remains in Active Directory but is no longer mail-enabled.

!!! Exchange Server 2013

This cmdlet is available only in on-premises Exchange.

Use the Disable-MailContact cmdlet to remove the Exchange attributes of an existing mail-enabled contact in Active Directory. The contact object remains in Active Directory but is no longer mail-enabled.

For information about the parameter sets in the Syntax section below, see Exchange cmdlet syntax (https://technet.microsoft.com/library/bb123552.aspx).

!!! Exchange Server 2016

This cmdlet is available only in on-premises Exchange.

Use the Disable-MailContact cmdlet to remove email capabilities from existing mail contacts.

For information about the parameter sets in the Syntax section below, see Exchange cmdlet syntax (https://technet.microsoft.com/library/bb123552.aspx).

## SYNTAX

```
Disable-MailContact [-Identity] <MailContactIdParameter> [-Confirm] [-DomainController <Fqdn>]
 [-IgnoreDefaultScope] [-WhatIf] [<CommonParameters>]
```

## DESCRIPTION
!!! Exchange Server 2010

You need to be assigned permissions before you can run this cmdlet. Although all parameters for this cmdlet are listed in this topic, you may not have access to some parameters if they're not included in the permissions assigned to you. To see what permissions you need, see the "Recipient Provisioning Permissions" section in the Mailbox Permissions topic.

!!! Exchange Server 2013

You need to be assigned permissions before you can run this cmdlet. Although all parameters for this cmdlet are listed in this topic, you may not have access to some parameters if they're not included in the permissions assigned to you. To see what permissions you need, see the "Recipient Provisioning Permissions" section in the Recipients Permissions topic.

!!! Exchange Server 2016

The Disable-MailContact cmdlet mail-disables existing mail contacts by removing the email attributes that are required by Exchange. Mail-disabled contacts are invisible to the \*-MailContact cmdlets (with the exception of Enable-MailContact). All contacts (mail-enabled or not) are visible to the Get-Contact and Set-Contact cmdlets.

You need to be assigned permissions before you can run this cmdlet. Although this topic lists all parameters for the cmdlet, you may not have access to some parameters if they're not included in the permissions assigned to you. To find the permissions required to run any cmdlet or parameter in your organization, see Find the permissions required to run any Exchange cmdlet (https://technet.microsoft.com/library/mt432940.aspx).

## EXAMPLES

### Example 1 -------------------------- (Exchange Server 2010)
```
Disable-MailContact -Identity EdMeadows
```

This example mail-disables a mail-enabled contact.

### Example 1 -------------------------- (Exchange Server 2013)
```
Disable-MailContact -Identity EdMeadows
```

This example mail-disables a contact.

### Example 1 -------------------------- (Exchange Server 2016)
```
Disable-MailContact -Identity "EdMeadows"
```

This example mail-disables the mail contact named Ed Meadows.

## PARAMETERS

### -Identity
!!! Exchange Server 2010

The Identity parameter specifies the mail contact.

This parameter accepts the following values:

- Alias

  Example: JPhillips

- Canonical DN

  Example: Atlanta.Corp.Contoso.Com/Users/JPhillips

- Display Name

  Example: Jeff Phillips

- Distinguished Name (DN)

  Example: CN=JPhillips,CN=Users,DC=Atlanta,DC=Corp,DC=contoso,DC=com

- Domain\\Account

  Example: Atlanta\\JPhillips

- GUID

  Example: fb456636-fe7d-4d58-9d15-5af57d0354c2

- Immutable ID

  Example: fb456636-fe7d-4d58-9d15-5af57d0354c2@contoso.com

- Legacy Exchange DN

  Example: /o=Contoso/ou=AdministrativeGroup/cn=Recipients/cn=JPhillips

- SMTP Address

  Example: Jeff.Phillips@contoso.com

- User Principal Name

  Example: JPhillips@contoso.com



!!! Exchange Server 2013

The Identity parameter specifies the mail contact.

This parameter accepts the following values:

- Alias (for example, JPhillips)

- Canonical DN (for example, Atlanta.Corp.Contoso.Com/Users/JPhillips)

- Display Name (for example, Jeff Phillips)

- Distinguished Name (DN) (for example, CN=JPhillips,CN=Users,DC=Atlanta,DC=Corp,DC=contoso,DC=com)

- Domain\\Account (for example, Atlanta\\JPhillips)

- GUID (for example, fb456636-fe7d-4d58-9d15-5af57d0354c2)

- Immutable ID (for example, fb456636-fe7d-4d58-9d15-5af57d0354c2@contoso.com)

- Legacy Exchange DN (for example, /o=Contoso/ou=AdministrativeGroup/cn=Recipients/cn=JPhillips)

- SMTP Address (for example, Jeff.Phillips@contoso.com)

- User Principal Name (for example, JPhillips@contoso.com)



!!! Exchange Server 2016

The Identity parameter specifies the mail contact that you want to mail-disable. You can use any value that uniquely identifies the mail contact.

For example:

- Name

- Display name

- Alias

- Distinguished name (DN)

- Canonical DN

- Email address

- GUID



```yaml
Type: MailContactIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016

Required: True
Position: 1
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### -Confirm
!!! Exchange Server 2010, Exchange Server 2013

The Confirm switch specifies whether to show or hide the confirmation prompt. How this switch affects the cmdlet depends on if the cmdlet requires confirmation before proceeding.

- Destructive cmdlets (for example, Remove-* cmdlets) have a built-in pause that forces you to acknowledge the command before proceeding. For these cmdlets, you can skip the confirmation prompt by using this exact syntax: -Confirm:$false.

- Most other cmdlets (for example, New-* and Set-* cmdlets) don't have a built-in pause. For these cmdlets, specifying the Confirm switch without a value introduces a pause that forces you acknowledge the command before proceeding.



!!! Exchange Server 2016

The Confirm switch specifies whether to show or hide the confirmation prompt. How this switch affects the cmdlet depends on if the cmdlet requires confirmation before proceeding.

- Destructive cmdlets (for example, Remove-\* cmdlets) have a built-in pause that forces you to acknowledge the command before proceeding. For these cmdlets, you can skip the confirmation prompt by using this exact syntax: -Confirm:$false.

- Most other cmdlets (for example, New-\* and Set-\* cmdlets) don't have a built-in pause. For these cmdlets, specifying the Confirm switch without a value introduces a pause that forces you acknowledge the command before proceeding.



```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainController
!!! Exchange Server 2010

The DomainController parameter specifies the domain controller that's used by this cmdlet to read data from or write data to Active Directory. You identify the domain controller by its fully qualified domain name (FQDN). For example, dc01.contoso.com.

The DomainController parameter isn't supported on Edge Transport servers. An Edge Transport server uses the local instance of Active Directory Lightweight Directory Services (AD LDS) to read and write data.



!!! Exchange Server 2013, Exchange Server 2016

The DomainController parameter specifies the domain controller that's used by this cmdlet to read data from or write data to Active Directory. You identify the domain controller by its fully qualified domain name (FQDN). For example, dc01.contoso.com.



```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreDefaultScope
!!! Exchange Server 2010, Exchange Server 2013

The IgnoreDefaultScope parameter instructs the command to ignore the default recipient scope setting for the Exchange Management Shell session and use the entire forest as the scope. This allows the command to access Active Directory objects that aren't currently in the default scope. Using the IgnoreDefaultScope parameter introduces the following restrictions:

- You can't use the DomainController parameter. The command uses an appropriate global catalog server automatically.

- You can only use the DN for the Identity parameter. Other forms of identification, such as alias or GUID, aren't accepted.



!!! Exchange Server 2016

The IgnoreDefaultScope switch tells the command to ignore the default recipient scope setting for the Exchange Management Shell session, and to use the entire forest as the scope. This allows the command to access Active Directory objects that aren't currently available in the default scope.

Using the IgnoreDefaultScope switch introduces the following restrictions:

- You can't use the DomainController parameter. The command uses an appropriate global catalog server automatically.

- You can only use the DN for the Identity parameter. Other forms of identification, such as alias or GUID, aren't accepted.



```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016

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
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016

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

[Online Version](https://technet.microsoft.com/library/3c957be4-d13e-45c3-8730-3be45ffad19a.aspx)

