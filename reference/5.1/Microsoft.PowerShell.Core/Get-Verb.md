---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/11/2020
ms.locfileid: "93269157"
---
# Get-Verb

## SAMMANFATTNING
Hämtar godkända PowerShell-verb.

## SYNTAX

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Verb`Funktionen hämtar verb som har godkänts för användning i PowerShell-kommandon.

PowerShell rekommenderar att cmdlet-och funktions namn har Verb-Noun format och innehåller ett godkänt verb. Den här metoden gör kommando namn mer konsekventa, förutsägbara och enklare att använda.

Kommandon som använder icke godkända verb körs i PowerShell. Men när du importerar en modul som innehåller ett kommando med ett ej godkänt verb i namnet, `Import-Module` visar kommandot ett varnings meddelande.

> [!NOTE]
> Verb listan som `Get-Verb` returneras kanske inte är fullständig. En uppdaterad lista över godkända PowerShell-verb med beskrivningar finns i [godkända verb](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) i Microsoft docs.

## EXEMPEL

### Exempel 1 – Hämta en lista över alla verb

```powershell
Get-Verb
```

### Exempel 2 – Hämta en lista över godkända verb som börjar med "UN"

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### Exempel 3 – hämta alla godkända verb i säkerhets gruppen

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
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

### -verb

Hämtar endast de angivna verben.
Ange namnet på ett verb eller ett namn mönster.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## INDATA

### Inget

## UTDATA

### Markerat. Microsoft. PowerShell. commands. MemberDefinition

## ANTECKNINGAR

`Get-Verb` Returnerar en modifierad version av ett Microsoft. PowerShell. commands. MemberDefinition-objekt.
Objektet har inte standard egenskaperna för ett MemberDefinition-objekt. I stället har det verb-och grupp egenskaper. Verb-egenskapen innehåller en sträng med verbets namn. Grupp egenskapen innehåller en sträng med gruppen verb.

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

[Importera-modul](import-module.md)
