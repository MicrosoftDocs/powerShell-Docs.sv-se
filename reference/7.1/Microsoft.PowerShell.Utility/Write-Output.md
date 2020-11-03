---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: ec1b2eabbd49095d8daf48cb79033b494ea46de5
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272799"
---
# Write-Output

## SAMMANFATTNING
Skickar de angivna objekten till nästa-kommando i pipelinen. Om kommandot är det sista kommandot i pipelinen visas objekten i-konsolen.

## SYNTAX

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## BESKRIVNING

`Write-Output`Cmdleten skickar det angivna objektet nedåt i pipeline till nästa kommando.
Om kommandot är det sista kommandot i pipelinen visas objektet i-konsolen.

`Write-Output` skickar objekt nedåt i den primära pipelinen, även kallat "utdataström" eller "lyckad pipeline". Om du vill skicka fel-objekt går du till fel pipeline, använder Write-Error.

Denna cmdlet används vanligt vis i skript för att Visa strängar och andra objekt i-konsolen. Ett av de inbyggda aliasen för `Write-Output` är `echo` och liknar andra gränssnitt som använder `echo` , vilket är standard beteendet för att visa utdata i slutet av en pipeline. I PowerShell är det vanligt vis inte nödvändigt att använda cmdleten i instanser där utdata visas som standard. `Get-Process | Write-Output` motsvarar till exempel `Get-Process`. Eller, `echo "Home directory: $HOME"` kan skrivas, `"Home directory: $HOME"` .

Som standard `Write-Output` räknar upp genom samlingar som tillhandahålls till cmdleten. `Write-Output`Du kan dock även använda för att skicka samlingar nedåt i pipeline som ett enda objekt med parametern **noenumeration** .

## EXEMPEL

### Exempel 1: Hämta objekt och skriv dem till konsolen

```powershell
$P = Get-Process
Write-Output $P
```

Det första kommandot hämtar processer som körs på datorn och lagrar dem i `$P` variabeln.

Det andra och tredje kommandot visar process objekt i `$P` på-konsolen.

### Exempel 2: skicka utdata till en annan cmdlet

```powershell
Write-Output "test output" | Get-Member
```

Det här kommandot rör strängen "test output" till `Get-Member` cmdleten, som visar medlemmarna i klassen **system. String** , som demonstrerar att strängen skickades ut i pipeline.

### Exempel 3: utelämna uppräkning i utdata

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

Det här kommandot lägger till parametern **noenumeration** för att behandla en samling eller matris som ett enskilt objekt via pipelinen.

## PARAMETRAR

### – InputObject

Anger de objekt som ska skickas ned pipelinen. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Noenumeration

Som standard `Write-Output` räknar cmdleten alltid upp utdata. Parametern **Noenumeration** förhindrar standard beteendet och förhindrar att `Write-Output` utdata räknas upp. Parametern **noenumeration** har ingen verkan om kommandot omsluts av parenteser, eftersom parenteser tvingar fram uppräkningen. Räknar till exempel `(Write-Output 1,2,3)` fortfarande matrisen.

> [!NOTE]
> Den här växeln fungerar bara korrekt med PowerShell Core 6,2 och senare. I äldre versioner av PowerShell Core räknas samlingen fortfarande upp även om den här växeln används.

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

Du kan skicka pipe-objekt till `Write-Output` .

## UTDATA

### System. Management. Automation. PSObject

`Write-Output` Returnerar de objekt som skickas som inaktuella inmatade objekt.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Tee – objekt](Tee-Object.md)

[Skriv-debug](Write-Debug.md)

[Skriv-fel](Write-Error.md)

[Skriv värd](Write-Host.md)

[Skriv information](Write-Information.md)

[Skriv förlopp](Write-Progress.md)

[Skriv-verbose](Write-Verbose.md)

[Skriv varning](Write-Warning.md)
