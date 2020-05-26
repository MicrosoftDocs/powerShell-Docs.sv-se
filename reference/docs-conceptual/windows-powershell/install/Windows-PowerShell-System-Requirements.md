---
ms.date: 12/06/2019
keywords: powershell,cmdlet
title: Windows PowerShell-systemkrav
ms.openlocfilehash: 7c6e055cda8493651a7838b4ffc9a933032d9c0f
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809989"
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell-systemkrav

Den här artikeln innehåller en lista över system kraven för Windows PowerShell 3,0, Windows PowerShell 4,0, Windows PowerShell 5,0 och Windows PowerShell 5,1. Och särskilda funktioner, till exempel Windows PowerShell ISE (Integrated Scripting Environment), Common Information Model (CIM) kommandon och arbets flöden.

Windows® 8,1 och Windows Server® 2012 R2 innehåller alla program som krävs. Den här artikeln är avsedd för användare av tidigare versioner av Windows.

## <a name="operating-system-requirements"></a>Operativsystemskrav

### <a name="windows-powershell-51"></a>Windows PowerShell 5,1

Windows PowerShell 5,1 körs i följande versioner av Windows. Installera Windows Management Framework 5,1 för att köra Windows PowerShell 5,1. Mer information finns i [Installera och konfigurera WMF 5,1](../wmf/setup/install-configure.md).

|              Windows-version               |                           Systemkrav                            |
| ------------------------------------------ | ----------------------------------------------------------------------- |
| Windows Server 2019                        | Installeras som standard                                                    |
| Windows Server 2016                        | Installeras som standard                                                    |
| Windows Server 2012 R2                     | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows Server 2012                        | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 med Service Pack 1 | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 10 version 1607 och senare             | Installeras som standard                                                    |
| Windows 10, version 1507, 1511              | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 8,1                                | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 7 med Service Pack 1              | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-50"></a>Windows PowerShell 5.0

Windows PowerShell 5,0 körs i följande versioner av Windows. Installera Windows Management Framework 5,1 för att köra Windows PowerShell 5,0. Mer information finns i [Installera och konfigurera WMF 5,1](../wmf/setup/install-configure.md). Windows Management Framework 5,1 ersätter Windows Management Framework 5,0.

