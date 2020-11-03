---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: f73f22ff81a5aea6bff272328f0c523cd93a9c0d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266793"
---
# Get-PSProvider

## SAMMANFATTNING
Hämtar information om den angivna PowerShell-providern.

## SYNTAX

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-PSProvider`Cmdlet: en hämtar PowerShell-providern i den aktuella sessionen.
Du kan hämta en viss enhet eller alla enheter i sessionen.

Med PowerShell-providers kan du komma åt olika data lager som om de vore fil system enheter.
Information om PowerShell-leverantörer finns [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## EXEMPEL

### Exempel 1: Visa en lista över alla tillgängliga providers

```powershell
Get-PSProvider
```

Det här kommandot visar en lista över alla tillgängliga PowerShell-leverantörer.

### Exempel 2: Visa en lista över alla PowerShell-leverantörer som börjar med angivna bokstäver

```powershell
Get-PSProvider f*, r* | Format-List
```

Det här kommandot visar en lista över alla PowerShell-leverantörer med namn som börjar med bokstaven f eller r.

### Exempel 3: Sök efter snapin-moduler eller moduler som har lagts till providers i sessionen

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
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
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

Kommandona hittar PowerShell-snapin-modulerna eller moduler som har lagt till providrar i sessionen.
Alla PowerShell-element, inklusive providers, har sitt ursprung i en snapin-modul eller i en modul.

Dessa kommandon använder egenskaperna PSSnapin och module för det **ProviderInfo** -objekt som `Get-PSProvider` returneras.
Värdena för dessa egenskaper innehåller namnet på snapin-modulen eller modulen som lägger till providern.

Det första kommandot hämtar alla providers i sessionen och formaterar dem i en tabell med värdena för deras namn, modul och egenskaper för PSSnapin.

Det andra kommandot använder `Where-Object` cmdleten för att hämta de providrar som kommer från snapin-modulen **Microsoft. PowerShell. Security** .

### Exempel 4: matcha sökvägen för fil system leverantörens start egenskap

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

Det här exemplet visar att Tilde-symbolen (~) representerar värdet för fil systemets **Start** egenskap.
Värdet för **Start** egenskapen är valfritt, men för **fil Systems** leverantören definieras det som `$env:homedrive\$env:homepath` eller `$home` .

## PARAMETRAR

### -PSProvider

Anger namnet eller namnen på de PowerShell-leverantörer som denna cmdlet hämtar information om.

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Sträng []

Du kan skicka en eller flera providers namn strängar till denna cmdlet.

## UTDATA

### System. Management. Automation. ProviderInfo

Denna cmdlet returnerar objekt som representerar PowerShell-providern i sessionen.

## ANTECKNINGAR

## RELATERADE LÄNKAR
