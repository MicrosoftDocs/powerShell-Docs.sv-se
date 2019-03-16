---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
contributor: keithb
title: Installera och konfigurera WMF 5.1
ms.openlocfilehash: c439d0851189a89a81fa38194632dc54475a001d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055994"
---
# <a name="install-and-configure-wmf-51"></a>Installera och konfigurera WMF 5.1

## <a name="download-and-install-the-wmf-51-package"></a>Ladda ned och installera WMF 5.1-paketet

Hämta WMF 5.1-paketet för operativsystemet och arkitektur som du vill installera den på:

| Operativsystem       | Förutsättningar           | Paketet länkar                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Installera WMF 5.1 för Windows Server 2008 R2 och Windows 7

> [!NOTE]
> Installationsinstruktioner för Windows Server 2008 R2 och Windows 7 har ändrats och skiljer sig från anvisningarna för de andra paketen. Installationsinstruktioner för Windows Server 2012 R2, Windows Server 2012 och Windows 8.1 finns nedan.

**Installera WMF 5.1 på Windows Server 2008 R2 och Windows 7**

1. Navigera till den mapp dit du hämtade ZIP-filen.

2. Högerklicka på ZIP-filen och välj ”extrahera alla...”. ZIP-filen innehåller 2 filer: en MSU- och installera WMF5.1.PS1-skriptfilen.
När du har packat upp ZIP-filen, kan du kopiera innehållet till en dator som kör Windows 7 eller Windows Server 2008 R2.

3. När innehållet för ZIP-filen, öppna PowerShell som administratör och navigera till mappen som innehåller innehållet i ZIP-filen.

4. Kör skriptet Install-Wmf5.1.ps1 i den mappen och följ instruktionerna. Det här skriptet ska kontrollera krav på den lokala datorn och installera WMF 5.1 om kraven har uppfyllts. Kraven finns nedan.

Installera WMF5.1.ps1 använder följande parametrar för att underlätta automatisera installationen på Windows Server 2008 R2 och Windows 7:

- AcceptEula: När den här parametern finns LICENSAVTALET godkänns automatiskt och visas inte.
- AllowRestart: Den här parametern kan endast användas om AcceptEula har angetts. Om den här parametern ingår och en omstart krävs när du har installerat WMF 5.1, sker omstarten utan att fråga direkt när installationen har slutförts.

**WMF 5.1 krav för Windows Server 2008 R2 SP1 och Windows 7 SP1**

Installation av WMF 5.1 på Windows Server 2008 R2 SP1 eller Windows 7 SP1 kräver följande:
- Senaste servicepack måste vara installerad.
- WMF 3.0 **får inte** installeras. Installera WMF 5.1 via WMF 3.0 resulterar i förlust av PSModulePath, vilket kan orsaka att andra program att misslyckas. Innan du installerar WMF 5.1 måste antingen avinstallera WMF 3.0, eller spara PSModulePath och sedan återställa det manuellt efter att WMF 5.1-installationen är klar.
- WMF 5.1 kräver minst [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Du kan installera Microsoft .NET Framework 4.5.2 genom att följa anvisningarna i nedladdningsplatsen.

**WinRM-beroende**

Windows PowerShell Desired State Configuration (DSC) är beroende av WinRM.
WinRM är inte aktiverat som standard på Windows Server 2008 R2 och Windows 7.
Kör `Set-WSManQuickConfig`, utökade sessionen att aktivera WinRM i ett Windows PowerShell.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Installera WMF 5.1 för Windows Server 2012 R2, Windows Server 2012 och Windows 8.1

**Installera från Windows Explorer (eller Utforskaren i Windows Server 2012 R2 eller Windows 8.1)**

1. Navigera till den mapp dit du hämtade MSU-fil.
2. Dubbelklicka på MSU att köra den.

**Installera från Kommandotolken**

1. När du hämtat rätt paket för datorns arkitektur, öppna ett kommandotolksfönster med utökade användarrättigheter (Kör som administratör). På installationsalternativet Server Core av Windows Server 2012 R2, Windows Server 2012 eller Windows Server 2008 R2 SP1 öppnas kommandotolk med förhöjd behörighet som standard.
2. Ändra sökvägen till mappen dit du har hämtat eller kopierade WMF 5.1-installationspaketet.
3. Kör något av följande kommandon:
   - Kör på datorer som kör Windows Server 2012 R2 eller Windows 8.1 x64 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Kör på datorer som kör Windows Server 2012, `W2K12-KB3191565-x64.msu /quiet`.
   - Kör på datorer som kör Windows 8.1 x86 `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> Installera WMF 5.1 kräver en omstart. Med hjälp av den `/quiet` alternativet startar om systemet utan varning.
> Använd den `/norestart` alternativet för att undvika att starta om. WMF 5.1 kommer inte installeras förrän du har startats om.
