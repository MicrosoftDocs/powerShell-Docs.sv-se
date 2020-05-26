---
ms.date: 08/09/2017
keywords: PowerShell, cmdlet, Hämta, installera, konfigurera, Windows 10, Windows 8,1, Windows 8.0, Windows 7
title: Installera Windows PowerShell
ms.openlocfilehash: c94ef8493c7d41bcb26c39010591319a8df8da9a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810185"
---
# <a name="installing-windows-powershell"></a>Installera Windows PowerShell

Windows PowerShell installeras som standard i alla Windows, från och med Windows 7 SP1 och Windows Server 2008 R2 SP1.

Om du är intresse rad av PowerShell 6 och senare måste du installera PowerShell core i stället för Windows PowerShell. Information om detta finns i [Installera PowerShell Core på Windows](../../install/Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Hitta PowerShell i Windows 10, 8,1, 8,0 och 7

Ibland kan det vara svårt att hitta PowerShell-konsolen eller ISE (Integrated Scripting Environment) i Windows, eftersom platsen flyttas från en version av Windows till nästa.

Följande tabeller bör hjälpa dig att hitta PowerShell i Windows-versionen. Alla versioner som visas här är den ursprungliga versionen, som släpps utan uppdateringar.

### <a name="for-console"></a>För-konsol

|     Version      |                                                            Plats                                                            |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Windows 10       | Klicka på vänster nedre hörn på Windows-ikonen, börja skriva PowerShell                                                                  |
| Windows 8,1, 8,0 | Börja skriva PowerShell på Start skärmen.<br/>Om du har på Skriv bordet, klickar du på vänster nedre hörn på Windows-ikonen, börjar skriva PowerShell |
| Windows 7 SP1    | Klicka på vänster nedre hörn på Windows-ikonen i rutan Sök börjar du skriva PowerShell                                                |

### <a name="for-ise"></a>För ISE

|     Version      |                                                            Plats                                                            |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Windows 10       | Klicka på vänster nedre hörn på Windows-ikonen, börja skriva ISE                                                                         |
| Windows 8,1, 8,0 | På Start skärmen skriver du **POWERSHELL ISE**.<br/>Om du har på Skriv bordet, klickar du på vänster nedre hörn på Windows-ikonen, skriver **POWERSHELL ISE** |
| Windows 7 SP1    | Klicka på vänster nedre hörn på Windows-ikonen i rutan Sök börjar du skriva PowerShell                                                |

## <a name="finding-powershell-in-windows-server-versions"></a>Hitta PowerShell i Windows Server-versioner

Från och med Windows Server 2008 R2 kan Windows-operativsystemet installeras utan grafiskt användar gränssnitt (GUI). Versioner av Windows Server utan GUI heter **Core** -versioner och versioner med det grafiska användar gränssnittet kallas **Skriv bord**.

### <a name="windows-server-core-editions"></a>Windows Server Core-versioner

I alla Core-versioner när du loggar till servern får du ett fönster för kommando tolken i Windows.

Skriv `powershell` och tryck på **RETUR** för att starta PowerShell i kommando tolkens session. Skriv `exit` för att avsluta PowerShell-sessionen och återgå till kommando tolken.

### <a name="windows-server-desktop-editions"></a>Windows Server Desktop-versioner

I alla Skriv bords versioner klickar du på ikonen till vänster nedre hörn i Windows och börjar skriva PowerShell. Du får både konsol-och ISE-alternativ.

Det enda undantaget till regeln ovan är ISE i Windows Server 2008 R2 SP1; i det här fallet klickar du på ikonen till vänster nedre hörn i Windows, skriver PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Kontrol lera versionen av PowerShell

Om du vill ta reda på vilken version av PowerShell som du har installerat startar du en PowerShell-konsol (eller ISE) och skriver `$PSVersionTable` och trycker på **RETUR**. Leta efter `PSVersion` värdet.

## <a name="upgrading-existing-windows-powershell"></a>Uppgradera befintliga Windows PowerShell

Installations paketet för PowerShell ingår i ett WMF-installationsprogram. Versionen av WMF-installationsprogrammet matchar versionen av PowerShell; Det finns inget fristående installations program för Windows PowerShell.

Om du behöver uppdatera din befintliga version av PowerShell i Windows, använder du följande tabell för att hitta installations programmet för den version av PowerShell som du vill uppdatera till.

|                    Windows                     |                                  PS 3,0                                   |                                  PS 4,0                                   |                                  PS 5,0                                   |                                  PS 5,1                                   |
| ---------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Windows 10 (se Note1)<br/>Windows Server 2016 | -                                                                         | -                                                                         | -                                                                         | installeras                                                                 |
| Windows 8,1<br/>Windows Server 2012 R2         | -                                                                         | installeras                                                                 | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616) |
| Windows 8<br/>Windows Server 2012              | installeras                                                                 | [WMF 4,0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616) |
| Windows 7 SP1<br/>Windows Server 2008 R2 SP1   | [WMF 3,0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4,0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616) |

> [!NOTE]
> I den första versionen av Windows 10, med aktiverade automatiska uppdateringar, uppdateras PowerShell från version 5,0 till 5,1. Om den ursprungliga versionen av Windows 10 inte uppdateras via Windows-uppdateringar är PowerShell-versionen 5,0.

## <a name="need-azure-powershell"></a>Behöver Azure PowerShell

Om du letar efter **Azure PowerShell**, kan du börja med en [Översikt över Azure PowerShell](/powershell/azure/overview).

Annars kan du behöva [Installera och konfigurera Azure PowerShell](/powershell/azure/install-az-ps)

## <a name="see-also"></a>Se även

[Windows PowerShell-systemkrav](Windows-PowerShell-System-Requirements.md)

[Starta Windows Powershell](../Starting-Windows-PowerShell.md)
