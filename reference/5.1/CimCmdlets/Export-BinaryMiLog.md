---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: 1d202b7bbda359f859838475eb9f37730506bd1f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194366"
---
# <span data-ttu-id="7329b-103">Export-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="7329b-103">Export-BinaryMiLog</span></span>

## <span data-ttu-id="7329b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7329b-104">SYNOPSIS</span></span>
<span data-ttu-id="7329b-105">Skapar en binär kodad representation av ett objekt eller objekt och lagrar det i en fil.</span><span class="sxs-lookup"><span data-stu-id="7329b-105">Creates a binary encoded representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="7329b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7329b-106">SYNTAX</span></span>

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="7329b-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7329b-107">DESCRIPTION</span></span>

<span data-ttu-id="7329b-108">`Export-BinaryMILog`Cmdleten skapar en binär-baserad representation av ett objekt eller objekt och lagrar det i en fil.</span><span class="sxs-lookup"><span data-stu-id="7329b-108">The `Export-BinaryMILog` cmdlet creates a binary-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="7329b-109">Du kan sedan använda `Import-BinaryMiLog` cmdleten för att återskapa det sparade objektet baserat på innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="7329b-109">You can then use the `Import-BinaryMiLog` cmdlet to re-create the saved object based on the contents of that file.</span></span>

<span data-ttu-id="7329b-110">Denna cmdlet liknar `Import-Clixml` , förutom att `Export-BinaryMILog` lagrar det resulterande objektet i en binär kodad fil.</span><span class="sxs-lookup"><span data-stu-id="7329b-110">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="7329b-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7329b-111">EXAMPLES</span></span>

### <span data-ttu-id="7329b-112">Exempel 1 – Skapa en binär representation av CimInstances</span><span class="sxs-lookup"><span data-stu-id="7329b-112">Example 1 - Create a binary representation of CimInstances</span></span>

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

<span data-ttu-id="7329b-113">Detta kommando exporterar **CimInstances** till en binär mi-loggfil som anges av parametern Path.</span><span class="sxs-lookup"><span data-stu-id="7329b-113">This command exports **CimInstances** to a binary MI log file specified by the Path parameter.</span></span> <span data-ttu-id="7329b-114">Se exemplet för Import-BinaryMiLog för att se hur du återskapar **CimInstances** genom att importera den här filen.</span><span class="sxs-lookup"><span data-stu-id="7329b-114">See the example for Import-BinaryMiLog to see how to recreate the **CimInstances** by importing this file.</span></span>

## <span data-ttu-id="7329b-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7329b-115">PARAMETERS</span></span>

### <span data-ttu-id="7329b-116">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7329b-116">-InputObject</span></span>

<span data-ttu-id="7329b-117">Anger indatamängden för denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7329b-117">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="7329b-118">Du kan använda den här parametern, eller så kan du skicka en pipe till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7329b-118">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7329b-119">-Path</span><span class="sxs-lookup"><span data-stu-id="7329b-119">-Path</span></span>

<span data-ttu-id="7329b-120">Anger sökvägen till filen där den binära representationen av objektet ska lagras.</span><span class="sxs-lookup"><span data-stu-id="7329b-120">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="7329b-121">Parametern **Path** stöder jokertecken och relativa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="7329b-121">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="7329b-122">Denna cmdlet genererar ett fel om sökvägen matchar fler än en fil.</span><span class="sxs-lookup"><span data-stu-id="7329b-122">This cmdlet generates an error if the path resolves to more than one file.</span></span>

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

### <span data-ttu-id="7329b-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7329b-123">CommonParameters</span></span>

<span data-ttu-id="7329b-124">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7329b-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7329b-125">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7329b-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7329b-126">INDATA</span><span class="sxs-lookup"><span data-stu-id="7329b-126">INPUTS</span></span>

### <span data-ttu-id="7329b-127">Microsoft. Management. Infrastructure. CimInstance</span><span class="sxs-lookup"><span data-stu-id="7329b-127">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="7329b-128">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7329b-128">OUTPUTS</span></span>

### <span data-ttu-id="7329b-129">System. Object</span><span class="sxs-lookup"><span data-stu-id="7329b-129">System.Object</span></span>

## <span data-ttu-id="7329b-130">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7329b-130">NOTES</span></span>

## <span data-ttu-id="7329b-131">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7329b-131">RELATED LINKS</span></span>

[<span data-ttu-id="7329b-132">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="7329b-132">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="7329b-133">Importera – BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="7329b-133">Import-BinaryMiLog</span></span>](import-binarymilog.md)

[<span data-ttu-id="7329b-134">Importera – CliXml</span><span class="sxs-lookup"><span data-stu-id="7329b-134">Import-Clixml</span></span>](../microsoft.powershell.utility/import-clixml.md)
