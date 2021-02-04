---
ms.date: 01/25/2021
title: Felsöka cmdletar
description: Den här artikeln innehåller information och anvisningar för fel sökning av fel med hjälp av PowerShell-galleriet
ms.openlocfilehash: 8139147683b655b5f8532c3068387db6df12a98f
ms.sourcegitcommit: 0f003644684422e425a59b7361121e05ac772e15
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98771808"
---
# <a name="troubleshooting-cmdlets"></a>Felsöka cmdletar

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Så här löser du "varning! Package" ditt paket namn "Det gick inte att ladda ned" problem

Det rapporteras att `Install-Module` eller `Update-Module` ibland Miss lyckas på vissa datorer. Utifrån vår undersökning är det något att göra med nätverks anslutningen. Vi har nyligen uppdaterat NuGet-leverantören så att den kan ladda ned paket på ett tillförlitligt sätt. Du kan följa anvisningarna nedan om du vill installera den senaste versionen av NuGet-providern och sedan installera eller uppdatera modulen. Vi använder Azure-modulen som ett exempel nedan.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a>Nätverks slut punkter som krävs

Installations-och uppdaterings-cmdletarna kräver Internet åtkomst för att ansluta till de nätverks slut punkter som används av PowerShell-galleriet. Kontrol lera att nätverks åtkomst principerna tillåter att du ansluter till följande slut punkter.

- `psg-prod-eastus.azureedge.net` -CDN-värdnamn
- `az818661.vo.msecnd.net` -CDN-värdnamn
- `devopsgallerystorage.blob.core.windows.net` -lagrings kontots värdnamn
- `*.powershellgallery.com` – webbplats
- `go.microsoft.com` – omdirigerings tjänst
- `onegetcdn.azureedge.net` – Bootstrap NuGet-providern i `PowerShellGet/PackageManagement`

> [!NOTE]
> Cmdletar som interagerar med PowerShell-galleriet kan inte utföras med oväntade fel när PowerShell-galleriet tjänsterna har avbrottit. Om du vill se PowerShell-gallerietens aktuella status går du till sidan [PowerShell-galleriet status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) på GitHub.
