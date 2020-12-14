---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: 6198964f01a4c0dc70584cdb3e5c0e13f3965934
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709427"
---
# Group-Object

## SAMMANFATTNING
Grupperar objekt som innehåller samma värde för angivna egenskaper.

## SYNTAX

### Hash

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## BESKRIVNING

`Group-Object`Cmdleten visar objekt i grupper baserat på värdet för en angiven egenskap.
`Group-Object` Returnerar en tabell med en rad för varje egenskaps värde och en kolumn som visar antalet objekt med det värdet.

Om du anger mer än en egenskap, `Group-Object` grupperas de av värdena för den första egenskapen, och därefter grupperas de efter värdet för nästa egenskap i varje egenskaps grupp.

Från och med PowerShell 7 `Group-Object` kan du kombinera parametrarna **caseSensitive** och **AsHashtable** för att skapa en Skift läges känslig hash-tabell. Hash-tabellens nycklar använder SKIFT läges känsliga jämförelser och utdata av ett **system. Collections. hash** -objekt.

## EXEMPEL

### Exempel 1: Gruppera filer efter tillägg

Det här exemplet hämtar filerna rekursivt under `$PSHOME` och grupper dem efter fil namns tillägg. Utdata skickas till `Sort-Object` cmdleten, som sorteras efter antalet filer som hittas för det angivna tillägget. Det tomma **namnet** representerar kataloger.

I det här exemplet används **Noelement** -parametern för att utelämna medlemmarna i gruppen.

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### Exempel 2: gruppera heltal efter strider och Evens

Det här exemplet visar hur du använder skript block som värde för **egenskaps** parametern. Det här kommandot visar heltalen från 1 till 20, grupperat efter strider och även.

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### Exempel 3: gruppera händelse logg händelser efter EntryType

I det här exemplet visas de 1 000 senaste posterna i system händelse loggen, grupperade efter **EntryType**.

I utdata representerar kolumnen **Count** antalet poster i varje grupp. Kolumnen **namn** representerar de **EventType** -värden som definierar en grupp. **Grupp** kolumnen representerar objekten i varje grupp.

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### Exempel 4: gruppera processer efter prioritets klass

Det här exemplet visar effekterna av **Noelement** -parametern. De här kommandona grupperar processerna på datorn efter prioritets klass.

Det första kommandot använder `Get-Process` cmdleten för att hämta processerna på datorn och skickar de objekt som ligger nere i pipelinen. `Group-Object`grupperar objekten efter värdet för processens **priorityClass** -egenskap.

I det andra exemplet används **Noelement** -parametern för att eliminera medlemmar i gruppen från utdata. Resultatet är en tabell med bara egenskap svärdet **Count** och **Name** .

Resultatet visas i följande exempel på utdata.

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### Exempel 5: gruppera processer efter namn

I följande exempel används `Group-Object` för att gruppera flera instanser av processer som körs på den lokala datorn. `Where-Object` visar processer med fler än en instans.

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### Exempel 6: gruppera objekt i en hash-tabell

I det här exemplet används parametrarna **AsHashTable** och **enstring** för att returnera grupperna i en hash-tabell som en samling nyckel/värde-par.

I den resulterande hash-tabellen är varje egenskaps värde en nyckel och grupp elementen är värdena.
Eftersom varje nyckel är en egenskap för hash-tabellen, kan du använda punkt notation för att visa värdena.

Det första kommandot hämtar `Get` -och `Set` -cmdletarna i sessionen, grupperas efter verb, returnerar grupperna som en hash-tabell och sparar hash-tabellen i `$A` variabeln.

Det andra kommandot visar hash-tabellen i `$A` . Det finns två nyckel/värde-par, en för `Get` cmdletarna och en för `Set` cmdletarna.

