---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
contributor: keithb
title: Installera och konfigurera WMF 5.1
ms.openlocfilehash: 241f52be011e1afc87d25c9a934db0c1e0361b76
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "79406855"
---
# <a name="install-and-configure-wmf-51"></a>Installera och konfigurera WMF 5,1

> [!IMPORTANT]
> WMF 5,0 ersätts av WMF 5,1. Användare med WMF 5,0 måste uppgradera till WMF 5,1 för att få support.
> **WMF 5,1 kräver .NET Framework 4.5.2** (eller senare). Installationen kommer att lyckas, men viktiga funktioner kommer att Miss lyckas om .NET 4.5.2 (eller senare) inte är installerat.

## <a name="download-and-install-the-wmf-51-package"></a>Hämta och installera WMF 5,1-paketet

Hämta WMF 5,1-paketet för det operativ system och den arkitektur som du vill installera den på:

| Operativsystem       | Krav           | Paket länkar                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win 8.1 AndW2K12R2-KB3191564-x64. msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64. msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64. ZIP][]    |
| Windows 8,1            |                         | **x64:** [Win 8.1 andw2k12r2-kb3191564-x64. msu][]</br>**x86:** [Win 8.1-kb3191564-x86. msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64. zip][]</br>**x86:** [Win7-KB3191566-x86. zip][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64. msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86. ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64. ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win 8.1-KB3191564-x86. msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win 8.1 AndW2K12R2-KB3191564-x64. msu]: https://go.microsoft.com/fwlink/?linkid=839516

- WMF 5,1 Preview måste avinstalleras innan du installerar WMF 5,1 RTM.
- WMF 5,1 kan installeras direkt över WMF 5,0 eller WMF 4,0.
- Du **behöver inte** installera WMF 4,0 innan du installerar WMF 5,1 på Windows 7 och windows Server 2008 R2.

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Installera WMF 5,1 för Windows Server 2008 R2 och Windows 7

> [!NOTE]
> Installations anvisningar för Windows Server 2008 R2 och Windows 7 har ändrats och skiljer sig från anvisningarna för de andra paketen. Installations anvisningar för Windows Server 2012 R2, Windows Server 2012 och Windows 8,1 finns nedan.

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>WMF 5,1-krav för Windows Server 2008 R2 SP1 och Windows 7 SP1

Installationen av WMF 5,1 på antingen Windows Server 2008 R2 SP1 eller Windows 7 SP1 kräver följande:

- Senaste service pack måste vara installerat.
- WMF 3,0 **får inte** vara installerat. Installation av WMF 5,1 över WMF 3,0 leder till förlust av **PSModulePath** (`$env:PSModulePath`), vilket kan orsaka att andra program Miss lyckas. Innan du installerar WMF 5,1 måste du antingen avinstallera WMF 3,0 eller spara **PSModulePath** och sedan återställa den manuellt när WMF 5,1-installationen är klar.
- WMF 5,1 kräver minst [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).
  Du kan installera Microsoft .NET Framework 4.5.2 genom att följa anvisningarna på hämtnings platsen.

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>Installera WMF 5,1 på Windows Server 2008 R2 och Windows 7

1. Navigera till den mapp där du laddade ned ZIP-filen.

2. Högerklicka på ZIP-filen och välj **extrahera alla..**.. ZIP-filen innehåller två filer: en MSU-och `Install-WMF5.1.ps1` skript fil. När du har packat upp ZIP-filen kan du kopiera innehållet till alla datorer som kör Windows 7 eller Windows Server 2008 R2.

3. När du har extraherat ZIP-filens innehåll öppnar du PowerShell som administratör och navigerar sedan till den mapp som innehåller innehållet i ZIP-filen.

4. Kör `Install-WMF5.1.ps1` skriptet i mappen och följ instruktionerna. Det här skriptet kontrollerar kraven på den lokala datorn och installerar WMF 5,1 om kraven är uppfyllda. Kraven visas nedan.

   `Install-WMF5.1.ps1`använder följande parametrar för att under lätta automatiserad installation av Windows Server 2008 R2 och Windows 7:

   - **AcceptEula**: när den här parametern ingår godkänns licens avtalet automatiskt och visas inte.
   - **AllowRestart**: den här parametern kan endast användas om AcceptEula har angetts. Om den här parametern tas med och en omstart krävs efter installation av WMF 5,1 sker omstarten utan att du tillförar omedelbart efter att installationen har slutförts.

## <a name="winrm-dependency"></a>WinRM-beroende

Windows PowerShell Desired State Configuration (DSC) är beroende av WinRM. WinRM är inte aktiverat som standard på Windows Server 2008 R2 och Windows 7. Kör `Set-WSManQuickConfig`, i en upphöjd Windows PowerShell-session, för att aktivera WinRM.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Installera WMF 5,1 för Windows Server 2012 R2, Windows Server 2012 och Windows 8,1

### <a name="install-from-windows-file-explorer"></a>Installera från Utforskaren i Windows

1. Navigera till den mapp som du laddade ned MSU-filen till.
2. Dubbelklicka på MSU för att köra det.

### <a name="installing-from-the-command-prompt"></a>Installera från kommando tolken

1. När du har hämtat rätt paket för datorns arkitektur öppnar du ett kommando tolks fönster med utökade användar rättigheter (kör som administratör). På Server Core-installations alternativen för Windows Server 2012 R2, Windows Server 2012 eller Windows Server 2008 R2 SP1 öppnas kommando tolken med utökade användar rättigheter som standard.
2. Ändra kataloger till mappen där du har laddat ned eller kopierat WMF 5,1-installations paketet.
3. Kör något av följande kommandon:
   - På datorer som kör Windows Server 2012 R2 eller Windows 8,1 x64 kör `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`du.
   - På datorer som kör Windows Server 2012 kör `W2K12-KB3191565-x64.msu /quiet`du.
   - På datorer som kör Windows 8,1 x86 kör `Win8.1-KB3191564-x86.msu /quiet`du.

> [!NOTE]
> Installation av WMF 5,1 kräver en omstart. Om du `/quiet` använder alternativet startas systemet om utan varning. Använd `/norestart` alternativet för att undvika att starta om. WMF 5,1 kommer dock inte att installeras förrän du har startat om.
