---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Windows PowerShell-systemkrav
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: a15b5b33b5296befae833e520cfdfbd41a07b122
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell-systemkrav
Det här avsnittet beskrivs systemkraven för Windows PowerShell 3.0 och Windows PowerShell 4.0 i Windows PowerShell 5.0 och för särskilda funktioner, till exempel Windows PowerShell Integrated Scripting Environment (ISE), CIM-kommandon och arbetsflöden.

Windows® 8.1 och Windows Server® 2012 R2 inkluderar alla nödvändiga program. Det här avsnittet är avsedd för användare av tidigare versioner av Windows.

## <a name="operating-system-requirements"></a>Krav på operativsystem
Windows PowerShell 5.0 körs på följande versioner av Windows.

- Windows Server 2016 installeras som standard

- Windows Server 2012 R2, installera [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) att köra Windows PowerShell 5.0

- Installera Windows Server 2012, [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) att köra Windows PowerShell 5.0

- Installera Windows Server 2008 R2 med Service Pack 1 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) att köra Windows PowerShell 5.0

- Windows 8.1

- Installera Windows 7 med Service Pack 1, [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) att köra Windows PowerShell 5.0

Windows PowerShell 4.0 körs på följande versioner av Windows.

- Windows 8.1, installeras som standard

- Windows Server 2012 R2, installeras som standard

- Installera Windows 7 med Service Pack 1 [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) att köra Windows PowerShell 4.0

- Windows Server® 2008 R2 med Service Pack 1, installera [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) att köra Windows PowerShell 4.0

Windows PowerShell 3.0 körs på följande versioner av Windows.

- Windows 8 installeras som standard

- Windows Server 2012, installeras som standard

- Installera Windows 7 med Service Pack 1 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) att köra Windows PowerShell 3.0

- Windows Server® 2008 R2 med Service Pack 1, installera [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) att köra Windows PowerShell 3.0

- Windows Server 2008 med Service Pack 2, installera [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) att köra Windows PowerShell 3.0

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework-krav
Windows PowerShell 5.0 kräver en fullständig installation av Microsoft .NET Framework 4.5. Windows 8.1 och Windows Server 2012 R2 innehåller Microsoft .NET Framework 4.5 som standard.

Windows PowerShell 4.0 kräver en fullständig installation av Microsoft .NET Framework 4.5. Windows 8.1 och Windows Server 2012 R2 innehåller Microsoft .NET Framework 4.5 som standard.

Windows PowerShell 3.0 kräver en fullständig installation av Microsoft .NET Framework 4. Windows 8 och Windows Server 2012 ingår Microsoft .NET Framework 4.5 som standard, vilket uppfyller detta krav.

Om du vill installera Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) på Microsoft Download Center.

Om du vill installera en fullständig installation av Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) [Microsoft .NET Framework 4 (Webbinstallationsprogram)](http://go.microsoft.com/fwlink/?LinkID=212931) på Microsoft Download Center.

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0
Windows PowerShell 5.0 kräver Windows Management Framework 4.0 ska förinstalleras på Windows Server 2008 R2 SP1 och Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3.0
Windows PowerShell 3.0 och Windows PowerShell 4.0 kräver att 3.0 för WS-Management, som har stöd för WinRM-tjänsten och WSMan-protokollet. Programmet ingår i Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 och Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3.0
Windows PowerShell 3.0 och Windows PowerShell 4.0 kräver Windows Management Instrumentation 3.0 (WMI). Programmet ingår i Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 och Windows Management Framework 3.0. Om programmet inte är installerat på datorn kör inte funktioner som kräver WMI, till exempel CIM-kommandon.

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0
Windows PowerShell 3.0 och Windows PowerShell 4.0 Windows PowerShell 5.0 kompileras mot Runtime CLR (Common Language) 4.0.

## <a name="graphical-user-interface-requirements"></a>Kraven för grafiskt gränssnitt
Windows PowerShell är ett program med konsolen som inte kräver ett grafiskt användargränssnitt. Därför är den utmärkt för datorer som inte har skärmar eller Övervakare eller en användargränssnittet, till exempel installationsalternativet Server Core av Windows Server 2012 R2 eller Windows Server 2012.

Men vissa objekt, till exempel följande, kräver ett grafiskt användargränssnitt. Mer information finns i hjälpavsnittet för varje objekt.

- Windows PowerShell® Integrated Scripting Environment (ISE)

- Cmdletar

    1.  [Out-GridView-kontrollen](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Visa kommando](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Show-ControlPanelItem](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Show-EventLog](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- Parametrar

    1.  **ShowWindow** parameter för den [Get-Help](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.

    2.  **ShowSecurityDescriptorUI** parameter för den [Register-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) och [Set-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) cmdlets.

## <a name="windows-powershell-engine-requirements"></a>Krav för Windows PowerShell-motorn
Windows PowerShell 4.0 är avsedd att vara bakåtkompatibla med Windows PowerShell 3.0 och Windows PowerShell 2.0. Cmdlets, providers, snapin-moduler, moduler och skript som är skrivna för Windows PowerShell 2.0 och Windows PowerShell 3.0 kör oförändrad i Windows PowerShell 4.0.

Men på grund av en ändring i principen runtime aktivering i Microsoft .NET Framework 4 även Windows PowerShell värd för program som har skrivits för Windows PowerShell 2.0 och kompileras med Runtime CLR (Common Language) 2.0 kan inte köras utan ändringar i Windows PowerShell 3.0 som kompileras med CLR-4.0.

Windows PowerShell 2.0-motorn kräver Microsoft .NET Framework 2.0.50727 minst. Detta krav uppfylls genom att Microsoft .NET Framework 3.5 servicepack 1. Detta krav uppfylls inte av Microsoft .NET Framework 4 och senare versioner av Microsoft .NET Framework.

Information om att lägga till eller installera Windows PowerShell 2.0-motorn och lägga till eller installera de nödvändiga versionerna av Microsoft .NET Framework finns [installera Windows PowerShell 2.0 Engine](Installing-the-Windows-PowerShell-2.0-Engine.md). Information om hur du startar Windows PowerShell 2.0-motorn finns [starta Windows PowerShell 2.0 motorn](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Windows Preinstallation Environment
Windows PowerShell 2.0, Windows PowerShell 3.0 och Windows PowerShell 4.0 körs i Windows PE (Windows Preinstallation Environment). Följande cmdlets kan inte användas.

- [Background Intelligent Transfer Service (BITS)-Cmdlets](http://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-EventLog](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Save-Help](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Update-Help](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Dessutom den **WinRM** tjänsten finns inte på Windows PE.

## <a name="see-also"></a>Se även
- [Komma igång med Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [Installera Windows PowerShell](Installing-Windows-PowerShell.md)
- [Starta Windows PowerShell](Starting-Windows-PowerShell.md)