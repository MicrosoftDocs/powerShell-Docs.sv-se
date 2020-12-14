---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 7de62dbdef9d31a100042bb5a037f0486acfaa71
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709115"
---
# <span data-ttu-id="b8be0-102">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b8be0-102">Test-FileCatalog</span></span>

## <span data-ttu-id="b8be0-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b8be0-103">SYNOPSIS</span></span>
<span data-ttu-id="b8be0-104">`Test-FileCatalog` verifierar om hash-värdena i en katalog fil (. cat) matchar hasharna för de faktiska filerna för att verifiera deras äkthet.</span><span class="sxs-lookup"><span data-stu-id="b8be0-104">`Test-FileCatalog` validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

<span data-ttu-id="b8be0-105">Denna cmdlet stöds bara i Windows.</span><span class="sxs-lookup"><span data-stu-id="b8be0-105">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="b8be0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8be0-106">SYNTAX</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b8be0-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b8be0-107">DESCRIPTION</span></span>

<span data-ttu-id="b8be0-108">`Test-FileCatalog` verifierar filens äkthet genom att jämföra hash-filerna för en katalog fil (. cat) med hash-värdena för faktiska filer på disk.</span><span class="sxs-lookup"><span data-stu-id="b8be0-108">`Test-FileCatalog` validates the authenticity of files by comparing the file hashes of a catalog file (.cat) with the hashes of actual files on disk.</span></span> <span data-ttu-id="b8be0-109">Om det upptäcker eventuella avvikelser returneras statusen som ValidationFailed.</span><span class="sxs-lookup"><span data-stu-id="b8be0-109">If it detects any mismatches, it returns the status as ValidationFailed.</span></span> <span data-ttu-id="b8be0-110">Användare kan hämta all den här informationen med hjälp av parametern-detaljerad.</span><span class="sxs-lookup"><span data-stu-id="b8be0-110">Users can retrieve all this information by using the -Detailed parameter.</span></span> <span data-ttu-id="b8be0-111">Den visar också signerings status för katalogen i egenskapen signatur som motsvarar anrop av `Get-AuthenticodeSignature` cmdleten i katalog filen.</span><span class="sxs-lookup"><span data-stu-id="b8be0-111">It also displays signing status of catalog in Signature property which is equivalent to calling `Get-AuthenticodeSignature` cmdlet on the catalog file.</span></span> <span data-ttu-id="b8be0-112">Användare kan även hoppa över alla filer under valideringen med hjälp av parametern-FilesToSkip.</span><span class="sxs-lookup"><span data-stu-id="b8be0-112">Users can also skip any file during validation by using the -FilesToSkip parameter.</span></span>

<span data-ttu-id="b8be0-113">Denna cmdlet stöds bara i Windows.</span><span class="sxs-lookup"><span data-stu-id="b8be0-113">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="b8be0-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b8be0-114">EXAMPLES</span></span>

### <span data-ttu-id="b8be0-115">Exempel 1: skapa och validera en fil katalog</span><span class="sxs-lookup"><span data-stu-id="b8be0-115">Example 1: Create and validate a file catalog</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### <span data-ttu-id="b8be0-116">Exempel 2: verifiera en fil katalog med detaljerade utdata</span><span class="sxs-lookup"><span data-stu-id="b8be0-116">Example 2: Validate a file catalog with detailed output</span></span>

