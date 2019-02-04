---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: WMF 5.1-versionskommentarer
ms.openlocfilehash: 205c7dc895ba47a0967ebfccfcf337ea28296f31
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685041"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Viktig information om Windows Management Framework (WMF) 5.1 #

WMF 5.1 innehåller PowerShell, WMI, WinRM och Software Inventory Logging (SIL) komponenterna som släpptes med Windows Server 2016.
WMF 5.1 kan installeras på Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 och 2012 R2 och erbjuder ett antal förbättringar över WMF 5.0 RTM inklusive:

- Nya cmdlet:ar: lokala användare och grupper, Get-ComputerInfo
- PowerShellGet-förbättringarna omfattar att framtvinga signerade moduler och installera JEA-moduler
- PackageManagement har lagt till stöd för containrar, CBS-installation, EXE-baserad installation, CAB-paket
- Felsökningsförbättringar för DSC- och PowerShell-klasser
- Säkerhetsförbättringar, inklusive framtvingning av katalogsignerade moduler som kommer från Pull-servern och när du använder PowerShellGet-cmdletar
- Svar på ett antal förfrågningar och problem från användare

**Obs!**

- **WMF 5.1 kräver .NET Framework 4.5.2** (eller senare). Installationen lyckas, men viktiga funktioner kommer att misslyckas om .NET 4.5.2 (eller senare) har inte installerats. Instruktioner finns i den [installera och konfigurera WMF 5.1 ](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) avsnittet.
- WMF 5.1 förhandsversion måste avinstalleras innan du installerar WMF 5.1 RTM.
- WMF 5.1 kan installeras direkt via WMF 5.0 eller WMF 4.0.
- Det är __krävs inte__ att installera WMF 4.0 innan du installerar WMF 5.1 på Windows 7 och Windows Server 2008 R2. Det uppstod ett problem i WMF 5.1 förhandsversionen och har lösts.