|              Windows-version               |                           Systemkrav                            |
| ------------------------------------------ | ----------------------------------------------------------------------- |
| Windows Server 2019                        | Högre version installeras som standard                                     |
| Windows Server 2016                        | Högre version installeras som standard                                     |
| Windows Server 2012 R2                     | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows Server 2012                        | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 med Service Pack 1 | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 10 version 1607 och senare             | Högre version installeras som standard                                     |
| Windows 10, version 1507, 1511              | Installeras som standard                                                    |
| Windows 8,1                                | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 7 med Service Pack 1              | Installera [Windows Management Framework 5,1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-40"></a>Windows PowerShell 4.0

Windows PowerShell 4,0 körs i följande versioner av Windows. Om du vill köra Windows PowerShell 4,0 installerar du den angivna versionen av Windows Management Framework för ditt operativ system.

|               Windows-version               |                                             Systemkrav                                             |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Windows 8,1                                 | Installeras som standard                                                                                       |
| Windows Server 2012 R2                      | Installeras som standard                                                                                       |
| Windows® 7 med Service Pack 1              | Installera [Windows Management Framework 4,0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |
| Windows Server® 2008 R2 med Service Pack 1 | Installera [Windows Management Framework 4,0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |

### <a name="windows-powershell-30"></a>Windows PowerShell 3.0

Windows PowerShell 3,0 körs i följande versioner av Windows. Om du vill köra Windows PowerShell 3,0 installerar du den angivna versionen av Windows Management Framework för ditt operativ system.

|               Windows-version               |                                             Systemkrav                                             |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Windows 8                                   | Installeras som standard                                                                                       |
| Windows Server 2012                         | Installeras som standard                                                                                       |
| Windows® 7 med Service Pack 1              | Installera [Windows Management Framework 3,0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server® 2008 R2 med Service Pack 1 | Installera [Windows Management Framework 3,0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server 2008 med Service Pack 2     | Installera [Windows Management Framework 3,0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |

## <a name="microsoft-net-framework-requirements"></a>Krav för Microsoft .NET Framework

I följande tabell visas .NET Framework krav för Windows PowerShell.

|        Version         |                                                                                 .NET-krav                                                                                  |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Windows PowerShell 5,1 | Kräver en fullständig installation av Microsoft .NET Framework 4,5. Windows 8,1 och Windows Server 2012 R2 inkluderar Microsoft .NET Framework 4,5 som standard.                           |
| Windows PowerShell 5.0 | Kräver en fullständig installation av Microsoft .NET Framework 4,5. Windows 8,1 och Windows Server 2012 R2 inkluderar Microsoft .NET Framework 4,5 som standard.                           |
| Windows PowerShell 4.0 | Kräver en fullständig installation av Microsoft .NET Framework 4,5. Windows 8,1 och Windows Server 2012 R2 inkluderar Microsoft .NET Framework 4,5 som standard.                           |
| Windows PowerShell 3.0 | Kräver en fullständig installation av Microsoft .NET Framework 4. Windows 8 och Windows Server 2012 innehåller Microsoft .NET Framework 4,5 som standard, vilket uppfyller det här kravet. |

Använd följande länkar för att ladda ned Microsoft .NET Framework från Microsoft Download Center.

|                     Version                      |                                                     Länk                                                     |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| .NET Framework 4,5 ( `dotNetFx45_Full_setup.exe` ) | [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919)                               |
| .NET Framework 4 ( `dotNetFx40_Full_setup.exe` )   | [Microsoft .NET Framework 4 (webb installations program)](https://www.microsoft.com/en-us/download/details.aspx?id=17851) |

## <a name="windows-management-framework-40"></a>Windows Management Framework 4,0

Windows PowerShell 5,0 kräver att Windows Management Framework 4,0 förinstalleras på Windows Server 2008 R2 SP1 och Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3,0

Windows PowerShell 3,0 och Windows PowerShell 4,0 kräver WS-Management 3,0, som stöder WinRM-tjänsten och WSMan-protokollet. Det här programmet ingår i Windows 8,1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4,0 och Windows Management Framework 3,0.

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3,0

Windows PowerShell 3,0 och Windows PowerShell 4,0 kräver Windows Management Instrumentation 3,0 (WMI). Det här programmet ingår i Windows 8,1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4,0 och Windows Management Framework 3,0. Om programmet inte är installerat på datorn körs inte funktioner som kräver WMI, till exempel CIM-kommandon.

## <a name="common-language-runtime-40"></a>CLR (Common Language Runtime) 4,0

Windows PowerShell 3,0, Windows PowerShell 4,0 och Windows PowerShell 5,0 kompileras mot CLR (Common Language Runtime) 4,0.

## <a name="graphical-user-interface-requirements"></a>Grafiska användar gränssnitts krav

Windows PowerShell är ett konsol program som inte kräver ett grafiskt användar gränssnitt.
Det passar bra för datorer som inte har skärmar eller skärmar, eller ett användar gränssnitt, till exempel alternativ för Server Core-installation av Windows Server 2012 R2 eller Windows Server 2012.

Vissa objekt kräver ett grafiskt användar gränssnitt. Mer information finns i hjälp artikeln för varje objekt.

- Windows PowerShell ISE (Integrated Scripting Environment). Mer information finns i [Introduktion till Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).
- Cmdletar
  - [Out-GridView](/powershell/module/microsoft.powershell.utility/out-gridview)
  - [Visa-kommando](/powershell/module/Microsoft.PowerShell.Utility/Show-Command)
  - [Visa ControlPanelItem](/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)
  - [Visa-EventLog](/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)
- Parametrar
  - **ShowWindow** -parameter för cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) .
  - Parametern **ShowSecurityDescriptorUI** för cmdletarna [register-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) och [set-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) .

## <a name="windows-powershell-engine-requirements"></a>Krav för Windows PowerShell-motor

Windows PowerShell 4,0 är avsett att vara bakåtkompatibla med Windows PowerShell 3,0 och Windows PowerShell 2,0. Cmdlets, providers, snapin-moduler, moduler och skript som skrivits för Windows PowerShell 2,0 och Windows PowerShell 3,0 körs oförändrade i Windows PowerShell 4,0.

Men på grund av en ändring i aktiverings principen för körning i Microsoft .NET Framework 4, kan Windows PowerShell-värdprogram som skrivits för Windows PowerShell 2,0 och kompileras med CLR (Common Language Runtime) 2,0 inte köras utan modifiering i Windows PowerShell 3,0, som kompileras med CLR 4,0.

Minimi kravet för Windows PowerShell 2,0-motorn är Microsoft .NET Framework-2.0.50727. Detta krav uppfylls av Microsoft .NET Framework 3,5 Service Pack 1. Detta krav uppfylls inte av Microsoft .NET Framework 4 och senare versioner av Microsoft .NET Framework.

Information om hur du lägger till eller installerar Windows PowerShell 2,0-motorn och lägger till eller installerar de versioner av Microsoft .NET Framework som krävs finns i [Installera Windows powershell 2,0-motorn](Installing-the-Windows-PowerShell-2.0-Engine.md). Information om hur du startar Windows PowerShell 2,0-motorn finns i [Starta Windows PowerShell 2,0-motorn](../Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Windows Preinstallation Environment

Windows PowerShell 2,0, Windows PowerShell 3,0 och Windows PowerShell 4,0 körs i Windows Preinstallation Environment (Windows PE). Följande cmdletar stöds dock inte.

- Background Intelligent Transfer Service-cmdletar (BITS). Mer information finns i [BitsTransfer](/powershell/module/bitstransfer/?view=win10-ps).
- [Get-EventLog](/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)
- [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)
- [Spara – hjälp](/powershell/module/Microsoft.PowerShell.Core/Save-Help)
- [Uppdatera – hjälp](/powershell/module/Microsoft.PowerShell.Core/Update-Help)

**WinRM** -tjänsten finns inte i Windows PE.

## <a name="see-also"></a>Se även

[Installera Windows PowerShell](Installing-Windows-PowerShell.md)

[Starta Windows Powershell](../Starting-Windows-PowerShell.md)

[Windows Management Framework](../wmf/overview.md)
