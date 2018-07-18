---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Hantera tjänster
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: e2388f5d73a320a69faae0772c8403a7d77f8b52
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094178"
---
# <a name="managing-services"></a><span data-ttu-id="24566-103">Hantera tjänster</span><span class="sxs-lookup"><span data-stu-id="24566-103">Managing Services</span></span>

<span data-ttu-id="24566-104">Det finns åtta kärnor cmdlet: ar, avsedd för en mängd olika uppgifter för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="24566-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="24566-105">Vi bara lista och ändra körningstillstånd för tjänster, men du kan hämta en lista över cmdlet: ar med hjälp av **Get-Help \*-tjänsten**, och du hittar information om varje tjänst-cmdlet med hjälp av  **Get-Help \<Cmdlet-namn\>**, till exempel **Get-Help ny tjänsten**.</span><span class="sxs-lookup"><span data-stu-id="24566-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using **Get-Help \*-Service**, and you can find information about each Service cmdlet by using **Get-Help \<Cmdlet-Name\>**, such as **Get-Help New-Service**.</span></span>

## <a name="getting-services"></a><span data-ttu-id="24566-106">Hämta tjänster</span><span class="sxs-lookup"><span data-stu-id="24566-106">Getting Services</span></span>

<span data-ttu-id="24566-107">Du kan hämta tjänsterna på en lokal eller fjärransluten dator med hjälp av den **Get-Service** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24566-107">You can get the services on a local or remote computer by using the **Get-Service** cmdlet.</span></span> <span data-ttu-id="24566-108">Precis som med **Get-Process**med hjälp av den **Get-Service** utan parametrar returnerar alla tjänster.</span><span class="sxs-lookup"><span data-stu-id="24566-108">As with **Get-Process**, using the **Get-Service** command without parameters returns all services.</span></span> <span data-ttu-id="24566-109">Du kan filtrera efter namn, även med en asterisk som jokertecken:</span><span class="sxs-lookup"><span data-stu-id="24566-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="24566-110">Eftersom det inte är alltid uppenbart vad som är det verkliga namnet för tjänsten, kanske du vill söka efter tjänster efter visningsnamn.</span><span class="sxs-lookup"><span data-stu-id="24566-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="24566-111">Du kan göra detta efter specifika namn med jokertecken eller med en lista med namn som visas:</span><span class="sxs-lookup"><span data-stu-id="24566-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

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

<span data-ttu-id="24566-112">Du kan använda parametern ComputerName för cmdlet Get-Service för att få tjänsterna på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="24566-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="24566-113">Parametern ComputerName accepterar flera värden och jokertecken, så att du kan hämta tjänsterna på flera datorer med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="24566-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="24566-114">Följande kommando hämtar tjänsterna på fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="24566-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="24566-115">Hämta krävs och beroende tjänster</span><span class="sxs-lookup"><span data-stu-id="24566-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="24566-116">Cmdleten Get-Service har två parametrar som är mycket användbar för administration av tjänster.</span><span class="sxs-lookup"><span data-stu-id="24566-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="24566-117">Parametern DependentServices hämtar tjänster som är beroende av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="24566-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="24566-118">Parametern RequiredServices hämtar tjänster som den här tjänsten är beroende av.</span><span class="sxs-lookup"><span data-stu-id="24566-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="24566-119">Dessa parametrar kan bara visa värdena i DependentServices och ServicesDependedOn (alias = RequiredServices) egenskaperna för objektet System.ServiceProcess.ServiceController som gör det enklare för Get-Service returnerar, men de kommandon och göra komma den här informationen är mycket enklare.</span><span class="sxs-lookup"><span data-stu-id="24566-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="24566-120">Följande kommando hämtar de tjänster som krävs för LanmanWorkstation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="24566-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="24566-121">Följande kommando hämtar de tjänster som kräver LanmanWorkstation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="24566-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="24566-122">Du kan även få alla tjänster som har beroenden.</span><span class="sxs-lookup"><span data-stu-id="24566-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="24566-123">Kommandot gör just detta och sedan används Format-Table-cmdlet för att visa Status, namn, RequiredServices och DependentServices egenskaperna för tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="24566-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="24566-124">Stoppa, starta, pausa och startar om tjänster</span><span class="sxs-lookup"><span data-stu-id="24566-124">Stopping, Starting, Suspending, and Restarting Services</span></span>
<span data-ttu-id="24566-125">De cmdlet: ar alla ha samma allmänna formulär.</span><span class="sxs-lookup"><span data-stu-id="24566-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="24566-126">Tjänster kan anges med egna namn eller visningsnamn och ta listor och jokertecken som värden.</span><span class="sxs-lookup"><span data-stu-id="24566-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="24566-127">Om du vill stoppa utskriftshanteraren, använder du:</span><span class="sxs-lookup"><span data-stu-id="24566-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="24566-128">För att starta utskriftshanteraren när den är stoppad, använder du:</span><span class="sxs-lookup"><span data-stu-id="24566-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="24566-129">Om du vill pausa Utskriftshanteraren, använder du:</span><span class="sxs-lookup"><span data-stu-id="24566-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="24566-130">Den **Restart-Service** cmdlet fungerar på samma sätt som den andra cmdlet: ar, men vi visar några mer komplexa exempel för den.</span><span class="sxs-lookup"><span data-stu-id="24566-130">The **Restart-Service** cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="24566-131">I det enklaste användningsområdet anger du namnet på tjänsten:</span><span class="sxs-lookup"><span data-stu-id="24566-131">In the simplest use, you specify the name of the service:</span></span>

```
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="24566-132">Du ser att du får ett upprepade varningsmeddelande om utskriftshanteraren startar.</span><span class="sxs-lookup"><span data-stu-id="24566-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="24566-133">När du utför en åtgärd i tjänsten som tar lite tid, meddelar Windows PowerShell dig att den fortfarande försöker utföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="24566-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="24566-134">Om du vill starta om flera tjänster kan du hämta en lista över tjänster, filtrera dem och genomföra omstarten:</span><span class="sxs-lookup"><span data-stu-id="24566-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

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

<span data-ttu-id="24566-135">Dessa cmdlet: ar har inte en ComputerName-parameter, men du kan köra dem på en fjärrdator med hjälp av cmdleten Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="24566-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="24566-136">Till exempel följande kommando startar om utskriftshanteraren Server01 fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="24566-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="24566-137">Egenskaper för tjänsten</span><span class="sxs-lookup"><span data-stu-id="24566-137">Setting Service Properties</span></span>

<span data-ttu-id="24566-138">Cmdleten Set-Service ändrar egenskaperna för en tjänst på en lokal eller fjärransluten dator.</span><span class="sxs-lookup"><span data-stu-id="24566-138">The Set-Service cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="24566-139">Eftersom status för tjänsten är en egenskap, kan du använda denna cmdlet för att starta, stoppa och inaktivera en tjänst.</span><span class="sxs-lookup"><span data-stu-id="24566-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span> <span data-ttu-id="24566-140">Cmdleten Set-Service har också en startuptype för parameter som du kan ändra starttypen för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="24566-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="24566-141">För att använda Set-tjänst i Windows Vista och senare versioner av Windows, öppnar du Windows PowerShell med alternativet ”Kör som administratör”.</span><span class="sxs-lookup"><span data-stu-id="24566-141">To use Set-Service on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="24566-142">Mer information finns i [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="24566-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="24566-143">Se även</span><span class="sxs-lookup"><span data-stu-id="24566-143">See Also</span></span>

- <span data-ttu-id="24566-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="24566-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="24566-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="24566-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="24566-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="24566-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="24566-147">[Pausa tjänst [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="24566-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>