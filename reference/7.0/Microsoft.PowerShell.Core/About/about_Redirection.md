---
description: Förklarar hur du omdirigerar utdata från PowerShell till textfiler.
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: bc72f479650d67ed17b5fafef56565ccbebfea13
ms.sourcegitcommit: b9826dcf402db8a2b6d3eab37edb82c6af113343
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040877"
---
# <a name="about-redirection"></a>Om omdirigering

## <a name="short-description"></a>Kort beskrivning
Förklarar hur du omdirigerar utdata från PowerShell till textfiler.

## <a name="long-description"></a>Lång beskrivning

Som standard skickar PowerShell utdata till PowerShell-värden. Detta är vanligt vis konsol programmet. Du kan dock dirigera utdata till en textfil och du kan omdirigera fel utdata till den vanliga utdataströmmen.

Du kan använda följande metoder för att omdirigera utdata:

- Använd `Out-File` cmdleten som skickar kommandoutdata till en textfil.
  Normalt använder du `Out-File` cmdleten när du behöver använda dess parametrar, till exempel `Encoding` parametrarna,, `Force` `Width` eller `NoClobber` .

- Använd `Tee-Object` cmdleten, som skickar kommandoutdata till en textfil och sedan skickar den till pipelinen.

- Använd operatorerna för PowerShell-omdirigering. Att använda operatorn för omdirigering med ett fil mål är detsamma som att dirigera till utan `Out-File` extra parametrar.

Mer information om strömmar finns [about_Output_Streams](about_Output_Streams.md).

### <a name="redirectable-output-streams"></a>Omdirigerade utgående strömmar

PowerShell stöder omdirigering av följande utdata-strömmar.

| Skicka # |      Description       | Infört i  |    Skriv cmdlet     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **Lyckades** Skicka     | PowerShell 2,0 | `Write-Output`      |
| 2        | **Fel** Skicka       | PowerShell 2,0 | `Write-Error`       |
| 3        | **Varning** Skicka     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **Utförlig** Skicka     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **Felsök** Skicka       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **Information** Skicka | PowerShell 5.0 | `Write-Information` |
| *        | Alla strömmar            | PowerShell 3.0 |                     |

> [!NOTE]
> Det finns också en **förlopps** ström i PowerShell, men den stöder inte omdirigering.

### <a name="powershell-redirection-operators"></a>Operatorer för PowerShell-omdirigering

Operatorerna för PowerShell-omdirigering är följande, där `n` representerar Stream-numret. **Framgångs** strömmen ( `1` ) är standard om ingen ström anges.

| Operator |                         Beskrivning                         | Syntax |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | Skicka angiven data ström till en fil.                            | `n>`   |
| `>>`     | **Lägg till** angiven data ström i en fil.                      | `n>>`  |
| `>&1`    | _Omdirigerar_ den angivna data strömmen till den **framgångs rik** data strömmen. | `n>&1` |

> [!NOTE]
> Till skillnad från vissa UNIX-gränssnitt kan du bara omdirigera andra strömmar till strömmen som **lyckats** .

## <a name="examples"></a>Exempel

### <a name="example-1-redirect-errors-and-output-to-a-file"></a>Exempel 1: omdirigera fel och utdata till en fil

Det här exemplet körs `dir` på ett objekt som kommer att lyckas, och ett som kommer att vara fel.

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

Den använder `2>&1` för att dirigera om **fel** strömmen till  strömmen och `>` skicka den resulterande **framgångs** strömmen till en fil med namnet`dir.log`

### <a name="example-2-send-all-success-stream-data-to-a-file"></a>Exempel 2: skicka alla lyckade Ströms data till en fil

I det här exemplet skickas alla **lyckade** data ström data till en fil med namnet `script.log` .

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a>Exempel 3: skicka lyckade, varnings-och fel strömmar till en fil

