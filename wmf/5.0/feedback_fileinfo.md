---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="updates-to-fileinfo-object"></a>Uppdateringar till FileInfo-objektet
Filversionsinformation kan vilseledande särskilt i fall där filen var korrigeras. Den här versionen av WMF 5.0 lägger till nya **FileVersionRaw** och **ProductVersionRaw** skript egenskaper FileInfo objekt. Här är egenskaperna som visas för powershell.exe (förutsatt att $pid är det PowerShell-process-ID):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
