---
ms.date: 08/21/2020
keywords: powershell,cmdlet
title: Kör fjärrkommandon
description: Förklarar metoder för att köra kommandon på fjärrdatorer med hjälp av PowerShell.
ms.openlocfilehash: cff18a4f51c3ed8e3ed2c1f35862a88911e7ceb5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "94391416"
---
# <a name="running-remote-commands"></a>Kör fjärrkommandon

Du kan köra kommandon på en eller flera hundra datorer med ett enda PowerShell-kommando. Windows PowerShell stöder fjärrhantering med hjälp av olika tekniker, inklusive WMI, RPC och WS-Management.

PowerShell-kärnan stöder WMI, WS-Management och SSH-fjärrkommunikation. I PowerShell 6 stöds inte längre RPC. I PowerShell 7 och senare stöds endast RPC i Windows.

Mer information om fjärr kommunikation i PowerShell Core finns i följande artiklar:

- [SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]
- [WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Windows PowerShell-fjärrkommunikation utan konfiguration

Många Windows PowerShell-cmdlets har parametern ComputerName som gör att du kan samla in data och ändra inställningar på en eller flera fjärrdatorer. Dessa cmdletar använder varierande kommunikations protokoll och fungerar på alla Windows-operativsystem utan någon särskild konfiguration.

Dessa cmdlet: ar är:

- [Starta om datorn](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Rensa-EventLog](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Hämta process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

Normalt är cmdletar som stöder fjärr kommunikation utan särskild konfiguration att ha parametern ComputerName och inte parametern session. Om du vill hitta dessa cmdletar i din session skriver du:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell-fjärrkommunikation

Med hjälp av WS-Management-protokollet kan Windows PowerShell-fjärrkommunikation köra alla Windows PowerShell-kommandon på en eller flera fjärrdatorer. Du kan upprätta beständiga anslutningar, starta interaktiva sessioner och köra skript på fjärrdatorer.

Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.
Mer information, inklusive instruktioner, finns i [om krav för fjärrhantering](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

När du har konfigurerat Windows PowerShell-fjärrkommunikation är många olika kommunikations strategier tillgängliga för dig.
I den här artikeln listas bara några av dem. Mer information finns i [om fjärran sluten](/powershell/module/microsoft.powershell.core/about/about_remote).

### <a name="start-an-interactive-session"></a>Starta en interaktiv session

Om du vill starta en interaktiv session med en enda fjärrdator använder du cmdleten [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) . Om du till exempel vill starta en interaktiv session med Server01 fjärrdator skriver du:

```powershell
Enter-PSSession Server01
```

Kommando tolken ändras för att visa namnet på fjärrdatorn. Alla kommandon som du skriver vid prompten körs på fjärrdatorn och resultaten visas på den lokala datorn.

Om du vill avsluta den interaktiva sessionen skriver du:

```powershell
Exit-PSSession
```

Mer information om Enter-PSSession-och Exit-PSSession-cmdlet: ar finns i:

- [Retur-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Avsluta-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Köra ett fjärrkommando

Om du vill köra ett kommando på en eller flera datorer använder du cmdleten [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) . Om du till exempel vill köra kommandot [Get-värdet](/powershell/module/microsoft.powershell.utility/get-uiculture) på fjärrdatorerna Server01 och Server02, skriver du:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

Utdata returneras till datorn.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Kör ett skript

Om du vill köra ett skript på en eller flera fjärrdatorer använder du parametern sökväg för `Invoke-Command` cmdleten. Skriptet måste vara på eller tillgängligt för den lokala datorn. Resultatet returneras till den lokala datorn.

Följande kommando kör till exempel DiskCollect.ps1-skriptet på fjärrdatorerna, Server01 och Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Upprätta en permanent anslutning

Använd `New-PSSession` cmdleten för att skapa en beständig session på en fjärrdator. I följande exempel skapas fjärrsessioner på Server01 och Server02. Sessions-objekten lagras i `$s` variabeln.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Nu när sessionerna har upprättats kan du köra alla kommandon i dem. Och eftersom sessionerna är permanenta kan du samla in data från ett kommando och använda det i ett annat kommando.

Följande kommando kör till exempel ett Get-HotFix-kommando i sessionerna i $s-variabeln och sparar resultatet i $h variabeln. Variabeln $h skapas i varje session i $s, men den finns inte i den lokala sessionen.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Nu kan du använda data i `$h` variabeln med andra kommandon i samma session. Resultaten visas på den lokala datorn. Exempel:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Avancerad fjärr kommunikation

Windows PowerShell-fjärrhantering börjar bara här. Genom att använda de cmdletar som installeras med Windows PowerShell kan du upprätta och konfigurera fjärrsessioner både från lokala och fjärranslutna platser, skapa anpassade och begränsade sessioner, tillåta användare att importera kommandon från en fjärrsession som faktiskt körs implicit i fjärrsessionen, konfigurera säkerheten för en fjärrsession och mycket mer.

Windows PowerShell innehåller en WSMan-Provider. Providern skapar en `WSMAN:` enhet som gör det möjligt att navigera i en hierarki med konfigurations inställningar på den lokala datorn och fjärrdatorer.

Mer information om WSMan-providern finns i [WSMan-providern](/powershell/module/microsoft.wsman.management/about/about_wsman_provider) och [om WS-Management cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), eller i Windows PowerShell-konsolen skriver du `Get-Help wsman` .

Mer information finns i:

- [Om vanliga frågor och svar om fjärr anslutning](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [Registrera – PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [Importera – PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

Hjälp med fjärr kommunikations fel finns i [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting).

## <a name="see-also"></a>Se även

- [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [about_Remote_FAQ](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
- [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting)
- [about_PSSessions](/powershell/module/microsoft.powershell.core/about/about_PSSessions)
- [about_WS-Management_Cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets)
- [Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Importera – PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Registrera – PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [WSMan-Provider](/powershell/module/microsoft.wsman.management/about/about_wsman_provider)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
