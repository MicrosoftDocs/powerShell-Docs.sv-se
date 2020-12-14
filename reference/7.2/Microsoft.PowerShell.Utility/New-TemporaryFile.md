---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 1c66cd3b1cc2fccc58cd75c367b41c445deb1e72
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709073"
---
# <span data-ttu-id="22d5a-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="22d5a-102">New-TemporaryFile</span></span>

## <span data-ttu-id="22d5a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="22d5a-103">SYNOPSIS</span></span>
<span data-ttu-id="22d5a-104">Skapar en temporär fil.</span><span class="sxs-lookup"><span data-stu-id="22d5a-104">Creates a temporary file.</span></span>

## <span data-ttu-id="22d5a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="22d5a-105">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="22d5a-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="22d5a-106">DESCRIPTION</span></span>

<span data-ttu-id="22d5a-107">Denna cmdlet skapar temporära filer som du kan använda i skript.</span><span class="sxs-lookup"><span data-stu-id="22d5a-107">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="22d5a-108">`New-TemporaryFile`Cmdleten skapar en tom fil som har `.tmp` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="22d5a-108">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="22d5a-109">Denna cmdlet namnger filen `tmp<NNNN>.tmp` , där `<NNNN>` är ett slumpmässigt hexadecimalt tal.</span><span class="sxs-lookup"><span data-stu-id="22d5a-109">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="22d5a-110">Cmdleten skapar filen i **Temp** -mappen.</span><span class="sxs-lookup"><span data-stu-id="22d5a-110">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="22d5a-111">Denna cmdlet använder metoden [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) för att hitta **Temp** -mappen.</span><span class="sxs-lookup"><span data-stu-id="22d5a-111">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="22d5a-112">Den här metoden kontrollerar om det finns miljövariabler i följande ordning och använder den första sökvägen som hittades:</span><span class="sxs-lookup"><span data-stu-id="22d5a-112">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="22d5a-113">På Windows-plattformar:</span><span class="sxs-lookup"><span data-stu-id="22d5a-113">On Windows platforms:</span></span>

  1. <span data-ttu-id="22d5a-114">Sökvägen som anges av TMP-miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="22d5a-114">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="22d5a-115">Sökvägen som anges av miljövariabeln TEMP.</span><span class="sxs-lookup"><span data-stu-id="22d5a-115">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="22d5a-116">Den sökväg som anges av miljövariabeln USERPROFILE.</span><span class="sxs-lookup"><span data-stu-id="22d5a-116">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="22d5a-117">Windows-katalogen.</span><span class="sxs-lookup"><span data-stu-id="22d5a-117">The Windows directory.</span></span>

- <span data-ttu-id="22d5a-118">På andra plattformar än Windows: använder sökvägen som anges av miljövariabeln TMPDIR.</span><span class="sxs-lookup"><span data-stu-id="22d5a-118">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="22d5a-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="22d5a-119">EXAMPLES</span></span>

### <span data-ttu-id="22d5a-120">Exempel 1: skapa en temporär fil</span><span class="sxs-lookup"><span data-stu-id="22d5a-120">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="22d5a-121">Det här kommandot skapar en `.tmp` fil i den tillfälliga mappen och lagrar sedan en referens till filen i `$TempFile` variabeln.</span><span class="sxs-lookup"><span data-stu-id="22d5a-121">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="22d5a-122">Du kan använda den här filen senare i skriptet.</span><span class="sxs-lookup"><span data-stu-id="22d5a-122">You can use this file later in your script.</span></span>

## <span data-ttu-id="22d5a-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="22d5a-123">PARAMETERS</span></span>

### <span data-ttu-id="22d5a-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="22d5a-124">-Confirm</span></span>

<span data-ttu-id="22d5a-125">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="22d5a-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="22d5a-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="22d5a-126">-WhatIf</span></span>

<span data-ttu-id="22d5a-127">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="22d5a-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="22d5a-128">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="22d5a-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="22d5a-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="22d5a-129">CommonParameters</span></span>

<span data-ttu-id="22d5a-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="22d5a-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="22d5a-131">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="22d5a-131">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="22d5a-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="22d5a-132">INPUTS</span></span>

## <span data-ttu-id="22d5a-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="22d5a-133">OUTPUTS</span></span>

### <span data-ttu-id="22d5a-134">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="22d5a-134">System.IO.FileInfo</span></span>

<span data-ttu-id="22d5a-135">Denna cmdlet returnerar ett **fileinfo** -objekt som representerar den temporära filen.</span><span class="sxs-lookup"><span data-stu-id="22d5a-135">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="22d5a-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="22d5a-136">NOTES</span></span>

## <span data-ttu-id="22d5a-137">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="22d5a-137">RELATED LINKS</span></span>

