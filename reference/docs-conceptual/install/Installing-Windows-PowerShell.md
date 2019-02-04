---
ms.date: 08/09/2017
keywords: PowerShell, cmdlet, hämta, installera, inställningar, windows 10, windows 8.1, windows 8.0, windows 7
title: Installera Windows PowerShell
ms.openlocfilehash: 1630ba445c88953b2729232ae7d80afa326f25e6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687330"
---
# <a name="installing-windows-powershell"></a>Installera Windows PowerShell

Windows PowerShell är installerat som standard i alla Windows, från och med Windows 7 SP1 och Windows Server 2008 R2 SP1.

Om du är intresserad av i PowerShell 6 och senare, måste du installera PowerShell Core i stället för Windows PowerShell. För att se [installera PowerShell Core på Windows](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Att hitta PowerShell i Windows 10, 8.1, 8.0 och 7

Ibland hitta PowerShell kan ISE (Integrated Scripting Environment) i Windows-konsolen eller konsolen vara svårt, när dess plats flyttas från en version av Windows till nästa.

I tabellerna nedan hjälper dig att hitta PowerShell i din Windows-version.
Alla versioner som anges här är den ursprungliga versionen som lanseras med inga uppdateringar.

### <a name="for-console"></a>För konsolen

Version | Position
-- | --
Windows 10 | Klicka på nedre hörnet Windows ikonen till vänster, börja skriva PowerShell
Windows 8.1, 8.0 | Börja skriva PowerShell på start-skärmen.<br/>Om du är på skrivbordet klickar du på lägre hörnet Windows ikonen till vänster, börja skriva PowerShell
Windows 7 SP1 | Klicka på nedre hörnet Windows ikonen till vänster, på att skriva PowerShell search box början

### <a name="for-ise"></a>För ISE

Version | Position
-- | --
Windows 10 | Klicka på nedre hörnet Windows ikonen till vänster, börja skriva ISE
Windows 8.1, 8.0 | Skriv på startskärmen **PowerShell ISE**.<br/>Om fältet lämnas lägre hörnikon i Windows på skrivbordet, klicka på, skriver **PowerShell ISE**
Windows 7 SP1 | Klicka på nedre hörnet Windows ikonen till vänster, på att skriva PowerShell search box början

## <a name="finding-powershell-in-windows-server-versions"></a>Att hitta PowerShell i Windows Server-versioner

Från och med Windows Server 2008 R2, installeras Windows-operativsystem utan det grafiska användargränssnittet (GUI).
Versioner av Windows Server utan GUI namnges **Core** versioner och utgåvor med det grafiska Användargränssnittet är namngivna **Desktop**.

### <a name="windows-server-core-editions"></a>Windows Server Core-utgåvor

I alla Core-utgåvor när du loggar in på servern får du du ett kommandotolksfönster i Windows.

Typ `powershell` och tryck på **RETUR** starta PowerShell i kommandotolk-session.
Typ `exit` att avsluta PowerShell-sessionen och återgår till Kommandotolken.

### <a name="windows-server-desktop-editions"></a>Windows Server-Desktop-versioner

I alla utgåvor av skrivbord, klickar du på den vänstra lägre Windows hörnikon, börja skriva PowerShell.
Du får alternativ för både konsolen och ISE.

Det enda undantaget till ovanstående är ISE i Windows Server 2008 R2 SP1; i det här fallet klickar du på den vänstra lägre Windows hörnikon, Skriv PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Hur du kontrollerar versionen av PowerShell

Starta en PowerShell-konsol (eller ISE) för att hitta vilken version av PowerShell som du har installerat, och skriv `$PSVersionTable` och tryck på **RETUR**. Leta efter den `PSVersion` värde.

## <a name="upgrading-existing-windows-powershell"></a>Uppgradera den befintliga Windows PowerShell

Installationspaketet för PowerShell kommer i ett installationsprogram för WMF.
Versionen av WMF installationsprogrammet matchar versionen av PowerShell; Det finns inget fristående installationsprogram för Windows PowerShell.

Om du vill uppdatera den befintliga versionen av PowerShell i Windows, Använd följande tabell för att hitta installationsprogrammet för den versionen av PowerShell som du vill uppdatera till.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (se Note1)<br/>Windows Server 2016 | - | - | - | installerad
Windows 8.1<br/>Windows Server 2012 R2 | - | installerad | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | installerad | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> På den första versionen av Windows 10, med automatiska uppdateringar aktiverad, uppdateras PowerShell från version 5.0 5.1.
>
> Om den ursprungliga versionen av Windows 10 inte uppdateras via Windows-uppdateringar, är versionen av PowerShell 5.0.

## <a name="need-azure-powershell"></a>Need Azure PowerShell

Om du letar efter **Azure PowerShell**, du kan börja med [översikt av Azure PowerShell](/powershell/azure/overview).

I annat fall kanske du behöver är [installera och konfigurera Azure PowerShell](/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Se även

[Windows PowerShell-systemkrav](Windows-PowerShell-System-Requirements.md)

[Starta Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)