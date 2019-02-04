---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688527"
---
# <a name="uninstallation-instructions"></a>Anvisningar för avinstallation

## <a name="using-command-prompt"></a>Med hjälp av Kommandotolken
1.  Öppna **Kommandotolken.**
2.  Kör den [Windows Update fristående starta](https://support.microsoft.com/en-us/kb/934307) enligt nedan:

På Windows Server 2012 R2 och Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
På Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
På Windows Server 2008 R2 SP1 och Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>Med hjälp av Kontrollpanelen
1.  Öppna **Kontrollpanelen.**
2.  Öppna **program**, öppna sedan **avinstallera ett program.**
3.  Klicka på **Visa installerade uppdateringar.**
4.  Välj **Windows Management Framework 5.0** i listan över installerade uppdateringar. Detta motsvarar *KB3134758*, *KB3134759*, eller *KB3134760*. Klicka på **avinstallera.**
