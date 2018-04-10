---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 6356902193fc6ec651b2f7e53f8885cb59f17542
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="updates-to-fileinfo-object"></a>Uppdateringar till FileInfo-objektet
Filversionsinformation kan vilseledande särskilt i fall där filen var korrigeras. Den här versionen av WMF 5.0 lägger till nya **FileVersionRaw** och **ProductVersionRaw** skript egenskaper FileInfo objekt. Här är egenskaperna som visas för powershell.exe (förutsatt att $pid är det PowerShell-process-ID):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117