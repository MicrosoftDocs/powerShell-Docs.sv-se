---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222062"
---
# <a name="uninstallation-instructions"></a>Anvisningar för avinstallation

## <a name="using-command-prompt"></a>Med hjälp av Kommandotolken
1.  Öppna **kommandotolk.**
2.  Kör den [Windows Update fristående programstart](https://support.microsoft.com/en-us/kb/934307) enligt nedan:

På Windows Server 2012 R2 och Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
I Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
På Windows Server 2008 R2 SP1 och Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>Med hjälp av Kontrollpanelen
1.  Öppna **Kontrollpanelen.**
2.  Öppna **program**sedan öppnar **avinstallera ett program.**
3.  Klicka på **Visa installerade uppdateringar.**
4.  Välj **Windows Management Framework 5.0** från listan över installerade uppdateringar. Detta motsvarar *KB3134758*, *KB3134759*, eller *KB3134760*. Klicka på **avinstallera.**
