---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: 2853c5757b12e75e50948192e5a9e29889553b8e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708614"
---
# <span data-ttu-id="61a5c-102">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="61a5c-102">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="61a5c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="61a5c-103">SYNOPSIS</span></span>
<span data-ttu-id="61a5c-104">Importerar värden från en `.PSD1` fil utan att anropa dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="61a5c-104">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="61a5c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="61a5c-105">SYNTAX</span></span>

### <span data-ttu-id="61a5c-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="61a5c-106">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="61a5c-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="61a5c-107">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="61a5c-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="61a5c-108">DESCRIPTION</span></span>

<span data-ttu-id="61a5c-109">Cmdlet: en på `Import-PowerShellDataFile` ett säkert sätt importerar nyckel/värde-par från hash som definierats i en `.PSD1` fil.</span><span class="sxs-lookup"><span data-stu-id="61a5c-109">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="61a5c-110">Värdena kan importeras med hjälp av `Invoke-Expression` filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="61a5c-110">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="61a5c-111">Kör dock `Invoke-Expression` eventuell kod som finns i filen.</span><span class="sxs-lookup"><span data-stu-id="61a5c-111">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="61a5c-112">Detta kan producera oönskade resultat eller köra osäker kod.</span><span class="sxs-lookup"><span data-stu-id="61a5c-112">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="61a5c-113">`Import-PowerShellDataFile` importerar data utan att anropa koden.</span><span class="sxs-lookup"><span data-stu-id="61a5c-113">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span>

## <span data-ttu-id="61a5c-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="61a5c-114">EXAMPLES</span></span>

### <span data-ttu-id="61a5c-115">Exempel 1: Hämta värden från PSD1</span><span class="sxs-lookup"><span data-stu-id="61a5c-115">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="61a5c-116">I det här exemplet hämtas de nyckel/värde-par som lagras i den hash-tabellen som behålls i `Configuration.psd1` filen.</span><span class="sxs-lookup"><span data-stu-id="61a5c-116">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="61a5c-117">`Get-Content` används för att visa innehållet i `Configuration.psd1` filen.</span><span class="sxs-lookup"><span data-stu-id="61a5c-117">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

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

## <span data-ttu-id="61a5c-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="61a5c-118">PARAMETERS</span></span>

### <span data-ttu-id="61a5c-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="61a5c-119">-LiteralPath</span></span>

<span data-ttu-id="61a5c-120">Sökvägen till filen som importeras.</span><span class="sxs-lookup"><span data-stu-id="61a5c-120">The path to the file being imported.</span></span> <span data-ttu-id="61a5c-121">Alla tecken i sökvägen behandlas som litterala värden.</span><span class="sxs-lookup"><span data-stu-id="61a5c-121">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="61a5c-122">Jokertecken bearbetas inte.</span><span class="sxs-lookup"><span data-stu-id="61a5c-122">Wildcard characters are not processed.</span></span>

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

### <span data-ttu-id="61a5c-123">-Path</span><span class="sxs-lookup"><span data-stu-id="61a5c-123">-Path</span></span>

<span data-ttu-id="61a5c-124">Sökvägen till filen som importeras.</span><span class="sxs-lookup"><span data-stu-id="61a5c-124">The path to the file being imported.</span></span> <span data-ttu-id="61a5c-125">Jokertecken är tillåtna, men endast den första matchande filen importeras.</span><span class="sxs-lookup"><span data-stu-id="61a5c-125">Wildcards are allowed but only the first matching file is imported.</span></span>

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

### <span data-ttu-id="61a5c-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="61a5c-126">CommonParameters</span></span>

<span data-ttu-id="61a5c-127">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="61a5c-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="61a5c-128">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="61a5c-128">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="61a5c-129">INDATA</span><span class="sxs-lookup"><span data-stu-id="61a5c-129">INPUTS</span></span>

## <span data-ttu-id="61a5c-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="61a5c-130">OUTPUTS</span></span>

### <span data-ttu-id="61a5c-131">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="61a5c-131">System.Collections.Hashtable</span></span>

## <span data-ttu-id="61a5c-132">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="61a5c-132">NOTES</span></span>

## <span data-ttu-id="61a5c-133">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="61a5c-133">RELATED LINKS</span></span>

[<span data-ttu-id="61a5c-134">Invoke-uttryck</span><span class="sxs-lookup"><span data-stu-id="61a5c-134">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="61a5c-135">Importera – LocalizedData</span><span class="sxs-lookup"><span data-stu-id="61a5c-135">Import-LocalizedData</span></span>](Import-LocalizedData.md)

