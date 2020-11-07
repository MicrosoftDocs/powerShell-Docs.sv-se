---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 007b486b7b65d9b6481839643fe839eda49a1113
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346963"
---
# <span data-ttu-id="06355-103">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="06355-103">New-FileCatalog</span></span>

## <span data-ttu-id="06355-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="06355-104">SYNOPSIS</span></span>
<span data-ttu-id="06355-105">`New-FileCatalog` skapar en katalog fil med filhashar som kan användas för att verifiera äktheten för en fil.</span><span class="sxs-lookup"><span data-stu-id="06355-105">`New-FileCatalog` creates a catalog file of file hashes that can be used to validate the authenticity of a file.</span></span>

## <span data-ttu-id="06355-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="06355-106">SYNTAX</span></span>

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="06355-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="06355-107">DESCRIPTION</span></span>

<span data-ttu-id="06355-108">`New-FileCatalog` skapar en [Windows Catalog-fil](/windows-hardware/drivers/install/catalog-files) för en uppsättning mappar och filer.</span><span class="sxs-lookup"><span data-stu-id="06355-108">`New-FileCatalog` creates a [Windows catalog file](/windows-hardware/drivers/install/catalog-files) for a set of folders and files.</span></span> <span data-ttu-id="06355-109">Den här katalog filen innehåller hash-värden för alla filer i de angivna Sök vägarna.</span><span class="sxs-lookup"><span data-stu-id="06355-109">This catalog file contains hashes for all files in the provided paths.</span></span> <span data-ttu-id="06355-110">Användarna kan sedan distribuera katalogen med sina filer så att användarna kan verifiera om några ändringar har gjorts i mapparna sedan katalog skapande tiden.</span><span class="sxs-lookup"><span data-stu-id="06355-110">Users can then distribute the catalog with their files so that users can validate whether any changes have been made to the folders since catalog creation time.</span></span>

<span data-ttu-id="06355-111">Katalog version 1 och 2 stöds.</span><span class="sxs-lookup"><span data-stu-id="06355-111">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="06355-112">Version 1 använder den (föråldrade) SHA1-hashalgoritmen för att skapa filhasher och version 2 använder SHA256.</span><span class="sxs-lookup"><span data-stu-id="06355-112">Version 1 uses the (deprecated) SHA1 hashing algorithm to create file hashes, and version 2 uses SHA256.</span></span> <span data-ttu-id="06355-113">Katalog version 2 stöds inte i Windows Server 2008 R2 eller Windows 7.</span><span class="sxs-lookup"><span data-stu-id="06355-113">Catalog version 2 is not supported on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="06355-114">Du bör använda katalog version 2 på Windows 8, Windows Server 2012 och senare operativ system.</span><span class="sxs-lookup"><span data-stu-id="06355-114">You should use catalog version 2 on Windows 8, Windows Server 2012, and later operating systems.</span></span>

## <span data-ttu-id="06355-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="06355-115">EXAMPLES</span></span>

### <span data-ttu-id="06355-116">Exempel 1: skapa en fil katalog för `Microsoft.PowerShell.Utility`</span><span class="sxs-lookup"><span data-stu-id="06355-116">Example 1: Create a file catalog for `Microsoft.PowerShell.Utility`</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## <span data-ttu-id="06355-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="06355-117">PARAMETERS</span></span>

### <span data-ttu-id="06355-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="06355-118">-CatalogFilePath</span></span>

<span data-ttu-id="06355-119">En sökväg till en fil eller mapp där katalog filen (. cat) ska placeras.</span><span class="sxs-lookup"><span data-stu-id="06355-119">A path to a file or folder where the catalog file (.cat) should be placed.</span></span> <span data-ttu-id="06355-120">Om en mappsökväg anges används standard fil namnet `catalog.cat` .</span><span class="sxs-lookup"><span data-stu-id="06355-120">If a folder path is specified, the default filename `catalog.cat` will be used.</span></span>

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

### <span data-ttu-id="06355-121">-CatalogVersion</span><span class="sxs-lookup"><span data-stu-id="06355-121">-CatalogVersion</span></span>

<span data-ttu-id="06355-122">Accepterar `1.0` eller `2.0` som möjliga värden för att ange katalog versionen.</span><span class="sxs-lookup"><span data-stu-id="06355-122">Accepts `1.0` or `2.0` as possible values for specifying the catalog version.</span></span> <span data-ttu-id="06355-123">`1.0` bör undvikas när det är möjligt, eftersom det använder sig av den oskyddade SHA-1-hashalgoritmen, medan använder sig av `2.0` Secure SHA-1 256-algoritmen, men `1.0` är den enda algoritm som stöds på Windows 7 och Server 2008R2.</span><span class="sxs-lookup"><span data-stu-id="06355-123">`1.0` should be used avoided whenever possible, as it uses the insecure SHA-1 hash algorithm, while `2.0` uses the secure SHA-256 algorithm However, `1.0` is the only supported algorithm on Windows 7 and Server 2008R2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="06355-124">-Path</span><span class="sxs-lookup"><span data-stu-id="06355-124">-Path</span></span>

<span data-ttu-id="06355-125">Accepterar en sökväg eller en matris med sökvägar till filer eller mappar som ska ingå i katalog filen.</span><span class="sxs-lookup"><span data-stu-id="06355-125">Accepts a path or array of paths to files or folders that should be included in the catalog file.</span></span> <span data-ttu-id="06355-126">Om en mapp anges tas även alla filer i mappen med.</span><span class="sxs-lookup"><span data-stu-id="06355-126">If a folder is specified, all the files in the folder will be included as well.</span></span>

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

### <span data-ttu-id="06355-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="06355-127">-Confirm</span></span>

<span data-ttu-id="06355-128">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="06355-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="06355-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="06355-129">-WhatIf</span></span>

<span data-ttu-id="06355-130">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="06355-130">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="06355-131">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="06355-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="06355-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="06355-132">CommonParameters</span></span>

<span data-ttu-id="06355-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="06355-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="06355-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="06355-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="06355-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="06355-135">INPUTS</span></span>

### <span data-ttu-id="06355-136">System. String</span><span class="sxs-lookup"><span data-stu-id="06355-136">System.String</span></span>

<span data-ttu-id="06355-137">Pipelinen tar en sträng som används som katalog fil namn.</span><span class="sxs-lookup"><span data-stu-id="06355-137">The pipeline takes a string that is used as the catalog filename.</span></span>

## <span data-ttu-id="06355-138">UTDATA</span><span class="sxs-lookup"><span data-stu-id="06355-138">OUTPUTS</span></span>

### <span data-ttu-id="06355-139">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="06355-139">System.IO.FileInfo</span></span>

## <span data-ttu-id="06355-140">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="06355-140">NOTES</span></span>

<span data-ttu-id="06355-141">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="06355-141">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="06355-142">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="06355-142">RELATED LINKS</span></span>

[<span data-ttu-id="06355-143">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="06355-143">Test-FileCatalog</span></span>](Test-FileCatalog.md)

[<span data-ttu-id="06355-144">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="06355-144">PowerShellGet</span></span>](/powerShell/module/powershellget)
