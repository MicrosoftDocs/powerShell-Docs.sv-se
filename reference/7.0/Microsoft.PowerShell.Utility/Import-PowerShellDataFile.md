---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: f25191d27013469023b9fcfb03650a8693c6ddb4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93261932"
---
# <span data-ttu-id="55aa5-103">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="55aa5-103">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="55aa5-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="55aa5-104">SYNOPSIS</span></span>
<span data-ttu-id="55aa5-105">Importerar värden från en `.PSD1` fil utan att anropa dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="55aa5-105">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="55aa5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="55aa5-106">SYNTAX</span></span>

### <span data-ttu-id="55aa5-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="55aa5-107">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="55aa5-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="55aa5-108">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="55aa5-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="55aa5-109">DESCRIPTION</span></span>

<span data-ttu-id="55aa5-110">Cmdlet: en på `Import-PowerShellDataFile` ett säkert sätt importerar nyckel/värde-par från hash som definierats i en `.PSD1` fil.</span><span class="sxs-lookup"><span data-stu-id="55aa5-110">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="55aa5-111">Värdena kan importeras med hjälp av `Invoke-Expression` filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="55aa5-111">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="55aa5-112">Kör dock `Invoke-Expression` eventuell kod som finns i filen.</span><span class="sxs-lookup"><span data-stu-id="55aa5-112">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="55aa5-113">Detta kan producera oönskade resultat eller köra osäker kod.</span><span class="sxs-lookup"><span data-stu-id="55aa5-113">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="55aa5-114">`Import-PowerShellDataFile` importerar data utan att anropa koden.</span><span class="sxs-lookup"><span data-stu-id="55aa5-114">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span>

## <span data-ttu-id="55aa5-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="55aa5-115">EXAMPLES</span></span>

### <span data-ttu-id="55aa5-116">Exempel 1: Hämta värden från PSD1</span><span class="sxs-lookup"><span data-stu-id="55aa5-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="55aa5-117">I det här exemplet hämtas de nyckel/värde-par som lagras i den hash-tabellen som behålls i `Configuration.psd1` filen.</span><span class="sxs-lookup"><span data-stu-id="55aa5-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="55aa5-118">`Get-Content` används för att visa innehållet i `Configuration.psd1` filen.</span><span class="sxs-lookup"><span data-stu-id="55aa5-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## <span data-ttu-id="55aa5-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="55aa5-119">PARAMETERS</span></span>

### <span data-ttu-id="55aa5-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="55aa5-120">-LiteralPath</span></span>

<span data-ttu-id="55aa5-121">Sökvägen till filen som importeras.</span><span class="sxs-lookup"><span data-stu-id="55aa5-121">The path to the file being imported.</span></span> <span data-ttu-id="55aa5-122">Alla tecken i sökvägen behandlas som litterala värden.</span><span class="sxs-lookup"><span data-stu-id="55aa5-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="55aa5-123">Jokertecken bearbetas inte.</span><span class="sxs-lookup"><span data-stu-id="55aa5-123">Wildcard characters are not processed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="55aa5-124">-Path</span><span class="sxs-lookup"><span data-stu-id="55aa5-124">-Path</span></span>

<span data-ttu-id="55aa5-125">Sökvägen till filen som importeras.</span><span class="sxs-lookup"><span data-stu-id="55aa5-125">The path to the file being imported.</span></span> <span data-ttu-id="55aa5-126">Jokertecken är tillåtna, men endast den första matchande filen importeras.</span><span class="sxs-lookup"><span data-stu-id="55aa5-126">Wildcards are allowed but only the first matching file is imported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="55aa5-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="55aa5-127">CommonParameters</span></span>

<span data-ttu-id="55aa5-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="55aa5-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="55aa5-129">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="55aa5-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="55aa5-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="55aa5-130">INPUTS</span></span>

## <span data-ttu-id="55aa5-131">UTDATA</span><span class="sxs-lookup"><span data-stu-id="55aa5-131">OUTPUTS</span></span>

### <span data-ttu-id="55aa5-132">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="55aa5-132">System.Collections.Hashtable</span></span>

## <span data-ttu-id="55aa5-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="55aa5-133">NOTES</span></span>

## <span data-ttu-id="55aa5-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="55aa5-134">RELATED LINKS</span></span>

[<span data-ttu-id="55aa5-135">Invoke-uttryck</span><span class="sxs-lookup"><span data-stu-id="55aa5-135">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="55aa5-136">Importera – LocalizedData</span><span class="sxs-lookup"><span data-stu-id="55aa5-136">Import-LocalizedData</span></span>](Import-LocalizedData.md)
