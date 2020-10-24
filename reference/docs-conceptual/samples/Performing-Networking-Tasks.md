---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Utför nätverksuppgifter
description: Den här artikeln visar hur du använder WMI-klasser i PowerShell för att hantera nätverks konfigurations inställningar i Windows.
ms.openlocfilehash: 95b05c193f4168cdcdf8414399c4f8c569bff754
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500257"
---
# <a name="performing-networking-tasks"></a>Utför nätverksuppgifter

Eftersom TCP/IP är det vanligaste nätverks protokollet, omfattar de flesta administrations uppgifter för nätverks protokollet TCP/IP. I det här avsnittet använder vi PowerShell och WMI för att utföra dessa uppgifter.

## <a name="listing-ip-addresses-for-a-computer"></a>Lista IP-adresser för en dator

Använd följande kommando för att hämta alla IP-adresser som används på den lokala datorn:

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

Utdata från det här kommandot skiljer sig från de flesta egenskaps listor, eftersom värdena omges av klammerparenteser:

```Output
10.0.0.1
fe80::60ea:29a7:a233:7cb7
2601:600:a27f:a470:f532:6451:5630:ec8b
2601:600:a27f:a470:e167:477d:6c5c:342d
2601:600:a27f:a470:b021:7f0d:eab9:6299
2601:600:a27f:a470:a40e:ebce:1a8c:a2f3
2601:600:a27f:a470:613c:12a2:e0e0:bd89
2601:600:a27f:a470:444f:17ec:b463:7edd
2601:600:a27f:a470:10fd:7063:28e9:c9f3
2601:600:a27f:a470:60ea:29a7:a233:7cb7
2601:600:a27f:a470::2ec1
```

