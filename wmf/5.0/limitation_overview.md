---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 4eb2f0bac4f2169a9a06d80cb4fa214a09cdfa86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687029"
---
# <a name="known-issues-and-limitations"></a>Kända problem och begränsningar

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>PowerShell genvägar bryts när den används för första gången

**Lösning:** Gör något av följande åtgärder:

1. Högerklicka på genvägen till PowerShell. Välj ”Windows PowerShell” för att starta i ett icke-upphöjd-läge.
2. Högerklicka på genvägen till PowerShell. Högerklicka på ”Windows PowerShell” och välj ”Kör som administratör” att starta en förhöjd behörighet.

När du har utfört någon av ovanstående åtgärder, fungerar PowerShell-genvägar. Dessa åtgärder måste utföras en gång.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>PowerShell-moduler och DSC-resurser rapportera fel om ExecutionPolicy på Windows 7

Använda PowerShell-moduler och DSC-resurser kan resultera i fel som rapporterats om ExecutionPolicy på Windows 7.

**Lösning:** Ange körningsprincipen till RemoteSigned genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Ansluta till en gammal fjärrslutpunkten Exchange orsakar en krasch

Den gamla Exchange-slutpunkten omdirigerar till en ny slutpunkt. Det finns en bugg i omdirigering logik som uppstår i en krasch.

**Lösning:** Ansluta direkt till den nya slutpunkten.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Software Inventory Logging funktionen stoppas felaktigt efter installation av WMF 5.0 på Windows Server 2012 R2

När du installerar WMF 5.0 på en Windows Server 2012 R2 som redan kör SIL, stoppas felaktigt funktionen Software Inventory Logging efter installationen.

**Lösning:** Köra cmdleten Start-SilLogging en gång efter WMF-installationen eftersom installationsprocessen avbryts felaktigt funktionen Software Inventory Logging.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>`Get-ChildItem` fungerar inte om - LiteralPath och -Recurse används tillsammans

Om ett katalognamn innehåller ett ogiltigt jokertecken sedan `Get-ChildItem` skapas inte förväntat resultat när både - LiteralPath och -Recurse används tillsammans.

**Lösning:** Inte den bästa lösningen, men aktuella lösningen är att implementera rekursion i skriptet i stället för att förlita dig på cmdlet: en.

## <a name="sysprep-fails-after-wmf-50-installation"></a>Sysprep misslyckas efter installationen av WMF 5.0

Det finns två lösningar på problemet beroende på vilken version av Windows Server du kör.

**Lösning:**

- För system som kör **Windows Server 2008 R2**
  1. Öppna Powershell som administratör
  2. Kör följande kommando

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. Kör kommandot och ignorera felet, som de är förväntat.

     ```powershell
     Publish-SilData
     ```

  4. Ta bort filer i \Windows\System32\Logfiles\SIL\ katalog

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. Installera alla tillgängliga viktiga Windows uppdateringar och börja Sysyprep åtgärden normalt.

- För system som kör **Windows Server 2012**
  1. När du har installerat WMF 5.0 på servern för att d Sysprep, logga in som administratör.
  2. Kopiera Generize.xml från katalogen \Windows\System32\Sysprep\ActionFiles\ till en plats utanför Windows-katalogen, C:\ till exempel.
  3. Öppna din Generalize.xml kopia i anteckningar.
  4. Hitta och ta bort följande text, en instans av varje behov som ska tas bort (de är slutet av dokumentet).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Spara den redigerade kopian av Generalize.xml och stäng filen.
  6. Öppna en kommandotolk som administratör
  7. Kör följande kommando för att bli ägare av filen Generalize.xml i system32-mapp:

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. Kör följande kommando för att ange rätt behörighet för filen:

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - Svara Ja i Kommandotolken för bekräftelse.
     - Observera att `<AdministratorUserName>` ska ersättas med det användarnamn som är administratör på datorn. Till exempel ”administratör”.

  9. Kopiera filen du redigeras och sparas över i Sysprep-katalogen med följande kommando:

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - Svara Ja om du vill skriva över (Observera att om det finns ingen uppmaning om att skriva över, kontrollera den angivna sökvägen).
     - Förutsätter att den redigerade kopian av Generalize.xml kopierades till C:\.

  10. Generalize.XML har uppdaterats med lösningen. Kör Sysprep med alternativet generalize aktiverat.