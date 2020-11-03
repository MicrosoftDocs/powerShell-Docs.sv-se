---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266114"
---
# <span data-ttu-id="45f67-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="45f67-103">Get-Service</span></span>

## <span data-ttu-id="45f67-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="45f67-104">SYNOPSIS</span></span>
<span data-ttu-id="45f67-105">Hämtar tjänsterna på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="45f67-105">Gets the services on a local or remote computer.</span></span>

## <span data-ttu-id="45f67-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="45f67-106">SYNTAX</span></span>

### <span data-ttu-id="45f67-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="45f67-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="45f67-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="45f67-108">DisplayName</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="45f67-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="45f67-109">InputObject</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="45f67-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="45f67-110">DESCRIPTION</span></span>

<span data-ttu-id="45f67-111">Cmdleten **Get-service** hämtar objekt som representerar tjänsterna på en lokal dator eller på en fjärrdator, inklusive tjänster som körs och stoppas.</span><span class="sxs-lookup"><span data-stu-id="45f67-111">The **Get-Service** cmdlet gets objects that represent the services on a local computer or on a remote computer, including running and stopped services.</span></span>

<span data-ttu-id="45f67-112">Du kan dirigera denna cmdlet för att bara få vissa tjänster genom att ange tjänst namnet eller visnings namnet för tjänsterna, eller så kan du skicka pipe-tjänst objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45f67-112">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="45f67-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="45f67-113">EXAMPLES</span></span>

### <span data-ttu-id="45f67-114">Exempel 1: Hämta alla tjänster på datorn</span><span class="sxs-lookup"><span data-stu-id="45f67-114">Example 1: Get all services on the computer</span></span>

```powershell
Get-Service
```

<span data-ttu-id="45f67-115">Det här kommandot hämtar alla tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-115">This command gets all of the services on the computer.</span></span>
<span data-ttu-id="45f67-116">Det fungerar som om du skriver `Get-Service *` .</span><span class="sxs-lookup"><span data-stu-id="45f67-116">It behaves as though you typed `Get-Service *`.</span></span>
<span data-ttu-id="45f67-117">Standard visningen visar status, tjänst namn och visnings namn för varje tjänst.</span><span class="sxs-lookup"><span data-stu-id="45f67-117">The default display shows the status, service name, and display name of each service.</span></span>

### <span data-ttu-id="45f67-118">Exempel 2: Hämta tjänster som börjar med en Sök sträng</span><span class="sxs-lookup"><span data-stu-id="45f67-118">Example 2: Get services that begin with a search string</span></span>

```powershell
Get-Service "wmi*"
```

