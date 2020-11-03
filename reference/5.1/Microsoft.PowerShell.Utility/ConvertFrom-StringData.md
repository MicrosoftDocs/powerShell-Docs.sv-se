---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: f4b58605059d85cd2a215969c13f9cc2e5262465
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265172"
---
# ConvertFrom-StringData

## SAMMANFATTNING
Konverterar en sträng som innehåller ett eller flera nyckel-och värdepar till en hash-tabell.

## SYNTAX

```
ConvertFrom-StringData [-StringData] <String> [<CommonParameters>]
```

## BESKRIVNING

`ConvertFrom-StringData`Cmdleten konverterar en sträng som innehåller en eller flera nyckel-och värdepar till en hash-tabell. Eftersom varje nyckel/värde-par måste finnas på en separat rad används ofta följande strängar som indataformat. Som standard måste **nyckeln** skiljas från **värdet** med ett likhets tecken ( `=` ).

`ConvertFrom-StringData`Cmdleten anses vara en säker cmdlet som kan användas i `DATA` avsnittet i ett skript eller en funktion. När det används i ett `DATA` avsnitt måste innehållet i strängen följa reglerna för ett data avsnitt. Mer information finns i [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).

`ConvertFrom-StringData` stöder escape-tecken som tillåts av konventionella verktyg för maskin översättning. Det vill säga att cmdleten kan tolka omvända snedstreck ( `\` ) som escape-tecken i sträng data med hjälp av [regex. unescape-metoden](/dotnet/api/system.text.regularexpressions.regex.unescape)i stället för PowerShell-tecknet ( \` ) som normalt signalerar slutet på en rad i ett skript. Inuti denna-sträng fungerar inte autoskalning-tecken. Du kan också bevara ett omvänt snedstreck i resultatet genom att använda ett föregående omvänt snedstreck, t. ex `\\` .:. Avvisade omvända snedstreck, till exempel de som ofta används i fil Sök vägar, kan återges som otillåtna escape-sekvenser i resultatet.

## EXEMPEL

### Exempel 1: konvertera en a-citerad hit-sträng till en hash-tabell

I det här exemplet konverteras en a-sträng med användar meddelanden till en hash-tabell. I en sträng med en citat tecken ersätts inte värdena för variabler och uttryck utvärderas inte.
`ConvertFrom-StringData`Cmdleten konverterar värdet i `$Here` variabeln till en hash-tabell.

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### Exempel 2: konvertera en här-sträng som innehåller en kommentar

I det här exemplet konverteras en här-sträng som innehåller en kommentar och flera nyckel/värde-par till en hash-tabell.

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

Värdet för parametern **StringData** är en här-sträng, i stället för en variabel som innehåller en här-sträng. Båda formaten är giltiga. Denna-sträng innehåller en kommentar om en av strängarna.
`ConvertFrom-StringData` ignorerar kommentarer på en rad, men det `#` måste vara det första icke-blank tecken på raden. Alla tecken på raden efter `#` ignoreras.

### Exempel 3: konvertera en sträng till en hash-tabell

I det här exemplet konverteras en vanlig sträng med dubbla citat tecken (inte en här sträng) till en hash-tabell och sparas i `$A` variabeln.

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

För att uppfylla villkoret att varje nyckel/värde-par måste finnas på en separat rad, använder strängen PowerShell-starttecknet ( \` n) för att avgränsa paren.

### Exempel 4: Använd ConvertFrom-StringData i DATA avsnittet i ett skript

I det här exemplet visas ett `ConvertFrom-StringData` kommando som används i data avsnittet i ett skript.
I instruktionerna under DATA avsnittet visas texten för användaren.

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

Eftersom texten innehåller variabel namn måste den omges av en sträng med en citat tecken så att variabler tolkas bokstavligen och inte expanderas. Variabler är inte tillåtna i **data** -avsnittet.

### Exempel 5: Använd pipeline-operatorn för att skicka en sträng

Det här exemplet visar att du kan använda en pipeline-operator ( `|` ) för att skicka en sträng till `ConvertFrom-StringData` . Värdet för `$Here` variabeln är skickas `ConvertFrom-StringData` och resultatet i `$Hash` variabeln.

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### Exempel 6: Använd escape-tecken för att lägga till nya rader och retur tecken

Det här exemplet visar hur du använder escape-tecken för att skapa nya rader och returnera tecken i källdata. Escape-sekvensen `\n` används för att skapa nya rader i ett block med text som är associerat med ett namn eller ett objekt i den resulterande hash-tabellen.

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### Exempel 7: Använd omvänt snedstreck escape-tecken för att rendera en fil Sök väg korrekt

Det här exemplet visar hur du använder ett omvänt snedstreck i sträng data för att tillåta att en fil Sök väg återges korrekt i den resulterande `ConvertFrom-StringData` hash-tabellen. Det dubbla omvända snedstrecket garanterar att tecknen för litteral omvänt snedstreck återges korrekt i utdata för hash-tabellen.

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## PARAMETRAR

### -StringData

Anger den sträng som ska konverteras. Du kan använda den här parametern eller skicka en sträng till `ConvertFrom-StringData` . Parameter namnet är valfritt.

Värdet för den här parametern måste vara en sträng som innehåller ett eller flera nyckel/värde-par. Varje nyckel/värde-par måste finnas på en separat rad, eller varje par måste avgränsas med rad matnings tecken ( \` n).

Du kan inkludera kommentarer i strängen, men kommentarerna får inte finnas på samma rad som ett nyckel/värde-par. `ConvertFrom-StringData` ignorerar kommentarer på en rad. `#`Specialtecknet måste vara det första icke-blank tecken på raden. Alla tecken på raden efter `#` ignoreras. Kommentarerna ingår inte i hash-tabellen.

En här-sträng är en sträng som består av en eller flera rader. Citat tecken inom denna-sträng tolkas bokstavligen som en del av sträng data. Mer information finns i [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller ett nyckel/värde-par till `ConvertFrom-StringData` .

## UTDATA

### System. Collections. hash

Denna cmdlet returnerar en hash-tabell som den skapar från nyckel/värde-par.

## ANTECKNINGAR

En här-sträng är en sträng som består av en eller flera rader inom vilka citat tecken tolkas bokstavligen.

Denna cmdlet kan vara användbar i skript som visar användar meddelanden på flera talade språk. Du kan använda hash-tabeller i lexikonet för att isolera text strängar från kod, till exempel i resursfiler, och för att formatera text strängarna för användning i översättnings verktyg.

## RELATERADE LÄNKAR
