---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: 0a935f03e479ed84fa8167f7c4c29e91bd774009
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264350"
---
# Get-TypeData

## Sammanfattning
Hämtar utökade typ data i den aktuella sessionen.

## Syntax

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## Beskrivning

`Get-TypeData`Cmdlet: en hämtar utökade typ data i den aktuella sessionen. Detta inkluderar typ data som har lagts till i sessionen av `Types.ps1xml` fil-och dynamiska typ data som har lagts till med hjälp av parametern för `Update-TypeData` cmdleten.

Du kan använda de utökade typ data som `Get-TypeData` returnerar för att undersöka typ data i sessionen och skicka dem till `Update-TypeData` `Remove-TypeData` cmdletarna och.

Utökade typ data lägger till egenskaper och metoder för objekt i PowerShell. Du kan använda de tillagda egenskaperna och metoderna på samma sätt som du använder de egenskaper och metoder som definieras i objekt typen. Men när du skriver skript bör du vara medveten om att de tillagda egenskaperna och metoderna kanske inte finns i varje PowerShell-session.

Mer information om `Types.ps1xml` filer finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md). Mer information om dynamiska data typer som `Update-TypeData` cmdleten lägger till finns i `Update-TypeData` .

Den här cmdleten introducerades i Windows PowerShell 3,0.

## Exempel

### Exempel 1: Hämta alla utökade typ data

Det här exemplet hämtar alla utökade typ data i den aktuella sessionen.

 ```powershell
Get-TypeData
```

### Exempel 2: Hämta typer efter namn

Det här exemplet hämtar alla typer i den aktuella sessionen som har namn som innehåller händelser.

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### Exempel 3: Hämta skript blocket som skapar ett egenskaps värde

Det här exemplet hämtar skript blocket som skapar värdet för egenskapen **EventID** för **EventLogEntry** -objekt.

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### Exempel 4: Hämta skript blocket som definierar en egenskap för ett angivet objekt

Det här exemplet hämtar skript blocket som definierar egenskapen **datetime** för **system. DateTime** -objekt i PowerShell.

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

Kommandot använder `Get-TypeData` cmdleten för att hämta de utökade data typerna för **system. datum/tid** -typen. Kommandot hämtar egenskapen **members** för **TypeData** -objektet.

Egenskapen **members** innehåller en hash-tabell med egenskaper och metoder som definieras av utökade typ data. Varje nyckel i hash-tabellen medlemmar är ett egenskaps-eller metod namn och varje värde är definitionen av egenskapen eller metod svärdet.

Kommandot hämtar **datetime** -nyckeln i **members** och dess egenskaps värde för **GetScriptBlock** .

Utdata visar skript blocket som skapar värdet för egenskapen **datetime** för varje **system. DateTime** -objekt i PowerShell.

## Parametrar

### -TypeName

Anger ange data som en matris enbart för de typer som har angivna namn. Som standard `Get-TypeData` hämtar alla typer i sessionen.

Ange typ namn eller namn mönster. Fullständiga namn eller namn mönster med jokertecken krävs, även för typer i namn området system. Jokertecken stöds och parameter namn **TypeName** är valfritt. Du kan också skicka pipe-namn till `Get-TypeData` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Indata

### System. String

Du kan skicka pipe-typnamn till `Get-TypeData` .

## Utdata

### System. Management. Automation. körnings utrymmen. TypeData

## Kommentarer

`Get-TypeData` hämtar endast utökade typ data i den aktuella sessionen. Den får inte utökad typ av data som finns på datorn, men som inte har lagts till i den aktuella sessionen, till exempel utökade typer som har definierats i moduler som inte har importer ATS till den aktuella sessionen.

## Relaterade länkar

[about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Remove-TypeData](Remove-TypeData.md)

[Uppdatera – TypeData](Update-TypeData.md)

