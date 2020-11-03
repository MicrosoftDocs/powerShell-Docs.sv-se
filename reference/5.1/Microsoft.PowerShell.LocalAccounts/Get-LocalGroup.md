---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroup
ms.openlocfilehash: 2cd77c2766840527825b0ccf68abaac3c2ea6c16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263517"
---
# Get-LocalGroup

## SAMMANFATTNING
Hämtar de lokala säkerhets grupperna.

## SYNTAX

### Standard (standard)

```
Get-LocalGroup [[-Name] <String[]>] [<CommonParameters>]
```

### SecurityIdentifier

```
Get-LocalGroup [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **Get-localgroup** hämtar lokala säkerhets grupper i Security Account Manager.
Den här cmdleten hämtar inbyggda standard grupper och lokala säkerhets grupper som du skapar.

> [!NOTE]
> Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.

## EXEMPEL

### Exempel 1: Hämta gruppen Administratörer

```
PS C:\> Get-LocalGroup -Name "Administrators"
Name           Description
----           -----------
Administrators Administrators have complete and unrestricted access to the computer/domain
```

Det här kommandot hämtar den lokala gruppen Administratörer.
Kommandot visar egenskaper för gruppen i-konsolen.

## PARAMETRAR

### -Name
Anger en matris med namn på de säkerhets grupper som denna cmdlet hämtar.
Du kan använda jokertecknet.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
Anger en matris med säkerhets-ID: n (sid) för de säkerhets grupper som denna cmdlet hämtar.

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String, system. Security. Principal. SecurityIdentifier
Du kan skicka en sträng eller en SID till denna cmdlet.

## UTDATA

### System. Management. Automation. SecurityAccountsManager. LocalGroup
Den här cmdleten returnerar en lokal grupp.

## ANTECKNINGAR

* Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa. De möjliga källorna är följande:

- Lokal
- Active Directory
- Azure Active Directory grupp
- Microsoft-konto

**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows. För tidigare versioner är egenskapen tom.

## RELATERADE LÄNKAR

[New-LocalGroup](New-LocalGroup.md)

[Ta bort-LocalGroup](Remove-LocalGroup.md)

[Byt namn – lokal](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
