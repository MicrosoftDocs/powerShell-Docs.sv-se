---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/enable-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-LocalUser
ms.openlocfilehash: 80d062578e7114b69e5cb5f3367b56da3871b9df
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263528"
---
# Enable-LocalUser

## SAMMANFATTNING
Aktiverar ett lokalt användar konto.

## SYNTAX

### InputObject

```
Enable-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Default

```
Enable-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Enable-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en Enable-lokal användare** aktiverar lokala användar konton.
När ett användar konto har inaktiverats kan användaren inte logga in.
När ett användar konto är aktiverat kan användaren logga in.

> [!NOTE]
> Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.

## EXEMPEL

### Exempel 1: aktivera ett konto genom att ange ett namn

```
PS C:\> Enable-LocalUser -Name "Admin02"
```

Det här kommandot aktiverar det användar konto som heter Admin02.

### Exempel 2: aktivera ett konto med hjälp av pipelinen

```
PS C:\> Get-LocalUser -Name "Administrator" | Enable-LocalUser
```

Det här kommandot hämtar det inbyggda administratörs kontot med hjälp av **Get-lokal användare** och skickar det sedan till den aktuella cmdleten med hjälp av pipeline-operatorn.
Denna cmdlet aktiverar det kontot.

## PARAMETRAR

### – InputObject
Anger en matris med användar konton som denna cmdlet aktiverar.
Använd Get-LocalUser-cmdleten om du vill skaffa ett användar konto.

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Anger en matris med namn på de användar konton som denna cmdlet aktiverar.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
Anger en matris med användar konton som denna cmdlet aktiverar.

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

[Get-lokal användare](Get-LocalUser.md)

[New-lokal användare](New-LocalUser.md)

[Remove-lokal användare](Remove-LocalUser.md)

[Byt namn – lokal användare](Rename-LocalUser.md)

[Set-lokal användare](Set-LocalUser.md)
