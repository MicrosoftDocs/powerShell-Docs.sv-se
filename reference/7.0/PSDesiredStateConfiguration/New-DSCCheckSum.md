---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 2a66f906025f7a25609080e0b8da7f01755cd2fa
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262185"
---
# <span data-ttu-id="0cfa0-103">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="0cfa0-103">New-DscChecksum</span></span>

## <span data-ttu-id="0cfa0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0cfa0-104">SYNOPSIS</span></span>
<span data-ttu-id="0cfa0-105">Skapar kontroll Summa filer för DSC-dokument och DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-105">Creates checksum files for DSC documents and DSC resources.</span></span>

## <span data-ttu-id="0cfa0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0cfa0-106">SYNTAX</span></span>

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0cfa0-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0cfa0-107">DESCRIPTION</span></span>

<span data-ttu-id="0cfa0-108">Cmdlet: en **New-DSCCheckSum** genererar en kontroll Summa filer för DSC-dokument (Desired State Configuration) och komprimerade DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-108">The **New-DSCCheckSum** cmdlet generates checksum files for PowerShell Desired State Configuration (DSC) documents and compressed DSC resources.</span></span>
<span data-ttu-id="0cfa0-109">Denna cmdlet skapar en kontroll Summa fil för varje konfiguration och resurs som ska användas i pull-läge.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-109">This cmdlet generates a checksum file for each configuration and resource to be used in pull mode.</span></span>
<span data-ttu-id="0cfa0-110">DSC-tjänsten använder kontroll summorna för att kontrol lera att rätt konfiguration och resurser finns på målnoden.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-110">The DSC service uses the checksums to make sure that the correct configuration and resources exist on the target node.</span></span>
<span data-ttu-id="0cfa0-111">Placera kontroll summorna tillsammans med tillhör ande DSC-dokument och komprimerade DSC-resurser i DSC-tjänstens arkiv.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-111">Place the checksums together with the associated DSC documents and compressed DSC resources in the DSC service store.</span></span>

## <span data-ttu-id="0cfa0-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0cfa0-112">EXAMPLES</span></span>

### <span data-ttu-id="0cfa0-113">Exempel 1: skapa kontroll Summa filer för alla konfigurationer i en angiven sökväg</span><span class="sxs-lookup"><span data-stu-id="0cfa0-113">Example 1: Create checksum files for all configurations in a specific path</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="0cfa0-114">Det här kommandot skapar en kontroll Summa filer för alla konfigurationer i sökvägen C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-114">This command creates checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="0cfa0-115">Alla filer för kontroll summor som redan finns hoppas över.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-115">Any checksum files that already exist are skipped.</span></span>

### <span data-ttu-id="0cfa0-116">Exempel 2: skapa kontroll Summa filer för alla konfigurationer i en angiven sökväg och skriv över de befintliga kontroll summor filerna</span><span class="sxs-lookup"><span data-stu-id="0cfa0-116">Example 2: Create checksum files for all configurations in a specific path and overwrite the existing checksum files</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

<span data-ttu-id="0cfa0-117">Det här kommandot skapar nya kontroll summor filer för alla konfigurationer i sökvägen C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-117">This command creates new checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="0cfa0-118">Om du anger *Force* -parametern kommer kommandot att skriva över alla eventuella kontroll Summa filer som redan finns.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-118">Specifying the *Force* parameter causes the command to overwrite any checksum files that already exist.</span></span>

## <span data-ttu-id="0cfa0-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0cfa0-119">PARAMETERS</span></span>

### <span data-ttu-id="0cfa0-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0cfa0-120">-Confirm</span></span>

<span data-ttu-id="0cfa0-121">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0cfa0-122">-Force</span><span class="sxs-lookup"><span data-stu-id="0cfa0-122">-Force</span></span>

<span data-ttu-id="0cfa0-123">Anger att cmdleten skriver över den angivna utdatafilen om den redan finns.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-123">Indicates that the cmdlet overwrites the specified output file if it already exists.</span></span>

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

### <span data-ttu-id="0cfa0-124">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="0cfa0-124">-OutPath</span></span>

<span data-ttu-id="0cfa0-125">Anger sökväg och fil namn för filen med utgångs kontroll.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-125">Specifies the path and file name of the output checksum file.</span></span>

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

### <span data-ttu-id="0cfa0-126">-Path</span><span class="sxs-lookup"><span data-stu-id="0cfa0-126">-Path</span></span>

<span data-ttu-id="0cfa0-127">Anger sökvägen till indatafilen.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-127">Specifies the path of the input file.</span></span>

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

### <span data-ttu-id="0cfa0-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0cfa0-128">-WhatIf</span></span>

<span data-ttu-id="0cfa0-129">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0cfa0-130">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0cfa0-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0cfa0-131">CommonParameters</span></span>

<span data-ttu-id="0cfa0-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0cfa0-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0cfa0-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0cfa0-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0cfa0-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="0cfa0-134">INPUTS</span></span>

### <span data-ttu-id="0cfa0-135">Inget</span><span class="sxs-lookup"><span data-stu-id="0cfa0-135">None</span></span>

## <span data-ttu-id="0cfa0-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0cfa0-136">OUTPUTS</span></span>

### <span data-ttu-id="0cfa0-137">System. Object</span><span class="sxs-lookup"><span data-stu-id="0cfa0-137">System.Object</span></span>

## <span data-ttu-id="0cfa0-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0cfa0-138">NOTES</span></span>

## <span data-ttu-id="0cfa0-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0cfa0-139">RELATED LINKS</span></span>

[<span data-ttu-id="0cfa0-140">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0cfa0-140">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)
