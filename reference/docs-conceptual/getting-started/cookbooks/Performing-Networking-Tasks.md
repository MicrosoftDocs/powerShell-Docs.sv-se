---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Utför nätverksuppgifter
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 64c57c95a70bc4cad4b695a59d96673ed18afdf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954134"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="a8eb6-103">Utför nätverksuppgifter</span><span class="sxs-lookup"><span data-stu-id="a8eb6-103">Performing Networking Tasks</span></span>

<span data-ttu-id="a8eb6-104">Eftersom TCP/IP är det vanligaste nätverksprotokollet, omfattar de flesta administrationsuppgifter för låg nivå nätverket protokollet TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="a8eb6-105">I det här avsnittet använder vi Windows PowerShell och WMI för att utföra dessa uppgifter.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

### <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="a8eb6-106">Visar en lista över IP-adresser för en dator</span><span class="sxs-lookup"><span data-stu-id="a8eb6-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="a8eb6-107">Om du vill hämta alla IP-adresser som används på den lokala datorn, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="a8eb6-108">Utdata från kommandot skiljer sig från de flesta egenskapslistor eftersom värden står inom klammerparenteser:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="a8eb6-109">För att förstå varför klammerparenteserna visas, Använd cmdleten Get-medlem för att granska den **IPAddress** egenskapen:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="a8eb6-110">Egenskapen IP-adress för varje nätverkskort är faktiskt en matris.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="a8eb6-111">Klammerparenteser i definitionen indikerar att **IPAddress** är inte en **System.String** värde, men en matris med **System.String** värden.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

### <a name="listing-ip-configuration-data"></a><span data-ttu-id="a8eb6-112">Visar en lista över IP-konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="a8eb6-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="a8eb6-113">Om du vill visa detaljerad IP-konfigurationsdata för varje nätverkskort, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="a8eb6-114">Visa standard för konfigurationsobjektet nätverket nätverkskort är mycket uppsättning begränsade tillgänglig information.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="a8eb6-115">Använd Select-Object eller en formatering cmdlet, till exempel Format-List för att ange egenskaper som ska visas för djupgående undersökning och felsökning.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="a8eb6-116">Om du inte är intresserad av IPX eller WINS-egenskaper – förmodligen skiftläget för ett moderna TCP/IP-nätverk – du kan använda parametern ExcludeProperty i Select-Object för att dölja egenskaper med namn som börjar med ”WINS” eller ”IPX”:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="a8eb6-117">Det här kommandot returnerar detaljerad information om DHCP, DNS, Routning och andra egenskaper för mindre IP-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

### <a name="pinging-computers"></a><span data-ttu-id="a8eb6-118">Pinga datorer</span><span class="sxs-lookup"><span data-stu-id="a8eb6-118">Pinging Computers</span></span>

