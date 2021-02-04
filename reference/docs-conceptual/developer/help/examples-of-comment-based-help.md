---
ms.date: 01/11/2021
ms.topic: reference
title: Exempel på kommentarsbaserad hjälp
description: Exempel på kommentarsbaserad hjälp
ms.openlocfilehash: 237e65c59cc3b35f48b6d667c8fb297994b03638
ms.sourcegitcommit: 4879b9cdfa3f03b04a07b84442dc1ca9ae0f6b46
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/11/2021
ms.locfileid: "98105170"
---
# <a name="examples-of-comment-based-help"></a>Exempel på kommentarsbaserad hjälp

Det här avsnittet innehåller exempel som visar hur du använder en kommenterings-baserad hjälp för skript och funktioner.

## <a name="example-1-comment-based-help-for-a-function"></a>Exempel 1: Comment-Based hjälp för en funktion

 Följande exempel funktion innehåller kommenterings-baserad hjälp.

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        PS> extension -name "File"
        File.txt

        .EXAMPLE
        PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

Följande utdata visar resultatet av ett `Get-Help` kommando som visar hjälpen för `Add-Extension` funktionen.

```powershell
PS> Get-Help Add-Extension -full
```

```Output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a>Exempel 2: Comment-Based hjälp för ett skript

Följande exempel funktion innehåller kommenterings-baserad hjälp.

Lägg märke till de tomma raderna mellan stängningen **#>** och `Param` instruktionen. I ett skript som saknar `Param` instruktion måste det finnas minst två tomma rader mellan den sista kommentaren i hjälp avsnittet och den första funktions deklarationen. Utan dessa tomma rader `Get-Help` associeras hjälp avsnittet med funktionen i stället för skriptet.

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  PS> .\Update-Month.ps1

  .EXAMPLE
  PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

Följande kommando hämtar skript hjälpen. Eftersom skriptet inte finns i en katalog som anges i miljövariabeln PATH, `Get-Help` måste kommandot som hämtar skript-hjälpen ange skript Sök vägen.

```powershell
PS> Get-Help c:\ps-test\update-month.ps1 -full
```

```Output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a>Exempel 3: parameter beskrivningar i en param-instruktion

I det här exemplet visas hur du infogar parameter beskrivningar i `Param` instruktionen för en funktion eller ett skript. Det här formatet är mest användbart när parameter beskrivningar är korta.

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

Resultatet är detsamma som resultatet till exempel 1. `Get-Help` tolkar parameter beskrivningar som om de åtföljs av `.Parameter` nyckelordet.

## <a name="example-4--redirecting-to-an-xml-file"></a>Exempel 4: omdirigera till en XML-fil

Du kan skriva XML-baserade hjälp avsnitt för funktioner och skript. Även om det är enklare att implementera en kommenterad hjälp, krävs det en XML-baserad hjälp om du vill ha mer exakt kontroll över hjälp innehållet eller om du översätter hjälp ämnen till flera språk. I följande exempel visas de första raderna i `Update-Month.ps1` skriptet. Skriptet använder `.ExternalHelp` nyckelordet för att ange sökvägen till ett XML-baserat hjälp avsnitt för skriptet.

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

I följande exempel visas användningen av `.ExternalHelp` nyckelordet i en funktion.

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a>Exempel 5: omdirigera till ett annat hjälp avsnitt

Följande kod är ett utdrag från början av den inbyggda `Help` funktionen i PowerShell, som visar en skärm med hjälp text i taget. Eftersom hjälp avsnittet för Get-Help cmdlet: en beskriver hjälp funktionen, använder funktionen och för att `.ForwardHelpTargetName` `.ForwardHelpCategory` omdirigera användaren till hjälp avsnittet om Get-Help cmdlet.

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

Följande kommando använder den här funktionen. När en användare skriver ett `Get-Help` kommando för `Help` funktionen, `Get-Help` visar hjälp avsnittet för `Get-Help` cmdleten.

```powershell
PS> get-help help
```

```Output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```
