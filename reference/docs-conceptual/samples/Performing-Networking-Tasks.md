---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Utför nätverksuppgifter
ms.openlocfilehash: e581296b4b7609b374f206c447c4f797e3e2c400
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030853"
---
# <a name="performing-networking-tasks"></a>Utför nätverksuppgifter

Eftersom TCP/IP är det vanligaste nätverksprotokollet, omfattar de flesta administrationsuppgifter för på låg nivå network protocol TCP/IP. I det här avsnittet använder vi Windows PowerShell och WMI för att utföra dessa uppgifter.

## <a name="listing-ip-addresses-for-a-computer"></a>Visa en lista över IP-adresser för en dator

Om du vill hämta alla IP-adresser som används på den lokala datorn, använder du följande kommando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

Kommandots utdata skiljer sig från de flesta egenskapslistor eftersom värden står inom klammerparenteser:

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

För att förstå varför klammerparenteserna visas, använder du cmdleten Get-Member för att undersöka den **IPAddress** egenskapen:

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

Egenskapen IP-adress för varje nätverkskort är faktiskt en matris. Klammerparenteserna i definitionen indikerar att **IPAddress** är inte en **System.String** värde, men en matris med **System.String** värden.

## <a name="listing-ip-configuration-data"></a>Visa en lista över IP-konfigurationsdata

Om du vill visa detaljerad IP-konfigurationsdata för varje nätverkskort, använder du följande kommando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

Standardvisningen för konfiguration av nätverkskortsobjektet är en mycket reducerad uppsättning tillgänglig information. För detaljerad granskning och felsökning, Använd Select-Object eller en formatering cmdlet, till exempel Format-List, för att ange egenskaper som ska visas.

Om du inte är intresserad av IPX eller WINS-egenskaper – förmodligen skiftläget för ett moderna TCP/IP-nätverk – du kan använda parametern ExcludeProperty i Select-Object för att dölja egenskaper med namn som börjar med ”vinner” eller ”IPX”:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Det här kommandot returnerar detaljerad information om DHCP, DNS, Routning och andra egenskaper för mindre IP-konfiguration.

## <a name="pinging-computers"></a>Skicka signaler till datorer

Du kan utföra en enkel ping mot en dator med hjälp av av **Win32_PingStatus**. Följande kommando utför ping-kommandot, men returnerar långa utdata:

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Ett mer användbart formulär för sammanfattningsinformation en visning av egenskaperna adress, ResponseTime och StatusCode som genererats med följande kommando. Parametern Autosize för Format-Table ändrar storlek på tabellens kolumner så att de visas korrekt i Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Statuskoden 0 indikerar en lyckad ping.

Du kan använda en matris för att pinga flera datorer med ett enda kommando. Eftersom det finns mer än en adress, använder den **ForEach-Object** pinga varje adress separat:

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Du kan använda samma kommandoformatet pinga alla datorer i ett undernät, till exempel ett privat nätverk som använder nätverksnumret 192.168.1.0 och en standard klass C-nätmask (255.255.255.0)., endast adresser mellan 192.168.1.1 via 192.168.1.254 är oskadliga lokala adresser (0 är alltid reserveras för nätverksnumret och 255 är en undernät broadcast-adress).

För att representera en matris med tal mellan 1 och 254 i Windows PowerShell, Använd instruktionen **1..254.** En fullständig undernät ping kan utföras genom att generera matrisen och sedan lägga till värden till en partiell adress i ping-instruktionen:

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Observera att den här tekniken för att generera ett adressintervall kan användas för andra platser också. Du kan generera en fullständig uppsättning adresser i det här sättet:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Hämta egenskaper för nätverkskort

Tidigare i den här användarhandboken nämns vi att du kan hämta egenskaper för allmän konfiguration med hjälp av **Win32_NetworkAdapterConfiguration**. Även om det strikt sett inte är TCP/IP-information, nätverkskortinformation, till exempel MAC-adresser och typer av nätverkskort kan vara användbart för att förstå vad som händer med en dator. Använd följande kommando för att få en sammanfattning av den här informationen:

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Tilldela DNS-domän för ett nätverkskort

Om du vill tilldela DNS-domän för automatisk namnmatchning, Använd den **Win32_NetworkAdapterConfiguration SetDNSDomain** metod. Eftersom du tilldelar DNS-domän för varje nätverkskortskonfiguration oberoende av varandra, måste du använda en **ForEach-Object** instruktionen ska tilldelas varje kort domänen:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

Filtrera instruktionen ”IPEnabled = $true” är nödvändigt, eftersom även på ett nätverk som använder endast TCP/IP, flera konfigurationer för nätverkskort på en dator inte är SANT TCP/IP-kort; de är allmänt programelement stöder RAS, PPTP, QoS och andra tjänster för alla nätverkskort och därför har inte en adress för sina egna.

