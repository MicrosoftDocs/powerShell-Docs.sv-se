---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalUser
ms.openlocfilehash: a6352611b757dae828a2efef07f9ce65abaa5e2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266271"
---
# Set-LocalUser

## SAMMANFATTNING
Ändrar ett lokalt användar konto.

## SYNTAX

### Namn (standard)

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Name] <String> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-InputObject] <LocalUser> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Password <SecureString>] [-PasswordNeverExpires <Boolean>] [-SID] <SecurityIdentifier>
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **set-lokal användare** ändrar ett lokalt användar konto.
Denna cmdlet kan återställa lösen ordet för ett lokalt användar konto.

> [!NOTE]
> Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.

## EXEMPEL

### Exempel 1: ändra en beskrivning av ett användar konto

```
PS C:\> Set-LocalUser -Name "Admin07" -Description "Description of this account."
```

Det här kommandot ändrar beskrivningen av ett användar konto med namnet Admin07.

### Exempel 2: ändra lösen ordet för ett konto

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> $UserAccount = Get-LocalUser -Name "User02"
PS C:\> $UserAccount | Set-LocalUser -Password $Password
```

I det första kommandot uppmanas du att ange ett lösen ord med hjälp av Read-Host-cmdleten.
Kommandot lagrar lösen ordet som en säker sträng i variabeln $Password.

Det andra kommandot hämtar ett användar konto med namnet User02 med hjälp av **Get-lokal användare**.
Kommandot lagrar kontot i variabeln $UserAccount.

Det tredje kommandot anger det nya lösen ordet för det användar konto som lagras i $UserAccount.

## PARAMETRAR

### -AccountExpires
Anger när användar kontot upphör att gälla.
Använd Get-Date-cmdleten för att hämta ett **datetime** -objekt.

Om du inte vill att kontot ska upphöra att gälla anger du parametern *AccountNeverExpires* .

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AccountNeverExpires
Anger att kontot inte upphör att gälla.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beskrivning
Anger en kommentar för användar kontot.
Den maximala längden är 48 tecken.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullName
Anger det fullständiga namnet på användar kontot.
Det fullständiga namnet skiljer sig från användar kontots användar namn.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject
Anger det användar konto som denna cmdlet ändrar.
Använd Get-LocalUser-cmdleten om du vill skaffa ett användar konto.

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Anger namnet på det användar konto som denna cmdlet ändrar.

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Password
Anger ett lösen ord för användar kontot.
Ange inget lösen ord om användar kontot är anslutet till ett Microsoft-konto.

Du kan använda `Read-Host -GetCredential` , Hämta autentiseringsuppgifter eller ConvertTo-SecureString för att skapa ett **SecureString** -objekt för lösen ordet.

Om du utelämnar parametrarna för *lösen ord* och *NOPassword* , uppmanas du att ange användarens lösen ord i **set-lokal användare** .

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PasswordNeverExpires
Anger om lösen ordet upphör att gälla.

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID
Anger säkerhets-ID: t (SID) för det användar konto som denna cmdlet ändrar.

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UserMayChangePassword
Anger att användaren kan ändra lösen ordet för användar kontot.

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. SecurityAccountsManager. lokal användare, system. String, system. Security. Principal. SecurityIdentifier
Du kan skicka vidare en lokal användare, en sträng eller ett SID till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa. De möjliga källorna är följande:

- Lokal
- Active Directory
- Azure Active Directory grupp
- Microsoft-konto

**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows. För tidigare versioner är egenskapen tom.

## RELATERADE LÄNKAR

[Disable-lokal användare](Disable-LocalUser.md)

[Aktivera – lokal användare](Enable-LocalUser.md)

[Get-lokal användare](Get-LocalUser.md)

[New-lokal användare](New-LocalUser.md)

[Remove-lokal användare](Remove-LocalUser.md)

[Byt namn – lokal användare](Rename-LocalUser.md)