<span data-ttu-id="45f67-119">Detta kommando hämtar tjänster med tjänst namn som börjar med WMI (akronym för Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="45f67-119">This command retrieves services with service names that begin with WMI (the acronym for Windows Management Instrumentation).</span></span>

### <span data-ttu-id="45f67-120">Exempel 3: Visa tjänster som innehåller en Sök sträng</span><span class="sxs-lookup"><span data-stu-id="45f67-120">Example 3: Display services that include a search string</span></span>

```powershell
Get-Service -Displayname "*network*"
```

<span data-ttu-id="45f67-121">Det här kommandot visar tjänster med ett visnings namn som innehåller ordet nätverk.</span><span class="sxs-lookup"><span data-stu-id="45f67-121">This command displays services with a display name that includes the word network.</span></span>
<span data-ttu-id="45f67-122">Om du söker efter visnings namnet hittar du nätverksrelaterade tjänster även om tjänst namnet inte innehåller "net", till exempel xmlprov, nätverks etablerings tjänsten.</span><span class="sxs-lookup"><span data-stu-id="45f67-122">Searching the display name finds network-related services even when the service name does not include "Net", such as xmlprov, the Network Provisioning Service.</span></span>

### <span data-ttu-id="45f67-123">Exempel 4: Hämta tjänster som börjar med en Sök sträng och ett undantag</span><span class="sxs-lookup"><span data-stu-id="45f67-123">Example 4: Get services that begin with a search string and an exclusion</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

<span data-ttu-id="45f67-124">De här kommandona hämtar bara tjänsterna med tjänst namn som börjar med Win, med undantag för WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="45f67-124">These commands get only the services with service names that begin with win, except for the WinRM service.</span></span>

### <span data-ttu-id="45f67-125">Exempel 5: Visa tjänster som är aktiva för närvarande</span><span class="sxs-lookup"><span data-stu-id="45f67-125">Example 5: Display services that are currently active</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="45f67-126">Det här kommandot visar bara de tjänster som är aktiva för närvarande.</span><span class="sxs-lookup"><span data-stu-id="45f67-126">This command displays only the services that are currently active.</span></span>
<span data-ttu-id="45f67-127">Den använder cmdleten **Get-service** för att hämta alla tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-127">It uses the **Get-Service** cmdlet to get all of the services on the computer.</span></span>
<span data-ttu-id="45f67-128">Pipeline-operatorn (|) skickar resultaten till Where-Object-cmdlet, som endast väljer de tjänster som har en status egenskap som är lika med kör.</span><span class="sxs-lookup"><span data-stu-id="45f67-128">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects only the services with a Status property that equals Running.</span></span>

<span data-ttu-id="45f67-129">Status är bara en egenskap för tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="45f67-129">Status is only one property of service objects.</span></span>
<span data-ttu-id="45f67-130">Om du vill se alla egenskaper skriver du `Get-Service | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="45f67-130">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="45f67-131">Exempel 6: Hämta tjänsterna på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="45f67-131">Example 6: Get the services on a remote computer</span></span>

```powershell
Get-Service -ComputerName "Server02"
```

<span data-ttu-id="45f67-132">Detta kommando hämtar tjänsterna på den fjärranslutna Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-132">This command gets the services on the Server02 remote computer.</span></span>

<span data-ttu-id="45f67-133">Eftersom parametern *computername* för **Get-service** inte använder Windows PowerShell-fjärrkommunikation kan du använda den här parametern även om datorn inte har kon figurer ATS för fjärr kommunikation i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45f67-133">Because the *ComputerName* parameter of **Get-Service** does not use Windows PowerShell remoting, you can use this parameter even if the computer is not configured for remoting in Windows PowerShell.</span></span>

### <span data-ttu-id="45f67-134">Exempel 7: Visa en lista över tjänsterna på den lokala datorn som har beroende tjänster</span><span class="sxs-lookup"><span data-stu-id="45f67-134">Example 7: List the services on the local computer that have dependent services</span></span>

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

<span data-ttu-id="45f67-135">Det första kommandot använder cmdleten **Get-service** för att hämta tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-135">The first command uses the **Get-Service** cmdlet to get the services on the computer.</span></span>
<span data-ttu-id="45f67-136">En pipeline-operator (|) skickar tjänsterna till **Where-Object-** cmdleten, som väljer de tjänster vars **DependentServices** -egenskap inte är null.</span><span class="sxs-lookup"><span data-stu-id="45f67-136">A pipeline operator (|) sends the services to the **Where-Object** cmdlet, which selects the services whose **DependentServices** property is not null.</span></span>

<span data-ttu-id="45f67-137">En annan pipeline-operator skickar resultatet till Format-List-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45f67-137">Another pipeline operator sends the results to the Format-List cmdlet.</span></span>
<span data-ttu-id="45f67-138">Kommandot använder *egenskaps* parametern för att visa namnet på tjänsten, namnet på de beroende tjänsterna och en beräknad egenskap som visar antalet beroende tjänster som varje tjänst har.</span><span class="sxs-lookup"><span data-stu-id="45f67-138">The command uses its *Property* parameter to display the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services that each service has.</span></span>

### <span data-ttu-id="45f67-139">Exempel 8: sortera tjänster efter egenskaps värde</span><span class="sxs-lookup"><span data-stu-id="45f67-139">Example 8: Sort services by property value</span></span>

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

<span data-ttu-id="45f67-140">Det här kommandot visar att när du sorterar tjänster i stigande ordning efter värdet för deras **status** egenskap visas stoppade tjänster innan tjänsterna körs.</span><span class="sxs-lookup"><span data-stu-id="45f67-140">This command shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span>
<span data-ttu-id="45f67-141">Detta inträffar eftersom värdet för status är en uppräkning, där stoppad har värdet 1 och körs har värdet 4.</span><span class="sxs-lookup"><span data-stu-id="45f67-141">This happens because the value of Status is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span>

<span data-ttu-id="45f67-142">Om du vill visa en lista med tjänster som körs först använder du parametern *fallande* i Sort-Object-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="45f67-142">To list running services first, use the *Descending* parameter of the Sort-Object cmdlet.</span></span>

### <span data-ttu-id="45f67-143">Exempel 9: Hämta tjänster på flera datorer</span><span class="sxs-lookup"><span data-stu-id="45f67-143">Example 9: Get services on multiple computers</span></span>

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

<span data-ttu-id="45f67-144">Det här kommandot använder cmdleten **Get-service** för att köra ett Get-Service WinRM-kommando på två fjärranslutna datorer och den lokala datorn ("localhost").</span><span class="sxs-lookup"><span data-stu-id="45f67-144">This command uses the **Get-Service** cmdlet to run a Get-Service Winrm command on two remote computers and the local computer ("localhost").</span></span>

<span data-ttu-id="45f67-145">Kommandot körs på fjärrdatorerna och resultaten returneras till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-145">The command runs on the remote computers, and the results are returned to the local computer.</span></span>
<span data-ttu-id="45f67-146">En pipeline-operator (|) skickar resultaten till **Format-Table-** cmdleten, som formaterar tjänsterna som en tabell.</span><span class="sxs-lookup"><span data-stu-id="45f67-146">A pipeline operator (|) sends the results to the **Format-Table** cmdlet, which formats the services as a table.</span></span>
<span data-ttu-id="45f67-147">Kommandot **Format-Table** använder *egenskaps* parametern för att ange de egenskaper som visas i tabellen, inklusive egenskapen **MachineName** .</span><span class="sxs-lookup"><span data-stu-id="45f67-147">The **Format-Table** command uses the *Property* parameter to specify the properties displayed in the table, including the **MachineName** property.</span></span>

### <span data-ttu-id="45f67-148">Exempel 10: Hämta de beroende tjänsterna för en tjänst</span><span class="sxs-lookup"><span data-stu-id="45f67-148">Example 10: Get the dependent services of a service</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

<span data-ttu-id="45f67-149">Det här kommandot hämtar de tjänster som krävs av WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="45f67-149">This command gets the services that the WinRM service requires.</span></span>

<span data-ttu-id="45f67-150">Kommandot returnerar värdet för tjänstens **ServicesDependedOn** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="45f67-150">The command returns the value of the **ServicesDependedOn** property of the service.</span></span>

### <span data-ttu-id="45f67-151">Exempel 11: Hämta en tjänst via pipeline-operatören</span><span class="sxs-lookup"><span data-stu-id="45f67-151">Example 11: Get a service through the pipeline operator</span></span>

```powershell
"WinRM" | Get-Service
```

<span data-ttu-id="45f67-152">Det här kommandot hämtar WinRM-tjänsten på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-152">This command gets the WinRM service on the local computer.</span></span>
<span data-ttu-id="45f67-153">Det här exemplet visar att du kan skicka en tjänst namn sträng (inom citat tecken) till **Get-service**.</span><span class="sxs-lookup"><span data-stu-id="45f67-153">This example shows that you can pipe a service name string (enclosed in quotation marks) to **Get-Service**.</span></span>

## <span data-ttu-id="45f67-154">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="45f67-154">PARAMETERS</span></span>

### <span data-ttu-id="45f67-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="45f67-155">-ComputerName</span></span>

<span data-ttu-id="45f67-156">Hämtar de tjänster som körs på de angivna datorerna.</span><span class="sxs-lookup"><span data-stu-id="45f67-156">Gets the services running on the specified computers.</span></span>
<span data-ttu-id="45f67-157">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-157">The default is the local computer.</span></span>

<span data-ttu-id="45f67-158">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="45f67-158">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="45f67-159">Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.</span><span class="sxs-lookup"><span data-stu-id="45f67-159">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="45f67-160">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="45f67-160">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="45f67-161">Du kan använda parametern *computername* för **Get-service** även om datorn inte har kon figurer ATS för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="45f67-161">You can use the *ComputerName* parameter of **Get-Service** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="45f67-162">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="45f67-162">-DependentServices</span></span>

<span data-ttu-id="45f67-163">Anger att denna cmdlet endast hämtar de tjänster som är beroende av den angivna tjänsten.</span><span class="sxs-lookup"><span data-stu-id="45f67-163">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

<span data-ttu-id="45f67-164">Som standard hämtar denna cmdlet alla tjänster.</span><span class="sxs-lookup"><span data-stu-id="45f67-164">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45f67-165">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="45f67-165">-DisplayName</span></span>

<span data-ttu-id="45f67-166">Anger, som en sträng mat ris, visnings namnen för de tjänster som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="45f67-166">Specifies, as a string array, the display names of services to be retrieved.</span></span>
<span data-ttu-id="45f67-167">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="45f67-167">Wildcards are permitted.</span></span>
<span data-ttu-id="45f67-168">Som standard hämtar denna cmdlet alla tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-168">By default, this cmdlet gets all services on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="45f67-169">-Undanta</span><span class="sxs-lookup"><span data-stu-id="45f67-169">-Exclude</span></span>

<span data-ttu-id="45f67-170">Anger, som en sträng mat ris, en tjänst eller tjänster som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="45f67-170">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="45f67-171">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="45f67-171">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="45f67-172">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="45f67-172">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="45f67-173">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="45f67-173">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="45f67-174">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="45f67-174">-Include</span></span>

<span data-ttu-id="45f67-175">Anger, som en sträng mat ris, en tjänst eller tjänster som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="45f67-175">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="45f67-176">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="45f67-176">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="45f67-177">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="45f67-177">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="45f67-178">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="45f67-178">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="45f67-179">– InputObject</span><span class="sxs-lookup"><span data-stu-id="45f67-179">-InputObject</span></span>

<span data-ttu-id="45f67-180">Anger **ServiceController** -objekt som representerar de tjänster som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="45f67-180">Specifies **ServiceController** objects representing the services to be retrieved.</span></span>
<span data-ttu-id="45f67-181">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="45f67-181">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>
<span data-ttu-id="45f67-182">Du kan också skicka ett tjänst objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45f67-182">You can also pipe a service object to this cmdlet.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45f67-183">-Name</span><span class="sxs-lookup"><span data-stu-id="45f67-183">-Name</span></span>

<span data-ttu-id="45f67-184">Anger tjänst namnen för de tjänster som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="45f67-184">Specifies the service names of services to be retrieved.</span></span>
<span data-ttu-id="45f67-185">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="45f67-185">Wildcards are permitted.</span></span>
<span data-ttu-id="45f67-186">Som standard hämtar denna cmdlet alla tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-186">By default, this cmdlet gets all of the services on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="45f67-187">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="45f67-187">-RequiredServices</span></span>

<span data-ttu-id="45f67-188">Anger att denna cmdlet bara hämtar de tjänster som krävs för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="45f67-188">Indicates that this cmdlet gets only the services that this service requires.</span></span>

<span data-ttu-id="45f67-189">Den här parametern hämtar värdet för tjänstens **ServicesDependedOn** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="45f67-189">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>
<span data-ttu-id="45f67-190">Som standard hämtar denna cmdlet alla tjänster.</span><span class="sxs-lookup"><span data-stu-id="45f67-190">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="45f67-191">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45f67-191">CommonParameters</span></span>

<span data-ttu-id="45f67-192">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="45f67-192">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45f67-193">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="45f67-193">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45f67-194">INDATA</span><span class="sxs-lookup"><span data-stu-id="45f67-194">INPUTS</span></span>

### <span data-ttu-id="45f67-195">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="45f67-195">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="45f67-196">Du kan skicka vidare ett tjänst objekt eller ett tjänst namn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45f67-196">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="45f67-197">UTDATA</span><span class="sxs-lookup"><span data-stu-id="45f67-197">OUTPUTS</span></span>

### <span data-ttu-id="45f67-198">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="45f67-198">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="45f67-199">Denna cmdlet returnerar objekt som representerar tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="45f67-199">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="45f67-200">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="45f67-200">NOTES</span></span>

<span data-ttu-id="45f67-201">Du kan också referera till **Get-service** med det inbyggda aliaset "GSV".</span><span class="sxs-lookup"><span data-stu-id="45f67-201">You can also refer to **Get-Service** by its built-in alias, "gsv".</span></span> <span data-ttu-id="45f67-202">Mer information finns i about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="45f67-202">For more information, see about_Aliases.</span></span>

<span data-ttu-id="45f67-203">Den här cmdleten kan endast Visa tjänster när den aktuella användaren har behörighet att se dem.</span><span class="sxs-lookup"><span data-stu-id="45f67-203">This cmdlet can display services only when the current user has permission to see them.</span></span>
<span data-ttu-id="45f67-204">Om denna cmdlet inte visar tjänster kanske du inte har behörighet att se dem.</span><span class="sxs-lookup"><span data-stu-id="45f67-204">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="45f67-205">Om du vill hitta tjänst namnet och visnings namnet för varje tjänst i systemet skriver du `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="45f67-205">To find the service name and display name of each service on your system, type `Get-Service`.</span></span>
<span data-ttu-id="45f67-206">Tjänst namnen visas i kolumnen namn och visnings namnen visas i kolumnen DisplayName.</span><span class="sxs-lookup"><span data-stu-id="45f67-206">The service names appear in the Name column, and the display names appear in the DisplayName column.</span></span>

<span data-ttu-id="45f67-207">När du sorterar i stigande ordning efter status värde visas "stoppad" tjänster innan "körs"-tjänster.</span><span class="sxs-lookup"><span data-stu-id="45f67-207">When you sort in ascending order by status value, "Stopped" services appear before "Running" services.</span></span>
<span data-ttu-id="45f67-208">Tjänstens status egenskap är ett uppräknat värde där namnen på statusarna representerar heltals värden.</span><span class="sxs-lookup"><span data-stu-id="45f67-208">The Status property of a service is an enumerated value in which the names of the statuses represent integer values.</span></span>
<span data-ttu-id="45f67-209">Sorteringen baseras på heltal svärdet, inte namnet.</span><span class="sxs-lookup"><span data-stu-id="45f67-209">The sort is based on the integer value, not the name.</span></span>
<span data-ttu-id="45f67-210">"Körs" visas före "stoppad" eftersom "stoppad" har värdet "1" och "körs" har värdet "4".</span><span class="sxs-lookup"><span data-stu-id="45f67-210">"Running" appears before "Stopped" because "Stopped" has a value of "1", and "Running" has a value of "4".</span></span>

## <span data-ttu-id="45f67-211">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="45f67-211">RELATED LINKS</span></span>

[<span data-ttu-id="45f67-212">New-Service</span><span class="sxs-lookup"><span data-stu-id="45f67-212">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="45f67-213">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="45f67-213">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="45f67-214">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="45f67-214">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="45f67-215">Set-Service</span><span class="sxs-lookup"><span data-stu-id="45f67-215">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="45f67-216">Start-Service</span><span class="sxs-lookup"><span data-stu-id="45f67-216">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="45f67-217">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="45f67-217">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="45f67-218">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="45f67-218">Suspend-Service</span></span>](Suspend-Service.md)
