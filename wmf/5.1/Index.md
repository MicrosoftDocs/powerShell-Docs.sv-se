---
ms.date: 08/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: WMF 5.1-versionskommentarer
ms.openlocfilehash: 3081d200f0c6aac6074719bb1c204900aabf96c2
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522913"
---
# <a name="windows-management-framework-wmf-51"></a>WMF (Windows Management Framework) 5.1 #

WMF ger användare möjlighet att uppdatera befintliga Windows-datorer till de versionerna av PowerShell-, WMI-, WinRM- och SIL (Software Inventory Logging)-komponenterna som släpptes med Windows Server 2016.

WMF 5.1 kan installeras på Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 och 2012 R2 och erbjuder ett antal förbättringar över WMF 5.0 RTM inklusive:

- Nya cmdlet:ar: lokala användare och grupper, Get-ComputerInfo
- PowerShellGet-förbättringarna omfattar att framtvinga signerade moduler och installera JEA-moduler
- PackageManagement har lagt till stöd för containrar, CBS-installation, EXE-baserad installation, CAB-paket
- Felsökningsförbättringar för DSC- och PowerShell-klasser
- Säkerhetsförbättringar, inklusive framtvingning av katalogsignerade moduler som kommer från Pull-servern och när du använder PowerShellGet-cmdletar
- Svar på ett antal förfrågningar och problem från användare

Läs mer om nyheter i den här versionen genom att bläddra i avsnitten som finns under [nya scenarier och funktioner](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features).

Avsnittet [installera och konfigurera](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) listar kraven och ger installationsanvisningar för WMF.

Avsnittet [kompatibilitet](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) listar vilka versioner av WMF som kan installeras på vilka Windows-utgåvor.

[Produktkompatibilitet](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) listar de Microsoft-program som ännu inte godkänt WMF 5.1 för användning.

Information om de olika komponenterna i WMF finns i MSDN-dokumentationen:

- [PowerShell 5.1](https://docs.microsoft.com/powershell/)
- [WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)
- [WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)
- [Loggning av programvaruinventering](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)
