---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: 800cd9ea24bad09f532db26c5091735cd987eef0
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195046"
---
# <span data-ttu-id="7e172-102">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="7e172-102">Import-BinaryMiLog</span></span>

## <span data-ttu-id="7e172-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7e172-103">SYNOPSIS</span></span>
<span data-ttu-id="7e172-104">Används för att återskapa de sparade objekten baserat på innehållet i en export fil.</span><span class="sxs-lookup"><span data-stu-id="7e172-104">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="7e172-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7e172-105">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="7e172-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7e172-106">DESCRIPTION</span></span>

<span data-ttu-id="7e172-107">Använd denna cmdlet för att återskapa sparade objekt baserat på innehållet i en export fil som skapats av `Export-BinaryMILog` .</span><span class="sxs-lookup"><span data-stu-id="7e172-107">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="7e172-108">Denna cmdlet liknar `Import-Clixml` , förutom att `Export-BinaryMILog` lagrar det resulterande objektet i en binär kodad fil.</span><span class="sxs-lookup"><span data-stu-id="7e172-108">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="7e172-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7e172-109">EXAMPLES</span></span>

### <span data-ttu-id="7e172-110">Exempel 1 – återställa objekt som har exporter ATS till en fil</span><span class="sxs-lookup"><span data-stu-id="7e172-110">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="7e172-111">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7e172-111">PARAMETERS</span></span>

### <span data-ttu-id="7e172-112">-Path</span><span class="sxs-lookup"><span data-stu-id="7e172-112">-Path</span></span>

<span data-ttu-id="7e172-113">Anger sökvägen till filen där den binära representationen av objektet ska lagras.</span><span class="sxs-lookup"><span data-stu-id="7e172-113">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="7e172-114">Parametern **Path** stöder jokertecken och relativa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="7e172-114">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="7e172-115">Denna cmdlet genererar ett fel om sökvägen matchar fler än en fil.</span><span class="sxs-lookup"><span data-stu-id="7e172-115">This cmdlet generates an error if the path resolves to more than one file.</span></span>

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

### <span data-ttu-id="7e172-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e172-116">CommonParameters</span></span>
<span data-ttu-id="7e172-117">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e172-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e172-118">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7e172-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e172-119">INDATA</span><span class="sxs-lookup"><span data-stu-id="7e172-119">INPUTS</span></span>

### <span data-ttu-id="7e172-120">Inget</span><span class="sxs-lookup"><span data-stu-id="7e172-120">None</span></span>

## <span data-ttu-id="7e172-121">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7e172-121">OUTPUTS</span></span>

### <span data-ttu-id="7e172-122">System. Object</span><span class="sxs-lookup"><span data-stu-id="7e172-122">System.Object</span></span>

## <span data-ttu-id="7e172-123">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7e172-123">NOTES</span></span>

## <span data-ttu-id="7e172-124">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7e172-124">RELATED LINKS</span></span>
