---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: d40dc5d85fc1a6999eccac54e72f2f0870afd9b4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264225"
---
# Out-Host

## SAMMANFATTNING
Skickar utdata till kommando raden.

## SYNTAX

### Alla

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## BESKRIVNING

`Out-Host`Cmdleten skickar utdata till PowerShell-värden för visning. Värden visar utdata på kommando raden. Eftersom `Out-Host` är standard behöver du inte ange den om du inte vill använda dess parametrar.

`Out-Host` läggs automatiskt till varje kommando som körs. Den skickar ut pipelinen till värden som kör kommandot. `Out-Host` ignorerar ANSI escape-sekvenser. Escape-sekvenser hanteras av värden. `Out-Host` skickar ANSI escape-sekvenser till värden utan att försöka tolka eller ändra dem.

## EXEMPEL

### Exempel 1: Visa utdata en sida i taget

I det här exemplet visas en sida i taget i systemet.

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

`Get-Process` hämtar system processerna och skickar objekten nedåt i pipelinen. `Out-Host` använder **växlings** parametern för att visa en sida med data i taget.

### Exempel 2: Använd en variabel som inmatad

I det här exemplet används objekt som är lagrade i en variabel som inloggade `Out-Host` .

```powershell
$io = Get-History
Out-Host -InputObject $io
```

`Get-History` hämtar PowerShell-sessionens historik och lagrar objekten i `$io` variabeln.
`Out-Host` använder parametern **InputObject** för att ange `$io` variabeln och visar historiken.

## PARAMETRAR

### – InputObject

Anger de objekt som skrivs till-konsolen. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

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

### -Sid indelning

Anger att `Out-Host` visar en sida med utdata i taget och väntar på användarindata innan de återstående sidorna visas. Som standard visas alla utdata på en enda sida. Sid storleken bestäms av egenskaperna för värden.

Tryck på <kbd>blank steg</kbd> för att visa nästa sida med utdata eller <kbd>RETUR</kbd> tangenten för att visa nästa rad utdata. Tryck på <kbd>Q</kbd> för att avsluta.

**Sid indelning** liknar kommandot **more** .

> [!NOTE]
> **Växlings** parametern stöds inte av PowerShell ISE-värden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka objekt nedåt i pipelinen till `Out-Host` .

## UTDATA

### Inget

`Out-Host` genererar inga utdata. Den skickar objekt till värden för visning.

## ANTECKNINGAR

**Växlings** parametern stöds inte av alla PowerShell-värdar. Om du till exempel använder **växlings** parametern i PowerShell ISE visas följande fel: `out-lineoutput : The method or operation is not implemented.`

De cmdletar som **innehåller verbet** , `Out-` formaterar inte objekt. De återger objekt och skickar dem till det angivna visnings målet. Om du skickar ett oformaterat objekt till en `Out-` cmdlet skickar cmdleten den till en formaterings-cmdlet innan du återger den.

`Out-`Cmdletarna har inte parametrar för namn eller fil Sök vägar. Om du vill skicka data till en `Out-` cmdlet använder du pipelinen för att skicka ett PowerShell-kommandos utdata till cmdlet: en. Du kan också lagra data i en variabel och använda parametern **InputObject** för att skicka data till cmdleten.

`Out-Host` skickar data, men genererar inga utdata-objekt. Om du pipelinerar utdata från `Out-Host` till `Get-Member` cmdlet: en `Get-Member` rapporteras inga objekt.

## RELATERADE LÄNKAR

[Rensa värd](Clear-Host.md)

[Ut-standard](Out-Default.md)

[Ut-fil](../Microsoft.PowerShell.Utility/Out-File.md)

[Ut-null](Out-Null.md)

[Out-Printer](../Microsoft.PowerShell.Utility/Out-Printer.md)

[Out-sträng](../Microsoft.PowerShell.Utility/Out-String.md)

[Skriv värd](../Microsoft.PowerShell.Utility/Write-Host.md)
