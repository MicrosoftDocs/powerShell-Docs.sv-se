---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: JEA-krav
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084852"
---
# <a name="prerequisites"></a>Förutsättningar

> Gäller för: Windows PowerShell 5.0

Just Enough Administration är en funktion som ingår i Windows PowerShell 5.0 och senare.
Det här avsnittet beskrivs de krav som måste uppfyllas för att kunna börja använda JEA.

## <a name="install-jea"></a>Installera JEA

JEA är tillgängliga med Windows PowerShell 5.0 och senare, men för alla funktioner rekommenderas att du installerar den senaste versionen av PowerShell som är tillgängliga för ditt system.
I följande tabell beskrivs JEAS tillgänglighet på Windows Server:

Serveroperativsystem   | JEA-tillgänglighet
--------------------------|--------------------------------
Windows Server 2016       | Förinstallerad
Windows Server 2012 R2    | Alla funktioner i WMF 5.1
Windows Server 2012       | Alla funktioner i WMF 5.1
Windows Server 2008 R2    | Funktioner<sup>1</sup> med WMF 5.1

Du kan också använda JEA på datorn hem- eller arbetsnätverk:

Klientoperativsystem   | JEA-tillgänglighet
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Förinstallerad
Windows 10 1603, 1511     | Förinstallerad, med nedsatt funktionalitet<sup>2</sup>
Windows 10 1507           | Inte tillgänglig
Windows 8, 8.1            | Alla funktioner i WMF 5.1
Windows 7                 | Funktioner<sup>1</sup> med WMF 5.1

<sup>1</sup> JEA kan inte konfigureras för att använda grupphanterade tjänstkonton på Windows Server 2008 R2 eller Windows 7.
Virtuella konton och andra funktioner för JEA *är* stöds.

<sup>2</sup> Windows 10 version 1511 och 1603 stöder inte följande funktioner i JEA: körs som ett grupphanterat tjänstkonto, regler för villkorlig åtkomst i sessionskonfigurationer, enheten och att bevilja åtkomst till lokala användarkonton.
För att få stöd för dessa funktioner kan du uppdatera Windows till version 1607 (Anniversary Update) eller högre.

### <a name="check-which-version-of-powershell-is-installed"></a>Kontrollera vilken version av PowerShell är installerat

Om du vill kontrollera vilken version av PowerShell är installerat på datorn, kontrollera den `$PSVersionTable` variabel i en Windows PowerShell-kommandotolk.

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Du är redo att använda JEA om den *större* version är lika med eller större än **5**.
För bästa möjliga upplevelse och ska ha åtkomst till alla de senaste funktionerna, rekommenderar vi att du uppgraderar till PowerShell-version **5.1** när det är möjligt.

### <a name="install-windows-management-framework"></a>Installera Windows Management Framework

Om du kör en äldre version av PowerShell, kommer du behöva uppdatera datorn med den senaste uppdateringen av Windows Management Framework (WMF).
Uppdateringspaket och en länk till senaste WMF viktig information finns i den [Download Center](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).

Vi rekommenderar starkt att du testar din arbetsbelastning kompatibilitet med WMF innan du uppgraderar alla dina servrar.

Windows 10-användare bör installera de senaste funktionsuppdateringarna för att hämta den aktuella versionen av Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Aktivera PowerShell-fjärrkommunikation

PowerShell-fjärrkommunikation utgör grunden som JEA har skapats.
Det är därför nödvändigt att säkerställa att PowerShell-fjärrkommunikation är aktiverat och [ordentligt](/powershell/scripting/setup/winrmsecurity) på datorn innan du kan använda JEA.

PowerShell-fjärrkommunikation är aktiverat som standard på Windows Server 2012, 2012 R2 och 2016.
Du kan aktivera PowerShell-fjärrkommunikation genom att köra följande kommando i ett upphöjt PowerShell-fönster.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Aktivera PowerShell-modulen och skript block loggning (valfritt)

Följande steg aktiverar loggning för alla PowerShell-åtgärder på datorn.
Loggning av PowerShell-modulen krävs inte för JEA, men vi rekommenderar starkt att du aktiverar det att se till att köra kommandon användare är inloggade på en central plats.

Du kan konfigurera principen för loggning av PowerShell-modulen med hjälp av en Grupprincip.

1. Öppna Redigeraren för lokal princip på en arbetsstation eller ett grupprincipobjekt i Group Policy Management Console på en Active Directory-domänkontrollant
2. Gå till **Datorkonfiguration\\Administrationsmallar\\Windows-komponenter\\Windows PowerShell**
3. Dubbelklicka på **aktiverar loggning av modul**
4. Klicka på **aktiverat**
5. I avsnittet alternativ klickar du på **visa** bredvid Modulnamnen
6. Typ `\*` i popup-fönstret. Detta instruerar PowerShell för att logga kommandon från alla moduler.
7. Klicka på **OK** att ställa in principen
8. Dubbelklicka på **aktiverar loggning för PowerShell-skript Block**
9. Klicka på **aktiverat**
10. Klicka på **OK** att ställa in principen
11. (På domänanslutna datorer endast) Kör `gpupdate` eller vänta tills en grupprincip för att bearbeta den uppdaterade policyn och tillämpa inställningarna

Du kan också aktivera systemomfattande PowerShell avskrift via en Grupprincip.

## <a name="next-steps"></a>Nästa steg

[Skapa en roll funktionen fil](role-capabilities.md)

[Skapa en konfigurationsfil för session](session-configurations.md)

## <a name="see-also"></a>Se även

[Mer information om PowerShell-fjärrkommunikation och WinRM-säkerhet](/powershell/scripting/setup/winrmsecurity)

[*PowerShell ♥ blå teamet* blogginlägg om säkerhet](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)