---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: e42bc3d5e13f564a49e811d5a822912f72f5f1c0
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490745"
---
# <span data-ttu-id="baaa2-103">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="baaa2-103">Test-FileCatalog</span></span>

## <span data-ttu-id="baaa2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="baaa2-104">SYNOPSIS</span></span>
<span data-ttu-id="baaa2-105">`Test-FileCatalog` verifierar om hash-värdena i en katalog fil (. cat) matchar hasharna för de faktiska filerna för att verifiera deras äkthet.</span><span class="sxs-lookup"><span data-stu-id="baaa2-105">`Test-FileCatalog` validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

<span data-ttu-id="baaa2-106">Denna cmdlet stöds bara i Windows.</span><span class="sxs-lookup"><span data-stu-id="baaa2-106">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="baaa2-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="baaa2-107">SYNTAX</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="baaa2-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="baaa2-108">DESCRIPTION</span></span>

<span data-ttu-id="baaa2-109">`Test-FileCatalog` verifierar filens äkthet genom att jämföra hash-filerna för en katalog fil (. cat) med hash-värdena för faktiska filer på disk.</span><span class="sxs-lookup"><span data-stu-id="baaa2-109">`Test-FileCatalog` validates the authenticity of files by comparing the file hashes of a catalog file (.cat) with the hashes of actual files on disk.</span></span> <span data-ttu-id="baaa2-110">Om det upptäcker eventuella avvikelser returneras statusen som ValidationFailed.</span><span class="sxs-lookup"><span data-stu-id="baaa2-110">If it detects any mismatches, it returns the status as ValidationFailed.</span></span> <span data-ttu-id="baaa2-111">Användare kan hämta all den här informationen med hjälp av parametern-detaljerad.</span><span class="sxs-lookup"><span data-stu-id="baaa2-111">Users can retrieve all this information by using the -Detailed parameter.</span></span> <span data-ttu-id="baaa2-112">Den visar också signerings status för katalogen i egenskapen signatur som motsvarar anrop av `Get-AuthenticodeSignature` cmdleten i katalog filen.</span><span class="sxs-lookup"><span data-stu-id="baaa2-112">It also displays signing status of catalog in Signature property which is equivalent to calling `Get-AuthenticodeSignature` cmdlet on the catalog file.</span></span> <span data-ttu-id="baaa2-113">Användare kan även hoppa över alla filer under valideringen med hjälp av parametern-FilesToSkip.</span><span class="sxs-lookup"><span data-stu-id="baaa2-113">Users can also skip any file during validation by using the -FilesToSkip parameter.</span></span>

<span data-ttu-id="baaa2-114">Denna cmdlet stöds bara i Windows.</span><span class="sxs-lookup"><span data-stu-id="baaa2-114">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="baaa2-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="baaa2-115">EXAMPLES</span></span>

### <span data-ttu-id="baaa2-116">Exempel 1: skapa och validera en fil katalog</span><span class="sxs-lookup"><span data-stu-id="baaa2-116">Example 1: Create and validate a file catalog</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### <span data-ttu-id="baaa2-117">Exempel 2: verifiera en fil katalog med detaljerade utdata</span><span class="sxs-lookup"><span data-stu-id="baaa2-117">Example 2: Validate a file catalog with detailed output</span></span>

