---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: JEA-krav
ms.openlocfilehash: 1833bacf49eebcccefc10f7c85a39732559c1a97
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416723"
---
# <a name="prerequisites"></a>Förutsättningar

Bara tillräckligt med administration är en funktion som ingår i PowerShell 5,0 och högre. I den här artikeln beskrivs förutsättningar som måste vara uppfyllda för att börja använda JEA.


## <a name="check-which-version-of-powershell-is-installed"></a>Kontrol lera vilken version av PowerShell som är installerad

Om du vill kontrol lera vilken version av PowerShell som är installerad i systemet kontrollerar du `$PSVersionTable` variabeln i en Windows PowerShell-prompt.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA är tillgängligt med PowerShell 5,0 och högre. För alla funktioner rekommenderar vi att du installerar den senaste versionen av PowerShell som är tillgänglig för ditt system. I följande tabell beskrivs JEA tillgänglighet för Windows Server:

| Serveroperativsystem |                JEA tillgänglighet                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016 +    | Förinstallerad                                   |
| Windows Server 2012 R2  | Fullständiga funktioner med WMF 5,1                |
| Windows Server 2012     | Fullständiga funktioner med WMF 5,1                |
| Windows Server 2008 R2  | Begränsad funktionalitet<sup>1</sup> med WMF 5,1 |

Du kan också använda JEA på din hem-eller arbets dator:

| Klientoperativsystem: |                   JEA tillgänglighet                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607 +        | Förinstallerad                                         |
| Windows 10 1603, 1511   | Förinstallerad med begränsad funktionalitet<sup>2</sup> |
| Windows 10 1507         | Inte tillgänglig                                        |
| Windows 8, 8,1          | Fullständiga funktioner med WMF 5,1                      |
| Windows 7               | Begränsad funktionalitet<sup>1</sup> med WMF 5,1       |

- <sup>1</sup> Jea kan inte konfigureras för användning av grupphanterade tjänst konton i Windows Server 2008 R2 eller Windows 7. Virtuella konton och andra JEA- *funktioner stöds* .

- <sup>2</sup> följande Jea-funktioner stöds inte i Windows 10-versionerna 1511 och 1603:

  - Köra som ett grupphanterat tjänst konto
  - Regler för villkorlig åtkomst i konfigurationer för sessioner
  - Användar enheten
  - Bevilja åtkomst till lokala användar konton

  Om du vill ha stöd för dessa funktioner uppdaterar du Windows till version 1607 (uppdaterings uppdatering) eller högre.

### <a name="install-windows-management-framework"></a>Installera Windows Management Framework

Om du kör en äldre version av PowerShell kan du behöva uppdatera systemet med den senaste WMF-uppdateringen (Windows Management Framework). Mer information finns i WMF- [dokumentationen](/powershell/scripting/wmf/overview).

Vi rekommenderar att du testar din arbets belastnings kompatibilitet med WMF innan du uppgraderar alla dina servrar.

Windows 10-användare bör installera de senaste funktions uppdateringarna för att hämta den aktuella versionen av Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Aktivera PowerShell-fjärrkommunikation

PowerShell-fjärrkommunikation tillhandahåller den grund som JEA bygger på. Det är nödvändigt att se till att PowerShell-fjärrkommunikation är aktiverat och ordentligt säkert innan du kan använda JEA. Mer information finns i [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).

PowerShell-fjärrkommunikation är aktiverat som standard på Windows Server 2012, 2012 R2 och 2016. Du kan aktivera PowerShell-fjärrkommunikation genom att köra följande kommando i ett upphöjd PowerShell-fönster.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Aktivera PowerShell-modul och skript Blocks loggning (valfritt)

Följande steg aktiverar loggning för alla PowerShell-åtgärder i systemet. Loggning av PowerShell-modul krävs inte för JEA, men vi rekommenderar att du aktiverar loggning för att se till att de kommandon som användare kör loggas på en central plats.

Du kan konfigurera PowerShell-modulens loggnings princip med grupprincip.

1. Öppna redigerare för lokalt grupprincipobjekt på en arbets Station eller ett grupprincip objekt i konsolen grupprinciphantering på en Active Directory-domän kontrollant
2. Gå till **dator konfiguration\\Administrativa mallar\\Windows-komponenter\\Windows PowerShell**
3. Dubbelklicka på **Aktivera modul loggning**
4. Klicka på **aktive rad**
5. I avsnittet alternativ klickar du på **Visa** bredvid Modulnamn
6. Skriv `*` i popup-fönstret för att logga kommandon från alla moduler.
7. Klicka på **OK** för att ange principen
8. Dubbelklicka på **Aktivera loggning av PowerShell-skriptkommando**
9. Klicka på **aktive rad**
10. Klicka på **OK** för att ange principen
11. (Endast på domänanslutna datorer) Kör `gpupdate` eller vänta tills grupprincip att bearbeta den uppdaterade principen och tillämpa inställningarna

Du kan också aktivera PowerShell-avskrifter i hela systemet genom grupprincip.

## <a name="next-steps"></a>Nästa steg

[Skapa en roll funktions fil](role-capabilities.md)

[Skapa en konfigurations fil för sessionen](session-configurations.md)

## <a name="see-also"></a>Se även

[WinRM-säkerhet](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ det blå teamet](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
