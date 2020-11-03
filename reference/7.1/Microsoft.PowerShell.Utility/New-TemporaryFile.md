---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 406675d8bde1b6b9a28913c09d5374393705f93b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267579"
---
# <span data-ttu-id="6bafe-103">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="6bafe-103">New-TemporaryFile</span></span>

## <span data-ttu-id="6bafe-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6bafe-104">SYNOPSIS</span></span>
<span data-ttu-id="6bafe-105">Skapar en temporär fil.</span><span class="sxs-lookup"><span data-stu-id="6bafe-105">Creates a temporary file.</span></span>

## <span data-ttu-id="6bafe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6bafe-106">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6bafe-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6bafe-107">DESCRIPTION</span></span>

<span data-ttu-id="6bafe-108">Denna cmdlet skapar temporära filer som du kan använda i skript.</span><span class="sxs-lookup"><span data-stu-id="6bafe-108">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="6bafe-109">`New-TemporaryFile`Cmdleten skapar en tom fil som har `.tmp` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="6bafe-109">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="6bafe-110">Denna cmdlet namnger filen `tmp<NNNN>.tmp` , där `<NNNN>` är ett slumpmässigt hexadecimalt tal.</span><span class="sxs-lookup"><span data-stu-id="6bafe-110">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="6bafe-111">Cmdleten skapar filen i **Temp** -mappen.</span><span class="sxs-lookup"><span data-stu-id="6bafe-111">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="6bafe-112">Denna cmdlet använder metoden [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) för att hitta **Temp** -mappen.</span><span class="sxs-lookup"><span data-stu-id="6bafe-112">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="6bafe-113">Den här metoden kontrollerar om det finns miljövariabler i följande ordning och använder den första sökvägen som hittades:</span><span class="sxs-lookup"><span data-stu-id="6bafe-113">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="6bafe-114">På Windows-plattformar:</span><span class="sxs-lookup"><span data-stu-id="6bafe-114">On Windows platforms:</span></span>

  1. <span data-ttu-id="6bafe-115">Sökvägen som anges av TMP-miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="6bafe-115">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="6bafe-116">Sökvägen som anges av miljövariabeln TEMP.</span><span class="sxs-lookup"><span data-stu-id="6bafe-116">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="6bafe-117">Den sökväg som anges av miljövariabeln USERPROFILE.</span><span class="sxs-lookup"><span data-stu-id="6bafe-117">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="6bafe-118">Windows-katalogen.</span><span class="sxs-lookup"><span data-stu-id="6bafe-118">The Windows directory.</span></span>

- <span data-ttu-id="6bafe-119">På andra plattformar än Windows: använder sökvägen som anges av miljövariabeln TMPDIR.</span><span class="sxs-lookup"><span data-stu-id="6bafe-119">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="6bafe-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6bafe-120">EXAMPLES</span></span>

### <span data-ttu-id="6bafe-121">Exempel 1: skapa en temporär fil</span><span class="sxs-lookup"><span data-stu-id="6bafe-121">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="6bafe-122">Det här kommandot skapar en `.tmp` fil i den tillfälliga mappen och lagrar sedan en referens till filen i `$TempFile` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6bafe-122">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="6bafe-123">Du kan använda den här filen senare i skriptet.</span><span class="sxs-lookup"><span data-stu-id="6bafe-123">You can use this file later in your script.</span></span>

## <span data-ttu-id="6bafe-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6bafe-124">PARAMETERS</span></span>

### <span data-ttu-id="6bafe-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6bafe-125">-Confirm</span></span>

<span data-ttu-id="6bafe-126">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6bafe-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6bafe-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6bafe-127">-WhatIf</span></span>

<span data-ttu-id="6bafe-128">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="6bafe-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6bafe-129">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="6bafe-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6bafe-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6bafe-130">CommonParameters</span></span>

<span data-ttu-id="6bafe-131">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6bafe-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6bafe-132">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6bafe-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6bafe-133">INDATA</span><span class="sxs-lookup"><span data-stu-id="6bafe-133">INPUTS</span></span>

## <span data-ttu-id="6bafe-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6bafe-134">OUTPUTS</span></span>

### <span data-ttu-id="6bafe-135">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="6bafe-135">System.IO.FileInfo</span></span>

<span data-ttu-id="6bafe-136">Denna cmdlet returnerar ett **fileinfo** -objekt som representerar den temporära filen.</span><span class="sxs-lookup"><span data-stu-id="6bafe-136">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="6bafe-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6bafe-137">NOTES</span></span>

## <span data-ttu-id="6bafe-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6bafe-138">RELATED LINKS</span></span>

