---
description: Innehåller bakgrunds information om Windows Management Instrumentation (WMI) och Windows PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI_Cmdlets
ms.openlocfilehash: c2099c005cedf64e9621d66d6757419320c9b43e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271917"
---
# <a name="about-wmi-cmdlets"></a>Om WMI-cmdletar

## <a name="short-description"></a>KORT BESKRIVNING

Innehåller bakgrunds information om Windows Management Instrumentation (WMI) och Windows PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Det här avsnittet innehåller information om WMI-teknik, WMI-cmdletar för Windows PowerShell, WMI-baserad fjärr kommunikation, WMI-acceleratorer och WMI-felsökning. Det här avsnittet innehåller också länkar till mer information om WMI.

### <a name="about-wmi"></a>OM WMI

Windows Management Instrumentation (WMI) är Microsofts implementering av webbaserad företagshantering (WBEM), som är ett branschinitiativ för utveckling av en standardteknik för åtkomst av hanteringsinformation i en företagsmiljö. WMI använder branschstandarden CIM (Common Information Model) för att representera system, program, nätverk, enheter och andra hanterade komponenter. CIM har utvecklats och underhålls av DMTF (Distributed Management Task Force). Du kan använda WMI för att hantera både lokala och fjärranslutna datorer. Du kan till exempel använda WMI för att göra följande:

- Starta en process på en fjärrdator.
- Starta om en dator via en fjärr anslutning.
- Hämta en lista över de program som är installerade på en lokal dator eller fjärrdator.
- Fråga Windows-händelseloggen på en lokal dator eller fjärrdator.

### <a name="the-wmi-cmdlets-for-windows-powershell"></a>WMI-CMDLETAR FÖR WINDOWS POWERSHELL

Windows PowerShell implementerar WMI-funktioner via en uppsättning cmdletar som är tillgängliga i Windows PowerShell som standard. Du kan använda dessa cmdletar för att slutföra de slut punkt till slut punkts uppgifter som krävs för att hantera lokala och fjärranslutna datorer.

Följande WMI-cmdletar ingår.

|Cmdlet           |Beskrivning                                   |
|-----------------|----------------------------------------------|
|Get-WmiObject    |Hämtar instanser av WMI-klasser eller information  |
|                 |om tillgängliga klasser.                  |
|Invoke-WmiMethod |Anropar WMI-metoder.                            |
|Register-WmiEvent|Prenumererar på en WMI-händelse.                    |
|Remove-WmiObject |Tar bort WMI-klasser och-instanser.            |
|Set-WmiInstance  |Skapar eller ändrar instanser av WMI-klasser. |

### <a name="sample-commands"></a>EXEMPEL KOMMANDON
Följande kommando visar BIOS-information för den lokala datorn.

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

Följande kommando visar information om WinRM-tjänsten för tre fjärrdatorer.

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

Följande mer komplexa kommando avslutar alla instanser av ett program.

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a>WMI-BASERAD FJÄRR KOMMUNIKATION

Även om möjligheten att hantera ett lokalt system via WMI är användbar, är det fjärr kommunikations funktioner som gör WMI till ett kraftfullt administrativt verktyg. WMI använder Microsofts DCOM (Distributed Component Object Model) för att ansluta till och hantera system. Du kan behöva konfigurera vissa system för att tillåta DCOM-anslutningar.
Brand Väggs inställningar och nedlåsta DCOM-behörigheter kan blockera WMI: s möjlighet att fjärrhantera system.

### <a name="wmi-type-accelerators"></a>ACCELERATORER FÖR WMI-TYP

Windows PowerShell innehåller acceleratorer för WMI-typ. Dessa WMI-typer acceleratorer (genvägar) tillåter mer direkt åtkomst till ett WMI-objekt än en typ som inte är av typen Accelerator som tillåter.

Följande typ acceleratorer stöds med WMI:

[WMISEARCHER] – en genväg för att söka efter WMI-objekt.

[WMICLASS] – en genväg för att få åtkomst till statiska egenskaper och metoder för en klass.

[WMI] – en genväg för att hämta en enda instans av en klass.

