---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Avinstallera WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856191"
---
# <a name="uninstallation-instructions"></a>Anvisningar för avinstallation

## <a name="using-command-prompt"></a>Med hjälp av Kommandotolken

1. Öppna **Kommandotolken.**
2. Kör den [Windows Update fristående starta](https://support.microsoft.com/en-us/kb/934307) enligt nedan:

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

1. Öppna **Kontrollpanelen.**
2. Öppna **program**, öppna sedan **avinstallera ett program.**
3. Klicka på **Visa installerade uppdateringar.**
4. Välj **Windows Management Framework 5.0** i listan över installerade uppdateringar. Detta motsvarar *KB3134758*, *KB3134759*, eller *KB3134760*. Klicka på **avinstallera.**
