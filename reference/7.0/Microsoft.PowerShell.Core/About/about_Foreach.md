---
description: Beskriver ett språk kommando som du kan använda för att bläddra igenom alla objekt i en objekt samling.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: 42cea9f61330e16adcad0ad543acca21e35d5ca8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272390"
---
# <a name="about-foreach"></a>Om

## <a name="short-description"></a>Kort beskrivning
Beskriver ett språk kommando som du kan använda för att bläddra igenom alla objekt i en objekt samling.

## <a name="long-description"></a>Lång beskrivning

`Foreach`Instruktionen (kallas även en `Foreach` loop) är en språk konstruktion för stega igenom (iterera) en serie med värden i en samling objekt.

Den enklaste och mest typiska typen av samling att passera är en matris.
I en `Foreach` slinga är det vanligt att köra ett eller flera kommandon mot varje objekt i en matris.

## <a name="syntax"></a>Syntax

Följande visar `ForEach` syntaxen:

```
foreach ($<item> in $<collection>){<statement list>}
```

Den del av `ForEach` instruktionen som omges av parentes representerar en variabel och en samling att iterera. PowerShell skapar variabeln `$<item>` automatiskt när `Foreach` loopen körs. Före varje iteration genom loopen anges variabeln till ett värde i samlingen.
Blocket som följer efter en `Foreach` instruktion `{<statement list>}` innehåller en uppsättning kommandon som ska köras mot varje objekt i en samling.

### <a name="examples"></a>Exempel

`Foreach`Slingan i följande exempel visar till exempel värdena i `$letterArray` matrisen.

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

I det här exemplet `$letterArray` skapas och initieras matrisen med sträng värden `"a"` , `"b"` , `"c"` och `"d"` . Första gången som `Foreach` instruktionen körs anger den `$letter` variabeln som är lika med det första objektet i `$letterArray` ( `"a"` ). Sedan använder den `Write-Host` cmdleten för att visa bokstaven a. Nästa gången genom loopen `$letter` ställs in på `"b"` och så vidare. När `Foreach` loopen visar bokstaven d avslutar PowerShell slingan.

Hela `Foreach` instruktionen måste finnas på en rad för att köra den som ett kommando i PowerShell-Kommandotolken. Hela `Foreach` instruktionen behöver inte visas på en enda rad om du placerar kommandot i en. ps1-skriptfil i stället.

`Foreach` -instruktioner kan också användas tillsammans med cmdletar som returnerar en samling objekt. I följande exempel beskrivs de stegvisa anvisningarna i listan över objekt som returneras av `Get-ChildItem` cmdleten.

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

Du kan förfina exemplet genom att använda en `If` instruktion för att begränsa resultaten som returneras. I följande exempel `Foreach` Utför instruktionen samma upprepnings åtgärd som i föregående exempel, men lägger till en `If` instruktion som begränsar resultatet till filer som är större än 100 KB:

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

I det här exemplet `Foreach` använder slingan en egenskap i `$file` variabeln för att utföra en jämförelse åtgärd ( `$file.length -gt 100KB` ). `$file`Variabeln innehåller alla egenskaper i objektet som returneras av `Get-ChildItem` cmdleten. Därför kan du returnera mer än bara ett fil namn.
I nästa exempel returnerar PowerShell längden och den senaste åtkomst tiden i instruktions listan:

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
    Write-Host $file.length
    Write-Host $file.lastaccesstime
  }
}
```

I det här exemplet är du inte begränsad till att köra ett enda kommando i en instruktions lista.

Du kan också använda en variabel utanför en `Foreach` slinga och öka variabeln i slingan. I följande exempel räknas filer över 100 KB i storlek:

```powershell
$i = 0
foreach ($file in Get-ChildItem) {
  if ($file.length -gt 100KB) {
    Write-Host $file "file size:" ($file.length / 1024).ToString("F0") KB
    $i = $i + 1
  }
}

if ($i -ne 0) {
  Write-Host
  Write-Host $i " file(s) over 100 KB in the current directory."
}
else {
  Write-Host "No files greater than 100 KB in the current directory."
}
```

I föregående exempel `$i` är variabeln inställd på `0` utanför loopen och variabeln ökar i slingan för varje fil som finns större än 100 kB. När slingan avslutas `If` utvärderar en instruktion värdet för `$i` att visa antalet filer över 100 kB. Eller så visas ett meddelande om att det inte gick att hitta några filer över 100 KB.

I föregående exempel visas också hur du formaterar filens längd resultat:

```powershell
($file.length / 1024).ToString("F0")
```

Värdet divideras med 1 024 för att visa resultaten i kilobyte i stället för byte, och det resulterande värdet formateras sedan med hjälp av den fasta punktens format för att ta bort alla decimal värden från resultatet. 0 gör format specifikationen Visa inga decimal platser.

I följande exempel tolkar funktionen PowerShell-skript och-skript moduler och returnerar platsen för de funktioner som finns i. Exemplet visar hur du använder `MoveNext` -metoden (som fungerar ungefär som `skip X` i en `For` slinga) och `Current` egenskapen för `$foreach` variabeln i ett förgrunds skript block. Exempel funktionen kan hitta funktioner i ett skript även om det finns ovanligt, eller inkonsekvent funktions definitioner som sträcker sig över flera rader.

Mer information finns i [använda uppräknare](about_Automatic_Variables.md#using-enumerators).

```powershell
function Get-FunctionPosition {
  [CmdletBinding()]
  [OutputType('FunctionPosition')]
  param(
    [Parameter(Position = 0, Mandatory,
      ValueFromPipeline, ValueFromPipelineByPropertyName)]
    [ValidateNotNullOrEmpty()]
    [Alias('PSPath')]
    [System.String[]]
    $Path
  )

  process {
    try {
      $filesToProcess = if ($_ -is [System.IO.FileSystemInfo]) {
        $_
      } else {
        $filesToProcess = Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      foreach ($item in $filesToProcess) {
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $ast = $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors))
        if ($errors) {
          $msg = "File '{0}' has {1} parser errors." -f $item.FullName,
            $errors.Count
          Write-Warning $msg
        }
        :tokenLoop foreach ($token in $tokens) {
          if ($token.Kind -ne 'Function') {
            continue
          }
          $position = $token.Extent.StartLineNumber
          do {
            if (-not $foreach.MoveNext()) {
              break tokenLoop
            }
            $token = $foreach.Current
          } until ($token.Kind -in @('Generic', 'Identifier'))
          $functionPosition = [pscustomobject]@{
            Name       = $token.Text
            LineNumber = $position
            Path       = $item.FullName
          }
          Add-Member -InputObject $functionPosition `
            -TypeName FunctionPosition -PassThru
        }
      }
    }
    catch {
      throw
    }
  }
}
```

## <a name="see-also"></a>SE ÄVEN

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_If](about_If.md)

[-Objekt](xref:Microsoft.PowerShell.Core.ForEach-Object)
