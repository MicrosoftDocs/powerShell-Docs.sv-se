---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
contributor: keithb
title: Installera och konfigurera WMF 5.1
ms.openlocfilehash: 74c19d2eb04b77b1e2b1c8d8977f9b4db6e94e4f
ms.sourcegitcommit: 9910675e8758042b5949c99b381a926d2b4e8c21
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2017
---
# <a name="install-and-configure-wmf-51"></a>Installera och konfigurera WMF 5.1 #


## <a name="download-and-install-the-wmf-51-package"></a>Hämta och installera paketet WMF 5.1

Hämta WMF 5.1-paketet för operativsystemet och arkitektur som du vill installera den på:

| Operativsystem       | Förutsättningar       | Package länkar             |
|------------------------|---------------------|---------------------------|
| Windows Server 2012 R2 | | [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516)|
| Windows Server 2012    | | [W2K12-KB3191565-x64.msu](https://go.microsoft.com/fwlink/?linkid=839513)|
| Windows Server 2008 R2 | [.NET framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | [Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) | 
| Windows 8.1            |  | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516) </br> **x86:** [Win8.1-KB3191564-x86.msu](https://go.microsoft.com/fwlink/?linkid=839521) |
| Windows 7 SP1          | [.NET framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) </br> **x86:** [Win7-KB3191566-x86.ZIP](https://go.microsoft.com/fwlink/?linkid=839522)



## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Installera WMF 5.1 för Windows Server 2008 R2 och Windows 7

> **Obs:** installationsanvisningar för Windows Server 2008 R2 och Windows 7 har ändrats och skiljer sig från instruktioner för de andra paketen. Installationsinstruktioner för Windows Server 2012 R2, Windows Server 2012 och Windows 8.1 är lägre än.

**Installera WMF 5.1 på Windows Server 2008 R2 och Windows 7**

1. Navigera till mappen dit du hämtade ZIP-filen. 

2. Högerklicka på ZIP-filen och välj ”extrahera alla...”. Zip innehåller 2 filer: en MSU- och installera WMF5.1.PS1 skriptfilen. När du har packat ZIP-filen, kan du kopiera innehållet till en dator som kör Windows 7 eller Windows Server 2008 R2.  

3. När du extraherar ZIP filinnehåll öppnar du PowerShell som administratör och navigera till mappen som innehåller den  
innehållet i ZIP-filen. 

4. Kör skriptet Install-Wmf5.1.ps1 i den mappen och följ instruktionerna. Det här skriptet Kontrollera krav på den lokala datorn och installera WMF 5.1 om krav har uppfyllts. Kraven finns nedan. 

Installera WMF5.1.ps1 använder följande parametrar för att underlätta automatisk installation på Windows Server 2008 R2 och Windows 7:

- AcceptEula: När den här parametern finns LICENSAVTALET godkänns automatiskt och visas inte.
- AllowRestart: Den här parametern kan bara användas om AcceptEula har angetts. Om den här parametern ingår, och en omstart krävs när du har installerat WMF 5.1, sker omstart utan att fråga omedelbart när installationen är klar. 

**WMF 5.1 krav för Windows Server 2008 R2 SP1 och Windows 7 SP1**

Installation av WMF 5.1 på Windows Server 2008 R2 SP1 eller Windows 7 SP1 kräver följande:
- Senaste servicepack måste vara installerad.
- WMF 3.0 **får inte** installeras. Installera WMF 5.1 över WMF 3.0 leder till förlust av PSModulePath, vilket kan orsaka att andra program för att misslyckas. Innan du installerar WMF 5.1 måste antingen avinstallera WMF 3.0 eller spara PSModulePath och sedan återskapa den manuellt efter att WMF 5.1 installationen är klar. 
- WMF 5.1 kräver minst [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Du kan installera Microsoft .NET Framework 4.5.2 genom att följa anvisningarna i nedladdningsplatsen.

**WinRM-beroende** 

Windows PowerShell önskad tillstånd Configuration (DSC) är beroende av WinRM. WinRM är inte aktiverad som standard i Windows Server 2008 R2 och Windows 7. Kör `Set-WSManQuickConfig`, utökade sessionen att aktivera WinRM i en Windows PowerShell.


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Installera WMF 5.1 för Windows Server 2012 R2, Windows Server 2012 och Windows 8.1
**Installera från Windows Explorer (eller Utforskaren i Windows Server 2012 R2 eller Windows 8.1)**

1. Navigera till mappen dit du hämtade MSU-fil.

2. Dubbelklicka på MSU att köra den.

**Installera från Kommandotolken**

1. När du har hämtat rätt paket för datorns arkitektur, öppna ett kommandotolksfönster med utökade användarrättigheter (Kör som administratör). På installationsalternativet Server Core av Windows Server 2012 R2, Windows Server 2012 eller Windows Server 2008 R2 SP1 öppnas kommandotolk med förhöjd behörighet som standard.

2. Ändra sökvägen till mappen som du har hämtat eller kopierat WMF 5.1 installationspaketet.

3. Kör något av följande kommandon:
    - Kör på datorer som kör Windows Server 2012 R2 eller Windows 8.1 x64 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
    - Kör på datorer som kör Windows Server 2012 `W2K12-KB3191565-x64.msu /quiet`.
    - Kör på datorer som kör Windows 8.1 x86 `Win8.1-KB3191564-x86.msu /quiet`.
    
