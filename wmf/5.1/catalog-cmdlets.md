---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Katalog-cmdletar
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057662"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="6f0a1-103">Katalog-cmdletar</span><span class="sxs-lookup"><span data-stu-id="6f0a1-103">Catalog Cmdlets</span></span>

<span data-ttu-id="6f0a1-104">Vi har lagt till två nya-cmdlets i [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) modul för att generera och verifiera windows catalog-filer.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="6f0a1-105">Ny FileCatalog</span><span class="sxs-lookup"><span data-stu-id="6f0a1-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="6f0a1-106">`New-FileCatalog` skapar en windows-katalogfil för mappar och filer.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="6f0a1-107">En katalogfil innehåller hashvärden för alla filer i angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="6f0a1-108">Användare kan distribuera mapparna tillsammans med motsvarande katalogfilen som representerar dessa mappar.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="6f0a1-109">En katalogfil kan användas av mottagaren av innehållet för att kontrollera om några ändringar har gjorts till mapparna när katalogen har skapats.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="6f0a1-110">Vi stöder skapa katalogversion 1 och 2.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="6f0a1-111">Version 1 används SHA1 hash-algoritm för att skapa värden och version 2 används SHA256.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="6f0a1-112">Katalogversion 2 stöds inte på *Windows Server 2008 R2* och *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="6f0a1-113">Det rekommenderas att använda katalogversion 2 om du använder plattformar *Windows 8*, *Windows Server 2012* och senare.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="6f0a1-114">Ange variablerna CatalogFilePath och sökvägen för att matcha platsen för modulmanifestet om du vill använda det här kommandot på en befintlig modul.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="6f0a1-115">I exemplet nedan är modulmanifestet i C:\Program Files\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="6f0a1-116">Detta skapar katalogfilen.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="6f0a1-117">För att verifiera integriteten hos en katalogfil (Pester.cat i ovan exemplet) måste den signeras med den [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="6f0a1-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="6f0a1-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="6f0a1-119">`Test-FileCatalog` verifierar katalogen som representerar en uppsättning mappar.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="6f0a1-120">Denna cmdlet jämför hash-värden för alla filer och deras relativa sökvägar hittades i katalogfilen med de som sparas till disk.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="6f0a1-121">Om den identifierar eventuella matchningsfel mellan värden och sökvägar returnerar statusvärdet `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="6f0a1-122">Användare kan hämta alla den här informationen med hjälp av den `Detailed` växla.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="6f0a1-123">Signering av katalogen visas som den `Signature` fält som är samma som anropar den [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdleten på katalogfilen.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="6f0a1-124">Användare kan även hoppa över alla filer under verifieringen genom att använda den `FilesToSkip` parametern.</span><span class="sxs-lookup"><span data-stu-id="6f0a1-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
