---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Hantera tjänster
ms.openlocfilehash: 7a238a3fea857c5dac1c12ca0d0371a49e6bf58c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870531"
---
# <a name="managing-services"></a><span data-ttu-id="50886-103">Hantera tjänster</span><span class="sxs-lookup"><span data-stu-id="50886-103">Managing Services</span></span>

<span data-ttu-id="50886-104">Det finns åtta Core Service-cmdletar som är utformade för ett brett utbud av tjänst uppgifter.</span><span class="sxs-lookup"><span data-stu-id="50886-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="50886-105">Vi kommer bara att titta på att visa och ändra körnings tillstånd för tjänster, men du kan hämta en lista över tjänst- `Get-Help \*-Service`cmdletar med hjälp av, och du kan hitta information om `Get-Help <Cmdlet-Name>`varje tjänst- `Get-Help New-Service`cmdlet med hjälp av, till exempel.</span><span class="sxs-lookup"><span data-stu-id="50886-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="50886-106">Hämtar tjänster</span><span class="sxs-lookup"><span data-stu-id="50886-106">Getting Services</span></span>

<span data-ttu-id="50886-107">Du kan hämta tjänsterna på en lokal dator eller fjärrdator med hjälp av `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="50886-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="50886-108">Som med `Get-Process`kan du `Get-Service` använda kommandot utan parametrar för att returnera alla tjänster.</span><span class="sxs-lookup"><span data-stu-id="50886-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="50886-109">Du kan filtrera efter namn, även använda en asterisk som jokertecken:</span><span class="sxs-lookup"><span data-stu-id="50886-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="50886-110">Eftersom det inte alltid är uppenbart vad det riktiga namnet för tjänsten är, kan du hitta tjänster efter visnings namn.</span><span class="sxs-lookup"><span data-stu-id="50886-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="50886-111">Du kan göra detta med ett angivet namn, använda jokertecken eller med en lista med visnings namn:</span><span class="sxs-lookup"><span data-stu-id="50886-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
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

<span data-ttu-id="50886-112">Du kan använda parametern ComputerName för Get-service-cmdlet: en för att hämta tjänsterna på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="50886-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="50886-113">Parametern ComputerName accepterar flera värden och jokertecken, så att du kan hämta tjänsterna på flera datorer med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="50886-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="50886-114">Följande kommando hämtar till exempel tjänsterna på den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="50886-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="50886-115">Hämtar nödvändiga och beroende tjänster</span><span class="sxs-lookup"><span data-stu-id="50886-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="50886-116">Cmdleten Get-service har två parametrar som är mycket användbara vid tjänst administration.</span><span class="sxs-lookup"><span data-stu-id="50886-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="50886-117">Parametern DependentServices hämtar tjänster som är beroende av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="50886-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="50886-118">Parametern RequiredServices hämtar tjänster som den här tjänsten är beroende av.</span><span class="sxs-lookup"><span data-stu-id="50886-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="50886-119">Dessa parametrar visar bara värdena för egenskaperna DependentServices och ServicesDependedOn (alias = RequiredServices) för objektet system. ServiceProcess. ServiceController som Get-service returnerar, men de fören klar kommandon och gör så att den här informationen blir mycket enklare.</span><span class="sxs-lookup"><span data-stu-id="50886-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="50886-120">Följande kommando hämtar de tjänster som LanmanWorkstation-tjänsten kräver.</span><span class="sxs-lookup"><span data-stu-id="50886-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="50886-121">Följande kommando hämtar de tjänster som kräver LanmanWorkstation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="50886-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="50886-122">Du kan till och med hämta alla tjänster som har beroenden.</span><span class="sxs-lookup"><span data-stu-id="50886-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="50886-123">Följande kommando fungerar precis som och använder sedan Format-Table-cmdlet: en för att visa egenskaperna status, Name, RequiredServices och DependentServices för tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="50886-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="50886-124">Stoppa, starta, pausa och starta om tjänster</span><span class="sxs-lookup"><span data-stu-id="50886-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="50886-125">Alla tjänst-cmdletar har samma generella form.</span><span class="sxs-lookup"><span data-stu-id="50886-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="50886-126">Tjänster kan anges med eget namn eller visnings namn och ta listor och jokertecken som värden.</span><span class="sxs-lookup"><span data-stu-id="50886-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="50886-127">Om du vill stoppa utskrifts hanteraren använder du:</span><span class="sxs-lookup"><span data-stu-id="50886-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="50886-128">Starta utskrifts hanteraren när den har stoppats genom att använda:</span><span class="sxs-lookup"><span data-stu-id="50886-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="50886-129">Om du vill pausa utskrifts hanteraren använder du:</span><span class="sxs-lookup"><span data-stu-id="50886-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="50886-130">`Restart-Service` Cmdleten fungerar på samma sätt som de andra tjänst-cmdletarna, men vi kommer att visa några mer komplexa exempel för den.</span><span class="sxs-lookup"><span data-stu-id="50886-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="50886-131">I den enklaste användningen anger du namnet på tjänsten:</span><span class="sxs-lookup"><span data-stu-id="50886-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="50886-132">Du ser att du får ett upprepande varnings meddelande om utskrifts hanteraren startar.</span><span class="sxs-lookup"><span data-stu-id="50886-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="50886-133">När du utför en tjänst åtgärd som tar en stund meddelar Windows PowerShell dig att den fortfarande försöker utföra uppgiften.</span><span class="sxs-lookup"><span data-stu-id="50886-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="50886-134">Om du vill starta om flera tjänster kan du hämta en lista över tjänster, filtrera dem och sedan utföra omstarten:</span><span class="sxs-lookup"><span data-stu-id="50886-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
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

<span data-ttu-id="50886-135">Dessa tjänst-cmdletar har ingen ComputerName-parameter, men du kan köra dem på en fjärrdator med hjälp av cmdleten Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="50886-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="50886-136">Följande kommando startar till exempel om Spooler-tjänsten på fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="50886-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="50886-137">Ställer in tjänst egenskaper</span><span class="sxs-lookup"><span data-stu-id="50886-137">Setting Service Properties</span></span>

<span data-ttu-id="50886-138">`Set-Service` Cmdleten ändrar egenskaperna för en tjänst på en lokal eller fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="50886-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="50886-139">Eftersom tjänstens status är en egenskap kan du använda denna cmdlet för att starta, stoppa och pausa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="50886-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="50886-140">Cmdleten Set-service har också en Startuptype tjänst-parameter som låter dig ändra tjänstens starttyp.</span><span class="sxs-lookup"><span data-stu-id="50886-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="50886-141">Om du `Set-Service` vill använda i Windows Vista och senare versioner av Windows öppnar du Windows PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="50886-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="50886-142">Mer information finns i [set-service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span><span class="sxs-lookup"><span data-stu-id="50886-142">For more information, see [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span></span>

## <a name="see-also"></a><span data-ttu-id="50886-143">Se även</span><span class="sxs-lookup"><span data-stu-id="50886-143">See Also</span></span>

- [<span data-ttu-id="50886-144">Get-Service</span><span class="sxs-lookup"><span data-stu-id="50886-144">Get-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [<span data-ttu-id="50886-145">Set-Service</span><span class="sxs-lookup"><span data-stu-id="50886-145">Set-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [<span data-ttu-id="50886-146">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="50886-146">Restart-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [<span data-ttu-id="50886-147">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="50886-147">Suspend-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
