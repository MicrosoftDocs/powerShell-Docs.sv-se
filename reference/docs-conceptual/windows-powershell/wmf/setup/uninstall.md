---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Avinstallera WMF 5.0
ms.openlocfilehash: fa76bacb4b62025d0d2350b9a0e072068ca83ab1
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236313"
---
# <a name="uninstallation-instructions"></a>Avinstallations anvisningar

## <a name="using-command-prompt"></a>Använda kommando tolken

1. Öppna **kommando tolken.**
2. Kör [Windows Update fristående start](https://support.microsoft.com/kb/934307) programmet som det visas nedan:

På Windows Server 2012 R2 och Windows 8,1:

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

## <a name="using-control-panel"></a>Använda kontroll panelen

1. Öppna **kontroll panelen.**
2. Öppna **program**och öppna sedan **Avinstallera ett program.**
3. Klicka på **Visa installerade uppdateringar.**
4. Välj **Windows Management Framework 5,0** i listan över installerade uppdateringar. Detta motsvarar *KB3134758*, *KB3134759*eller *KB3134760*. Klicka på **Avinstallera.**
