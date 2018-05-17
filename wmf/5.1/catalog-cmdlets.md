---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Katalog-cmdletar
ms.openlocfilehash: 7eaca09667af0eb5d719f23e987bb112e8514978
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="catalog-cmdlets"></a>Katalog-Cmdlets

Vi har lagt till två nya cmdlet: ar i [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) modul som ska generera och verifiera filer för windows-katalogen.

## <a name="new-filecatalog"></a>Ny FileCatalog
--------------------------------

`New-FileCatalog` skapar en windows-katalogfil för mappar och filer. En katalogfil innehåller hashvärden för alla filer i angiven sökväg. Användarna kan distribuera mapparna tillsammans med motsvarande katalogfil som representerar mapparna. En katalogfil kan användas av mottagaren av innehållet om några ändringar har gjorts till mapparna efter katalogen skapades.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Vi stöder skapar katalogversion 1 och 2. Version 1 används SHA1 hash-algoritm för att skapa filhash och version 2 används SHA256. Katalogversion 2 stöds inte på *Windows Server 2008 R2* och *Windows 7*. Det rekommenderas att använda katalogversion 2 om använder plattformar *Windows 8*, *Windows Server 2012* och högre.

Ange variablerna CatalogFilePath och sökvägen för att matcha sökvägen till modulmanifestet om du vill använda det här kommandot på en befintlig modul. I exemplet nedan är modulmanifestet i C:\Program Files\Windows PowerShell\Modules\Pester.

![](../images/NewFileCatalog.jpg)

Då skapas katalogfilen.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

För att verifiera integriteten hos en katalogfil (Pester.cat i ovan exmaple) bör den signeras med den [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.


## <a name="test-filecatalog"></a>Testa FileCatalog
--------------------------------

`Test-FileCatalog` verifierar katalogen som representerar en uppsättning mappar.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Denna cmdlet jämför hash-värden för alla filer och deras relativa sökvägar som hittades i katalogfilen med de som sparas till disk. Om den identifierar eventuella matchningsfel mellan värden och sökvägar returneras statusen `ValidationFailed`.
Användare kan hämta alla den här informationen med hjälp av den `Detailed` växla. Katalogen signering status visas som den `Signature` fältet, som är samma som anropar den [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet på katalogfilen.
Användare kan också hoppa över en fil vid verifiering av med hjälp av den `FilesToSkip` parameter.
