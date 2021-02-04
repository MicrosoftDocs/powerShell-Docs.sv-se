---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: d7942abff2974064c52a8a9ac086a280959b3a63
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860856"
---
# <span data-ttu-id="28a34-102">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="28a34-102">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="28a34-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="28a34-103">SYNOPSIS</span></span>
<span data-ttu-id="28a34-104">Importerar värden från en `.PSD1` fil utan att anropa dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="28a34-104">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="28a34-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="28a34-105">SYNTAX</span></span>

### <span data-ttu-id="28a34-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="28a34-106">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

### <span data-ttu-id="28a34-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="28a34-107">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

## <span data-ttu-id="28a34-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="28a34-108">DESCRIPTION</span></span>

<span data-ttu-id="28a34-109">Cmdlet: en på `Import-PowerShellDataFile` ett säkert sätt importerar nyckel/värde-par från hash som definierats i en `.PSD1` fil.</span><span class="sxs-lookup"><span data-stu-id="28a34-109">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="28a34-110">Värdena kan importeras med hjälp av `Invoke-Expression` filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="28a34-110">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="28a34-111">Kör dock `Invoke-Expression` eventuell kod som finns i filen.</span><span class="sxs-lookup"><span data-stu-id="28a34-111">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="28a34-112">Detta kan producera oönskade resultat eller köra osäker kod.</span><span class="sxs-lookup"><span data-stu-id="28a34-112">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="28a34-113">`Import-PowerShellDataFile` importerar data utan att anropa koden.</span><span class="sxs-lookup"><span data-stu-id="28a34-113">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span> <span data-ttu-id="28a34-114">Som standard finns det en nyckel gräns på 500 men kan kringgås med **SkipLimitCheck** -växeln.</span><span class="sxs-lookup"><span data-stu-id="28a34-114">By default there is a 500 key limit but can be bypassed with the **SkipLimitCheck** switch.</span></span>

## <span data-ttu-id="28a34-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="28a34-115">EXAMPLES</span></span>

### <span data-ttu-id="28a34-116">Exempel 1: Hämta värden från PSD1</span><span class="sxs-lookup"><span data-stu-id="28a34-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="28a34-117">I det här exemplet hämtas de nyckel/värde-par som lagras i den hash-tabellen som behålls i `Configuration.psd1` filen.</span><span class="sxs-lookup"><span data-stu-id="28a34-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="28a34-118">`Get-Content` används för att visa innehållet i `Configuration.psd1` filen.</span><span class="sxs-lookup"><span data-stu-id="28a34-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

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

## <span data-ttu-id="28a34-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="28a34-119">PARAMETERS</span></span>

### <span data-ttu-id="28a34-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="28a34-120">-LiteralPath</span></span>

<span data-ttu-id="28a34-121">Sökvägen till filen som importeras.</span><span class="sxs-lookup"><span data-stu-id="28a34-121">The path to the file being imported.</span></span> <span data-ttu-id="28a34-122">Alla tecken i sökvägen behandlas som litterala värden.</span><span class="sxs-lookup"><span data-stu-id="28a34-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="28a34-123">Jokertecken bearbetas inte.</span><span class="sxs-lookup"><span data-stu-id="28a34-123">Wildcard characters are not processed.</span></span>

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

### <span data-ttu-id="28a34-124">-Path</span><span class="sxs-lookup"><span data-stu-id="28a34-124">-Path</span></span>

<span data-ttu-id="28a34-125">Sökvägen till filen som importeras.</span><span class="sxs-lookup"><span data-stu-id="28a34-125">The path to the file being imported.</span></span> <span data-ttu-id="28a34-126">Jokertecken är tillåtna, men endast den första matchande filen importeras.</span><span class="sxs-lookup"><span data-stu-id="28a34-126">Wildcards are allowed but only the first matching file is imported.</span></span>

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

### <span data-ttu-id="28a34-127">-SkipLimitCheck</span><span class="sxs-lookup"><span data-stu-id="28a34-127">-SkipLimitCheck</span></span>

<span data-ttu-id="28a34-128">Som standard `Import-PowerShellDataFile` importeras bara 500 nycklar från en `.psd1` fil.</span><span class="sxs-lookup"><span data-stu-id="28a34-128">By default `Import-PowerShellDataFile` imports only 500 keys from a `.psd1` file.</span></span> <span data-ttu-id="28a34-129">Använd **SkipLimitCheck** för att importera fler än 500 nycklar.</span><span class="sxs-lookup"><span data-stu-id="28a34-129">Use **SkipLimitCheck** to import more than 500 keys.</span></span>

```yaml
Type: Switch
Parameter Sets: All
Aliases:

Required: False
Position: 0
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28a34-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="28a34-130">CommonParameters</span></span>

<span data-ttu-id="28a34-131">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="28a34-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="28a34-132">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="28a34-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="28a34-133">INDATA</span><span class="sxs-lookup"><span data-stu-id="28a34-133">INPUTS</span></span>

## <span data-ttu-id="28a34-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="28a34-134">OUTPUTS</span></span>

### <span data-ttu-id="28a34-135">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="28a34-135">System.Collections.Hashtable</span></span>

## <span data-ttu-id="28a34-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="28a34-136">NOTES</span></span>

## <span data-ttu-id="28a34-137">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="28a34-137">RELATED LINKS</span></span>

[<span data-ttu-id="28a34-138">Invoke-uttryck</span><span class="sxs-lookup"><span data-stu-id="28a34-138">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="28a34-139">Importera – LocalizedData</span><span class="sxs-lookup"><span data-stu-id="28a34-139">Import-LocalizedData</span></span>](Import-LocalizedData.md)
