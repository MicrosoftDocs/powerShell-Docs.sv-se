---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: a1459c276d8d6b2d031bc4b4f7ab521f7582a4cb
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/11/2020
ms.locfileid: "93269163"
---
# Get-Verb

## SAMMANFATTNING
Hämtar godkända PowerShell-verb.

## SYNTAX

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Verb`Funktionen hämtar verb som har godkänts för användning i PowerShell-kommandon.

Vi rekommenderar att PowerShell-cmdlet och funktions namn har `Verb-Noun` formatet och innehåller ett godkänt verb. Den här metoden gör kommando namn mer konsekventa, förutsägbara och enklare att använda.

Kommandon som använder icke godkända verb, körs fortfarande i PowerShell. Men när du importerar en modul som innehåller ett kommando med ett ej godkänt verb i namnet, `Import-Module` visar kommandot ett varnings meddelande.

> [!NOTE]
> Verb listan som `Get-Verb` returneras kanske inte är fullständig. En uppdaterad lista över godkända PowerShell-verb med beskrivningar finns i [godkända verb](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) i Microsoft docs.

## Exempel

### Exempel 1 – Hämta en lista över alla verb

```powershell
Get-Verb
```

### Exempel 2 – Hämta en lista över godkända verb som börjar med "UN"

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### Exempel 3 – hämta alla godkända verb i säkerhets gruppen

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
```

### Exempel 4 – hittar alla kommandon i en modul som har ej godkända verb

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## PARAMETRAR

### -Verb

Hämtar endast de angivna verben. Ange namnet på ett verb eller ett namn mönster. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – Grupp

Hämtar endast de angivna grupperna. Ange namnet på en grupp. Jokertecken är inte tillåtna.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

## UTDATA

### System. Management. Automation. VerbInfo

## ANTECKNINGAR

PowerShell-verb tilldelas en grupp baserat på den vanligaste användningen. Grupperna är utformade för att göra verben enkla att hitta och jämföra och inte begränsa användningen. Du kan använda valfritt godkänt verb för alla typer av kommandon.

Varje PowerShell-verb tilldelas en av följande grupper.

- Common: Definiera allmänna åtgärder som kan gälla för nästan alla cmdletar, till exempel Add.
- Kommunikation: definiera åtgärder som gäller för kommunikation, till exempel Anslut.
- Data: definiera åtgärder som gäller för data hantering, till exempel säkerhets kopiering.
- Diagnostik: definiera åtgärder som gäller diagnostik, till exempel fel sökning.
- Livs cykel: definiera åtgärder som gäller för livs cykeln för en cmdlet, till exempel fullständig.
- Säkerhet: definiera åtgärder som ska vidtas för säkerhet, till exempel återkalla.
- Övrigt: definiera andra typer av åtgärder.

Några av cmdletarna som installeras med PowerShell, till exempel `Tee-Object` och `Where-Object` , använder inte godkända verb. Dessa cmdletar är historiska undantag och deras verb klassificeras som **reserverade**.

## RELATERADE LÄNKAR

[Importera-modul](../microsoft.powershell.core/import-module.md)
