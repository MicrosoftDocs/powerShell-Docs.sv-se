---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea powershell säkerhet
title: JEA krav
ms.openlocfilehash: 92a74d89a0e982e9f45e69d92b261756de33c038
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="prerequisites"></a>Förutsättningar

> Gäller för: Windows PowerShell 5.0

Bara tillräckligt Administration är en funktion som ingår i Windows PowerShell 5.0 och senare.
Det här avsnittet beskrivs de krav som måste uppfyllas för att börja använda JEA.

## <a name="install-jea"></a>Installera JEA

JEA är tillgängliga med Windows PowerShell 5.0 och senare, men full funktionalitet vi rekommenderar att du installerar den senaste versionen av PowerShell som är tillgängliga för ditt system.
I följande tabell beskrivs JEAS tillgänglighet i Windows Server:

Serveroperativsystem   | JEA tillgänglighet
--------------------------|--------------------------------
Windows Server 2016       | Förinstallerat
Windows Server 2012 R2    | Fullständig funktionalitet med WMF 5.1
Windows Server 2012       | Fullständig funktionalitet med WMF 5.1
Windows Server 2008 R2    | Funktioner<sup>1</sup> med WMF 5.1

Du kan också använda JEA på datorn hem- eller:

Klientens operativsystem   | JEA tillgänglighet
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Förinstallerat
Windows 10 1603, 1511     | Förinstallerat, med nedsatt funktionalitet<sup>2</sup>
Windows 10 1507           | Inte tillgänglig
Windows 8, 8.1            | Fullständig funktionalitet med WMF 5.1
Windows 7                 | Funktioner<sup>1</sup> med WMF 5.1

<sup>1</sup> JEA kan inte konfigureras för att använda grupphanterade tjänstkonton i Windows Server 2008 R2 eller Windows 7.
Virtuella konton och andra funktioner i JEA *är* stöds.

<sup>2</sup> Windows 10 version 1511 och 1603 stöder inte följande funktioner i JEA: körs som en grupp hanteras tjänstkonto, regler för villkorlig åtkomst i sessionskonfigurationer, enheten och att bevilja åtkomst till lokala användarkonton.
Uppdatera Windows för att få stöd för dessa funktioner, till version 1607 (årsdagar uppdatering) eller högre.

### <a name="check-which-version-of-powershell-is-installed"></a>Kontrollera vilken version av PowerShell är installerat

Om du vill kontrollera vilken version av PowerShell är installerat på datorn, kontrollera den `$PSVersionTable` variabeln i en Windows PowerShell-Kommandotolken.

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Du är redo att använda JEA om den *större* version är lika med eller större än **5**.
För bästa möjliga upplevelse och tillgång till de senaste funktionerna, rekommenderas det att du uppgraderar till PowerShell-version **5.1** när det är möjligt.

### <a name="install-windows-management-framework"></a>Installera Windows Management Framework

Om du kör en äldre version av PowerShell behöver du uppdatera datorn med den senaste uppdateringen av Windows Management Framework (WMF).
Uppdateringspaket och en länk till senaste WMF viktig information finns i den [Download Center](https://aka.ms/WMF5).

Det rekommenderas starkt att du testar din arbetsbelastning kompatibilitet med WMF innan du uppgraderar alla dina servrar.

Windows 10 användare ska installera de senaste funktionsuppdateringarna för att erhålla den aktuella versionen av Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Aktivera PowerShell-fjärrkommunikation

PowerShell-fjärrkommunikation utgör grunden som JEA är inbyggd.
Det är därför kontrollera PowerShell-fjärrkommunikation är aktiverad och [ordentligt](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) på datorn innan du kan använda JEA.

PowerShell-fjärrkommunikation är aktiverad som standard på Windows Server 2012 och 2012 R2 2016.
Du kan aktivera PowerShell-fjärrkommunikation genom att köra följande kommando i ett upphöjt PowerShell-fönster.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Aktivera PowerShell-modulen och skript block-loggning (valfritt)

Följande steg aktiverar du loggning för alla PowerShell-åtgärder på datorn.
Loggning av PowerShell-modul krävs inte för JEA, men vi rekommenderar starkt att du aktiverar det så kör kommandon användare är inloggade på en central plats.

Du kan konfigurera principen för loggning av PowerShell-modulen med hjälp av en Grupprincip.

1. Öppna Redigeraren för lokal grupp på en arbetsstation eller ett grupprincipobjekt i hanteringskonsolen för Grupprincip på en Active Directory-domänkontrollant
2. Gå till **Datorkonfiguration\\Administrationsmallar\\Windows-komponenter\\Windows PowerShell**
3. Dubbelklicka på **aktiverar du loggning av modul**
4. Klicka på **aktiverad**
5. I avsnittet alternativ klickar du på **visa** bredvid Modulnamnen
6. Typen ”**\***” i popup-fönstret. Detta instruerar PowerShell för att logga kommandon från alla moduler.
7. Klicka på **OK** att ställa in principen
8. Dubbelklicka på **aktiverar du loggning för PowerShell-skript Block**
9. Klicka på **aktiverad**
10. Klicka på **OK** att ställa in principen
11. (På domänanslutna datorer endast) Kör **gpupdate** eller vänta tills en grupprincip för att bearbeta den uppdaterade principen och tillämpar inställningarna

Du kan också aktivera systemomfattande PowerShell skrivfel via en Grupprincip.

## <a name="next-steps"></a>Nästa steg

- [Skapa en roll kapaciteten fil](role-capabilities.md)
- [Skapa en konfigurationsfil för session](session-configurations.md)

## <a name="see-also"></a>Se även

- [Mer information om säkerhet i PowerShell-fjärrkommunikation och WinRM](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [*PowerShell ♥ blå teamet* blogginlägg om säkerhet](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)