<span data-ttu-id="a8eb6-119">Du kan utföra en enkel ping mot en datorn med hjälp av **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="a8eb6-120">Följande kommando utför ping, men returnerar långa utdata:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="a8eb6-121">Ett mer användbar formulär för sammanfattningsinformation en visning av egenskaperna adress, ResponseTime och StatusCode som genererats med följande kommando.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="a8eb6-122">Parametern Autosize för Format-Table storlek tabellkolumnerna så att de visas korrekt i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="a8eb6-123">En StatusCode 0 anger en lyckad ping.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="a8eb6-124">Du kan använda en matris för att pinga flera datorer med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="a8eb6-125">Eftersom det finns mer än en adress, använder den **ForEach-Object** att pinga varje adress separat:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="a8eb6-126">Du kan använda samma kommandoformat för att pinga alla datorer i ett undernät, till exempel ett privat nätverk som använder nätverksnummer 192.168.1.0 och standard klass C nätmask (255.255.255.0)., endast adresser mellan 192.168.1.1 via 192.168.1.254 berättigade lokala adresser (0 är alltid har reserverats för nätverksnumret och 255 är en undernät broadcast-adress).</span><span class="sxs-lookup"><span data-stu-id="a8eb6-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="a8eb6-127">Representerar en matris med tal mellan 1 och 254 i Windows PowerShell använder du uttrycket **1..254.**</span><span class="sxs-lookup"><span data-stu-id="a8eb6-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="a8eb6-128">En fullständig undernät ping kan utföras genom att generera matrisen och sedan lägga till värden till en partiell adress i instruktionen ping:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="a8eb6-129">Observera att den här tekniken för att generera ett adressintervall kan användas samt någon annanstans.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="a8eb6-130">Du kan skapa en fullständig uppsättning adresser i det här sättet:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="a8eb6-131">Hämta egenskaper för nätverkskort</span><span class="sxs-lookup"><span data-stu-id="a8eb6-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="a8eb6-132">Tidigare i den här användarhandboken nämnts kan du hämta egenskaper för allmän konfiguration med hjälp av **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="a8eb6-133">Även om inte strikt TCP/IP-information, nätverkskortinformation, till exempel MAC-adresser och typer av nätverkskort kan användas för att förstå vad som händer med en dator.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="a8eb6-134">Använd följande kommando för att få en översikt över den här informationen:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="a8eb6-135">Tilldela DNS-domän för ett nätverkskort</span><span class="sxs-lookup"><span data-stu-id="a8eb6-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="a8eb6-136">Om du vill tilldela DNS-domän för automatisk namnmatchning, Använd den **Win32_NetworkAdapterConfiguration SetDNSDomain** metod.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="a8eb6-137">Eftersom du tilldelar DNS-domän för varje nätverkskortskonfiguration separat, måste du använda en **ForEach-Object** instruktionen för att tilldela varje kort domänen:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="a8eb6-138">Instruktionen filtrering ”IPEnabled = $true” är nödvändigt eftersom även på ett nätverk som använder endast TCP/IP flera konfigurationerna för nätverkskortet på en dator inte är SANT TCP/IP-nätverkskorten; de allmänna element stöder RAS, PPTP, QoS och andra tjänster för alla nätverkskort och därmed har inte en adress av sina egna.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="a8eb6-139">Du kan filtrera kommandot med hjälp av den **Where-Object** cmdlet, istället för att använda den **Get-WmiObject** filter.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="a8eb6-140">Utföra åtgärder för DHCP-konfiguration</span><span class="sxs-lookup"><span data-stu-id="a8eb6-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="a8eb6-141">Ändra DHCP information innebär att arbeta med en uppsättning nätverkskort, precis som DNS-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="a8eb6-142">Det finns flera olika åtgärder du kan utföra med hjälp av WMI och vi kommer att gå igenom några av de vanliga.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

#### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="a8eb6-143">När du fastställer DHCP-aktiverade nätverkskort</span><span class="sxs-lookup"><span data-stu-id="a8eb6-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="a8eb6-144">Om du vill söka efter de DHCP-aktiverade nätverkskort på en dator, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="a8eb6-145">Om du vill exkludera nätverkskort med problem med IP-konfiguration kan du hämta IP-aktiverade nätverkskort:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="a8eb6-146">Hämta egenskaper för DHCP</span><span class="sxs-lookup"><span data-stu-id="a8eb6-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="a8eb6-147">Eftersom DHCP-relaterade egenskaper för ett kort vanligtvis börjar med ”DHCP”, kan du använda egenskapen-parametern för Format-Table ska visas endast de egenskaperna:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="a8eb6-148">Aktivera DHCP på varje nätverkskort</span><span class="sxs-lookup"><span data-stu-id="a8eb6-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="a8eb6-149">För att aktivera DHCP på alla nätverkskort, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="a8eb6-150">Du kan använda den **Filter** instruktionen ”IPEnabled = $true och DHCPEnabled = $false” att undvika att aktivera DHCP där det redan har aktiverats, men utan det här steget inte orsakar fel.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="a8eb6-151">Frisläppa och förnya DHCP-lån på särskilda nätverkskort</span><span class="sxs-lookup"><span data-stu-id="a8eb6-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="a8eb6-152">Den **Win32_NetworkAdapterConfiguration** klassen har **ReleaseDHCPLease** och **RenewDHCPLease** metoder.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="a8eb6-153">Båda används på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-153">Both are used in the same way.</span></span> <span data-ttu-id="a8eb6-154">I allmänhet kan använda dessa metoder om du bara behöver frigöra eller förnya adresser för ett nätverkskort i ett visst undernät.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="a8eb6-155">Det enklaste sättet att filtret nätverkskort i ett undernät är att välja endast de konfigurationer som använder en gateway för det undernätet.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="a8eb6-156">Till exempel släpper följande kommando alla DHCP-lån på nätverkskort på den lokala datorn som erhåller DHCP-lån från 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="a8eb6-157">Den enda förändringen för att förnya ett DHCP-lån är att använda den **RenewDHCPLease** metod i stället för den **ReleaseDHCPLease** metod:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="a8eb6-158">När du använder metoderna på en fjärrdator, Tänk på att du kan förlora åtkomsten till fjärrdatorn om du är ansluten till den via kortet med utgivna eller förnyat lånet.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="a8eb6-159">Frisläppa och förnya DHCP-lån på alla nätverkskort</span><span class="sxs-lookup"><span data-stu-id="a8eb6-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="a8eb6-160">Du kan utföra globala DHCP-adress versioner eller uppdateringar på alla nätverkskort med hjälp av den **Win32_NetworkAdapterConfiguration** metoder, **ReleaseDHCPLeaseAll** och **RenewDHCPLeaseAll** .</span><span class="sxs-lookup"><span data-stu-id="a8eb6-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="a8eb6-161">Dock kommandot måste gälla för WMI-klassen, i stället för en särskild adapter eftersom släppa och förnya lån globalt utförs på klassen inte på ett visst nätverkskort.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="a8eb6-162">Du kan hämta en referens till en WMI-klass, i stället för klassinstanser, genom att visa en lista över alla WMI-klasser och sedan välja önskad klass efter namn.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="a8eb6-163">Till exempel returnerar följande kommando Win32_NetworkAdapterConfiguration-klassen:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="a8eb6-164">Du kan hantera hela kommandot som klassen och sedan anropa den **ReleaseDHCPAdapterLease** metod på den.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="a8eb6-165">I följande kommando, parentes runt den **Get-WmiObject** och **Where-Object** pipeline element dirigera Windows PowerShell för att utvärdera dem först:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="a8eb6-166">Du kan använda samma kommandoformat för att anropa den **RenewDHCPLeaseAll** metod:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a><span data-ttu-id="a8eb6-167">Skapa en nätverksresurs</span><span class="sxs-lookup"><span data-stu-id="a8eb6-167">Creating a Network Share</span></span>

<span data-ttu-id="a8eb6-168">Så här skapar du en nätverksresurs i **Win32_Share skapa** metoden:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="a8eb6-169">Du kan också skapa resursen med hjälp av **net share** i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a><span data-ttu-id="a8eb6-170">Tar bort en nätverksresurs</span><span class="sxs-lookup"><span data-stu-id="a8eb6-170">Removing a Network Share</span></span>

<span data-ttu-id="a8eb6-171">Du kan ta bort en nätverksresurs med **Win32_Share**, men processen skiljer sig från att skapa en resurs, eftersom du behöver hämta specifika resursen tas bort, snarare än den **Win32_Share** klass.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="a8eb6-172">Följande instruktion tar bort resurs ”TempShare”:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="a8eb6-173">**Net share** fungerar också:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="a8eb6-174">Ansluter en Windows-tillgänglig nätverksenhet</span><span class="sxs-lookup"><span data-stu-id="a8eb6-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="a8eb6-175">Den **ny PSDrive** cmdlets skapar ett Windows PowerShell-enhet, men enheter som har skapats på detta sätt är bara tillgängliga för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="a8eb6-176">Du kan använda för att skapa en ny nätverksansluten enhet, den **WScript.Network** COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="a8eb6-177">Följande kommando mappar resursen \\ \\FPS01\\användare till en lokal enhet B:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="a8eb6-178">Den **net Använd** kommandot fungerar också:</span><span class="sxs-lookup"><span data-stu-id="a8eb6-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="a8eb6-179">Enheter mappade med antingen **WScript.Network** eller net användning är omedelbart tillgängliga för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8eb6-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>