Om du vill veta varför klamrarna visas använder du `Get-Member` cmdleten för att undersöka egenskapen **IPAddress** :

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Get-Member -Name IPAddress
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_NetworkAdapterConfiguration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   string[] IPAddress {get;}
```

Egenskapen IPAddress för varje nätverkskort är i själva verket en matris. Klamrarna i definitionen anger att **IPAddress** inte är ett **system. String** -värde, men en matris med **system. String** -värden.

## <a name="listing-ip-configuration-data"></a>Lista IP-konfigurationsdata

Om du vill visa detaljerad information om IP-konfigurationen för varje nätverkskort, använder du följande kommando:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

Standard visningen för nätverkskortets konfigurations objekt är en mycket begränsad uppsättning av tillgänglig information. För djupgående inspektion och fel sökning använder `Select-Object` eller en format-cmdlet, till exempel `Format-List` , för att ange vilka egenskaper som ska visas.

I moderna TCP/IP-nätverk är du förmodligen inte intresse rad av IPX-eller WINS-egenskaperna. Du kan använda **ExcludeProperty** -parametern för `Select-Object` för att dölja egenskaper med namn som börjar med "WINS" eller "IPX".

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

Det här kommandot returnerar detaljerad information om DHCP, DNS, Routning och andra egenskaper för smärre IP-konfigurationer.

## <a name="pinging-computers"></a>Pinga datorer

Du kan utföra en enkel ping mot en dator med hjälp av **Win32_PingStatus**. Följande kommando utför ping, men returnerar långa utdata:

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

Ett mer användbart formulär för sammanfattnings information som visar egenskaperna Address, SLA svarstid och StatusCode, som genereras av följande kommando. **AutoSize** -parametern för `Format-Table` ändrar storlek på tabell kolumnerna så att de visas korrekt i PowerShell.

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

En StatusCode av 0 visar en lyckad ping.

Du kan använda en matris för att pinga flera datorer med ett enda kommando. Eftersom det finns mer än en adress använder `ForEach-Object` du för att pinga varje adress separat:

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

Du kan använda samma kommando format för att pinga alla datorer i ett undernät, t. ex. ett privat nätverk som använder nätverks nummer 192.168.1.0 och en standard nätmask för klass C., endast adresser i intervallet 192.168.1.1 via 192.168.1.254 är legitima lokala adresser (0 är alltid reserverat för nätverks numret och 255 är en broadcast-adress för undernät).

Om du vill visa en matris med talen från 1 till 254 i PowerShell använder du instruktionen **1.. 254.**
Ett fullständigt undernät ping kan utföras genom att generera matrisen och sedan lägga till värdena på en del av adressen i ping-instruktionen:

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

Observera att den här tekniken för att skapa ett adress intervall också kan användas på andra platser. Du kan generera en fullständig uppsättning adresser på det här sättet:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Hämtar egenskaper för nätverkskort

Tidigare nämnde vi att du kan hämta allmänna konfigurations egenskaper med hjälp av klassen **Win32_NetworkAdapterConfiguration** . Även om det inte är strikt TCP/IP-information kan nätverkskort information, till exempel MAC-adresser och kort typer, vara användbar för att förstå vad som händer med en dator. Använd följande kommando för att få en sammanfattning av den här informationen:

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Tilldela DNS-domänen för ett nätverkskort

Om du vill tilldela DNS-domänen för automatisk namn matchning använder du **SetDNSDomain** -metoden för **Win32_NetworkAdapterConfiguration**. Eftersom du tilldelar DNS-domänen för varje nätverkskorts konfiguration oberoende måste du använda en `ForEach-Object` instruktion för att tilldela domänen till varje kort:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

Filtrerings instruktionen `IPEnabled=$true` är nödvändig, eftersom även om det finns flera nätverkskort konfigurationer på en dator som bara använder TCP/IP-kort. de är allmänna program varu element som stöder ras, PPTP, QoS och andra tjänster för alla kort och därför inte har en egen adress.

Du kan filtrera kommandot med hjälp av `Where-Object` -cmdleten i stället för att använda `Get-CimInstance` filtret.

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>Utföra uppgifter för DHCP-konfiguration

Att ändra DHCP-information innebär att du arbetar med en uppsättning nätverkskort, precis som DNS-konfigurationen gör. Det finns flera olika åtgärder som du kan utföra med hjälp av WMI, och vi kommer att gå igenom några vanliga åtgärder.

### <a name="determining-dhcp-enabled-adapters"></a>Bestämma DHCP-Enabled nätverkskort

Använd följande kommando för att hitta de DHCP-aktiverade korten på en dator:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

Om du vill utesluta kort med problem med IP-konfiguration kan du bara hämta IP-aktiverade nätverkskort:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a>Hämtar DHCP-egenskaper

Eftersom DHCP-relaterade egenskaper för ett kort i allmänhet börjar med `DHCP` , kan du använda egenskaps parametern för `Format-Table` för att endast visa de egenskaperna:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>Aktivera DHCP på varje kort

Använd följande kommando för att aktivera DHCP på alla kort:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

Du kan använda **filter** instruktionen `IPEnabled=$true and DHCPEnabled=$false` för att undvika att aktivera DHCP där det redan har Aktiver ATS, men bortse från det här steget resulterar inte i fel.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Släppa och förnya DHCP-lån på vissa kort

**Win32_NetworkAdapterConfiguration** -klassen har metoder för **ReleaseDHCPLease** och **RenewDHCPLease** . Båda används på samma sätt. I allmänhet använder du dessa metoder om du bara behöver frigöra eller förnya adresser för en adapter i ett visst undernät. Det enklaste sättet att filtrera nätverkskort i ett undernät är att välja de kort konfigurationer som använder gatewayen för det under nätet. Följande kommando frigör till exempel alla DHCP-lån på kort på den lokala datorn som erhåller DHCP-lån från 192.168.1.254:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

Den enda ändringen för att förnya ett DHCP-lån är att använda metoden **RenewDHCPLease** i stället för **ReleaseDHCPLease** -metoden:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> När du använder dessa metoder på en fjärrdator bör du vara medveten om att du kan förlora åtkomsten till fjärrsystemet om du är ansluten till den via kortet med det släppta eller förnyade lånet.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Släppa och förnya DHCP-lån på alla kort

Du kan utföra globala DHCP-uppdateringar eller förnyelser på alla kort med hjälp av **Win32_NetworkAdapterConfiguration** metoder, **ReleaseDHCPLeaseAll** och **RenewDHCPLeaseAll**.
Kommandot måste dock gälla för WMI-klassen, i stället för ett visst kort, eftersom det går att frigöra och förnya lån globalt i klassen, inte på ett specifikt kort.

Du kan få en referens till en WMI-klass i stället för klass instanser genom att lista alla WMI-klasser och sedan välja enbart den önskade klassen efter namn. Följande kommando returnerar till exempel klassen **Win32_NetworkAdapterConfiguration** :

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Du kan behandla hela kommandot som klass och sedan anropa metoden **ReleaseDHCPAdapterLease** på den. I följande kommando är parenteserna omgivande `Get-CimInstance` och `Where-Object` pipelines elementen Direct PowerShell för att utvärdera dem först:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

Du kan använda samma kommando format för att anropa metoden **RenewDHCPLeaseAll** :

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Skapa en nätverks resurs

Om du vill skapa en nätverks resurs använder du metoden **skapa** för **Win32_Share**:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

Du kan också skapa resursen med hjälp av `net share` i PowerShell i Windows:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Ta bort en nätverks resurs

Du kan ta bort en nätverks resurs med **Win32_Share**, men processen skiljer sig något från att skapa en resurs, eftersom du måste hämta den resurs som ska tas bort, i stället för **Win32_Share** -klassen. Följande instruktion tar bort resursen **TempShare**:

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

I Windows `net share` fungerar det också:

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Ansluta en Windows-tillgänglig nätverks enhet

`New-PSDrive`Cmdletarna skapar en PowerShell-enhet, men enheter som skapas på det här sättet är bara tillgängliga för PowerShell. Om du vill skapa en ny nätverksansluten enhet kan du använda **wscript. Network** com-objektet. Följande kommando mappar resursen till en `\\FPS01\users` lokal enhet `B:` .

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

I Windows `net use` fungerar kommandot även:

```powershell
net use B: \\FPS01\users
```

Enheter som mappas med antingen **wscript. Network** eller `net use` är omedelbart tillgängliga för PowerShell.
