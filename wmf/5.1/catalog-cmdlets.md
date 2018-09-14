---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Katalog-cmdletar
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522896"
---
# <a name="catalog-cmdlets"></a>Katalog-cmdletar

Vi har lagt till två nya-cmdlets i [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) modul för att generera och verifiera windows catalog-filer.

## <a name="new-filecatalog"></a>Ny FileCatalog
--------------------------------

`New-FileCatalog` skapar en windows-katalogfil för mappar och filer. En katalogfil innehåller hashvärden för alla filer i angiven sökväg. Användare kan distribuera mapparna tillsammans med motsvarande katalogfilen som representerar dessa mappar. En katalogfil kan användas av mottagaren av innehållet för att kontrollera om några ändringar har gjorts till mapparna när katalogen har skapats.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Vi stöder skapa katalogversion 1 och 2. Version 1 används SHA1 hash-algoritm för att skapa värden och version 2 används SHA256. Katalogversion 2 stöds inte på *Windows Server 2008 R2* och *Windows 7*. Det rekommenderas att använda katalogversion 2 om du använder plattformar *Windows 8*, *Windows Server 2012* och senare.

Ange variablerna CatalogFilePath och sökvägen för att matcha platsen för modulmanifestet om du vill använda det här kommandot på en befintlig modul. I exemplet nedan är modulmanifestet i C:\Program Files\Windows PowerShell\Modules\Pester.

![](../images/NewFileCatalog.jpg)

Detta skapar katalogfilen.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

För att verifiera integriteten hos en katalogfil (Pester.cat i ovan exemplet) måste den signeras med den [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.


## <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

`Test-FileCatalog` verifierar katalogen som representerar en uppsättning mappar.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Denna cmdlet jämför hash-värden för alla filer och deras relativa sökvägar hittades i katalogfilen med de som sparas till disk. Om den identifierar eventuella matchningsfel mellan värden och sökvägar returnerar statusvärdet `ValidationFailed`.
Användare kan hämta alla den här informationen med hjälp av den `Detailed` växla. Signering av katalogen visas som den `Signature` fält som är samma som anropar den [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdleten på katalogfilen.
Användare kan även hoppa över alla filer under verifieringen genom att använda den `FilesToSkip` parametern.
