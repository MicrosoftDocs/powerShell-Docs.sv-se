---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
title: WMF 5.1-versionskommentarer
ms.openlocfilehash: eb22267c1af28a9fcdd049c76d363fff687f6167
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Viktig information om Windows Management Framework (WMF) 5.1 #

WMF 5.1 innehåller PowerShell, WMI, WinRM och Software Inventory Logging (SIL) komponenter som släpptes med Windows Server 2016.
WMF 5.1 kan installeras på Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 och 2012 R2 och erbjuder ett antal förbättringar över WMF 5.0 RTM inklusive:

- Nya cmdlet:ar: lokala användare och grupper, Get-ComputerInfo
- PowerShellGet-förbättringarna omfattar att framtvinga signerade moduler och installera JEA-moduler
- PackageManagement har lagt till stöd för behållare, CBS-installation, EXE-baserad installation, CAB-paket
- Felsökningsförbättringar för DSC- och PowerShell-klasser
- Säkerhetsförbättringar, inklusive framtvingning av katalogsignerade moduler som kommer från Pull-servern och när du använder PowerShellGet-cmdletar
- Svar på ett antal förfrågningar och problem från användare

**Viktig information:**

- **WMF 5.1 kräver .NET Framework 4.5.2** (eller senare). Installationen lyckas, men viktiga funktioner misslyckas om .NET 4.5.2 (eller senare) har inte installerats. Instruktioner finns i den [installera och konfigurera WMF 5.1 ](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) avsnittet.
- WMF 5.1 Preview måste avinstalleras innan du installerar WMF 5.1 RTM.
- WMF 5.1 kan installeras direkt via WMF 5.0 eller WMF 4.0.
- Det är __krävs inte__ att installera WMF 4.0 innan du installerar WMF 5.1 på Windows 7 och Windows Server 2008 R2. Som var ett problem för WMF 5.1 förhandsversionen och har lösts.