---
description: Beskriver hur du definierar och använder parameter uppsättningar i avancerade funktioner.
title: about_Parameter_Sets
ms.date: 01/05/2021
ms.openlocfilehash: 876f6336dd344412b514ea22d413a97a98c9cd02
ms.sourcegitcommit: eb7ad1850550032880f5529b4e4281514cba1673
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917821"
---
# <a name="about-parameter-sets"></a>Om parameter uppsättningar

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver hur du definierar och använder parameter uppsättningar i avancerade funktioner.

## <a name="long-description"></a>LÅNG BESKRIVNING

PowerShell använder parameter uppsättningar för att ge dig möjlighet att skriva en enda funktion som kan utföra olika åtgärder för olika scenarier. Parameter uppsättningar gör att du kan exponera olika parametrar för användaren. Och för att returnera annan information baserat på de parametrar som anges av användaren.

## <a name="parameter-set-requirements"></a>Krav för parameter uppsättning

Följande krav gäller för alla parameter uppsättningar.

- Varje parameter uppsättning måste ha en unik kombination av parametrar. Om möjligt måste minst en av de unika parametrarna vara en obligatorisk parameter.

- En parameter uppsättning som innehåller flera positions parametrar måste definiera unika positioner för varje parameter. Det går inte att ange samma position med två positions parametrar.

- Endast en parameter i en mängd kan deklarera `ValueFromPipeline` nyckelordet med värdet `true` . Flera parametrar kan definiera `ValueFromPipelineByPropertyName` nyckelordet med värdet `true` .

- Om ingen parameter uppsättning anges för en parameter, tillhör parametern alla parameter uppsättningar.

> [!NOTE]
> Det finns en gräns på 32 parameter uppsättningar.

## <a name="default-parameter-sets"></a>Standard parameter uppsättningar

När flera parameter uppsättningar definieras `DefaultParameterSetName` anger nyckelordet för attributet **CmdletBinding** standard parameter uppsättningen.
PowerShell använder standard parametern som anges när den inte kan avgöra vilken parameter som ska användas baserat på den information som ges till kommandot. Mer information om attributet **CmdletBinding** finns i [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).

## <a name="declaring-parameter-sets"></a>Deklarera parameter uppsättningar

Om du vill skapa en parameter uppsättning måste du ange `ParameterSetName` nyckelordet för attributet **parameter** för varje parameter i parameter uppsättningen. För parametrar som tillhör flera parameter uppsättningar lägger du till ett **parameter** -attribut för varje parameter uppsättning.

Med attributet **parameter** kan du definiera parametern på olika sätt för varje parameter uppsättning. Du kan till exempel definiera en parameter som obligatorisk i en uppsättning och valfri i en annan. Varje parameter uppsättning måste dock innehålla minst en unik parameter.

Parametrar som inte har en tilldelad parameter uppsättnings namn tillhör alla parameter uppsättningar.

### <a name="example"></a>Exempel

Följande exempel funktion räknar antalet rader, tecken och ord i en textfil. Med parametrar kan du ange vilka värden som du vill ska returneras och vilka filer du vill mäta. Det finns fyra parameter uppsättningar definierade:

- Sökväg
- PathAll
- LiteralPath
- LiteralPathAll

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

Varje parameter uppsättning måste ha en unik parameter eller en unik kombination av parametrar. Parameter uppsättningarna `Path` och är `PathAll` mycket likartade men parametern **all** är unik för `PathAll` parameter uppsättningen. Samma sak gäller för `LiteralPath` `LiteralPathAll` parameter uppsättningarna och. Även om `PathAll` parametern och `LiteralPathAll` anger båda har parametern **all** , särskiljer **sökvägen** och **LiteralPath** -parametrarna.

Använd `Get-Command -Syntax` visar syntaxen för varje parameter uppsättning. Men det visar inte namnet på parameter uppsättningen. I följande exempel visas vilka parametrar som kan användas i varje parameter uppsättning.

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a>Parameter uppsättningar i åtgärd

I det här exemplet använder vi `PathAll` parameter uppsättningen.

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```

