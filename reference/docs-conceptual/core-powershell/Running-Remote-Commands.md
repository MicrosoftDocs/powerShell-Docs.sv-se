---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Kör fjärrkommandon
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: d21d1def1e25895f65b3578bf2892d56f14cc150
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482887"
---
# <a name="running-remote-commands"></a>Kör fjärrkommandon

Du kan köra kommandon på en eller flera hundra datorer med ett enda Windows PowerShell-kommando. Windows PowerShell stöder fjärrhantering med hjälp av olika teknologier, inklusive WMI-, RPC- och WS-Management.

## <a name="remoting-in-powershell-core"></a>Fjärrkommunikation i PowerShell Core

PowerShell Core, den nya versionen av PowerShell på Windows-, macOS- och Linux, stöder WMI, WS-Management och fjärrkommunikation med SSH.
(RPC stöds inte längre.)

Mer information om hur du konfigurerar detta finns i:

* [SSH fjärrkommunikation i PowerShell Core][ssh-remoting]
* [WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]

## <a name="remoting-without-configuration"></a>Fjärrkommunikation utan konfiguration

Många Windows PowerShell-cmdlets har parametern ComputerName som gör det möjligt att samla in data och ändra inställningar på en eller flera fjärrdatorer. De använder olika kommunikationsteknik och många arbete på alla Windows-operativsystem som har stöd för Windows PowerShell utan någon specialkonfiguration.

Dessa cmdletar är:

* [Starta om datorn](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Testa anslutning](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Rensa händelseloggen](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-händelseloggen](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get-HotFix](https://go.microsoft.com/fwlink/?LinkId=821586)
* [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Ange tjänst](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

Normalt har parametern ComputerName cmdlets som stöder fjärrkommunikation utan särskild konfiguration och har inte parametern Session. Om du vill söka efter dessa cmdlets i sessionen, skriver du:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell-fjärrkommunikation

Windows PowerShell-fjärrkommunikation, som använder protokollet WS-Management, kan du köra Windows PowerShell-kommando på en eller flera fjärrdatorer. Gör det möjligt att upprätta beständiga anslutningar, starta 1:1 interaktiva sessioner och köra skript på flera datorer.

Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering. Mer information, inklusive instruktioner finns i [om Remote krav](https://technet.microsoft.com/library/dd315349.aspx).

När du har konfigurerat Windows PowerShell-fjärrkommunikation finns många fjärrkommunikation strategier för dig. Resten av det här dokumentet visar några av dem. Mer information finns i [om Remote](https://technet.microsoft.com/library/dd347744.aspx) och [om Remote vanliga frågor och svar](https://technet.microsoft.com/library/dd347744.aspx).

### <a name="start-an-interactive-session"></a>Starta en interaktiv Session

Starta en interaktiv session med en enda fjärrdator med den [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.
Skriv till exempel om du vill starta en interaktiv session med Server01 fjärrdatorn:

```powershell
Enter-PSSession Server01
```

Kommandotolken ändras och visar namnet på den dator som du är ansluten. Därefter alla kommandon som du anger i Kommandotolken kör på fjärrdatorn och resultatet visas på den lokala datorn.

Om du vill avsluta den interaktiva sessionen, skriver du:

```powershell
Exit-PSSession
```

Mer information om Enter-PSSession och avsluta-PSSession cmdlets finns [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) och [avsluta-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).

### <a name="run-a-remote-command"></a>Kör ett kommando

Kör kommandon på en eller flera fjärrdatorer med den [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.
Till exempel för att köra en [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) på Server01 och Server02 fjärrdatorerna, typ:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

Resultatet returneras till din dator.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

Mer information om cmdleten Invoke-Command finns [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="run-a-script"></a>Köra ett skript

Använd parametern FilePath för Invoke-Command-cmdlet om du vill köra ett skript på en eller flera fjärrdatorer. Skriptet måste vara på eller tillgänglig för den lokala datorn. Resultaten returneras till den lokala datorn.

Exempelvis kör följande kommando DiskCollect.ps1 skriptet på fjärrdatorer Server01 och Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

Mer information om cmdleten Invoke-Command finns [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="establish-a-persistent-connection"></a>Upprätta en beständig anslutning

Skapa en session på fjärrdatorn för att köra en serie relaterade kommandon som delar data, och sedan använda cmdleten Invoke-Command för att köra kommandon i sessionen som du skapar. Använd cmdleten New-PSSession om du vill skapa en fjärrsession.

Följande kommando skapar en fjärrsession på Server01 dator och en annan fjärrsession på Server02 dator. Session-objekt sparas i variabeln $s.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Nu när sessioner upprättas, kan du köra ett kommando i dem. Och eftersom sessioner är beständiga samla in data i ett kommando och använda den i ett efterföljande kommando.

Till exempel följande kommando körs kommandot Get-snabbkorrigeringen i sessioner i variabeln $s och sparar resultatet i variabeln $h. Variabeln $h skapas i alla sessioner i $s, men finns inte i den lokala sessionen.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Nu kan du använda informationen i variabeln $h i efterföljande kommandon, till exempel på följande sätt. Resultatet visas på den lokala datorn.

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Avancerade fjärrkommunikation

Windows PowerShell-fjärrhantering börjar bara här. Med hjälp av cmdlets som installerats med Windows PowerShell kan du upprätta och konfigurera fjärrsessioner båda från lokala och fjärranslutna parterna, skapa anpassade och ej tillförlitliga sessioner, kan du importera kommandon från en fjärrsession som faktiskt kör implicit på fjärrsessionen, konfigurera säkerheten för en fjärrsession och mycket mer.

För att underlätta fjärrkonfiguration inkluderar Windows PowerShell en WSMan-provider. WSMAN: enheten som providern skapar kan du navigera i en hierarki med konfigurationsinställningarna på den lokala datorn och fjärrdatorer.
Mer information om WSMan-providern finns [WSMan-providern](https://technet.microsoft.com/library/dd819476.aspx) och [om WS-Management-Cmdlets](https://technet.microsoft.com/library/dd819481.aspx), eller ange ”Get-Help wsman” i Windows PowerShell-konsolen.

Mer information finns i följande avsnitt:

- [Om fjärråtkomst vanliga frågor och svar](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Hjälp med fjärrkommunikation fel finns i [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Se även

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [Om fjärrfelsökning](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [Ny PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan-providern](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md