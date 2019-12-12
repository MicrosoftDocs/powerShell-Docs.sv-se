---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Utför nätverksuppgifter
ms.openlocfilehash: e581296b4b7609b374f206c447c4f797e3e2c400
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030853"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="ff462-103">Utför nätverksuppgifter</span><span class="sxs-lookup"><span data-stu-id="ff462-103">Performing Networking Tasks</span></span>

<span data-ttu-id="ff462-104">Eftersom TCP/IP är det vanligaste nätverks protokollet, omfattar de flesta administrations uppgifter för nätverks protokollet TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="ff462-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="ff462-105">I det här avsnittet använder vi Windows PowerShell och WMI för att utföra dessa uppgifter.</span><span class="sxs-lookup"><span data-stu-id="ff462-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="ff462-106">Lista IP-adresser för en dator</span><span class="sxs-lookup"><span data-stu-id="ff462-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="ff462-107">Använd följande kommando för att hämta alla IP-adresser som används på den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="ff462-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="ff462-108">Utdata från det här kommandot skiljer sig från de flesta egenskaps listor, eftersom värdena omges av klammerparenteser:</span><span class="sxs-lookup"><span data-stu-id="ff462-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="ff462-109">Om du vill veta varför klamrarna visas använder du cmdleten Get-Member för att undersöka egenskapen **IPAddress** :</span><span class="sxs-lookup"><span data-stu-id="ff462-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="ff462-110">Egenskapen IPAddress för varje nätverkskort är i själva verket en matris.</span><span class="sxs-lookup"><span data-stu-id="ff462-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="ff462-111">Klamrarna i definitionen anger att **IPAddress** inte är ett **system. String** -värde, men en matris med **system. String** -värden.</span><span class="sxs-lookup"><span data-stu-id="ff462-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="ff462-112">Lista IP-konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="ff462-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="ff462-113">Om du vill visa detaljerad information om IP-konfigurationen för varje nätverkskort, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="ff462-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="ff462-114">Standard visningen för nätverkskortets konfigurations objekt är en mycket begränsad uppsättning av tillgänglig information.</span><span class="sxs-lookup"><span data-stu-id="ff462-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="ff462-115">För djupgående inspektion och fel sökning använder du Select-Object eller en format-cmdlet, till exempel format-lista, för att ange vilka egenskaper som ska visas.</span><span class="sxs-lookup"><span data-stu-id="ff462-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="ff462-116">Om du inte är intresse rad av IPX-eller WINS-egenskaper – förmodligen fallet i ett modernt TCP/IP-nätverk, kan du använda ExcludeProperty-parametern för Select-Object för att dölja egenskaper med namn som börjar med "WINS" eller "IPX:"</span><span class="sxs-lookup"><span data-stu-id="ff462-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="ff462-117">Det här kommandot returnerar detaljerad information om DHCP, DNS, Routning och andra egenskaper för smärre IP-konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="ff462-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="ff462-118">Pinga datorer</span><span class="sxs-lookup"><span data-stu-id="ff462-118">Pinging Computers</span></span>

