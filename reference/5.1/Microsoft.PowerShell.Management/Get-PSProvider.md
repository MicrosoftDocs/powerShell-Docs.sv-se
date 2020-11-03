---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 997d86460837946a2cf18fc78f058f21472dd909
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266109"
---
# Get-PSProvider

## SAMMANFATTNING
Hämtar information om den angivna Windows PowerShell-providern.

## SYNTAX

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en get-PSProvider** hämtar Windows PowerShell-providers i den aktuella sessionen.
Du kan hämta en viss enhet eller alla enheter i sessionen.

Med Windows PowerShell-providers kan du komma åt olika data lager som om de vore fil system enheter.
Information om Windows PowerShell-leverantörer finns about_Providers.

## EXEMPEL

### Exempel 1: Visa en lista över alla tillgängliga providers

```
PS C:\> Get-PSProvider
```

Det här kommandot visar en lista över alla tillgängliga Windows PowerShell-leverantörer.

### Exempel 2: Visa en lista över alla Windows PowerShell-leverantörer som börjar med angivna bokstäver

```
PS C:\> Get-PSProvider f*, r* | Format-List
```

Det här kommandot visar en lista över alla Windows PowerShell-leverantörer med namn som börjar med bokstaven f eller r.

### Exempel 3: Sök efter snapin-moduler eller moduler som har lagts till providers i sessionen

```
PS C:\> Get-PSProvider | Format-Table name, module, pssnapin -auto

Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security

PS C:\> Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}

Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

Kommandona hittar de Windows PowerShell-snapin-moduler eller moduler som har lagt till providrar i sessionen.
Alla Windows PowerShell-element, inklusive providers, har sitt ursprung i en snapin-modul eller i en modul.

Dessa kommandon använder egenskaperna PSSnapin och module för **ProviderInfo** -objektet som returnerar **-PSProvider** returnerar.
Värdena för dessa egenskaper innehåller namnet på snapin-modulen eller modulen som lägger till providern.

Det första kommandot hämtar alla providers i sessionen och formaterar dem i en tabell med värdena för deras namn, modul och egenskaper för PSSnapin.

Det andra kommandot använder cmdleten Where-Object för att hämta de leverantörer som kommer från snapin-modulen **Microsoft. PowerShell. Security** .

### Exempel 4: matcha sökvägen för fil system leverantörens start egenskap

```
PS C:\> Resolve-Path ~

Path
----
C:\Users\User01

PS C:\> (get-psprovider FileSystem).home
C:\Users\User01
```

Det här exemplet visar att Tilde-symbolen (~) representerar värdet för fil systemets start egenskap.
Värdet för start egenskapen är valfritt, men för fil Systems leverantören definieras det som $env: HOMEDRIVE \$ miljö: HOMEPATH eller $Home.

## PARAMETRAR

### -PSProvider
Anger namn eller namn på de Windows PowerShell-leverantörer som den här cmdlet: en hämtar information om.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Sträng []

Du kan skicka en eller flera providers namn strängar till denna cmdlet.

## UTDATA

### System. Management. Automation. ProviderInfo
Denna cmdlet returnerar objekt som representerar Windows PowerShell-providers i sessionen.

## ANTECKNINGAR

## RELATERADE LÄNKAR

## RELATERADE LÄNKAR
