---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 5280ef5ff95679dc8721be8f5f81031a4ffe796f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085269"
---
# <a name="updates-to-fileinfo-object"></a>Uppdateringar till FileInfo-objektet
Kan vilseledande filversionsinformation särskilt i fall där filen var korrigeras. Den här versionen av WMF 5.0 lägger till nya **FileVersionRaw** och **ProductVersionRaw** skript egenskaper till FileInfo-objekt. Här är egenskaperna som visas för powershell.exe (förutsatt att $pid är ID för PowerShell-process):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
