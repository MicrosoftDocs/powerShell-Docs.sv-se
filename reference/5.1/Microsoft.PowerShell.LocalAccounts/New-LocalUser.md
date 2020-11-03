---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalUser
ms.openlocfilehash: d83f3ad12481df0849ff2fe3f61d553a9ffdcdde
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265569"
---
# New-LocalUser

## SAMMANFATTNING

Skapar ett lokalt användar konto.

## SYNTAX

### Lösen ord (standard)

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NOPassword

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`New-LocalUser`Cmdleten skapar ett lokalt användar konto. Denna cmdlet skapar ett lokalt användar konto eller ett lokalt användar konto som är anslutet till en Microsoft-konto.

> [!NOTE]
> Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.

## EXEMPEL

### Exempel 1: skapa ett användar konto

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

Det här kommandot skapar ett lokalt användar konto och anger inte parametrarna **AccountExpires** eller **Password** . Det innebär att kontot inte upphör att gälla eller har ett lösen ord som standard.

### Exempel 2: skapa ett användar konto som har ett lösen ord

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

I det första kommandot uppmanas du att ange ett lösen ord med hjälp av `Read-Host` cmdleten. Kommandot lagrar lösen ordet som en säker sträng i `$Password` variabeln.

Det andra kommandot skapar ett lokalt användar konto med hjälp av det lösen ord som lagras i `$Password` . Kommandot anger ett användar namn, ett fullständigt namn och en beskrivning för användar kontot.

## PARAMETRAR

### -AccountExpires

Anger när användar kontot upphör att gälla. Använd cmdleten för att hämta ett **datetime** -objekt `Get-Date` .
Om du inte anger den här parametern upphör inte kontot att gälla.

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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
Accept pipeline input: True (ByPropertyName)
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Inaktive rad

Anger att den här cmdleten skapar användar kontot som inaktiverat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FullName

Anger det fullständiga namnet på användar kontot. Det fullständiga namnet skiljer sig från användar kontots användar namn.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger användar namnet för användar kontot.

Om du skapar ett lokalt användar konto för det lokala systemet kan användar namnet innehålla upp till 20 versaler eller gemener. Ett användar namn får inte innehålla följande tecken:

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

Ett användar namn får inte bestå av bara punkter `.` eller blank steg.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -NOPassword

Anger att användar kontot saknar lösen ord.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoPassword
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Password

Anger ett lösen ord för användar kontot. Du kan använda `Read-Host -GetCredential` , `Get-Credential` eller `ConvertTo-SecureString` för att skapa ett **SecureString** -objekt för lösen ordet.

Om du utelämnar parametrarna för **lösen ord** och **NOPassword** , `New-LocalUser` uppmanas du att ange lösen ordet för den nya användaren.

```yaml
Type: System.Security.SecureString
Parameter Sets: Password
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PasswordNeverExpires

Anger om lösen ordet upphör att gälla.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Password
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UserMayNotChangePassword

Anger att användaren inte kan ändra lösen ordet för användar kontot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String, system. DateTime, system. Boolean, system. Security. SecureString

Du kan skicka en sträng, ett **datetime** -objekt, ett booleskt värde eller en säker sträng till denna cmdlet.

## UTDATA

### System. Management. Automation. SecurityAccountsManager. lokal användare

Denna cmdlet returnerar ett **lokal användare** -objekt.
Det här objektet innehåller information om användar kontot.

## ANTECKNINGAR

- Ett användar namn får inte vara identiskt med andra användar namn eller grupp namn på datorn. Ett användar namn får inte bestå av bara punkter `.` eller blank steg. Ett användar namn kan innehålla upp till 20 versaler eller gemener. Ett användar namn får inte innehålla följande tecken:

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

- Ett lösen ord kan innehålla upp till 127 tecken.
- Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa. De möjliga källorna är följande:

  - Lokal
  - Active Directory
  - Azure Active Directory grupp
  - Microsoft-konto

> [!NOTE]
> **PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows. För tidigare versioner är egenskapen tom.

## RELATERADE LÄNKAR

[Disable-lokal användare](Disable-LocalUser.md)

[Aktivera – lokal användare](Enable-LocalUser.md)

[Get-lokal användare](Get-LocalUser.md)

[Remove-lokal användare](Remove-LocalUser.md)

[Byt namn – lokal användare](Rename-LocalUser.md)

[Set-lokal användare](Set-LocalUser.md)
