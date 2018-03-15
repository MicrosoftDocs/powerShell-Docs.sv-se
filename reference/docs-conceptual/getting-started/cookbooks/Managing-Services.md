---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Hantera tjänster"
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 1e83566b1cb3c0c9c3c78a5877e52552ee51b0e9
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="managing-services"></a><span data-ttu-id="1057e-103">Hantera tjänster</span><span class="sxs-lookup"><span data-stu-id="1057e-103">Managing Services</span></span>
<span data-ttu-id="1057e-104">Det finns åtta kärnor cmdlet: ar, utformad för en mängd olika uppgifter för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1057e-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="1057e-105">Beskrivs bara visa och ändra körs för tjänster, men du kan hämta en lista cmdlet: ar med hjälp av **Get-Help \&#42;-tjänsten**, och du kan hitta information om varje tjänst-cmdlet med hjälp av **Get-Help < Cmdlet Name >**, som **Get-Help ny tjänst**.</span><span class="sxs-lookup"><span data-stu-id="1057e-105">We will look only at listing and changing running state for services, but you can get a list Service cmdlets by using **Get-Help \&#42;-Service**, and you can find information about each Service cmdlet by using **Get-Help<Cmdlet-Name>**, such as **Get-Help New-Service**.</span></span>

## <a name="getting-services"></a><span data-ttu-id="1057e-106">Hämta tjänster</span><span class="sxs-lookup"><span data-stu-id="1057e-106">Getting Services</span></span>
<span data-ttu-id="1057e-107">Du kan hämta tjänsterna på en lokal eller fjärransluten dator med hjälp av den **Get-Service** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1057e-107">You can get the services on a local or remote computer by using the **Get-Service** cmdlet.</span></span> <span data-ttu-id="1057e-108">Precis som med **Get-Process**med hjälp av den **Get-Service** utan parametrar returnerar alla tjänster.</span><span class="sxs-lookup"><span data-stu-id="1057e-108">As with **Get-Process**, using the **Get-Service** command without parameters returns all services.</span></span> <span data-ttu-id="1057e-109">Du kan filtrera efter namn, även med en asterisk som jokertecken:</span><span class="sxs-lookup"><span data-stu-id="1057e-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```
PS> Get-Service -Name se*
Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="1057e-110">Eftersom det inte alltid är uppenbara verkliga namn för tjänsten är, kanske du vill söka efter tjänster enligt visningsnamn.</span><span class="sxs-lookup"><span data-stu-id="1057e-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="1057e-111">Du kan göra detta efter specifika namn med jokertecken eller med en lista över visningsnamn:</span><span class="sxs-lookup"><span data-stu-id="1057e-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```
PS> Get-Service -DisplayName se*
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center
PS> Get-Service -DisplayName ServiceLayer,Server
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="1057e-112">Du kan använda parametern ComputerName av cmdleten Get-Service för att hämta tjänsterna på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="1057e-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="1057e-113">Parametern ComputerName accepterar flera värden och jokertecken, så du kan hämta tjänsterna på flera datorer med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="1057e-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="1057e-114">Till exempel hämtar följande kommando tjänster på fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="1057e-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="1057e-115">Hämta krävs och beroende tjänster</span><span class="sxs-lookup"><span data-stu-id="1057e-115">Getting Required and Dependent Services</span></span>
<span data-ttu-id="1057e-116">Get-Service-cmdlet har två parametrar som är användbar om tjänsten administration.</span><span class="sxs-lookup"><span data-stu-id="1057e-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="1057e-117">Parametern DependentServices hämtar tjänster som är beroende av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1057e-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="1057e-118">Parametern RequiredServices hämtar tjänster som den här tjänsten är beroende.</span><span class="sxs-lookup"><span data-stu-id="1057e-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="1057e-119">Dessa parametrar kan bara visa värdena i DependentServices och ServicesDependedOn (alias = RequiredServices) egenskaper för objektet System.ServiceProcess.ServiceController som returnerar Get-Service, men de förenklar kommandon och göra komma den här informationen är mycket enklare.</span><span class="sxs-lookup"><span data-stu-id="1057e-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="1057e-120">Följande kommando hämtar de tjänster som krävs för LanmanWorkstation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1057e-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices
Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="1057e-121">Följande kommando hämtar de tjänster som kräver tjänsten LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="1057e-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -DependentServices
Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="1057e-122">Du kan även få alla tjänster som har beroenden.</span><span class="sxs-lookup"><span data-stu-id="1057e-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="1057e-123">Följande kommando använder just och sedan används Format-Table-cmdlet för att visa Status, namn, RequiredServices och DependentServices egenskaperna för tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="1057e-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```
Get-Service -Name * | where {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="1057e-124">Stoppa, starta, pausa och starta om tjänster</span><span class="sxs-lookup"><span data-stu-id="1057e-124">Stopping, Starting, Suspending, and Restarting Services</span></span>
<span data-ttu-id="1057e-125">I cmdlet: ar alla har samma allmänna formulär.</span><span class="sxs-lookup"><span data-stu-id="1057e-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="1057e-126">Tjänster kan anges med namn eller namn och ta listor och jokertecken som värden.</span><span class="sxs-lookup"><span data-stu-id="1057e-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="1057e-127">Om du vill stoppa utskriftshanteraren, använder du:</span><span class="sxs-lookup"><span data-stu-id="1057e-127">To stop the print spooler, use:</span></span>

```
Stop-Service -Name spooler
```

<span data-ttu-id="1057e-128">Starta utskriftshanteraren när den har avbrutits med:</span><span class="sxs-lookup"><span data-stu-id="1057e-128">To start the print spooler after it is stopped, use:</span></span>

```
Start-Service -Name spooler
```

<span data-ttu-id="1057e-129">Om du vill pausa Utskriftshanteraren, använder du:</span><span class="sxs-lookup"><span data-stu-id="1057e-129">To suspend the print spooler, use:</span></span>

```
Suspend-Service -Name spooler
```

<span data-ttu-id="1057e-130">Den **Restart-Service** cmdlet fungerar på samma sätt som andra cmdletar för tjänsten, men vi visar exempel mer komplexa för den.</span><span class="sxs-lookup"><span data-stu-id="1057e-130">The **Restart-Service** cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="1057e-131">Den enklaste används, kan du ange namnet på tjänsten:</span><span class="sxs-lookup"><span data-stu-id="1057e-131">In the simplest use, you specify the name of the service:</span></span>

```
PS> Restart-Service -Name spooler
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="1057e-132">Du ser att du får ett upprepade varningsmeddelande om utskriftshanteraren startas.</span><span class="sxs-lookup"><span data-stu-id="1057e-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="1057e-133">När du utför en åtgärd i tjänsten som tar en stund, meddelar Windows PowerShell dig att den fortfarande försöker utföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="1057e-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="1057e-134">Om du vill starta om flera tjänster kan du hämta en lista över tjänster, filtrera dem och genomföra omstarten:</span><span class="sxs-lookup"><span data-stu-id="1057e-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="1057e-135">Dessa cmdlet: ar har inte en parameter för datornamn, men du kan köra dem på en fjärrdator med hjälp av cmdleten Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="1057e-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="1057e-136">Till exempel följande kommando startar om utskriftshanteraren Server01 fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="1057e-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="1057e-137">Egenskaper för tjänsten</span><span class="sxs-lookup"><span data-stu-id="1057e-137">Setting Service Properties</span></span>
<span data-ttu-id="1057e-138">Cmdlet Set-tjänsten ändrar egenskaperna för en tjänst på en lokal eller fjärransluten dator.</span><span class="sxs-lookup"><span data-stu-id="1057e-138">The Set-Service cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="1057e-139">Eftersom tjänstestatus är en egenskap måste använda du denna cmdlet för att starta, stoppa och inaktivera en tjänst.</span><span class="sxs-lookup"><span data-stu-id="1057e-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span> <span data-ttu-id="1057e-140">Cmdlet Set-tjänsten har också en StartupType-parameter som låter dig ändra starttyp för tjänst.</span><span class="sxs-lookup"><span data-stu-id="1057e-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="1057e-141">För att använda Set-tjänst i Windows Vista och senare versioner av Windows, öppnar du Windows PowerShell med alternativet ”Kör som administratör”.</span><span class="sxs-lookup"><span data-stu-id="1057e-141">To use Set-Service on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="1057e-142">Mer information finns i [Set-tjänst [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="1057e-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="1057e-143">Se även</span><span class="sxs-lookup"><span data-stu-id="1057e-143">See Also</span></span>
- <span data-ttu-id="1057e-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="1057e-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="1057e-145">[Ange tjänst [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="1057e-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="1057e-146">[Starta om tjänsten [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="1057e-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="1057e-147">[Pausa tjänst [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="1057e-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>

