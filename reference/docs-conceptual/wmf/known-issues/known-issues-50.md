---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Kända problem i WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71145133"
---
# <a name="known-issues-in-wmf-50"></a>Kända problem i WMF 5.0

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>PowerShell-genvägar är brutna när de används för första gången

**Lösning:** Utför någon av följande åtgärder:

1. Högerklicka på PowerShell-genvägen. Välj Windows PowerShell för att starta i ett icke-förhöjd läge.
2. Högerklicka på PowerShell-genvägen. Högerklicka på "Windows PowerShell" och välj "kör som administratör" för att starta i ett förhöjd läge.

När du har utfört någon av ovanstående åtgärder kommer PowerShell-genvägar att fungera. De här åtgärderna behöver bara utföras en gång.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>PowerShell-moduler och DSC-resurser rapporterar fel om ExecutionPolicy i Windows 7

I Windows 7 kan använda PowerShell-moduler och DSC-resurser resultera i fel som rapporteras om ExecutionPolicy.

**Lösning:** Ange ExecutionPolicy till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (kör som administratör):

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Att ansluta till en gammal fjärrslutpunkt i Exchange orsakar en krasch

Den gamla Exchange-slutpunkten omdirigeras till en ny slut punkt. Det finns ett fel i den omdirigerings logik som resulterar i en krasch.

**Lösning:** Anslut direkt till den nya slut punkten.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Funktionen för loggning av program varu inventering stoppades felaktigt efter installationen av WMF 5,0 på Windows Server 2012 R2

När du installerar WMF 5,0 på en Windows Server 2012 R2 som redan kör SIL stoppas loggnings funktionen för program varu inventering felaktigt efter installationen.

**Lösning:** Kör `Start-SilLogging` cmdleten en gång efter WMF-installationen, som installations processen kommer att felaktigt stoppa funktionen för Software Inventory Logging.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>`Get-ChildItem`fungerar inte om-LiteralPath och-rekursivt används tillsammans

Om ett katalog namn innehåller ett ogiltigt jokertecken `Get-ChildItem` kommer inte att generera förväntade resultat när både-LiteralPath och-rekursivt används tillsammans.

**Lösning:** Inte idealisk, men den aktuella lösningen är att implementera rekursion i skriptet i stället för att använda cmdleten.

## <a name="sysprep-fails-after-wmf-50-installation"></a>Sysprep Miss lyckas efter installation av WMF 5,0

Det finns två sätt att lösa problemet, beroende på vilken version av Windows Server du kör.

**Lösning**

- För system som kör **Windows Server 2008 R2**
  1. Öppna PowerShell som administratör
  2. Kör följande kommando

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. Kör kommandot och Ignorera felet, eftersom det förväntas.

     ```powershell
     Publish-SilData
     ```

  4. Ta bort filerna i \Windows\System32\Logfiles\SIL\-katalogen

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. Installera alla tillgängliga viktiga Windows-uppdateringar och starta Sysyprep-åtgärden normalt.

- För system som kör **Windows Server 2012**
  1. Logga in som administratör när du har installerat WMF 5,0 på servern som ska Sysprep.
  2. Kopiera Generize. XML från katalogen `\Windows\System32\Sysprep\ActionFiles\` till en plats utanför Windows-katalogen, `C:\` till exempel.
  3. Öppna din generalize. XML-kopia med anteckningar.
  4. Hitta och ta bort följande text, en instans av varje måste tas bort (de kommer snart i slutet av dokumentet).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Spara den redigerade kopian av generalize. xml och Stäng filen.
  6. Öppna en kommando tolk som administratör
  7. Kör följande kommando för att bli ägare till filen generalize. xml i mappen System32:

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. Kör följande kommando för att ange rätt behörighet för filen:

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - Svara Ja när du uppmanas att bekräfta.
     - Observera att `<AdministratorUserName>` ska ersättas med det användar namn som är administratör på datorn. Till exempel "administratör".

  9. Kopiera filen som du redigerade och sparade över till Sysprep-katalogen med följande kommando:

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - Svara ja till Skriv över (Observera att om det inte finns någon uppfråga för att skriva över, måste du kontrol lera sökvägen som anges).
     - Förutsätter att din redigerade kopia av generalize. XML har kopierats till C:\.

  10. Generalize. XML har nu uppdaterats med lösningen. Kör Sysprep med generalize-alternativet aktiverat.