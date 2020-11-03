---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: c4bfe6b4ed04ae638421c18f5095403057dc03c9
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262377"
---
# <span data-ttu-id="dc116-103">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="dc116-103">New-TemporaryFile</span></span>

## <span data-ttu-id="dc116-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dc116-104">SYNOPSIS</span></span>
<span data-ttu-id="dc116-105">Skapar en temporär fil.</span><span class="sxs-lookup"><span data-stu-id="dc116-105">Creates a temporary file.</span></span>

## <span data-ttu-id="dc116-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dc116-106">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dc116-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dc116-107">DESCRIPTION</span></span>

<span data-ttu-id="dc116-108">Denna cmdlet skapar temporära filer som du kan använda i skript.</span><span class="sxs-lookup"><span data-stu-id="dc116-108">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="dc116-109">`New-TemporaryFile`Cmdleten skapar en tom fil som har `.tmp` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="dc116-109">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="dc116-110">Denna cmdlet namnger filen `tmp<NNNN>.tmp` , där `<NNNN>` är ett slumpmässigt hexadecimalt tal.</span><span class="sxs-lookup"><span data-stu-id="dc116-110">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="dc116-111">Cmdleten skapar filen i **Temp** -mappen.</span><span class="sxs-lookup"><span data-stu-id="dc116-111">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="dc116-112">Denna cmdlet använder metoden [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) för att hitta **Temp** -mappen.</span><span class="sxs-lookup"><span data-stu-id="dc116-112">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="dc116-113">Den här metoden kontrollerar om det finns miljövariabler i följande ordning och använder den första sökvägen som hittades:</span><span class="sxs-lookup"><span data-stu-id="dc116-113">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="dc116-114">På Windows-plattformar:</span><span class="sxs-lookup"><span data-stu-id="dc116-114">On Windows platforms:</span></span>

  1. <span data-ttu-id="dc116-115">Sökvägen som anges av TMP-miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="dc116-115">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="dc116-116">Sökvägen som anges av miljövariabeln TEMP.</span><span class="sxs-lookup"><span data-stu-id="dc116-116">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="dc116-117">Den sökväg som anges av miljövariabeln USERPROFILE.</span><span class="sxs-lookup"><span data-stu-id="dc116-117">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="dc116-118">Windows-katalogen.</span><span class="sxs-lookup"><span data-stu-id="dc116-118">The Windows directory.</span></span>

- <span data-ttu-id="dc116-119">På andra plattformar än Windows: använder sökvägen som anges av miljövariabeln TMPDIR.</span><span class="sxs-lookup"><span data-stu-id="dc116-119">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="dc116-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dc116-120">EXAMPLES</span></span>

### <span data-ttu-id="dc116-121">Exempel 1: skapa en temporär fil</span><span class="sxs-lookup"><span data-stu-id="dc116-121">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="dc116-122">Det här kommandot skapar en `.tmp` fil i den tillfälliga mappen och lagrar sedan en referens till filen i `$TempFile` variabeln.</span><span class="sxs-lookup"><span data-stu-id="dc116-122">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="dc116-123">Du kan använda den här filen senare i skriptet.</span><span class="sxs-lookup"><span data-stu-id="dc116-123">You can use this file later in your script.</span></span>

## <span data-ttu-id="dc116-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dc116-124">PARAMETERS</span></span>

### <span data-ttu-id="dc116-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dc116-125">-Confirm</span></span>

<span data-ttu-id="dc116-126">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dc116-126">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc116-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dc116-127">-WhatIf</span></span>

<span data-ttu-id="dc116-128">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="dc116-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="dc116-129">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="dc116-129">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc116-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dc116-130">CommonParameters</span></span>

<span data-ttu-id="dc116-131">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dc116-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dc116-132">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="dc116-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="dc116-133">INDATA</span><span class="sxs-lookup"><span data-stu-id="dc116-133">INPUTS</span></span>

## <span data-ttu-id="dc116-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dc116-134">OUTPUTS</span></span>

### <span data-ttu-id="dc116-135">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="dc116-135">System.IO.FileInfo</span></span>

<span data-ttu-id="dc116-136">Denna cmdlet returnerar ett **fileinfo** -objekt som representerar den temporära filen.</span><span class="sxs-lookup"><span data-stu-id="dc116-136">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="dc116-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dc116-137">NOTES</span></span>

## <span data-ttu-id="dc116-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dc116-138">RELATED LINKS</span></span>
