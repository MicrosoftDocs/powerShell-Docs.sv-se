---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/get-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-IseSnippet
ms.openlocfilehash: c43dae3f178ae778d78fe3718fa85fd2635eba86
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268113"
---
# Get-IseSnippet

## SAMMANFATTNING
Hämtar kodfragment som användaren har skapat.

## SYNTAX

```
Get-IseSnippet [<CommonParameters>]
```

## BESKRIVNING

`Get-IseSnippet`Cmdlet: en hämtar de PS1XML-filer som innehåller återanvändbara text-kodfragment som användaren skapade. Det fungerar bara i Windows PowerShell ISE (Integrated Scripting Environment).

När du använder `New-IseSnippet` cmdleten för att skapa ett kodfragment `New-IseSnippet` skapar en `<SnippetTitle>.Snippets.ps1xml` fil i `$home\Documents\WindowsPowerShell\Snippets` katalogen.
`Get-IseSnippet` hämtar kodfragments-filerna i katalogen kodfragment.

Denna cmdlet tillhandahåller inte inbyggda kodfragment eller kodfragment som importeras från moduler via `Import-IseSnippet` cmdleten.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Hämta alla användardefinierade kod avsnitt

Det här exemplet hämtar alla användardefinierade kod avsnitt i katalogen kodfragment.

```powershell
Get-IseSnippet
```

### Exempel 2: kopiera alla användardefinierade kod avsnitt från fjärrdatorer till en delad katalog

I det här exemplet kopieras alla användare-skapade kodfragment från en grupp fjärrdatorer till en katalog med delade avsnitt.

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

`Invoke-Command` körs `Get-IseSnippet` på datorerna i `Servers.txt` filen. En pipeline-operator ( `|` ) skickar kodfragmentet till `Copy-Item` cmdleten, som kopierar dem till den katalog som anges av **mål** parametern.

### Exempel 3: Visa rubrik och text för varje kod avsnitt på en lokal dator

I det här exemplet `Get-IseSnippet` används `Select-Xml` cmdletarna och för att Visa rubrik och text för varje kodfragment på den lokala datorn.

```powershell
#Parse-Snippet Function
function Parse-Snippet {
  $SnippetFiles = Get-IseSnippet
  $SnippetNamespace = @{x="http://schemas.microsoft.com/PowerShell/Snippets"}
  foreach ($SnippetFile in $SnippetFiles) {
     Write-Host ""
     $Title = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Title" |
       ForEach-Object {$_.Node.InnerXML}
     $Text = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Script" |
       ForEach-Object {$_.Node.InnerText}
     Write-Host "Title: $Title"
     Write-Host "Text: $Text"
   }
}
```

```Output
Title: Mandatory
Text:
Param
(
  [parameter(Mandatory=True)]
  [String[]]
  $<ParameterName>
)

Title: Copyright
Text:  (c) Fabrikam, Inc. 2012
```

### Exempel 4: Visa rubriken och beskrivningen för alla kodfragment i sessionen

I det här exemplet visas rubriken och beskrivningen av alla kodfragment i sessionen, inklusive inbyggda kodfragment, användardefinierade kodfragment och importerade kod avsnitt.

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

`$PSISE`Variabeln representerar Windows PowerShell ISE värd programmet. Egenskapen **CurrentPowerShellTab** för `$PSISE` variabeln representerar den aktuella sessionen. Egenskapen **kodfragment** representerar kodfragment i den aktuella sessionen.

`$PSISE.CurrentPowerShellTab.Snippets`Kommandot returnerar ett **Microsoft. PowerShell. Host. ISE. ISESnippet** -objekt som representerar ett kodfragment, till skillnad från `Get-IseSnippet` cmdleten. `Get-IseSnippet` Returnerar ett fil objekt (system. io. FileInfo) som representerar en kodfragments fil.

`Format-Table`Cmdleten visar egenskaperna **DisplayTitle** och **Description** för kodfragmenten i en tabell.

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

### System. IO. FileInfo

Denna cmdlet returnerar ett fil objekt som representerar kodfragments filen.

## ANTECKNINGAR

* `New-IseSnippet`Cmdlet: en lagrar nya användare-skapade kodfragment i osignerade. ps1xml-filer. Det innebär att Windows PowerShell inte kan lägga till dem i en session där körnings principen är **AllSigned** eller **begränsad**. I en **begränsad** eller **AllSigned** session kan du skapa, hämta och importera osignerade kodfragment, men du kan inte använda dem i sessionen.

  Om du vill använda osignerade användar kods tycken som `Get-IseSnippet` cmdleten returnerar ändrar du körnings principen och startar sedan om Windows PowerShell ISE.

  Mer information om körnings principer för Windows PowerShell finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).

## RELATERADE LÄNKAR

[New-IseSnippet](New-IseSnippet.md)

[Importera – IseSnippet](Import-IseSnippet.md)
