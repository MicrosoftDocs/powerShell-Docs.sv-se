---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: 61e3a7f941155ccf3db84a7e9ec8d2c48b4cceea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264968"
---
# <span data-ttu-id="c76b0-103">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="c76b0-103">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="c76b0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c76b0-104">SYNOPSIS</span></span>
<span data-ttu-id="c76b0-105">Importerar värden från en `.PSD1` fil utan att anropa dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="c76b0-105">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="c76b0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c76b0-106">SYNTAX</span></span>

### <span data-ttu-id="c76b0-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="c76b0-107">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [[-Path] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="c76b0-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="c76b0-108">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="c76b0-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c76b0-109">DESCRIPTION</span></span>

<span data-ttu-id="c76b0-110">Cmdlet: en på `Import-PowerShellDataFile` ett säkert sätt importerar nyckel/värde-par från hash som definierats i en `.PSD1` fil.</span><span class="sxs-lookup"><span data-stu-id="c76b0-110">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="c76b0-111">Värdena kan importeras med hjälp av `Invoke-Expression` filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="c76b0-111">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="c76b0-112">Kör dock `Invoke-Expression` eventuell kod som finns i filen.</span><span class="sxs-lookup"><span data-stu-id="c76b0-112">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="c76b0-113">Detta kan producera oönskade resultat eller köra osäker kod.</span><span class="sxs-lookup"><span data-stu-id="c76b0-113">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="c76b0-114">`Import-PowerShellDataFile` importerar data utan att anropa koden.</span><span class="sxs-lookup"><span data-stu-id="c76b0-114">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span>

## <span data-ttu-id="c76b0-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c76b0-115">EXAMPLES</span></span>

### <span data-ttu-id="c76b0-116">Exempel 1: Hämta värden från PSD1</span><span class="sxs-lookup"><span data-stu-id="c76b0-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="c76b0-117">I det här exemplet hämtas de nyckel/värde-par som lagras i den hash-tabellen som behålls i `Configuration.psd1` filen.</span><span class="sxs-lookup"><span data-stu-id="c76b0-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="c76b0-118">`Get-Content` används för att visa innehållet i `Configuration.psd1` filen.</span><span class="sxs-lookup"><span data-stu-id="c76b0-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

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

## <span data-ttu-id="c76b0-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c76b0-119">PARAMETERS</span></span>

### <span data-ttu-id="c76b0-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c76b0-120">-LiteralPath</span></span>

<span data-ttu-id="c76b0-121">Sökvägen till filen som importeras.</span><span class="sxs-lookup"><span data-stu-id="c76b0-121">The path to the file being imported.</span></span> <span data-ttu-id="c76b0-122">Alla tecken i sökvägen behandlas som litterala värden.</span><span class="sxs-lookup"><span data-stu-id="c76b0-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="c76b0-123">Jokertecken bearbetas inte.</span><span class="sxs-lookup"><span data-stu-id="c76b0-123">Wildcard characters are not processed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c76b0-124">-Path</span><span class="sxs-lookup"><span data-stu-id="c76b0-124">-Path</span></span>

<span data-ttu-id="c76b0-125">Sökvägen till filen som importeras.</span><span class="sxs-lookup"><span data-stu-id="c76b0-125">The path to the file being imported.</span></span> <span data-ttu-id="c76b0-126">Jokertecken är tillåtna, men endast den första matchande filen importeras.</span><span class="sxs-lookup"><span data-stu-id="c76b0-126">Wildcards are allowed but only the first matching file is imported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c76b0-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c76b0-127">CommonParameters</span></span>

<span data-ttu-id="c76b0-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c76b0-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c76b0-129">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="c76b0-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c76b0-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="c76b0-130">INPUTS</span></span>

## <span data-ttu-id="c76b0-131">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c76b0-131">OUTPUTS</span></span>

### <span data-ttu-id="c76b0-132">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="c76b0-132">System.Collections.Hashtable</span></span>

## <span data-ttu-id="c76b0-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c76b0-133">NOTES</span></span>

## <span data-ttu-id="c76b0-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c76b0-134">RELATED LINKS</span></span>

[<span data-ttu-id="c76b0-135">Invoke-uttryck</span><span class="sxs-lookup"><span data-stu-id="c76b0-135">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="c76b0-136">Importera – LocalizedData</span><span class="sxs-lookup"><span data-stu-id="c76b0-136">Import-LocalizedData</span></span>](Import-LocalizedData.md)