Det här exemplet visar hur du kan kombinera omdirigerings operatörer för att uppnå önskat resultat.

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > C:\Temp\redirection.log
```

- `3>&1` omdirigerar **varnings** strömmen till den **framgångs rik** data strömmen.
- `2>&1` omdirigerar **fel** strömmen till den **framgångs rik** strömmen (som även innehåller alla **varnings** data från data)
- `>` omdirigerar den **framgångs rik** data strömmen (som nu innehåller både **varnings** -och **fel** strömmar) till en fil `C:\temp\redirection.log` med namnet.

### <a name="example-4-redirect-all-streams-to-a-file"></a>Exempel 4: omdirigera alla strömmar till en fil

Det här exemplet skickar alla strömmar utdata från ett skript `script.ps1` som kallas för en fil med namnet `script.log`

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a>Exempel 5: utelämna alla Write-Host och informations data strömmar

I det här exemplet ignoreras alla informations data strömmar. Om du vill läsa mer om **information** Stream-cmdletar, se [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) och [Write-information](xref:Microsoft.PowerShell.Utility.Write-Information)

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a>Exempel 6: Visa effekterna av åtgärds inställningar

Variabler och parametrar för åtgärds inställningar kan ändra vad som skrivs till en viss data ström. Skriptet i det här exemplet visar hur värdet för `$ErrorActionPreference` påverkar vad som skrivs till **fel** strömmen.

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

När vi kör det här skriptet uppmanas vi att få frågan när det `$ErrorActionPreference` är inställt på `Inquire` .

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

När vi undersöker logg filen ser vi följande:

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a>Kommentarer

De omdirigerings operatörer som inte lägger till data ( `>` och `n>` ) skriver över det aktuella innehållet i den angivna filen utan varning.

Om filen däremot är skrivskyddad, dold eller en system fil, **Miss lyckas** omdirigeringen. Operatorerna Lägg till omdirigering ( `>>` och `n>>` ) skriver inte till en skrivskyddad fil, utan lägger till innehåll i en system fil eller en dold fil.

Använd `Out-File` cmdleten med parametern för att tvinga fram en omdirigering av innehåll till en skrivskyddad, dold eller system fil `Force` .

När du skriver till filer använder omdirigerings operatörerna `UTF8NoBOM` encoding. Om filen har en annan kodning kanske utdata inte är korrekt formaterade. Om du vill skriva till filer med en annan kodning använder du `Out-File` cmdleten med dess `Encoding` parameter.

### <a name="potential-confusion-with-comparison-operators"></a>Potentiell förvirring med jämförelse operatörer

`>`Operatorn är inte att förväxlas med [större än-](about_Comparison_Operators.md#-gt--ge--lt-and--le) jämförelse operatorn (ofta betecknad som `>` i andra programmeringsspråk).

Beroende på vilka objekt som jämförs kan utdata som används `>` vara korrekta (eftersom 36 inte är större än 42).

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

En kontroll av det lokala fil systemet kan dock se att en fil som heter `42` har skrivits, med innehållet `36` .

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

Försök att använda omvänd jämförelse `<` (mindre än) ger ett systemfel:

```powershell
PS> if (36 < 42) { "true" } else { "false" }
ParserError:
Line |
   1 |  if (36 < 42) { "true" } else { "false" }
     |         ~
     | The '<' operator is reserved for future use.
```

Om en numerisk jämförelse är den nödvändiga åtgärden `-lt` och `-gt` ska användas. Mer information finns i `-gt` operatorn i [about_Comparison_Operators](about_Comparison_Operators.md#-gt--ge--lt-and--le).

## <a name="see-also"></a>Se även

- [Ut-fil](xref:Microsoft.PowerShell.Utility.Out-File)
- [Tee – objekt](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [Skriv-debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Skriv-fel](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Skriv värd](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Skriv information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Skriva-utdata](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Skriv förlopp](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Skriv-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Skriv varning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_Output_Streams](about_Output_Streams.md)
- [about_Operators](about_Operators.md)
- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Path_Syntax](about_Path_Syntax.md)
