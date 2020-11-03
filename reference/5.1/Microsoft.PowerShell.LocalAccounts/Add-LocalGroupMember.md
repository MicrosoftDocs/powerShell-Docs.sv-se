---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-LocalGroupMember
ms.openlocfilehash: 06993c8f6618472f4809e37fbf83d298d13ae515
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263535"
---
# Add-LocalGroupMember

## SAMMANFATTNING
Lägger till medlemmar i en lokal grupp.

## SYNTAX

### Group

```
Add-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Default

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Add-LocalGroupMember`Cmdleten lägger till användare eller grupper i en lokal säkerhets grupp. Alla rättigheter och behörigheter som tilldelas en grupp tilldelas till alla medlemmar i gruppen.

Medlemmar i gruppen Administratörer på en lokal dator har fullständig behörighet på den datorn. Begränsa antalet användare i gruppen Administratörer.

Om datorn är ansluten till en domän kan du lägga till användar konton, dator konton och grupp konton från domänen och från betrodda domäner till en lokal grupp.

> [!NOTE]
> Om datorn är ansluten till en domän och du försöker lägga till en lokal användare som har samma namn som en medlem i domänen läggs domän medlemmen till.

## EXEMPEL

### Exempel 1: Lägg till medlemmar i gruppen Administratörer

Det här kommandot lägger till flera medlemmar i den lokala gruppen Administratörer. De nya medlemmarna inkluderar ett lokalt användar konto, ett Microsoft-konto, ett Azure Active Directory konto och en domän grupp. I det här exemplet används ett plats hållare-värde för användar namnet för ett konto på Outlook.com.

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

## PARAMETRAR

### – Grupp

Anger den säkerhets grupp som denna cmdlet lägger till medlemmar i.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Medlem

Anger en matris med användare eller grupper som denna cmdlet lägger till i en säkerhets grupp. Du kan ange användare eller grupper efter namn, säkerhets-ID (SID) eller **LocalPrincipal** -objekt.

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Anger namnet på den säkerhets grupp som denna cmdlet lägger till medlemmar i.

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID

Anger säkerhets-ID: t för den säkerhets grupp som denna cmdlet lägger till medlemmar i.

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
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

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

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

### System. Management. Automation. SecurityAccountsManager. LocalGroup, system. String, system. Security. Principal. SecurityIdentifier

Du kan skicka vidare ett lokalt huvud namn, en sträng eller ett SID till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.

Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa. De möjliga källorna är följande:

- Lokal
- Active Directory
- Azure Active Directory grupp
- Microsoft-konto

**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows. För tidigare versioner är egenskapen tom.

## RELATERADE LÄNKAR

[Get-LocalGroupMember](Get-LocalGroupMember.md)

[New-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroupMember](Remove-LocalGroupMember.md)
