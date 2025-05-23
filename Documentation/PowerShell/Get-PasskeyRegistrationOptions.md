---
external help file: DSInternals.Passkeys-help.xml
Module Name: DSInternals.Passkeys
online version: https://github.com/MichaelGrafnetter/webauthn-interop/tree/main/Documentation/PowerShell/Get-PasskeyRegistrationOptions.md
schema: 2.0.0
---

# Get-PasskeyRegistrationOptions

## SYNOPSIS
Retrieves creation options required to generate and register a Microsoft Entra ID or Okta compatible passkey.

## SYNTAX

```
Get-PasskeyRegistrationOptions [-UserId] <String> [[-ChallengeTimeout] <TimeSpan>]
 [-ProgressAction <ActionPreference>] [<CommonParameters>]
```

## DESCRIPTION

Retrieves the [credential creation options](https://w3c.github.io/webauthn/#dictionary-makecredentialoptions) required to generate a Microsoft Entra ID or Okta-compatible passkey.

## EXAMPLES

### EXAMPLE 1 (Entra ID)
```
PS \> Connect-MgGraph -Scopes 'UserAuthenticationMethod.ReadWrite.All'
PS \> Get-PasskeyRegistrationOptions -UserId 'AdeleV@contoso.com'
```

### EXAMPLE 2 (Entra ID)
```
PS \> Connect-MgGraph -Scopes 'UserAuthenticationMethod.ReadWrite.All'
PS \> Get-PasskeyRegistrationOptions -UserId 'AdeleV@contoso.com' -ChallengeTimeout (New-TimeSpan -Minutes 10)
```

### EXAMPLE 3 (Okta)
```
PS \> Connect-Okta -Tenant example.okta.com -ClientId 0oakmj8hvxvtvCy3P5d7
PS \> Get-PasskeyRegistrationOptions -UserId 00eDuihq64pgP1gVD0x7
```

### EXAMPLE 4 (Okta)
```
PS \> Connect-Okta -Tenant example.okta.com -ClientId 0oakmj8hvxvtvCy3P5d7
PS \> Get-PasskeyRegistrationOptions -UserId 00eDuihq64pgP1gVD0x7 -ChallengeTimeout (New-TimeSpan -Seconds 60)
```

## PARAMETERS

### -UserId
The unique identifier of user. 
For Entra ID, this is the object id (GUID) or UPN. 
For Okta, this is the unique identifier of Okta user.

```yaml
Type: String
Parameter Sets: (All)
Aliases: User

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ChallengeTimeout
Overrides the timeout of the server-generated challenge returned in the request. 
For Entra ID, the default value is 5 minutes, with the accepted range being between 5 minutes and 30 days. 
For Okta, the default value is 300 seconds, with the accepted range being between 1 second and 1 day.

```yaml
Type: TimeSpan
Parameter Sets: (All)
Aliases: Timeout

Required: False
Position: 2
Default value: (New-TimeSpan -Minutes 5)
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### DSInternals.Win32.WebAuthn.WebauthnCredentialCreationOption

## NOTES
Self-service operations aren't supported with Entra ID.

## RELATED LINKS

[More info about Entra ID](https://learn.microsoft.com/en-us/graph/api/fido2authenticationmethod-creationoptions)
<br>
[More info about Okta](https://developer.okta.com/docs/api/openapi/okta-management/management/tag/UserFactor/#tag/UserFactor/operation/enrollFactor)
