---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 3679c13c2d28f28f3102b24f6369f1dc264d6884
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="installation-instructions"></a>Instruktioner för installation

Hämta rätt paket för operativsystemet och arkitektur:

| Operativsystem       | Arkitektur | Paketnamn              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


**Installera WMF 5.0 från Utforskaren i Windows (eller Utforskaren i Windows Server 2012 R2 och Windows 8.1):**

1. Navigera till mappen dit du hämtade MSU-fil.

2. Dubbelklicka på MSU att köra den.

**Installera WMF 5.0 från kommandoraden:**

1. När du har hämtat rätt paket för datorns arkitektur, öppna ett kommandotolksfönster med utökade användarrättigheter (Kör som administratör). På installationsalternativet Server Core av Windows Server 2012 R2 eller Windows Server 2012 eller Windows Server 2008 R2 SP1 öppnas kommandotolk med förhöjd behörighet som standard.

2. Ändra sökvägen till mappen som du har hämtat eller kopierat WMF 5.0 installationspaketet.

3. Kör något av följande kommandon:
    - Kör på datorer som kör Windows Server 2012 R2 eller Windows 8.1 x64 **Win8.1AndW2K12R2-KB3134758-x64.msu/quiet**.
    - Kör på datorer som kör Windows Server 2012 **W2K12-KB3134759-x64.msu/quiet**.
    - Kör på datorer som kör Windows Server 2008 R2 SP1 eller Windows 7 SP1 x 64, **Win7AndW2K8R2-KB3134760-x64.msu/quiet**.
    - Kör på datorer som kör Windows 8.1 x86 **Win8.1-KB3134758-x86.msu/quiet**.
    - Kör på datorer som kör Windows 7 SP1 x 86 **Win7-KB3134760-x86.msu/quiet**.

**Övrig installationsinformation för Windows Server 2008 SP1 och Windows 7 SP1:**

Kontrollera att följande krav är uppfyllda:
- Senaste servicepack installerat.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) har installerats

*WinRM beroende:* Windows PowerShell önskad tillstånd Configuration (DSC) är beroende av WinRM. WinRM är inte aktiverad som standard i Windows Server 2008 R2 och Windows 7. Att aktivera WinRM utökade i en Windows PowerShell genom att köra sessionen **Set-WSManQuickConfig**.
