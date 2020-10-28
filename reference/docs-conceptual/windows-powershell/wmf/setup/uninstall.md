---
ms.date: 06/12/2017
title: Avinstallera WMF 5.0
description: Den här artikeln förklarar hur du avinstallerar WMF från äldre versioner av Windows.
ms.openlocfilehash: d8078ea918db2c1cf9a7ddd6ea8d1413b593c0ff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660806"
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
2. Öppna **program** och öppna sedan **Avinstallera ett program.**
3. Klicka på **Visa installerade uppdateringar.**
4. Välj **Windows Management Framework 5,0** i listan över installerade uppdateringar. Detta motsvarar *KB3134758* , *KB3134759* eller *KB3134760* . Klicka på **Avinstallera.**