```powershell
Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
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

## <span data-ttu-id="b8be0-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b8be0-117">PARAMETERS</span></span>

### <span data-ttu-id="b8be0-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="b8be0-118">-CatalogFilePath</span></span>

<span data-ttu-id="b8be0-119">En sökväg till en katalog fil (. cat) som innehåller de hashar som ska användas för verifiering.</span><span class="sxs-lookup"><span data-stu-id="b8be0-119">A path to a catalog file (.cat) that contains the hashes to be used for validation.</span></span>

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

### <span data-ttu-id="b8be0-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b8be0-120">-Confirm</span></span>

<span data-ttu-id="b8be0-121">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b8be0-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b8be0-122">-Detaljerad</span><span class="sxs-lookup"><span data-stu-id="b8be0-122">-Detailed</span></span>

<span data-ttu-id="b8be0-123">Returnerar mer information ett mer detaljerat `CatalogInformation` objekt som innehåller de testade filerna, deras förväntade/faktiska hash-värden och en Authenticode-signatur i katalog filen om den är signerad.</span><span class="sxs-lookup"><span data-stu-id="b8be0-123">Returns more information a more detailed `CatalogInformation` object that contains the files tested, their expected/actual hashes, and an Authenticode signature of the catalog file if it's signed.</span></span>

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

### <span data-ttu-id="b8be0-124">-FilesToSkip</span><span class="sxs-lookup"><span data-stu-id="b8be0-124">-FilesToSkip</span></span>

<span data-ttu-id="b8be0-125">En matris med sökvägar som inte ska testas som en del av verifieringen.</span><span class="sxs-lookup"><span data-stu-id="b8be0-125">An array of paths that should not be tested as part of the validation.</span></span>

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

### <span data-ttu-id="b8be0-126">-Path</span><span class="sxs-lookup"><span data-stu-id="b8be0-126">-Path</span></span>

<span data-ttu-id="b8be0-127">En mapp eller en matris med filer som ska val IDE ras mot katalog filen.</span><span class="sxs-lookup"><span data-stu-id="b8be0-127">A folder or array of files that should be validated against the catalog file.</span></span>

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

### <span data-ttu-id="b8be0-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b8be0-128">-WhatIf</span></span>

<span data-ttu-id="b8be0-129">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="b8be0-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b8be0-130">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b8be0-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b8be0-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8be0-131">CommonParameters</span></span>

<span data-ttu-id="b8be0-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b8be0-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8be0-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b8be0-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b8be0-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="b8be0-134">INPUTS</span></span>

### <span data-ttu-id="b8be0-135">System. IO. DirectoryInfo [], system. string []</span><span class="sxs-lookup"><span data-stu-id="b8be0-135">System.IO.DirectoryInfo[], System.String[]</span></span>

<span data-ttu-id="b8be0-136">Pipelinen accepterar en matris med strängar eller `DirectoryInfo` objekt som representerar sökvägar till de filer som behöver verifieras.</span><span class="sxs-lookup"><span data-stu-id="b8be0-136">The pipeline accepts an array of strings or `DirectoryInfo` objects that represent paths to the files that need to be validated.</span></span>

## <span data-ttu-id="b8be0-137">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b8be0-137">OUTPUTS</span></span>

### <span data-ttu-id="b8be0-138">System. Management. Automation. CatalogValidationStatus</span><span class="sxs-lookup"><span data-stu-id="b8be0-138">System.Management.Automation.CatalogValidationStatus</span></span>

<span data-ttu-id="b8be0-139">Standard retur typen som innehåller värdet antingen `Valid` eller `ValidationFailed` .</span><span class="sxs-lookup"><span data-stu-id="b8be0-139">The default return type containing a value of either `Valid` or `ValidationFailed`.</span></span>

### <span data-ttu-id="b8be0-140">System. Management. Automation. CatalogInformation</span><span class="sxs-lookup"><span data-stu-id="b8be0-140">System.Management.Automation.CatalogInformation</span></span>

<span data-ttu-id="b8be0-141">Ett mer detaljerat objekt som returneras när `-Detailed` du använder som kan användas för att analysera särskilda filer som kanske inte har godkänts av verifiering, vilka hash-värden som förväntades jämfört med och upptäcktes, och algoritmen som används i katalogen.</span><span class="sxs-lookup"><span data-stu-id="b8be0-141">A more detailed object returned when using `-Detailed` which can be used to analyze specific files that may or may not have passed validation, which hashes were expected vs. found, and the algorithm used in the catalog.</span></span>

## <span data-ttu-id="b8be0-142">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b8be0-142">NOTES</span></span>

<span data-ttu-id="b8be0-143">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="b8be0-143">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="b8be0-144">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b8be0-144">RELATED LINKS</span></span>

[<span data-ttu-id="b8be0-145">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b8be0-145">New-FileCatalog</span></span>](New-FileCatalog.md)

[<span data-ttu-id="b8be0-146">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="b8be0-146">PowerShellGet</span></span>](/powershell/module/PowerShellGet)
