---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: ce777eff8b41fe6bde3c8e00050ec9db87174265
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195890"
---
# <span data-ttu-id="61ce7-103">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="61ce7-103">Import-BinaryMiLog</span></span>

## <span data-ttu-id="61ce7-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="61ce7-104">SYNOPSIS</span></span>
<span data-ttu-id="61ce7-105">Används för att återskapa de sparade objekten baserat på innehållet i en export fil.</span><span class="sxs-lookup"><span data-stu-id="61ce7-105">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="61ce7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="61ce7-106">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="61ce7-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="61ce7-107">DESCRIPTION</span></span>

<span data-ttu-id="61ce7-108">Använd denna cmdlet för att återskapa sparade objekt baserat på innehållet i en export fil som skapats av `Export-BinaryMILog` .</span><span class="sxs-lookup"><span data-stu-id="61ce7-108">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="61ce7-109">Denna cmdlet liknar `Import-Clixml` , förutom att `Export-BinaryMILog` lagrar det resulterande objektet i en binär kodad fil.</span><span class="sxs-lookup"><span data-stu-id="61ce7-109">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="61ce7-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="61ce7-110">EXAMPLES</span></span>

### <span data-ttu-id="61ce7-111">Exempel 1 – återställa objekt som har exporter ATS till en fil</span><span class="sxs-lookup"><span data-stu-id="61ce7-111">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="61ce7-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="61ce7-112">PARAMETERS</span></span>

### <span data-ttu-id="61ce7-113">-Path</span><span class="sxs-lookup"><span data-stu-id="61ce7-113">-Path</span></span>

<span data-ttu-id="61ce7-114">Anger sökvägen till filen där den binära representationen av objektet ska lagras.</span><span class="sxs-lookup"><span data-stu-id="61ce7-114">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="61ce7-115">Parametern **Path** stöder jokertecken och relativa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="61ce7-115">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="61ce7-116">Denna cmdlet genererar ett fel om sökvägen matchar fler än en fil.</span><span class="sxs-lookup"><span data-stu-id="61ce7-116">This cmdlet generates an error if the path resolves to more than one file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="61ce7-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="61ce7-117">CommonParameters</span></span>
<span data-ttu-id="61ce7-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="61ce7-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="61ce7-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="61ce7-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="61ce7-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="61ce7-120">INPUTS</span></span>

### <span data-ttu-id="61ce7-121">Inget</span><span class="sxs-lookup"><span data-stu-id="61ce7-121">None</span></span>

## <span data-ttu-id="61ce7-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="61ce7-122">OUTPUTS</span></span>

### <span data-ttu-id="61ce7-123">System. Object</span><span class="sxs-lookup"><span data-stu-id="61ce7-123">System.Object</span></span>

## <span data-ttu-id="61ce7-124">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="61ce7-124">NOTES</span></span>

## <span data-ttu-id="61ce7-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="61ce7-125">RELATED LINKS</span></span>