```powershell
Test-FileCatalog -Detailed -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## <span data-ttu-id="baaa2-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="baaa2-118">PARAMETERS</span></span>

### <span data-ttu-id="baaa2-119">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="baaa2-119">-CatalogFilePath</span></span>

<span data-ttu-id="baaa2-120">En sökväg till en katalog fil (. cat) som innehåller de hashar som ska användas för verifiering.</span><span class="sxs-lookup"><span data-stu-id="baaa2-120">A path to a catalog file (.cat) that contains the hashes to be used for validation.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="baaa2-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="baaa2-121">-Confirm</span></span>

<span data-ttu-id="baaa2-122">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="baaa2-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="baaa2-123">-Detaljerad</span><span class="sxs-lookup"><span data-stu-id="baaa2-123">-Detailed</span></span>

<span data-ttu-id="baaa2-124">Returnerar mer information ett mer detaljerat `CatalogInformation` objekt som innehåller de testade filerna, deras förväntade/faktiska hash-värden och en Authenticode-signatur i katalog filen om den är signerad.</span><span class="sxs-lookup"><span data-stu-id="baaa2-124">Returns more information a more detailed `CatalogInformation` object that contains the files tested, their expected/actual hashes, and an Authenticode signature of the catalog file if it's signed.</span></span>

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

### <span data-ttu-id="baaa2-125">-FilesToSkip</span><span class="sxs-lookup"><span data-stu-id="baaa2-125">-FilesToSkip</span></span>

<span data-ttu-id="baaa2-126">En matris med sökvägar som inte ska testas som en del av verifieringen.</span><span class="sxs-lookup"><span data-stu-id="baaa2-126">An array of paths that should not be tested as part of the validation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="baaa2-127">-Path</span><span class="sxs-lookup"><span data-stu-id="baaa2-127">-Path</span></span>

<span data-ttu-id="baaa2-128">En mapp eller en matris med filer som ska val IDE ras mot katalog filen.</span><span class="sxs-lookup"><span data-stu-id="baaa2-128">A folder or array of files that should be validated against the catalog file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="baaa2-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="baaa2-129">-WhatIf</span></span>

<span data-ttu-id="baaa2-130">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="baaa2-130">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="baaa2-131">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="baaa2-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="baaa2-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="baaa2-132">CommonParameters</span></span>

<span data-ttu-id="baaa2-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="baaa2-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="baaa2-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="baaa2-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="baaa2-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="baaa2-135">INPUTS</span></span>

### <span data-ttu-id="baaa2-136">System. IO. DirectoryInfo [], system. string []</span><span class="sxs-lookup"><span data-stu-id="baaa2-136">System.IO.DirectoryInfo[], System.String[]</span></span>

<span data-ttu-id="baaa2-137">Pipelinen accepterar en matris med strängar eller `DirectoryInfo` objekt som representerar sökvägar till de filer som behöver verifieras.</span><span class="sxs-lookup"><span data-stu-id="baaa2-137">The pipeline accepts an array of strings or `DirectoryInfo` objects that represent paths to the files that need to be validated.</span></span>

## <span data-ttu-id="baaa2-138">UTDATA</span><span class="sxs-lookup"><span data-stu-id="baaa2-138">OUTPUTS</span></span>

### <span data-ttu-id="baaa2-139">System. Management. Automation. CatalogValidationStatus</span><span class="sxs-lookup"><span data-stu-id="baaa2-139">System.Management.Automation.CatalogValidationStatus</span></span>

<span data-ttu-id="baaa2-140">Standard retur typen som innehåller värdet antingen `Valid` eller `ValidationFailed` .</span><span class="sxs-lookup"><span data-stu-id="baaa2-140">The default return type containing a value of either `Valid` or `ValidationFailed`.</span></span>

### <span data-ttu-id="baaa2-141">System. Management. Automation. CatalogInformation</span><span class="sxs-lookup"><span data-stu-id="baaa2-141">System.Management.Automation.CatalogInformation</span></span>

<span data-ttu-id="baaa2-142">Ett mer detaljerat objekt som returneras när `-Detailed` du använder som kan användas för att analysera särskilda filer som kanske inte har godkänts av verifiering, vilka hash-värden som förväntades jämfört med och upptäcktes, och algoritmen som används i katalogen.</span><span class="sxs-lookup"><span data-stu-id="baaa2-142">A more detailed object returned when using `-Detailed` which can be used to analyze specific files that may or may not have passed validation, which hashes were expected vs. found, and the algorithm used in the catalog.</span></span>

## <span data-ttu-id="baaa2-143">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="baaa2-143">NOTES</span></span>

## <span data-ttu-id="baaa2-144">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="baaa2-144">RELATED LINKS</span></span>

[<span data-ttu-id="baaa2-145">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="baaa2-145">New-FileCatalog</span></span>](New-FileCatalog.md)

[<span data-ttu-id="baaa2-146">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="baaa2-146">PowerShellGet</span></span>](/powershell/module/PowerShellGet)
