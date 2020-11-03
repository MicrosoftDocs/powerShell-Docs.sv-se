---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: cd784c5adac3aeeabc8e4cf9f5f4b0b67e9a000c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266042"
---
# <span data-ttu-id="5c84e-103">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="5c84e-103">New-DscChecksum</span></span>

## <span data-ttu-id="5c84e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5c84e-104">SYNOPSIS</span></span>
<span data-ttu-id="5c84e-105">Skapar kontroll Summa filer för DSC-dokument och DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="5c84e-105">Creates checksum files for DSC documents and DSC resources.</span></span>

## <span data-ttu-id="5c84e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5c84e-106">SYNTAX</span></span>

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5c84e-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5c84e-107">DESCRIPTION</span></span>
<span data-ttu-id="5c84e-108">Cmdlet: en **New-DSCCheckSum** genererar kontroll Summa filer för Windows PowerShell-dokument med önskad tillstånds konfiguration (DSC) och komprimerade DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="5c84e-108">The **New-DSCCheckSum** cmdlet generates checksum files for Windows PowerShell Desired State Configuration (DSC) documents and compressed DSC resources.</span></span>
<span data-ttu-id="5c84e-109">Denna cmdlet skapar en kontroll Summa fil för varje konfiguration och resurs som ska användas i pull-läge.</span><span class="sxs-lookup"><span data-stu-id="5c84e-109">This cmdlet generates a checksum file for each configuration and resource to be used in pull mode.</span></span>
<span data-ttu-id="5c84e-110">DSC-tjänsten använder kontroll summorna för att kontrol lera att rätt konfiguration och resurser finns på målnoden.</span><span class="sxs-lookup"><span data-stu-id="5c84e-110">The DSC service uses the checksums to make sure that the correct configuration and resources exist on the target node.</span></span>
<span data-ttu-id="5c84e-111">Placera kontroll summorna tillsammans med tillhör ande DSC-dokument och komprimerade DSC-resurser i DSC-tjänstens arkiv.</span><span class="sxs-lookup"><span data-stu-id="5c84e-111">Place the checksums together with the associated DSC documents and compressed DSC resources in the DSC service store.</span></span>

## <span data-ttu-id="5c84e-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5c84e-112">EXAMPLES</span></span>

### <span data-ttu-id="5c84e-113">Exempel 1: skapa kontroll Summa filer för alla konfigurationer i en angiven sökväg</span><span class="sxs-lookup"><span data-stu-id="5c84e-113">Example 1: Create checksum files for all configurations in a specific path</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="5c84e-114">Det här kommandot skapar en kontroll Summa filer för alla konfigurationer i sökvägen C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="5c84e-114">This command creates checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="5c84e-115">Alla filer för kontroll summor som redan finns hoppas över.</span><span class="sxs-lookup"><span data-stu-id="5c84e-115">Any checksum files that already exist are skipped.</span></span>

### <span data-ttu-id="5c84e-116">Exempel 2: skapa kontroll Summa filer för alla konfigurationer i en angiven sökväg och skriv över de befintliga kontroll summor filerna</span><span class="sxs-lookup"><span data-stu-id="5c84e-116">Example 2: Create checksum files for all configurations in a specific path and overwrite the existing checksum files</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

<span data-ttu-id="5c84e-117">Det här kommandot skapar nya kontroll summor filer för alla konfigurationer i sökvägen C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="5c84e-117">This command creates new checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="5c84e-118">Om du anger *Force* -parametern kommer kommandot att skriva över alla eventuella kontroll Summa filer som redan finns.</span><span class="sxs-lookup"><span data-stu-id="5c84e-118">Specifying the *Force* parameter causes the command to overwrite any checksum files that already exist.</span></span>

## <span data-ttu-id="5c84e-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5c84e-119">PARAMETERS</span></span>

### <span data-ttu-id="5c84e-120">-Force</span><span class="sxs-lookup"><span data-stu-id="5c84e-120">-Force</span></span>
<span data-ttu-id="5c84e-121">Anger att cmdleten skriver över den angivna utdatafilen om den redan finns.</span><span class="sxs-lookup"><span data-stu-id="5c84e-121">Indicates that the cmdlet overwrites the specified output file if it already exists.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5c84e-122">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="5c84e-122">-OutPath</span></span>
<span data-ttu-id="5c84e-123">Anger sökväg och fil namn för filen med utgångs kontroll.</span><span class="sxs-lookup"><span data-stu-id="5c84e-123">Specifies the path and file name of the output checksum file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5c84e-124">-Path</span><span class="sxs-lookup"><span data-stu-id="5c84e-124">-Path</span></span>
<span data-ttu-id="5c84e-125">Anger sökvägen till indatafilen.</span><span class="sxs-lookup"><span data-stu-id="5c84e-125">Specifies the path of the input file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5c84e-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5c84e-126">-Confirm</span></span>
<span data-ttu-id="5c84e-127">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5c84e-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5c84e-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5c84e-128">-WhatIf</span></span>
<span data-ttu-id="5c84e-129">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5c84e-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5c84e-130">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="5c84e-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5c84e-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5c84e-131">CommonParameters</span></span>
<span data-ttu-id="5c84e-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5c84e-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5c84e-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5c84e-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5c84e-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="5c84e-134">INPUTS</span></span>

## <span data-ttu-id="5c84e-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5c84e-135">OUTPUTS</span></span>

## <span data-ttu-id="5c84e-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5c84e-136">NOTES</span></span>

## <span data-ttu-id="5c84e-137">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5c84e-137">RELATED LINKS</span></span>

[<span data-ttu-id="5c84e-138">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c84e-138">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)
