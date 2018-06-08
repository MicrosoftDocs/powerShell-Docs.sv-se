---
ms.date: 08/09/2017
keywords: PowerShell cmdlet, hämta, installera, installationsprogrammet, windows 10, windows 8.1, windows 8.0, windows 7
title: Installera Windows PowerShell
ms.openlocfilehash: 89f0f689ebfcd34dd4c8ec3824ec8ab4bddc34d9
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483006"
---
# <a name="installing-windows-powershell"></a>Installera Windows PowerShell
Windows PowerShell är installerat som standard i alla Windows som börjar med Windows 7 SP1 och Windows Server 2008 R2 SP1.

Om du är intresserad av i PowerShell 6 och senare, måste du installera PowerShell Core i stället för Windows PowerShell. För att se [installera PowerShell Core på Windows](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Hitta PowerShell i Windows 10, 8.1, 8.0 och 7

Ibland hitta PowerShell kan-konsolen eller ISE (Integrated Scripting Environment) i Windows vara svårt, eftersom dess plats flyttas från en version av Windows till nästa.

I tabellerna nedan hjälper dig att hitta PowerShell i Windows-version.
Alla versioner som listas här är den ursprungliga versionen som släpptes tillsammans med inga uppdateringar.

### <a name="for-console"></a>För konsolen

Version | Position
-- | --
Windows 10 | Klicka på nedre hörnet Windows ikonen till vänster, börja skriva PowerShell
Windows 8.1, 8.0 | Börja skriva PowerShell på startskärmen.<br/>Klicka på nedre hörnet Windows ikonen till vänster om på skrivbordet, börja skriva PowerShell
Windows 7 SP1 | Klicka på nedre hörnet Windows ikonen till vänster, Sök rutan Start skriva PowerShell

### <a name="for-ise"></a>För ISE

Version | Position
-- | --
Windows 10 | Klicka på nedre hörnet Windows ikonen till vänster, börja skriva ISE
Windows 8.1, 8.0 | Skriv på startskärmen **PowerShell ISE**.<br/>Om på skrivbordet, klicka på nedre hörnet Windows-ikonen, Skriv **PowerShell ISE**
Windows 7 SP1 | Klicka på nedre hörnet Windows ikonen till vänster, Sök rutan Start skriva PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>Hitta PowerShell i Windows Server-versioner

Från och med Windows Server 2008 R2, installeras Windows-operativsystem utan det grafiska användargränssnittet (GUI).
Versioner av Windows Server utan GUI namnges **Core** versioner och utgåvor med det grafiska Användargränssnittet är namngivna **Desktop**.

### <a name="windows-server-core-editions"></a>Windows Server Core-utgåvor

I alla Core-utgåvor när du loggar på servern hämta du Windows Kommandotolkens fönster.

Typen `powershell` och tryck på **RETUR** starta PowerShell inuti kommandotolk-session.
Typen `exit` att avsluta PowerShell-session och återgå till Kommandotolken.

### <a name="windows-server-desktop-editions"></a>Windows Server-Desktop-versioner

I alla versioner av skrivbordet, klicka på vänster lägre hörnet Windows-ikonen, börja skriva PowerShell.
Du får alternativ för både konsolen och ISE.

Det enda undantaget till ovanstående regel är ISE i Windows Server 2008 R2 SP1; i det här fallet vänstra lägre hörnet Windows-ikonen, Skriv PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Så här kontrollerar du vilken version av PowerShell

Starta en PowerShell-konsol (eller ISE) för att söka efter vilken version av PowerShell som du har installerat, och skriv `$PSVersionTable` och tryck på **RETUR**. Leta efter den `PSVersion` värde.

## <a name="upgrading-existing-windows-powershell"></a>Uppgradera befintliga Windows PowerShell

Installationspaketet för PowerShell kommer inuti en WMF installer.
Versionen av WMF installer matchar versionen av PowerShell; Det finns inga fristående installationsprogram för Windows PowerShell.

Om du behöver uppdatera den befintliga versionen av PowerShell i Windows kan använda följande tabell för att hitta installationsprogrammet för den version av PowerShell som du vill uppdatera till.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (se Note1)<br/>Windows Server 2016 | - | - | - | installerad
Windows 8.1<br/>Windows Server 2012 R2 | - | installerad | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | installerad | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> **Anmärkning 1**:
  >>
  >> På den första versionen av Windows 10 med automatiska uppdateringar aktiverad, uppdateras PowerShell från version 5.0 5.1.
  >>
  >> Om den ursprungliga versionen av Windows 10 inte uppdateras via Windows-uppdateringar, är versionen av PowerShell 5.0.

## <a name="need-azure-powershell"></a>Behöver Azure PowerShell

Om du letar efter **Azure PowerShell**, du kan börja med [översikt av Azure PowerShell](https://docs.microsoft.com/powershell/azure).

I annat fall kanske du måste är [installera och konfigurera Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Se även

- [Systemkrav för Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Starta Windows PowerShell](Starting-Windows-PowerShell.md)