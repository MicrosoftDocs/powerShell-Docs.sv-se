---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Avinstallera WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145217"
---
# <a name="uninstallation-instructions"></a>Avinstallations anvisningar

## <a name="using-command-prompt"></a>Använda kommando tolken

1. Öppna **kommando tolken.**
2. Kör [Windows Update fristående start](https://support.microsoft.com/en-us/kb/934307) programmet som det visas nedan:

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
