---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: ce5dd31170bc47edaa04ca3c31deab62dc4ec354
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273272"
---
# <span data-ttu-id="9e4a4-103">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="9e4a4-103">Import-BinaryMiLog</span></span>

## <span data-ttu-id="9e4a4-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9e4a4-104">SYNOPSIS</span></span>
<span data-ttu-id="9e4a4-105">Används för att återskapa de sparade objekten baserat på innehållet i en export fil.</span><span class="sxs-lookup"><span data-stu-id="9e4a4-105">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="9e4a4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9e4a4-106">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="9e4a4-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9e4a4-107">DESCRIPTION</span></span>

<span data-ttu-id="9e4a4-108">Använd denna cmdlet för att återskapa sparade objekt baserat på innehållet i en export fil som skapats av `Export-BinaryMILog` .</span><span class="sxs-lookup"><span data-stu-id="9e4a4-108">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="9e4a4-109">Denna cmdlet liknar `Import-Clixml` , förutom att `Export-BinaryMILog` lagrar det resulterande objektet i en binär kodad fil.</span><span class="sxs-lookup"><span data-stu-id="9e4a4-109">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="9e4a4-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9e4a4-110">EXAMPLES</span></span>

### <span data-ttu-id="9e4a4-111">Exempel 1 – återställa objekt som har exporter ATS till en fil</span><span class="sxs-lookup"><span data-stu-id="9e4a4-111">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="9e4a4-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9e4a4-112">PARAMETERS</span></span>

### <span data-ttu-id="9e4a4-113">-Path</span><span class="sxs-lookup"><span data-stu-id="9e4a4-113">-Path</span></span>

<span data-ttu-id="9e4a4-114">Anger sökvägen till filen där den binära representationen av objektet ska lagras.</span><span class="sxs-lookup"><span data-stu-id="9e4a4-114">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="9e4a4-115">Parametern **Path** stöder jokertecken och relativa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="9e4a4-115">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="9e4a4-116">Denna cmdlet genererar ett fel om sökvägen matchar fler än en fil.</span><span class="sxs-lookup"><span data-stu-id="9e4a4-116">This cmdlet generates an error if the path resolves to more than one file.</span></span>

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

### <span data-ttu-id="9e4a4-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e4a4-117">CommonParameters</span></span>
<span data-ttu-id="9e4a4-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9e4a4-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e4a4-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9e4a4-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e4a4-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="9e4a4-120">INPUTS</span></span>

### <span data-ttu-id="9e4a4-121">Inget</span><span class="sxs-lookup"><span data-stu-id="9e4a4-121">None</span></span>

## <span data-ttu-id="9e4a4-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9e4a4-122">OUTPUTS</span></span>

### <span data-ttu-id="9e4a4-123">System. Object</span><span class="sxs-lookup"><span data-stu-id="9e4a4-123">System.Object</span></span>

## <span data-ttu-id="9e4a4-124">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9e4a4-124">NOTES</span></span>

## <span data-ttu-id="9e4a4-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9e4a4-125">RELATED LINKS</span></span>
