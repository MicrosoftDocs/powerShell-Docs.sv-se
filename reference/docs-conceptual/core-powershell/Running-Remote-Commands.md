---
ms.date: 08/14/2018
keywords: PowerShell cmdlet
title: Kör fjärrkommandon
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133840"
---
# <a name="running-remote-commands"></a>Kör fjärrkommandon

Du kan köra kommandon på en eller flera hundra datorer med ett enda PowerShell-kommando. Windows PowerShell har stöd för fjärrhantering med hjälp av olika tekniker, inklusive WMI, RPC- och WS-Management.

PowerShell Core har stöd för WMI, WS-Management och SSH-fjärrkommunikation. RPC stöds inte längre.

Mer information om fjärrkommunikation i PowerShell Core finns i följande artiklar:

- [SSH fjärrkommunikation i PowerShell Core][ssh-remoting]
- [WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Windows PowerShell-fjärrkommunikation utan konfiguration

Många Windows PowerShell-cmdlets har parametern ComputerName som hjälper dig att samla in data och ändra inställningarna för en eller flera fjärrdatorer. Dessa cmdletar använder olika kommunikationsprotokoll och fungerar på alla Windows-operativsystem utan någon specialkonfiguration.

Dessa cmdletar omfattar:

- [Starta om datorn](/powershell/module/microsoft.powershell.management/restart-computer)
- [Testa anslutning](/powershell/module/microsoft.powershell.management/test-connection)
- [Rensa händelselogg](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-händelseloggen](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-tjänst](/powershell/module/microsoft.powershell.management/get-service)
- [Set-tjänst](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

Normalt har parametern ComputerName cmdletar som stöder fjärrkommunikation utan särskild konfiguration och behöver inte parametern Session. För att hitta dessa cmdletar i sessionen, skriver du:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell-fjärrkommunikation

Windows PowerShell-fjärrkommunikation kan med hjälp av protokollet WS-Management, du köra alla Windows PowerShell-kommandon på en eller flera fjärrdatorer. Du kan fastställa beständiga anslutningar, starta interaktiva sessioner och köra skript på fjärrdatorer.

Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.
Mer information, inklusive anvisningar finns i [om Remote krav](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

När du har konfigurerat Windows PowerShell-fjärrkommunikation, är många strategier för fjärrkommunikation tillgängliga för dig.
Den här artikeln innehåller några av dem. Mer information finns i [om Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

### <a name="start-an-interactive-session"></a>Starta en interaktiv Session

Starta en interaktiv session med en fjärransluten dator med den [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.
Till exempel om du vill starta en interaktiv session med Server01 fjärrdatorn, skriver du:

```powershell
Enter-PSSession Server01
```

Kommandotolk-ändras och visar namnet på fjärrdatorn. Kommandon som du anger i Kommandotolken kör på fjärrdatorn och resultatet visas på den lokala datorn.

Om du vill avsluta den interaktiva sessionen, skriver du:

```powershell
Exit-PSSession
```

Mer information om cmdlet: Enter-PSSession och avsluta-PSSession finns:

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Avsluta-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Kör fjärrkommandon

Om du vill köra ett kommando på en eller flera datorer, Använd den [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet. Till exempel för att köra en [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) på Server01 och Server02 fjärrdatorerna, typ:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

Resultatet returneras till datorn.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Köra ett skript

Om du vill köra ett skript på en eller flera fjärrdatorer, använder du parametern FilePath för den `Invoke-Command` cmdlet. Skriptet måste infalla på eller är tillgängliga för den lokala datorn. Resultaten returneras till den lokala datorn.

Exempelvis kör följande kommando DiskCollect.ps1 skriptet på fjärrdatorer, Server01 och Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Upprätta en beständig anslutning

Använd den `New-PSSession` cmdlet för att skapa en beständig session på en fjärrdator. I följande exempel skapar fjärrsessioner på Server01 och Server02. Sessionsobjekt lagras i den `$s` variabeln.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Nu när sessioner upprättas, kan du köra alla kommandon i dem. Och eftersom sessioner är beständiga kan du samla in data från ett kommando och använda det i ett annat kommando.

Till exempel följande kommando kör ett kommando för Get-HotFix i sessioner i variabeln $s och sparas resultaten i variabeln $h. Variabeln $h skapas i varje sessioner i $s, men det finns inte i den lokala sessionen.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Nu kan du använda data i den `$h` variabeln med andra kommandon i samma session. Resultatet visas på den lokala datorn. Till exempel:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Avancerade fjärrkommunikation

Windows PowerShell fjärrhantering bara börjar här. Genom att använda de cmdletar som installeras med Windows PowerShell kan du etablera och konfigurera fjärrsessioner både från lokala och fjärranslutna upphör kan skapa anpassade och begränsade sessioner Tillåt användare att importera kommandon från en fjärrsession som faktiskt kör implicit på fjärrsessionen, konfigurerar du säkerheten för en fjärrsession och mycket mer.

Windows PowerShell innehåller en WSMan-provider. Providern skapar en `WSMAN:` enhet som du kan gå igenom en hierarki med konfigurationsinställningarna på den lokala datorn och fjärrdatorer.

Mer information om WSMan-providern finns i [WSMan-providern](https://technet.microsoft.com/library/dd819476.aspx) och [om WS-Management-cmdletar](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), eller i Windows PowerShell-konsolen skriver `Get-Help wsman`.

Mer information finns i följande avsnitt:

- [Om fjärråtkomst vanliga frågor och svar](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Hjälp med fjärrkommunikation fel finns i [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Se även

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Anropskommandot](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan-providern](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md