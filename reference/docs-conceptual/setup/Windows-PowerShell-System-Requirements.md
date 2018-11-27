---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Windows PowerShell-systemkrav
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: 8850cf26b0313dfb8898ccb66b4767d695860d4c
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320745"
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell-systemkrav
Det här avsnittet beskrivs systemkraven för Windows PowerShell 3.0, Windows PowerShell 4.0 och Windows PowerShell 5.0 och Windows PowerShell 5.1 och för särskilda funktioner, till exempel Windows PowerShell Integrated Scripting Environment (ISE), CIM-kommandon, och arbetsflöden.

Windows® 8.1 och Windows Server® 2012 R2 inkluderar alla nödvändiga program. Det här avsnittet är utformat för användare av tidigare versioner av Windows.

## <a name="operating-system-requirements"></a>Operativsystemkrav
Windows PowerShell 5.1 körs på följande versioner av Windows.

- Windows Server 2019, installeras som standard

- Windows Server 2016, installeras som standard

- Windows Server 2012 R2, installera [Windows Management Framework 5.1](https://aka.ms/wmf5download) att köra Windows PowerShell 5.1

- Installera Windows Server 2012, [Windows Management Framework 5.1](https://aka.ms/wmf5download) att köra Windows PowerShell 5.0

- Windows Server 2008 R2 med Service Pack 1, installera [Windows Management Framework 5.1](https://aka.ms/wmf5download) att köra Windows PowerShell 5.1

- Windows 10 version 1607 och upp - installeras som standard

- Installera Windows 10 version 1507, 1511 - [Windows Management Framework 5.1](https://aka.ms/wmf5download) att köra Windows PowerShell 5.1

- Windows 8.1, installera [Windows Management Framework 5.1](https://aka.ms/wmf5download) att köra Windows PowerShell 5.1

- Installera Windows 7 med Service Pack 1, [Windows Management Framework 5.1](https://aka.ms/wmf5download) att köra Windows PowerShell 5.1

Windows PowerShell 5.0 (Superceeded av Windows PowerShell 5.1) körs på följande versioner av Windows.

- Windows Server 2019, högre version som installeras som standard

- Windows Server 2016, högre version som installeras som standard

- Windows Server 2012 R2, installera [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) att köra Windows PowerShell 5.0

- Installera Windows Server 2012, [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) att köra Windows PowerShell 5.0

- Windows Server 2008 R2 med Service Pack 1, installera [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) att köra Windows PowerShell 5.0

- Windows 10 version 1607 och upp – högre version som installeras som standard

- Windows 10 version 1507, 1511 - installeras som standard

- Windows 8.1, installera [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) att köra Windows PowerShell 5.0

- Installera Windows 7 med Service Pack 1, [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) att köra Windows PowerShell 5.0

Windows PowerShell 4.0 körs på följande versioner av Windows.

- Windows 8.1, installeras som standard

- Windows Server 2012 R2 som installeras som standard

- Windows® 7 med Service Pack 1, installera [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) att köra Windows PowerShell 4.0

- Windows Server® 2008 R2 med Service Pack 1, installera [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) att köra Windows PowerShell 4.0

Windows PowerShell 3.0 körs på följande versioner av Windows.

- Windows 8 installeras som standard

- Windows Server 2012, installeras som standard

- Windows® 7 med Service Pack 1, installera [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) att köra Windows PowerShell 3.0

- Windows Server® 2008 R2 med Service Pack 1, installera [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) att köra Windows PowerShell 3.0

- Windows Server 2008 med Service Pack 2, installera [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) att köra Windows PowerShell 3.0

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework-krav
Windows PowerShell 5.1 kräver den fullständiga installationen av Microsoft .NET Framework 4.5. Windows 8.1 och Windows Server 2012 R2 inkluderar Microsoft .NET Framework 4.5 som standard.

Windows PowerShell 5.0 kräver den fullständiga installationen av Microsoft .NET Framework 4.5. Windows 8.1 och Windows Server 2012 R2 inkluderar Microsoft .NET Framework 4.5 som standard.

Windows PowerShell 4.0 kräver den fullständiga installationen av Microsoft .NET Framework 4.5. Windows 8.1 och Windows Server 2012 R2 inkluderar Microsoft .NET Framework 4.5 som standard.

Windows PowerShell 3.0 kräver den fullständiga installationen av Microsoft .NET Framework 4. Windows 8 och Windows Server 2012 innehåller Microsoft .NET Framework 4.5 som standard, vilket uppfyller det här kravet.

Om du vill installera Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), se [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919) på Microsoft Download Center.

Om du vill installera den fullständiga installationen av Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), se [Microsoft .NET Framework 4 (Webbinstallationsprogram)](https://go.microsoft.com/fwlink/?LinkID=212931) på Microsoft Download Center.

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0
Windows PowerShell 5.0 kräver Windows Management Framework 4.0 ska förinstalleras på Windows Server 2008 R2 SP1 och Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3.0
Windows PowerShell 3.0 och Windows PowerShell 4.0 kräver WS-Management 3.0, som har stöd för WinRM-tjänsten och WSMan-protokollet. Det här programmet ingår i Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 och Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3.0
Windows PowerShell 3.0 och Windows PowerShell 4.0 kräver Windows Management Instrumentation 3.0 (WMI). Det här programmet ingår i Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 och Windows Management Framework 3.0. Om det här programmet inte är installerad på datorn, kör inte funktioner som kräver WMI, till exempel CIM-kommandon.

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0
Windows PowerShell 3.0 och Windows PowerShell 4.0 Windows PowerShell 5.0 kompileras mot Runtime CLR (Common Language) 4.0.

## <a name="graphical-user-interface-requirements"></a>Grafiska gränssnittet krav
Windows PowerShell är ett konsol-baserade program som inte kräver ett grafiskt användargränssnitt. Därför är det väl lämpade för datorer som inte har skärmar eller Övervakare eller en användargränssnittet, till exempel installationsalternativet Server Core av Windows Server 2012 R2 eller Windows Server 2012.

Men vissa objekt, till exempel följande, kräver ett grafiskt användargränssnitt. Mer information finns i hjälpavsnittet för varje objekt.

- Windows PowerShell® Integrated Scripting Environment (ISE)

- Cmdletar

    1.  [Out-GridView.](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Visa kommando](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Visa ControlPanelItem](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Visa händelseloggen](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- Parametrar

    1.  **ShowWindow** -parametern för den [Get-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.

    2.  **ShowSecurityDescriptorUI** -parametern för den [Register-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) och [Set-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) cmdletar.

## <a name="windows-powershell-engine-requirements"></a>Krav för Windows PowerShell-motorn
Windows PowerShell 4.0 är avsett att vara bakåtkompatibla med Windows PowerShell 3.0 och Windows PowerShell 2.0. Cmdlet: ar, leverantörer, snapin-moduler, moduler och skript som har skrivits för Windows PowerShell 2.0 och Windows PowerShell 3.0 kör oförändrad i Windows PowerShell 4.0.

Men på grund av en ändring i principen runtime aktivering i Microsoft .NET Framework 4, även Windows PowerShell-värd program som har skrivits för Windows PowerShell 2.0 och kompileras med Runtime CLR (Common Language) 2.0 kan inte köras utan ändringar i Windows PowerShell 3.0 som kompileras med CLR 4.0.

Windows PowerShell 2.0-motorn kräver Microsoft .NET Framework 2.0.50727 minst. Detta krav uppfylls genom att Microsoft .NET Framework 3.5 servicepack 1. Detta krav uppfylls inte av Microsoft .NET Framework 4 och senare versioner av Microsoft .NET Framework.

Information om att lägga till eller installera Windows PowerShell 2.0-motorn och lägga till eller installera de nödvändiga versionerna av Microsoft .NET Framework finns i [installera Windows PowerShell 2.0-motorn](Installing-the-Windows-PowerShell-2.0-Engine.md). Information om att starta Windows PowerShell 2.0-motorn, finns i [starta Windows PowerShell 2.0-motorn](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Windows Preinstallation Environment
Windows PowerShell 2.0, Windows PowerShell 3.0 och Windows PowerShell 4.0 körs i Windows Preinstallation Environment (Windows PE). Följande cmdletar stöds dock inte.

- [Background Intelligent Transfer Service (BITS)-cmdletar](https://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-händelseloggen](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Save-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Update-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Dessutom den **WinRM** finns inte på Windows PE.

## <a name="see-also"></a>Se även
- [Komma igång med Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [Installera Windows PowerShell](Installing-Windows-PowerShell.md)
- [Starta Windows PowerShell](Starting-Windows-PowerShell.md)
