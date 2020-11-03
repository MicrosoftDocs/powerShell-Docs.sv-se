---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263877"
---
# Import-IseSnippet

## SAMMANFATTNING
Importerar ISE-kodfragment till den aktuella sessionen

## SYNTAX

### FromFolder (standard)

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### FromModule

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## BESKRIVNING

`Import-IseSnippet`Cmdleten importerar åter användning av text "fragment" från en modul eller en katalog till den aktuella sessionen. Kodfragmenten är omedelbart tillgängliga för användning i Windows PowerShell ISE. Denna cmdlet fungerar bara i Windows PowerShell ISE (Integrated Scripting Environment).

Om du vill visa och använda de importerade kodfragmenten klickar du på **Starta kodfragment** på Windows PowerShell ISE **Redigera** -menyn eller trycker på <kbd>CTRL</kbd> + <kbd>J</kbd>.

Importerade kodfragment är bara tillgängliga i den aktuella sessionen. Om du vill importera kodfragmenten till alla Windows PowerShell ISE-sessioner, lägger du till ett `Import-IseSnippet` kommando i din Windows PowerShell-profil eller kopierar kodfragmentet till din lokala kodfragments katalog `$home\Documents\WindowsPowershell\Snippets` .

För att importera kodfragment måste de vara korrekt formaterade i XML-kodfragmentet för Windows PowerShell ISE kodfragment och sparas i Snippet.ps1XML-filer. Använd cmdleten för att skapa kvalificerade kodfragment `New-IseSnippet` . `New-IseSnippet` skapar en `<SnippetTitle>.Snippets.ps1xml` fil i `$home\Documents\WindowsPowerShell\Snippets` katalogen. Du kan flytta eller kopiera kodfragmenten till katalogen kodfragment i en Windows PowerShell-modul, eller till en annan katalog.

`Get-IseSnippet`Cmdleten, som hämtar användarbaserade kodfragment i den lokala kodfragment katalogen, hämtar inte importerade kodfragment.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: importera kodfragment från en katalog

I det här exemplet importeras kodfragmenten från `\\Server01\Public\Snippets` katalogen till den aktuella sessionen. Den använder parametern **rekursivt** för att hämta kodfragment från alla under kataloger i avsnittet kod avsnitt.

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### Exempel 2: importera kodfragment från en modul

I det här exemplet importeras kodfragmenten från **SnippetModule** -modulen. Kommandot använder parametern **ListAvailable** för att importera kodfragmenten även om **SnippetModule** -modulen inte importeras till användarens session när kommandot körs.

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### Exempel 3: hitta kodfragment i moduler

Det här exemplet hämtar kodfragment i alla installerade moduler i PSModulePath-miljövariabeln.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### Exempel 4: importera alla modul-kodfragment

I det här exemplet importeras alla kodfragment från alla installerade moduler till den aktuella sessionen. Normalt behöver du inte köra ett kommando som detta eftersom moduler som har kodfragment använder `Import-IseSnippet` cmdleten för att importera dem åt dig när modulen importeras.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### Exempel 5: kopiera alla kodfragment

I det här exemplet kopieras kodfragment-filerna från alla installerade moduler till avsnittet kodfragment för den aktuella användaren. Till skillnad från importerade kodfragment, som endast påverkar den aktuella sessionen, är de kopierade kodfragmenten tillgängliga i alla Windows PowerShell ISE-sessioner.

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## PARAMETRAR

### – ListAvailable

Anger att denna cmdlet hämtar kodfragment från moduler som är installerade på datorn, även om modulerna inte importeras till den aktuella sessionen. Om den här parametern utelämnas och modulen som anges av parametern **modul** inte importeras till den aktuella sessionen, Miss lyckas försöket att hämta kodfragmenten från modulen.

Den här parametern är endast giltig när parametern **module** används i kommandot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Modul

Importerar kodfragment från den angivna modulen till den aktuella sessionen. Jokertecken stöds inte.

Den här parametern importerar kodfragment från Snippet.ps1XML-filer i under katalogen kodfragment i-modulens sökväg, till exempel `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` .

Den här parametern är utformad för att användas av modulens författare i ett start skript, till exempel ett skript som anges i nyckeln **ScriptsToProcess** för ett modul manifest. Kodfragment i en modul importeras inte automatiskt med modulen, men du kan använda ett `Import-IseSnippet` kommando för att importera dem.

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen till den katalog kod avsnitt där denna cmdlet importerar kodfragment.

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – Rekursivt

Anger att denna cmdlet importerar kodfragment från alla under kataloger till värdet för parametern **Path** .

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

### Inget

Den här cmdleten tar inte emot några ininformation från pipelinen.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

- Du kan inte använda `Get-IseSnippet` cmdleten för att hämta importerade kodfragment. `Get-IseSnippet` hämtar endast kodfragment i `$home\Documents\WindowsPowerShell\Snippets` katalogen.
- `Import-IseSnippet` använder den statiska metoden **load** static för **Microsoft. PowerShell. Host. ISE. ISESnippetCollection** -objekt. Du kan också använda **load** -metoden för kodfragment i Windows PowerShell ISE objekt modellen: `$psISE.CurrentPowerShellTab.Snippets.Load()`
- `New-IseSnippet`Cmdlet: en lagrar nya användare-skapade kodfragment i osignerade. ps1xml-filer. Det innebär att Windows PowerShell inte kan läsa in dem i en session där körnings principen är **AllSigned** eller **begränsad**. I en **begränsad** eller **AllSigned** session kan du skapa, hämta och importera osignerade kodfragment, men du kan inte använda dem i sessionen.

  Om du vill använda osignerade användar kods tycken som `Import-IseSnippet` cmdleten returnerar ändrar du körnings principen och startar sedan om Windows PowerShell ISE.

  Mer information om körnings principer för Windows PowerShell finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).

## RELATERADE LÄNKAR

[Get-IseSnippet](Get-IseSnippet.md)

[New-IseSnippet](New-IseSnippet.md)