Det tredje kommandot använder punkt notation `$A.Get` för att visa värdena för **Get** -nyckeln i `$A` . Värdena är **CmdletInfo** -objekt. Parametern **enstring** konverterar inte objekten i grupperna till strängar.

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                                Version    Source
-----------     ----                                -------    ------
Cmdlet          Get-Acl                             7.0.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                           7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AppLockerFileInformation        2.0.0.0    AppLocker
Cmdlet          Get-AppLockerPolicy                 2.0.0.0    AppLocker
...
```

### Exempel 7: skapa en Skift läges känslig hash-tabell

I det här exemplet kombineras parametrarna **caseSensitive** och **AsHashTable** för att skapa en Skift läges känslig hash-tabell. Filerna i exemplet har fil namns tilläggen `.txt` och `.TXT` .

```powershell
$hash = Get-ChildItem -Path C:\Files | Group-Object -Property Extension -CaseSensitive -AsHashTable
$hash
```

```Output
Name           Value
----           -----
.TXT           {C:\Files\File7.TXT, C:\Files\File8.TXT, C:\Files\File9.TXT}
.txt           {C:\Files\file1.txt, C:\Files\file2.txt, C:\Files\file3.txt}
```

`$hash`Variabeln lagrar objektet **system. Collections. hash** . `Get-ChildItem` hämtar fil namnen från `C:\Files` katalogen och skickar **system. io. fileinfo** -objekten nedåt i pipelinen. `Group-Object` grupperar objekten med hjälp av **egenskaps** värde **tillägget**. Parametrarna **caseSensitive** och **AsHashTable** skapar hash-tabellen och nycklarna grupperas med Skift läges känsliga nycklar `.txt` och `.TXT` .

## PARAMETRAR

### -AsHashTable

Anger att denna cmdlet returnerar gruppen som en hash-tabell. Nycklarna för hash-tabellen är de egenskaps värden som objekten grupperas med. Värdena för hash-tabellen är de objekt som har det egenskap svärdet.

**AsHashTable** -parametern returnerar däremot varje hash-tabell där varje nyckel är en instans av det grupperade objektet. Nycklarna i hash-tabellen är strängar när de används med parametern **enstring** .

Från och med PowerShell 7, för att skapa Skift läges känsliga hash-tabeller, inkluderar **caseSensitive** och **AsHashtable** i kommandot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uppsträng

Anger att denna cmdlet konverterar hash-tabellens nycklar till strängar. Nycklar för hash-tabellen är som standard instanser av det grupperade objektet. Den här parametern är endast giltig när den används med parametern **AsHashTable** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CaseSensitive

Anger att denna cmdlet gör grupperingen Skift läges känslig. Utan den här parametern kan egenskaps värden för objekt i en grupp ha olika fall.

Från och med PowerShell 7, för att skapa Skift läges känsliga hash-tabeller, inkluderar **caseSensitive** och **AsHashtable** i kommandot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Kultur

Anger kulturen som ska användas när strängar jämförs.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som ska grupperas. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

När du använder parametern **InputObject** för att skicka en samling objekt till `Group-Object` , `Group-Object` tar emot ett objekt som representerar samlingen. Därför skapas en enskild grupp med objektet som medlem.

Om du vill gruppera objekten i en samling, rör du objekten till `Group-Object` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Noelement

Anger att denna cmdlet utelämnar medlemmarna i en grupp från resultaten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Egenskap

Anger egenskaperna för gruppering. Objekten är ordnade i grupper baserat på värdet för den angivna egenskapen.

Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap. Den beräknade egenskapen kan vara ett skript block eller en hash-tabell. Giltiga nyckel/värde-par är:

- Uttryck- `<string>` eller `<script block>`

Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare alla objekt till `Group-Object` .

## UTDATA

### Microsoft. PowerShell. commands. GroupInfo eller system. Collections. hash

När du använder parametern **AsHashTable** `Group-Object` returneras ett **hash** -objekt.
Annars returnerar den ett **GroupInfo** -objekt.

## ANTECKNINGAR

Du kan använda parametern **groupby** i cmdletarna för formatering, till exempel `Format-Table` och `Format-List` , för att gruppera objekt. Till skillnad från `Group-Object` , som skapar en enskild tabell med en rad för varje egenskaps värde, skapar **groupby** -parametrarna en tabell för varje egenskaps värde med en rad för varje objekt som har egenskap svärdet.

`Group-Object` kräver inte att de objekt som grupperas är av samma Microsoft .NET Core-typ. När du grupperar objekt av olika .NET Core-typer, `Group-Object` använder följande regler:

- Samma egenskaps namn och-typer.

  Om objekten har en egenskap med det angivna namnet och egenskapsvärdena har samma .NET Core-typ grupperas egenskapsvärdena genom att använda samma regler som skulle användas för objekt av samma typ.

- Samma egenskaps namn, olika typer.

  Om objekten har en egenskap med det angivna namnet, men egenskapsvärdena har en annan .NET Core-typ i olika objekt, `Group-Object` använder .net Core-typen för den första förekomsten av egenskapen som .net Core-typ för den egenskaps gruppen. När ett objekt har en egenskap med en annan typ, konverteras egenskap svärdet till typen för den gruppen. Om typ konverteringen Miss lyckas tas objektet inte med i gruppen.

- Egenskaper saknas.

  Objekt som inte har någon angiven egenskap kan inte grupperas. Objekt som inte är grupperade visas i det slutliga **GroupInfo** objektets utdata i en grupp med namnet `AutomationNull.Value` .

## RELATERADE LÄNKAR

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Jämför objekt](Compare-Object.md)

[-Objekt](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Mått – objekt](Measure-Object.md)

[Nytt – objekt](New-Object.md)

[Select-Object](Select-Object.md)

[Sortera objekt](Sort-Object.md)

[Tee – objekt](Tee-Object.md)

[Where-objekt](../Microsoft.PowerShell.Core/Where-Object.md)
