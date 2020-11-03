---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 08ff101019db6baa8b84f56e862f140a028e9539
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267086"
---
# Get-Alias

## SAMMANFATTNING
Hämtar alias för den aktuella sessionen.

## SYNTAX

### Standard (standard)

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### Definition

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **Get-alias** hämtar alias i den aktuella sessionen.
Detta inkluderar inbyggda alias, alias som du har angett eller importerat och alias som du har lagt till i din PowerShell-profil.

**Get-alias** tar som standard ett alias och returnerar kommando namnet.
När du använder *definitions* parametern tar **Get-alias** ett kommando namn och returnerar dess alias.

Från och med Windows PowerShell 3,0 visar **Get-alias** icke-avstavade aliasnamn i ett `<alias> -> <definition>` format för att göra det ännu enklare att hitta den information som du behöver.

## EXEMPEL

### Exempel 1: Hämta alla alias i den aktuella sessionen

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

Det här kommandot hämtar alla alias i den aktuella sessionen.

Utdata visar det `<alias> -> <definition>` format som introducerades i Windows PowerShell 3,0.
Det här formatet används endast för alias som inte innehåller bindestreck, eftersom alias med bindestreck är vanligt vis önskade namn för cmdlets och functions, i stället för smek namn.

### Exempel 2: Hämta alias efter namn

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

Det här kommandot hämtar alla alias som börjar med GP eller SP, förutom alias som slutar med PS.

### Exempel 3: Hämta alias för en cmdlet

```powershell
Get-Alias -Definition Get-ChildItem
```

Det här kommandot hämtar aliasen för Get-ChildItem-cmdleten.

Som standard hämtar cmdleten **Get-alias** objekt namnet när du känner till aliaset.
*Definitions* parametern hämtar aliaset när du känner till objekt namnet.

### Exempel 4: Hämta alias efter egenskap

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

Det här kommandot hämtar alla alias där värdet för egenskapen Options är ReadOnly.
Det här kommandot är ett snabbt sätt att hitta de alias som är inbyggda i PowerShell, eftersom de har alternativet ReadOnly.

Alternativen är bara en egenskap hos de AliasInfo-objekt som **Get-alias** hämtar.
Om du vill hitta alla egenskaper och metoder för AliasInfo-objekt skriver du `Get-Alias | get-member` .

### Exempel 5: Hämta alias efter namn och filtrera efter start bokstav

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

Det här exemplet hämtar alias för kommandon som har namn som slutar med "-PSSession", förutom de som börjar med "e".

Kommandot använder *omfattnings* parametern för att tillämpa kommandot i det globala omfånget.
Detta är användbart i skript när du vill hämta alias i sessionen.

## PARAMETRAR

### -Definition

Hämtar alias för det angivna objektet.
Ange namnet på en cmdlet, funktion, skript, fil eller körbar fil.

Den här parametern heter *definition* , eftersom den söker efter objekt namnet i egenskapen definition i objektet alias.

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Undanta

Utesluter de angivna objekten.
Värdet för den här parametern kvalificerar namn-och definitions parametrarna.
Ange ett namn, en definition eller ett mönster, till exempel "s *".
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

Anger de alias som denna cmdlet hämtar.
Jokertecken är tillåtna.
Som standard `Get-Alias` hämtar alla alias som definierats för den aktuella sessionen.
Parameter namnets **namn** är valfritt.
Du kan också skicka namn på alias till `Get-Alias` .

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – Omfattning

Anger omfattningen som denna cmdlet hämtar alias för.
De acceptabla värdena för den här parametern är:

- Global
- Lokal
- Skript
- Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)

Lokalt är standard.
Mer information finns i about_Scopes.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan hämta alias för att **Hämta alias**.

## UTDATA

### System. Management. Automation. AliasInfo

**Get-alias** returnerar ett objekt som representerar varje alias.
**Get-alias** returnerar samma objekt för varje alias, men PowerShell använder ett pil-baserat format för att visa namnen på icke-avstavade alias.

## ANTECKNINGAR

- Om du vill skapa ett nytt alias använder Set-Alias eller New-alias. Använd Remove-Item om du vill ta bort ett alias.
- Formatet för den pilbaserade aliaset används inte för alias som innehåller bindestreck. Detta är sannolikt att föredra ersättnings namn för cmdlets och functions, i stället för vanliga förkortningar eller smek namn.

## RELATERADE LÄNKAR

[Exportera-alias](Export-Alias.md)

[Importera-alias](Import-Alias.md)

[Nytt-alias](New-Alias.md)

[Set-alias](Set-Alias.md)

[Aliasresurspost](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)
