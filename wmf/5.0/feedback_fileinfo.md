---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 587f3f592f4aab53c95bbc6d37ea37d7f2364aec
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="updates-to-fileinfo-object"></a>Uppdateringar till FileInfo objekt
Filversionsinformation kan vilseledande särskilt i fall där filen var korrigeras. Den här versionen av WMF 5.0 lägger till nya **FileVersionRaw** och **ProductVersionRaw** skript egenskaper FileInfo objekt. Här är egenskaperna som visas för powershell.exe (förutsatt att $pid är det PowerShell-process-ID):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117

