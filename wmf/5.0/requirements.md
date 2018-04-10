---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 7e24bb4ee4d0658b0619f7f008e3740f647f124f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="system-requirements"></a>Systemkrav

- Installera de senaste uppdateringarna för Windows innan du installerar WMF 5.0 RTM.
- Du kan installera WMF 5.0 RTM för endast för följande operativsystem:

    | Operativsystem       | Versioner         | Förutsättningar        |  Package länkar |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 SP1 | Alla utom IA64 | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) och [.NET Framework 4.5 eller senare](https://msdn.microsoft.com/library/5a4x27ek.aspx) är installerade| [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | Pro, Enterprise | | **x64:**  [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86:**  [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 SP1 | Alla | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) och [.NET Framework 4.5 eller senare](https://msdn.microsoft.com/library/5a4x27ek.aspx) är installerade | **x64:**  [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86:**  [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962)|

# <a name="installation-instructions"></a>Instruktioner för installation

### <a name="to-install-wmf-50-from-windows-explorer-or-file-explorer"></a>Installera WMF 5.0 från Utforskaren i Windows (eller Utforskaren):

1. Navigera till mappen dit du hämtade MSU-fil.

2. Dubbelklicka på MSU att köra den.

### <a name="to-install-wmf-50-from-command-prompt"></a>Installera WMF 5.0 från kommandoraden:

1. När du har hämtat rätt paket för datorns arkitektur, öppna ett kommandotolksfönster med utökade användarrättigheter (Kör som administratör). På installationsalternativet Server Core av Windows Server 2012 R2 eller Windows Server 2012 eller Windows Server 2008 R2 SP1 öppnas kommandotolk med förhöjd behörighet som standard.

2. Ändra sökvägen till mappen som du har hämtat eller kopierat WMF 5.0 installationspaketet.

3. Kör något av följande kommandon:
    - Kör på datorer som kör Windows Server 2012 R2 eller Windows 8.1 x64 **Win8.1AndW2K12R2-KB3134758-x64.msu/quiet**.
    - Kör på datorer som kör Windows Server 2012 **W2K12-KB3134759-x64.msu/quiet**.
    - Kör på datorer som kör Windows Server 2008 R2 SP1 eller Windows 7 SP1 x 64, **Win7AndW2K8R2-KB3134760-x64.msu/quiet**.
    - Kör på datorer som kör Windows 8.1 x86 **Win8.1-KB3134758-x86.msu/quiet**.
    - Kör på datorer som kör Windows 7 SP1 x 86 **Win7-KB3134760-x86.msu/quiet**.

### <a name="additional-installation-notes-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Övrig installationsinformation för Windows Server 2008 R2 SP1 och Windows 7 SP1:

Kontrollera att följande krav är uppfyllda:
- Senaste servicepack installerat.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) är installerad.
- [.NET framework 4.5 eller senare](https://msdn.microsoft.com/library/5a4x27ek.aspx) är installerad.

**WMF 4.0 beroende**

Windows Server 2008 R2 SP1 och Windows 7 SP1-system har inbyggda PowerShell 2.0, WinRM och WMI. WMF 3.0 och WMF 4.0 paket som uppdaterar dessa inbyggda komponenter har getts ut efter lanseringen av Windows Server 2008 R2 SP1 och Windows 7 SP1. Installera/avinstallera WMF 3.0 och WMF 4.0-paket som upptäckts problem i följande uppgraderingsmetod:

- Built-in --> WMF 4.0
- Built-in --> WMF 3.0 --> WMF4.0.

Vi har löst alla problem i WMF 4.0-paket. Det är därför en förutsättning för WMF 4.0 för att installera WMF 5.0 på Windows Server 2008 R2 SP1 och Windows 7 SP1. Nedan visas specifika problem som kan uppstå om du inte installerar WMF 4.0 innan du uppgraderar till WMF 5.0:

- Loggen för vidarebefordrade händelser är tillgänglig och EventCollector loggen inte visas i Loggboken när du har avinstallerat WMF 3.0 eller WMF 5.0 (utan nödvändiga WMF 4.0 installerat) i Windows 7 SP1 och Windows Server 2008 R2 SP1 ([KB2809215](https://support.microsoft.com/en-us/kb/2809215)).
- Anpassning till *PSModulePath* miljövariabeln hämtar återställer till standardvärdet när du uppgraderar direkt från den inbyggda PowerShell 2.0 till WMF 5.0 ([KB2872035](https://support.microsoft.com/en-us/kb/2872035)) eller från WMF 3.0 till WMF 5.0. ([KB2872047](https://support.microsoft.com/en-us/kb/2872047)) i Windows 7 SP1 och Windows Server 2008 R2 SP1.

**WinRM-beroende**

Windows PowerShell önskad tillstånd Configuration (DSC) är beroende av WinRM. WinRM är inte aktiverad som standard i Windows Server 2008 R2 SP1 och Windows 7 SP1. Att aktivera WinRM utökade i en Windows PowerShell genom att köra sessionen **Set-WSManQuickConfig**.

# <a name="uninstallation-instructions"></a>Anvisningar för avinstallation

### <a name="using-command-prompt"></a>Med hjälp av Kommandotolken

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

### <a name="using-control-panel"></a>Med hjälp av Kontrollpanelen

1.  Öppna **Kontrollpanelen.**

2.  Öppna **program**sedan öppnar **avinstallera ett program.**

3.  Klicka på **Visa installerade uppdateringar.**

4.  Välj **Windows Management Framework 5.0** från listan över installerade uppdateringar. Detta motsvarar *KB3134758*, *KB3134759*, eller *KB3134760*. Klicka på **avinstallera.**