[WMISEARCHER] är en typ Accelerator för en ManagementObjectSearcher. Det kan ta en sträng konstruktor för att skapa en sökre som du sedan kan göra en GET () på.

Ett exempel:

```powershell
PS> $s = [WmiSearcher]'Select * from Win32_Process where Handlecount > 1000'
PS> $s.Get() |sort handlecount |ft handlecount,__path,name -auto

count  __PATH                                              name
-----  ------                                              ----
1105   \\SERVER01\root\cimv2:Win32_Process.Handle="3724"   PowerShell...
1132   \\SERVER01\root\cimv2:Win32_Process.Handle="1388"   winlogon.exe
1495   \\SERVER01\root\cimv2:Win32_Process.Handle="2852"   iexplore.exe
1699   \\SERVER01\root\cimv2:Win32_Process.Handle="1204"   OUTLOOK.EXE
1719   \\SERVER01\root\cimv2:Win32_Process.Handle="1912"   iexplore.exe
2579   \\SERVER01\root\cimv2:Win32_Process.Handle="1768"   svchost.exe
```

[WMICLASS] är en typ Accelerator för ManagementClass. Detta har en sträng konstruktor som tar en lokal eller absolut WMI-sökväg till en WMI-klass och returnerar ett objekt som är kopplat till den klassen.

Ett exempel:

```powershell
PS> $c = [WMICLASS]"root\cimv2:WIn32_Process"
PS> $c |fl *
Name             : Win32_Process
__GENUS          : 1
__CLASS          : Win32_Process
__SUPERCLASS     : CIM_Process
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Process
__PROPERTY_COUNT : 45
__DERIVATION     : {CIM_Process, CIM_LogicalElement,
                   CIM_ManagedSystemElement}
__SERVER         : SERVER01
__NAMESPACE      : ROOT\cimv2
__PATH           : \\SERVER01\ROOT\cimv2:Win32_Process
```

[WMI] är en typ Accelerator för ManagementObject. Detta har en sträng konstruktor som tar en lokal eller absolut WMI-sökväg till en WMI-instans och returnerar ett objekt som är kopplat till den instansen.

Ett exempel:

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a>WMI-FELSÖKNING

Följande problem är de vanligaste problemen som kan uppstå när du försöker ansluta till en fjärrdator.

Problem 1: fjärrdatorn är inte online.

Om en dator är offline går det inte att ansluta till den med hjälp av WMI.
Du kan få följande felmeddelande:

```
Remote server machine does not exist or is unavailable
```

Om du får det här fel meddelandet kontrollerar du att datorn är online. Försök att pinga fjärran sluten dator.

Problem 2: du har inte lokal administratörs behörighet på fjärrdatorn.

Du måste ha lokal administratörs behörighet på fjärrdatorn för att kunna använda WMI via fjärr anslutning. Om du inte gör det kommer åtkomst till datorn att nekas.

För att verifiera namn områdes säkerhet:

1. Klicka på Start, högerklicka på den här datorn och klicka sedan på hantera.
2. Expandera tjänster och program i dator hantering, högerklicka på WMI-kontroll och klicka sedan på egenskaper.
3. I dialog rutan Egenskaper för WMI-kontroll klickar du på fliken säkerhet.

Problem 3: en brand vägg blockerar åtkomsten till fjärrdatorn.

WMI använder protokollen DCOM (Distributed COM) och RPC (Remote Procedure Call) för att passera nätverket. Som standard blockerar många brand väggar DCOM-och RPC-trafik. Om brand väggen blockerar dessa protokoll kommer anslutningen att Miss förväntas. Windows-brandväggen i Microsoft Windows XP Service Pack 2 är till exempel konfigurerad för att automatiskt blockera all oönskad nätverks trafik, inklusive DCOM och WMI. I standard konfigurationen avvisar Windows-brandväggen en inkommande WMI-begäran och följande fel meddelande visas:

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a>SE ÄVEN

[Om WMI](/windows/win32/wmisdk/about-wmi)

[WMI-felsökning](/windows/win32/wmisdk/wmi-troubleshooting)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[Invoke-WmiMethod](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[Registrera – WmiEvent](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[Remove-WmiObject](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[Set-WmiInstance](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
