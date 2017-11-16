---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Utföra nätverksuppgifter"
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 4d7a91595b9d9d637ce915be2c2be9c20879dd8b
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="performing-networking-tasks"></a>Utföra nätverksuppgifter
Eftersom TCP/IP är det vanligaste nätverksprotokollet, omfattar de flesta administrationsuppgifter för låg nivå nätverket protokollet TCP/IP. I det här avsnittet använder vi Windows PowerShell och WMI för att utföra dessa uppgifter.

### <a name="listing-ip-addresses-for-a-computer"></a>Visar en lista över IP-adresser för en dator
Om du vill hämta alla IP-adresser som används på den lokala datorn, använder du följande kommando:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Format-Table -Property IPAddress
```

Utdata från kommandot skiljer sig från de flesta egenskapslistor eftersom värden står inom klammerparenteser:

<a name="preipaddress"></a><pre>IPAddress
---------
{192.168.1.80} {192.168.148.1} {192.168.171.1} {0.0.0.0}</pre>

För att förstå varför klammerparenteserna visas, Använd cmdleten Get-medlem för att granska den **IPAddress** egenskapen:

<pre>PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Get-Member -Name IPAddress
TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapter
Configuration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}</pre>

Egenskapen IP-adress för varje nätverkskort är faktiskt en matris. Klammerparenteser i definitionen indikerar att **IPAddress** är inte en **System.String** värde, men en matris med **System.String** värden.

### <a name="listing-ip-configuration-data"></a>Visar en lista över IP-konfigurationsdata
Om du vill visa detaljerad IP-konfigurationsdata för varje nätverkskort, använder du följande kommando:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName .
```

Visa standard för konfigurationsobjektet nätverket nätverkskort är mycket uppsättning begränsade tillgänglig information. Använd Select-Object eller en formatering cmdlet, till exempel Format-List för att ange egenskaper som ska visas för djupgående undersökning och felsökning.

Om du inte är intresserad av IPX eller WINS-egenskaper – förmodligen skiftläget för ett moderna TCP/IP-nätverk – du kan använda parametern ExcludeProperty i Select-Object för att dölja egenskaper med namn som börjar med ”WINS” eller ”IPX”:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Det här kommandot returnerar detaljerad information om DHCP, DNS, Routning och andra egenskaper för mindre IP-konfiguration.

### <a name="pinging-computers"></a>Pinga datorer
Du kan utföra en enkel ping mot en datorn med hjälp av **Win32_PingStatus**. Följande kommando utför ping, men returnerar långa utdata:

```
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Ett mer användbar formulär för sammanfattningsinformation en visning av egenskaperna adress, ResponseTime och StatusCode som genererats med följande kommando. Parametern Autosize för Format-Table storlek tabellkolumnerna så att de visas korrekt i Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
A status code of 0 indicates a successful ping.
```

Du kan använda en matris för att pinga flera datorer med ett enda kommando. Eftersom det finns mer än en adress, använder den **ForEach-Object** att pinga varje adress separat:

```
"127.0.0.1","localhost","research.microsoft.com" | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Du kan använda samma kommandoformat för att pinga alla datorer i ett undernät, till exempel ett privat nätverk som använder nätverksnummer 192.168.1.0 och standard klass C nätmask (255.255.255.0)., endast adresser mellan 192.168.1.1 via 192.168.1.254 berättigade lokala adresser (0 är alltid har reserverats för nätverksnumret och 255 är en undernät broadcast-adress).

Representerar en matris med tal mellan 1 och 254 i Windows PowerShell använder du uttrycket **1..254.** En fullständig undernät ping kan utföras genom att generera matrisen och sedan lägga till värden till en partiell adress i instruktionen ping:

```
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Observera att den här tekniken för att generera ett adressintervall kan användas samt någon annanstans. Du kan skapa en fullständig uppsättning adresser i det här sättet:

`$ips = 1..254 | ForEach-Object -Process {"192.168.1." + $_}`

### <a name="retrieving-network-adapter-properties"></a>Hämta egenskaper för nätverkskort
Tidigare i den här användarhandboken nämnts kan du hämta egenskaper för allmän konfiguration med hjälp av **Win32_NetworkAdapterConfiguration**. Även om inte strikt TCP/IP-information, nätverkskortinformation, till exempel MAC-adresser och typer av nätverkskort kan användas för att förstå vad som händer med en dator. Använd följande kommando för att få en översikt över den här informationen:

```
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Tilldela DNS-domän för ett nätverkskort
Om du vill tilldela DNS-domän för automatisk namnmatchning, Använd den **Win32_NetworkAdapterConfiguration SetDNSDomain** metod. Eftersom du tilldelar DNS-domän för varje nätverkskortskonfiguration separat, måste du använda en **ForEach-Object** instruktionen för att tilldela varje kort domänen:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain("fabrikam.com") }
```

Instruktionen filtrering ”IPEnabled = true” är nödvändigt eftersom även på ett nätverk som använder endast TCP/IP flera konfigurationerna för nätverkskortet på en dator inte är SANT TCP/IP-nätverkskorten; de allmänna element stöder RAS, PPTP, QoS och andra tjänster för alla nätverkskort och därmed har inte en adress av sina egna.

