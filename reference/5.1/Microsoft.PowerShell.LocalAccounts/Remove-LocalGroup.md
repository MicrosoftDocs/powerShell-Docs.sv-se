---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265574"
---
# Remove-LocalGroup

## SAMMANFATTNING
Tar bort lokala säkerhets grupper.

## SYNTAX

### InputObject

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Default

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **Remove-localgroup** tar bort lokala säkerhets grupper.
Den här cmdleten tar bara bort en lokal grupp.
De användar konton, dator konton eller grupp konton som tillhör gruppen tas inte bort.
Det går inte att återställa en borttagen grupp.

Om du tar bort en grupp och sedan skapar en annan grupp som har samma grupp namn, måste du ange nya behörigheter för den nya gruppen.
Den nya gruppen ärver inte de behörigheter som har tilldelats gruppen.

> [!NOTE]
> Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.

## EXEMPEL

### Exempel 1: ta bort en säkerhets grupp

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

Det här kommandot tar bort gruppen med namnet SecurityGroup04.

## PARAMETRAR

### – InputObject
Anger en matris med säkerhets grupper som denna cmdlet tar bort.
Använd Get-LocalGroup-cmdleten för att hämta grupper.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Anger en matris med namn på de säkerhets grupper som denna cmdlet tar bort.

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
Anger en matris med säkerhets-ID: n (sid) för de säkerhets grupper som denna cmdlet tar bort.

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

### System. Management. Automation. SecurityAccountsManager. LocalGroup, system. String, system. Security. Principal. SecurityIdentifier
Du kan skicka vidare en säkerhets grupp, en sträng eller ett SID till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Denna cmdlet kan inte ta bort följande standard grupper:

- Administratörer
- Ansvariga för säkerhetskopiering
- Ansvariga för kryptering
- Distribuerade COM-användare
- Händelseloggläsare
- Gäster
- Hyper-V-administratörer
- IIS_IUSRS
- Ansvariga för nätverkskonfigurering
- Användare av prestandaloggar
- Användare av prestanda övervakning
- Privilegierade användare
- Användare av fjärrskrivbord
- Fjärrhanteringsanvändare
- Ansvariga för replikering
- Användare
- WinRMRemoteWMIUsers__

* Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa. De möjliga källorna är följande:

- Lokal
- Active Directory
- Azure Active Directory grupp
- Microsoft-konto

**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows. För tidigare versioner är egenskapen tom.

## RELATERADE LÄNKAR

[Get-LocalGroup](Get-LocalGroup.md)

[New-LocalGroup](New-LocalGroup.md)

[Byt namn – lokal](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
