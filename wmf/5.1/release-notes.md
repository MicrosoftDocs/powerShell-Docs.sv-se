---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
title: WMF 5.1 viktig information
ms.openlocfilehash: ce9bc7791facfcc2cce9468689e88a26154bda7d
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Viktig information om Windows Management Framework (WMF) 5.1 #

WMF 5.1 innehåller PowerShell, WMI, WinRM och Software Inventory Logging (SIL) komponenter som släpptes med Windows Server 2016.
WMF 5.1 kan installeras på Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 och 2012 R2, och ger ett antal förbättringar över WMF 5.0 RTM inklusive:

- Nya cmdlet: ar: lokala användare och grupper. Get-ComputerInfo
- PowerShellGet förbättringar omfattar att använda signerade moduler och installera JEA moduler
- PackageManagement tillagt stöd för behållare, CBS installationsprogrammet EXE-baserad installation, CAB-paket
- Förbättringar av DSC-och PowerShell-felsökning
- Förbättringar av säkerhet inklusive tillämpning av katalogen signerats moduler som kommer från servern hämtar och när du använder PowerShellGet-cmdlets
- Svar på ett antal frågor och problem

**Viktig information:**

- **WMF 5.1 kräver .NET Framework 4.5.2** (eller senare). Installationen lyckas, men viktiga funktioner misslyckas om .NET 4.5.2 (eller senare) har inte installerats. Instruktioner finns i den [installera och konfigurera WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) avsnittet.
- WMF 5.1 Preview måste avinstalleras innan du installerar WMF 5.1 RTM.
- WMF 5.1 kan installeras direkt via WMF 5.0 eller WMF 4.0.
- Det är __krävs inte__ att installera WMF 4.0 innan du installerar WMF 5.1 på Windows 7 och Windows Server 2008 R2. Som var ett problem för WMF 5.1 förhandsversionen och har lösts.  