Du kan filtrera kommandot med hjälp av den **Where-Object** cmdlet, istället för att använda den **Get-WmiObject** filter.

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain("fabrikam.com")}
```

### <a name="performing-dhcp-configuration-tasks"></a>Utföra åtgärder för DHCP-konfiguration
Ändra DHCP information innebär att arbeta med en uppsättning nätverkskort, precis som DNS-konfigurationen. Det finns flera olika åtgärder du kan utföra med hjälp av WMI och vi kommer att gå igenom några av de vanliga.

#### <a name="determining-dhcp-enabled-adapters"></a>När du fastställer DHCP-aktiverade nätverkskort
Om du vill söka efter de DHCP-aktiverade nätverkskort på en dator, använder du följande kommando:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName .
```

Om du vill exkludera nätverkskort med problem med IP-konfiguration kan du hämta IP-aktiverade nätverkskort:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a>Hämta egenskaper för DHCP
Eftersom DHCP-relaterade egenskaper för ett kort vanligtvis börjar med ”DHCP”, kan du använda egenskapen-parametern för Format-Table ska visas endast de egenskaperna:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a>Aktivera DHCP på varje nätverkskort
För att aktivera DHCP på alla nätverkskort, använder du följande kommando:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Du kan använda den **Filter** instruktionen ”IPEnabled = true och DHCPEnabled = false” att undvika att aktivera DHCP där det redan har aktiverats, men utan det här steget inte orsakar fel.

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Frisläppa och förnya DHCP-lån på särskilda nätverkskort
Den **Win32_NetworkAdapterConfiguration** klassen har **ReleaseDHCPLease** och **RenewDHCPLease** metoder. Båda används på samma sätt. I allmänhet kan använda dessa metoder om du bara behöver frigöra eller förnya adresser för ett nätverkskort i ett visst undernät. Det enklaste sättet att filtret nätverkskort i ett undernät är att välja endast de konfigurationer som använder en gateway för det undernätet. Till exempel släpper följande kommando alla DHCP-lån på nätverkskort på den lokala datorn som erhåller DHCP-lån från 192.168.1.254:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

Den enda förändringen för att förnya ett DHCP-lån är att använda den **RenewDHCPLease** metod i stället för den **ReleaseDHCPLease** metod:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> När du använder metoderna på en fjärrdator, Tänk på att du kan förlora åtkomsten till fjärrdatorn om du är ansluten till den via kortet med utgivna eller förnyat lånet.

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Frisläppa och förnya DHCP-lån på alla nätverkskort
Du kan utföra globala DHCP-adress versioner eller uppdateringar på alla nätverkskort med hjälp av den **Win32_NetworkAdapterConfiguration** metoder, **ReleaseDHCPLeaseAll** och **RenewDHCPLeaseAll** . Dock kommandot måste gälla för WMI-klassen, i stället för en särskild adapter eftersom släppa och förnya lån globalt utförs på klassen inte på ett visst nätverkskort.

Du kan hämta en referens till en WMI-klass, i stället för klassinstanser, genom att visa en lista över alla WMI-klasser och sedan välja önskad klass efter namn. Till exempel returnerar följande kommando Win32_NetworkAdapterConfiguration-klassen:

```
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"}
```

Du kan hantera hela kommandot som klassen och sedan anropa den **ReleaseDHCPAdapterLease** metod på den. I följande kommando, parentes runt den **Get-WmiObject** och **Where-Object** pipeline element dirigera Windows PowerShell för att utvärdera dem först:

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).ReleaseDHCPLeaseAll()
```

Du kan använda samma kommandoformat för att anropa den **RenewDHCPLeaseAll** metod:

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a>Skapa en nätverksresurs
Så här skapar du en nätverksresurs i **Win32_Share skapa** metoden:

```
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Win32_Share"}).Create("C:\temp","TempShare",0,25,"test share of the temp folder")
```

Du kan också skapa resursen med hjälp av **net share** i Windows PowerShell:

```
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a>Tar bort en nätverksresurs
Du kan ta bort en nätverksresurs med **Win32_Share**, men processen skiljer sig från att skapa en resurs, eftersom du behöver hämta specifika resursen tas bort, snarare än den **Win32_Share** klass. Följande instruktion tar bort resurs ”TempShare”:

```
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Net share** fungerar också:

```
PS> net share tempshare /delete
tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a>Ansluter en Windows-tillgänglig nätverksenhet
Den **ny PSDrive** cmdlets skapar ett Windows PowerShell-enhet, men enheter som har skapats på detta sätt är bara tillgängliga för Windows PowerShell. Du kan använda för att skapa en ny nätverksansluten enhet, den **WScript.Network** COM-objekt. Följande kommando mappar resursen \\ \\FPS01\\användare till en lokal enhet B:

```
(New-Object -ComObject WScript.Network).MapNetworkDrive("B:", "\\FPS01\users")
```

Den **net Använd** kommandot fungerar också:

```
net use B: \\FPS01\users
```

Enheter mappade med antingen **WScript.Network** eller net användning är omedelbart tillgängliga för Windows PowerShell.