Du kan filtrera kommandot med hjälp av den **Where-Object** cmdlet, istället för att använda den **Get-WmiObject** filter.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>Utför åtgärder för DHCP-konfiguration

Ändra information om DHCP innebär att arbeta med en uppsättning nätverkskort, precis som DNS-konfigurationen. Det finns flera olika åtgärder som du kan utföra med hjälp av WMI och vi ska gå igenom några av de vanliga.

### <a name="determining-dhcp-enabled-adapters"></a>Fastställa DHCP-aktiverade nätverkskort

För att hitta de DHCP-aktiverade nätverkskort på en dator, använder du följande kommando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

Du kan hämta IP-aktiverade nätverkskort om du vill exkludera kort med IP-konfigurationsproblem:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a>Hämta egenskaper för DHCP

Eftersom DHCP-relaterade egenskaper för ett nätverkskort som är allmänt börjar med ”DHCP” bör använda du parametern egenskapen av Format-Table för att visa endast de egenskaperna:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>Aktivera DHCP på varje kort

Om du vill aktivera DHCP på alla nätverkskort, använder du följande kommando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Du kan använda den **Filter** instruktionen ”IPEnabled = $true och DHCPEnabled = $false” att undvika att aktivera DHCP där det redan har aktiverats, men utelämna det här steget inte orsakar fel.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Lansera och förnya DHCP-lån på specifika nätverkskort

Den **Win32_NetworkAdapterConfiguration** klassen har **ReleaseDHCPLease** och **RenewDHCPLease** metoder. Båda används på samma sätt. I allmänhet använda dessa metoder om du bara vill frigöra eller förnya adresser för en adapter i ett specifikt undernät. Det enklaste sättet att filtret nätverkskort i ett undernät är att välja endast de konfigurationer av nätverkskort som använder gatewayen för det undernätet. Till exempel släpper följande kommando alla DHCP-lån på nätverkskort på den lokala datorn som får DHCP-lån från 192.168.1.254:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

Den enda ändringen för att förnya ett DHCP-lån är att använda den **RenewDHCPLease** metoden i stället för den **ReleaseDHCPLease** metod:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> När du använder dessa metoder på en fjärrdator, Tänk på att du kan förlora åtkomsten till fjärrsystemet om du är ansluten till den via adapter med utgivna eller förnyat lånet.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Lansera och förnya DHCP-lån på alla nätverkskort

Du kan utföra global DHCP-adress versioner eller förnyelser på alla kort med hjälp av den **Win32_NetworkAdapterConfiguration** metoder, **ReleaseDHCPLeaseAll** och **RenewDHCPLeaseAll** . Men kommandot måste gälla för WMI-klass i stället för en särskild adapter eftersom lanserar och förnya lån globalt utförs på klassen, inte på ett visst nätverkskort.

Du kan hämta en referens till en WMI-klass, i stället för klassinstanser, genom att visa en lista över alla WMI-klasser och sedan välja önskad klass efter namn. Till exempel returnerar följande kommando Win32_NetworkAdapterConfiguration-klassen:

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Du kan hantera hela kommandot som klassen och sedan anropa den **ReleaseDHCPAdapterLease** metod på den. I följande kommando, parenteser som omger den **Get-WmiObject** och **Where-Object** pipeline element dirigera Windows PowerShell för att utvärdera dem först:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

Du kan använda samma kommandoformat för att anropa den **RenewDHCPLeaseAll** metod:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Skapa en nätverksresurs

Skapa en nätverksresurs, att använda den **Win32_Share skapa** metoden:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

Du kan också skapa resursen med hjälp av **nätverksresurs** i Windows PowerShell:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Ta bort en nätverksresurs

Du kan ta bort en nätverksresurs med **Win32_Share**, men processen är något annorlunda från att skapa en resurs, eftersom du behöver hämta den specifika resursen som ska tas bort, snarare än **Win32_Share** klass. Följande uttryck tar bort resurs ”TempShare”:

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Net share** fungerar även:

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Ansluta en Windows-tillgänglig nätverksenhet

Den **New PSDrive** cmdletar skapar en Windows PowerShell-enhet, men enheter som skapats på detta sätt är endast tillgängliga för Windows PowerShell. Du kan använda för att skapa en ny nätverksansluten enhet, den **WScript.Network** COM-objektet. Följande kommando mappar resursen \\ \\FPS01\\användare till en lokal enhet B:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

Den **nätverksanv** kommandot fungerar också:

```powershell
net use B: \\FPS01\users
```

Styr mappade med antingen **WScript.Network** eller net Använd är omedelbart tillgängliga för Windows PowerShell.
