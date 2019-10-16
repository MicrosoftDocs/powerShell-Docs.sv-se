---
ms.date: 06/12/2017
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Felsöka cmdletar
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352116"
---
# <a name="troubleshooting-cmdlets"></a>Felsöka cmdletar

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Så här löser du "varning! Package" ditt paket namn "Det gick inte att ladda ned" problem

Det rapporteras att `Install-Module` eller `Update-Module` ibland Miss lyckas på vissa datorer. Utifrån vår undersökning är det något att göra med nätverks anslutningen. Vi har nyligen uppdaterat NuGet-leverantören så att den kan ladda ned paket på ett tillförlitligt sätt. Du kan följa anvisningarna nedan om du vill installera den senaste versionen av NuGet-providern och sedan installera eller uppdatera modulen. Vi använder Azure-modulen som ett exempel nedan.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a>Nätverks slut punkter som krävs

Installations-och uppdaterings-cmdletarna kräver Internet åtkomst för att ansluta till de nätverks slut punkter som används av PowerShell-galleriet. Kontrol lera att nätverks åtkomst principerna tillåter att du ansluter till följande slut punkter.

- oneget.org
- go.microsoft.com
- az818661.vo.msecnd.net
- www.powershellgallery.com
- devopsgallerystorage.blob.core.windows.net