<span data-ttu-id="ff462-119">Du kan utföra en enkel ping mot en dator med hjälp av **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="ff462-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="ff462-120">Följande kommando utför ping, men returnerar långa utdata:</span><span class="sxs-lookup"><span data-stu-id="ff462-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="ff462-121">Ett mer användbart formulär för sammanfattnings information som visar egenskaperna Address, SLA svarstid och StatusCode, som genereras av följande kommando.</span><span class="sxs-lookup"><span data-stu-id="ff462-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="ff462-122">Parametern AutoSize i format-Table ändrar storlek på tabell kolumnerna så att de visas korrekt i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff462-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="ff462-123">En StatusCode av 0 visar en lyckad ping.</span><span class="sxs-lookup"><span data-stu-id="ff462-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="ff462-124">Du kan använda en matris för att pinga flera datorer med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="ff462-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="ff462-125">Eftersom det finns mer än en adress, använder du det **förgrunds objekt** för att pinga varje adress separat:</span><span class="sxs-lookup"><span data-stu-id="ff462-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="ff462-126">Du kan använda samma kommando format för att pinga alla datorer i ett undernät, till exempel ett privat nätverk som använder nätverks nummer 192.168.1.0 och en standard klass C-nätmask (255.255.255.0)., endast adresser i intervallet 192.168.1.1 via 192.168.1.254 är legitima lokala adresser (0 är alltid reserverad för nätverks numret och 255 är en broadcast-adress för undernät).</span><span class="sxs-lookup"><span data-stu-id="ff462-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="ff462-127">Om du vill visa en matris med talen från 1 till 254 i Windows PowerShell använder du instruktionen **1.. 254.**</span><span class="sxs-lookup"><span data-stu-id="ff462-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="ff462-128">Ett fullständigt undernät ping kan utföras genom att generera matrisen och sedan lägga till värdena på en del av adressen i ping-instruktionen:</span><span class="sxs-lookup"><span data-stu-id="ff462-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="ff462-129">Observera att den här tekniken för att skapa ett adress intervall också kan användas på andra platser.</span><span class="sxs-lookup"><span data-stu-id="ff462-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="ff462-130">Du kan generera en fullständig uppsättning adresser på det här sättet:</span><span class="sxs-lookup"><span data-stu-id="ff462-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="ff462-131">Hämtar egenskaper för nätverkskort</span><span class="sxs-lookup"><span data-stu-id="ff462-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="ff462-132">Tidigare i den här användar handboken nämnde vi att du kan hämta allmänna konfigurations egenskaper med hjälp av **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="ff462-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="ff462-133">Även om det inte är strikt TCP/IP-information kan nätverkskort information, till exempel MAC-adresser och kort typer, vara användbar för att förstå vad som händer med en dator.</span><span class="sxs-lookup"><span data-stu-id="ff462-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="ff462-134">Använd följande kommando för att få en sammanfattning av den här informationen:</span><span class="sxs-lookup"><span data-stu-id="ff462-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="ff462-135">Tilldela DNS-domänen för ett nätverkskort</span><span class="sxs-lookup"><span data-stu-id="ff462-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="ff462-136">Använd metoden **Win32_NetworkAdapterConfiguration SetDNSDomain** för att tilldela DNS-domänen för automatisk namn matchning.</span><span class="sxs-lookup"><span data-stu-id="ff462-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="ff462-137">Eftersom du tilldelar DNS-domänen för varje nätverkskorts konfiguration oberoende, måste du använda en **förgrunds objekt-** instruktion för att tilldela domänen till varje kort:</span><span class="sxs-lookup"><span data-stu-id="ff462-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="ff462-138">Filtrerings instruktionen "IPEnabled = $true" är nödvändig, eftersom även i ett nätverk som bara använder TCP/IP, så är flera av nätverkskortens konfigurationer på en dator inte äkta TCP/IP-kort. de är allmänna program varu element som stöder RAS, PPTP, QoS och andra tjänster för alla kort och därför inte har en egen adress.</span><span class="sxs-lookup"><span data-stu-id="ff462-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="ff462-139">Du kan filtrera kommandot med hjälp av cmdleten **Where-Object** i stället för att använda **Get-WmiObject** -filtret.</span><span class="sxs-lookup"><span data-stu-id="ff462-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="ff462-140">Utföra uppgifter för DHCP-konfiguration</span><span class="sxs-lookup"><span data-stu-id="ff462-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="ff462-141">Att ändra DHCP-information innebär att du arbetar med en uppsättning nätverkskort, precis som DNS-konfigurationen gör.</span><span class="sxs-lookup"><span data-stu-id="ff462-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="ff462-142">Det finns flera olika åtgärder som du kan utföra med hjälp av WMI, och vi kommer att gå igenom några vanliga åtgärder.</span><span class="sxs-lookup"><span data-stu-id="ff462-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="ff462-143">Fastställa DHCP-aktiverade nätverkskort</span><span class="sxs-lookup"><span data-stu-id="ff462-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="ff462-144">Använd följande kommando för att hitta de DHCP-aktiverade korten på en dator:</span><span class="sxs-lookup"><span data-stu-id="ff462-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="ff462-145">Om du vill utesluta kort med problem med IP-konfiguration kan du bara hämta IP-aktiverade nätverkskort:</span><span class="sxs-lookup"><span data-stu-id="ff462-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="ff462-146">Hämtar DHCP-egenskaper</span><span class="sxs-lookup"><span data-stu-id="ff462-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="ff462-147">Eftersom DHCP-relaterade egenskaper för ett kort i allmänhet börjar med "DHCP" kan du använda egenskaps parametern för format-tabellen för att visa endast de egenskaperna:</span><span class="sxs-lookup"><span data-stu-id="ff462-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="ff462-148">Aktivera DHCP på varje kort</span><span class="sxs-lookup"><span data-stu-id="ff462-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="ff462-149">Använd följande kommando för att aktivera DHCP på alla kort:</span><span class="sxs-lookup"><span data-stu-id="ff462-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="ff462-150">Du kan använda **filter** instruktionen "IPEnabled = $True och DHCPEnabled = $false" för att undvika att aktivera DHCP där det redan har Aktiver ATS, men bortse från det här steget kommer inte att orsaka fel.</span><span class="sxs-lookup"><span data-stu-id="ff462-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="ff462-151">Släppa och förnya DHCP-lån på vissa kort</span><span class="sxs-lookup"><span data-stu-id="ff462-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="ff462-152">**Win32_NetworkAdapterConfiguration** -klassen har metoder för **ReleaseDHCPLease** och **RenewDHCPLease** .</span><span class="sxs-lookup"><span data-stu-id="ff462-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="ff462-153">Båda används på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="ff462-153">Both are used in the same way.</span></span> <span data-ttu-id="ff462-154">I allmänhet använder du dessa metoder om du bara behöver frigöra eller förnya adresser för en adapter i ett visst undernät.</span><span class="sxs-lookup"><span data-stu-id="ff462-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="ff462-155">Det enklaste sättet att filtrera nätverkskort i ett undernät är att välja de kort konfigurationer som använder gatewayen för det under nätet.</span><span class="sxs-lookup"><span data-stu-id="ff462-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="ff462-156">Följande kommando frigör till exempel alla DHCP-lån på kort på den lokala datorn som erhåller DHCP-lån från 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="ff462-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="ff462-157">Den enda ändringen för att förnya ett DHCP-lån är att använda metoden **RenewDHCPLease** i stället för **ReleaseDHCPLease** -metoden:</span><span class="sxs-lookup"><span data-stu-id="ff462-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="ff462-158">När du använder dessa metoder på en fjärrdator bör du vara medveten om att du kan förlora åtkomsten till fjärrsystemet om du är ansluten till den via kortet med det släppta eller förnyade lånet.</span><span class="sxs-lookup"><span data-stu-id="ff462-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="ff462-159">Släppa och förnya DHCP-lån på alla kort</span><span class="sxs-lookup"><span data-stu-id="ff462-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="ff462-160">Du kan utföra globala DHCP-uppdateringar eller förnyelser på alla kort med hjälp av **Win32_NetworkAdapterConfiguration** metoder, **ReleaseDHCPLeaseAll** och **RenewDHCPLeaseAll**.</span><span class="sxs-lookup"><span data-stu-id="ff462-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="ff462-161">Kommandot måste dock gälla för WMI-klassen, i stället för ett visst kort, eftersom det går att frigöra och förnya lån globalt i klassen, inte på ett specifikt kort.</span><span class="sxs-lookup"><span data-stu-id="ff462-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="ff462-162">Du kan få en referens till en WMI-klass i stället för klass instanser genom att lista alla WMI-klasser och sedan välja enbart den önskade klassen efter namn.</span><span class="sxs-lookup"><span data-stu-id="ff462-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="ff462-163">Följande kommando returnerar till exempel klassen Win32_NetworkAdapterConfiguration:</span><span class="sxs-lookup"><span data-stu-id="ff462-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="ff462-164">Du kan behandla hela kommandot som klass och sedan anropa metoden **ReleaseDHCPAdapterLease** på den.</span><span class="sxs-lookup"><span data-stu-id="ff462-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="ff462-165">I följande kommando kan parenteserna som omger Windows PowerShell för att utvärdera dem först i följande kommando:</span><span class="sxs-lookup"><span data-stu-id="ff462-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="ff462-166">Du kan använda samma kommando format för att anropa metoden **RenewDHCPLeaseAll** :</span><span class="sxs-lookup"><span data-stu-id="ff462-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="ff462-167">Skapa en nätverks resurs</span><span class="sxs-lookup"><span data-stu-id="ff462-167">Creating a Network Share</span></span>

