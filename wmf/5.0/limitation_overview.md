---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="known-issues-and-limitations"></a>Kända problem och begränsningar

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>PowerShell genvägar bryts när den används för första gången
------------------------------------------------------------

**Lösning:** utför något av följande åtgärder:

1.  Högerklicka på genvägen för PowerShell. Välj ”Windows PowerShell” för att starta i ett icke-upphöjd-läge.
2.  Högerklicka på genvägen för PowerShell. Högerklicka på ”Windows PowerShell” och välj ”Kör som administratör” att starta en förhöjd behörighet.

När du har utfört någon av ovanstående åtgärder fungerar PowerShell genvägar. Dessa åtgärder måste utföras en gång.


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>PowerShell-moduler och DSC resurser rapportera fel om körningsprincipen på Windows 7
-------------------------------------------------------------------------------------
Användningen av PowerShell-moduler och DSC-resurser kan resultera i fel som rapporteras om körningsprincipen på Windows 7.

**Lösning:** inställd på körningsprincipen på RemoteSigned genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Ansluter till en gammal fjärrslutpunkten Exchange orsakar en krasch
------------------------------------------------------------

Den gamla Exchange-slutpunkten omdirigerar till en ny slutpunkt. Det finns ett fel i omdirigering av logik som uppstår i en krasch.

**Lösning:** Anslut direkt till ny slutpunkt.


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Software Inventory Logging funktionen stoppas felaktigt efter installationen av WMF 5.0 på Windows Server 2012 R2
-------------------------------------------------------------------------------------------------------------

När du installerar WMF 5.0 på en Windows Server 2012 R2 som redan kör SIL stoppas felaktigt funktionen Software Inventory Logging efter installationen.

**Lösning:** köra cmdleten Start-SilLogging en gång efter WMF-installationen som installationen avbryts felaktigt funktionen Software Inventory Logging.

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>Get-ChildItem fungerar inte om - LiteralPath och -Recurse används tillsammans
--------------------------------------------------------------------------

Om ett katalognamn innehåller ett ogiltigt jokertecken, sedan Get-ChildItem kommer inte att generera förväntat resultat när både - LiteralPath och -Recurse används tillsammans.

**Lösning:** inte den bästa lösningen, men aktuella lösningen är att implementera rekursion i skriptet i stället för att förlita dig på cmdleten.


<a name="sysprep-fails-after-wmf-50-installation"></a>Sysprep misslyckas efter installationen av WMF 5.0
----------------------------------------

Det finns två lösningar på problemet beroende på vilken version av Windows Server körs.

**Lösning:**
- För datorer som kör **Windows Server 2008 R2**
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
  5. Installera alla tillgängliga viktiga uppdateringar för Windows och börja Sysyprep åtgärden normalt.

- För datorer som kör **Windows Server 2012**
  1.    När du har installerat WMF 5.0 på servern för att d Sysprep, logga in som administratör.
  2.    Kopiera Generize.xml från katalogen \Windows\System32\Sysprep\ActionFiles\ till en plats utanför Windows-katalogen C:\ t.ex.
  3.    Öppna din Generalize.xml kopia med anteckningar.
  4.    Hitta och ta bort följande text, en instans av varje måste tas bort (de är i slutet av dokumentet).

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    Spara den redigerade kopian av Generalize.xml och stäng filen.
  6.    Öppna en kommandotolk som administratör
  7.    Kör följande kommando för att bli ägare till Generalize.xml-fil i mappen system32:

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    Kör följande kommando för att ange behörighet för filen:

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * Svarar Ja i Kommandotolken för att bekräfta.
      * Observera att `<AdministratorUserName>` ska ersättas med det användarnamn som är administratör på datorn. Till exempel ”administratör”.

  9.    Kopiera filen du redigeras och sparas över till katalogen Sysprep med följande kommando:

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * Svara på Ja om du vill skriva över (Observera att om det finns ingen fråga för att ersätta dubbla Kontrollera den angivna sökvägen).
      * Förutsätter att den redigerade kopian av Generalize.xml kopierades till C:\.

  10.   Generalize.XML har uppdaterats med lösningen. Kör Sysprep med alternativet generalize aktiverat.
