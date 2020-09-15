---
title: Exempel på kommentarsbaserad hjälp
ms.date: 09/12/2016
ms.openlocfilehash: fe5d054c84952367a4e7c2d5d9e32551a4e5c3a8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772305"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="bd9e1-102">Exempel på kommentarsbaserad hjälp</span><span class="sxs-lookup"><span data-stu-id="bd9e1-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="bd9e1-103">Det här avsnittet innehåller exempel som visar hur du använder en kommenterings-baserad hjälp för skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="bd9e1-104">Exempel 1: kommenterings-baserad hjälp för en funktion</span><span class="sxs-lookup"><span data-stu-id="bd9e1-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="bd9e1-105">Följande exempel funktion innehåller kommenterings-baserad hjälp.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-105">The following sample function includes comment-based Help.</span></span>

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
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="bd9e1-106">Följande utdata visar resultatet av ett `Get-Help` kommando som visar hjälpen för `Add-Extension` funktionen.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-106">The following output shows the results of a `Get-Help` command that displays the help for the `Add-Extension` function.</span></span>

```powershell
C:\PS> get-help add-extension -full
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

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="bd9e1-107">Exempel 2: kommenterings-baserad hjälp för ett skript</span><span class="sxs-lookup"><span data-stu-id="bd9e1-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="bd9e1-108">Följande exempel funktion innehåller kommenterings-baserad hjälp.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="bd9e1-109">Lägg märke till de tomma raderna mellan stängningen **#>** och `Param` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="bd9e1-110">I ett skript som saknar `Param` instruktion måste det finnas minst två tomma rader mellan den sista kommentaren i hjälp avsnittet och den första funktions deklarationen.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="bd9e1-111">Utan dessa tomma rader `Get-Help` associeras hjälp avsnittet med funktionen i stället för skriptet.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-111">Without these blank lines, `Get-Help` associates the Help topic with the function, instead of the script.</span></span>

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
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="bd9e1-112">Följande kommando hämtar skript hjälpen.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-112">The following command gets the script Help.</span></span> <span data-ttu-id="bd9e1-113">Eftersom skriptet inte finns i en katalog som anges i miljövariabeln PATH, `Get-Help` måste kommandot som hämtar skript-hjälpen ange skript Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-113">Because the script is not in a directory that is listed in the Path environment variable, the `Get-Help` command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
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

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="bd9e1-114">Exempel 3: parameter beskrivningar i en param-instruktion</span><span class="sxs-lookup"><span data-stu-id="bd9e1-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="bd9e1-115">I det här exemplet visas hur du infogar parameter beskrivningar i `Param` instruktionen för en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-115">This example shows how to insert parameter descriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="bd9e1-116">Det här formatet är mest användbart när parameter beskrivningar är korta.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-116">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="bd9e1-117">Resultatet är detsamma som resultatet till exempel 1.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="bd9e1-118">`Get-Help` tolkar parameter beskrivningar som om de åtföljs av `.Parameter` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-118">`Get-Help` interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="bd9e1-119">Exempel 4: omdirigera till en XML-fil</span><span class="sxs-lookup"><span data-stu-id="bd9e1-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="bd9e1-120">Du kan skriva XML-baserade hjälp avsnitt för funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="bd9e1-121">Även om det är enklare att implementera en kommenterad hjälp, krävs det en XML-baserad hjälp om du vill ha mer exakt kontroll över hjälp innehållet eller om du översätter hjälp ämnen till flera språk. I följande exempel visas de första raderna i `Update-Month.ps1` skriptet.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the `Update-Month.ps1` script.</span></span> <span data-ttu-id="bd9e1-122">Skriptet använder `.ExternalHelp` nyckelordet för att ange sökvägen till ett XML-baserat hjälp avsnitt för skriptet.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="bd9e1-123">I följande exempel visas användningen av `.ExternalHelp` nyckelordet i en funktion.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="bd9e1-124">Exempel 5: omdirigera till ett annat hjälp avsnitt</span><span class="sxs-lookup"><span data-stu-id="bd9e1-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="bd9e1-125">Följande kod är ett utdrag från början av den inbyggda `Help` funktionen i PowerShell, som visar en skärm med hjälp text i taget.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-125">The following code is an excerpt from the beginning of the built-in `Help` function in PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="bd9e1-126">Eftersom hjälp avsnittet för cmdleten Get-Help beskriver Help-funktionen, använder Help-funktionen `.ForwardHelpTargetName` `.ForwardHelpCategory` nyckelorden och för att omdirigera användaren till hjälp avsnittet om cmdleten Get-Help.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="bd9e1-127">Följande kommando använder den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-127">The following command uses this feature.</span></span> <span data-ttu-id="bd9e1-128">När en användare skriver ett `Get-Help` kommando för `Help` funktionen, `Get-Help` visar hjälp avsnittet för `Get-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bd9e1-128">When a user types a `Get-Help` command for the `Help` function, `Get-Help` displays the Help topic for the `Get-Help` cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```Output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```