<span data-ttu-id="ff462-168">Skapa en nätverks resurs genom att använda metoden **Win32_Share skapa** :</span><span class="sxs-lookup"><span data-stu-id="ff462-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="ff462-169">Du kan också skapa resursen med hjälp av **net share** i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ff462-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="ff462-170">Ta bort en nätverks resurs</span><span class="sxs-lookup"><span data-stu-id="ff462-170">Removing a Network Share</span></span>

<span data-ttu-id="ff462-171">Du kan ta bort en nätverks resurs med **Win32_Share**, men processen skiljer sig något från att skapa en resurs, eftersom du måste hämta den resurs som ska tas bort, i stället för **Win32_Share** -klassen.</span><span class="sxs-lookup"><span data-stu-id="ff462-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="ff462-172">Följande instruktion tar bort resursen "TempShare":</span><span class="sxs-lookup"><span data-stu-id="ff462-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="ff462-173">**Net share** fungerar också:</span><span class="sxs-lookup"><span data-stu-id="ff462-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="ff462-174">Ansluta en Windows-tillgänglig nätverks enhet</span><span class="sxs-lookup"><span data-stu-id="ff462-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="ff462-175">Cmdletarna **New-PSDrive** skapar en Windows PowerShell-enhet, men enheter som skapas på det här sättet är bara tillgängliga för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff462-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="ff462-176">Om du vill skapa en ny nätverksansluten enhet kan du använda **wscript. Network** com-objektet.</span><span class="sxs-lookup"><span data-stu-id="ff462-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="ff462-177">Följande kommando mappar resurs \\\\FPS01\\användare till lokal enhet B:</span><span class="sxs-lookup"><span data-stu-id="ff462-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="ff462-178">**Net use** -kommandot fungerar också:</span><span class="sxs-lookup"><span data-stu-id="ff462-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="ff462-179">Enheter som mappas med antingen **wscript. Network** eller net use är omedelbart tillgängliga för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff462-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>
