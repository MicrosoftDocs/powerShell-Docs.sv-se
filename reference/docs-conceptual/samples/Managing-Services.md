---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Hantera tjänster
description: PowerShell innehåller flera cmdletar som hjälper dig att hantera tjänster på lokala och fjärranslutna datorer.
ms.openlocfilehash: 003803cdaa37e51b3788f3f897cbec7d6e243ca8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500359"
---
# <a name="managing-services"></a><span data-ttu-id="445d0-104">Hantera tjänster</span><span class="sxs-lookup"><span data-stu-id="445d0-104">Managing Services</span></span>

<span data-ttu-id="445d0-105">Det finns åtta Core Service-cmdletar som är utformade för ett brett utbud av tjänst uppgifter.</span><span class="sxs-lookup"><span data-stu-id="445d0-105">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="445d0-106">Vi kommer bara att titta på att visa och ändra körnings tillstånd för tjänster, men du kan hämta en lista över tjänst-cmdletar med hjälp av `Get-Help \*-Service` , och du kan hitta information om varje tjänst-cmdlet med hjälp av `Get-Help <Cmdlet-Name>` , till exempel `Get-Help New-Service` .</span><span class="sxs-lookup"><span data-stu-id="445d0-106">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="445d0-107">Hämtar tjänster</span><span class="sxs-lookup"><span data-stu-id="445d0-107">Getting Services</span></span>

<span data-ttu-id="445d0-108">Du kan hämta tjänsterna på en lokal dator eller fjärrdator med hjälp av `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="445d0-108">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="445d0-109">Som med `Get-Process` kan du använda `Get-Service` kommandot utan parametrar för att returnera alla tjänster.</span><span class="sxs-lookup"><span data-stu-id="445d0-109">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="445d0-110">Du kan filtrera efter namn, även använda en asterisk som jokertecken:</span><span class="sxs-lookup"><span data-stu-id="445d0-110">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="445d0-111">Eftersom det inte alltid är uppenbart vad det riktiga namnet för tjänsten är, kan du hitta tjänster efter visnings namn.</span><span class="sxs-lookup"><span data-stu-id="445d0-111">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="445d0-112">Du kan göra detta med ett angivet namn, använda jokertecken eller med en lista med visnings namn:</span><span class="sxs-lookup"><span data-stu-id="445d0-112">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

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

<span data-ttu-id="445d0-113">Du kan använda parametern ComputerName i Get-Service-cmdlet: en för att hämta tjänsterna på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="445d0-113">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="445d0-114">Parametern ComputerName accepterar flera värden och jokertecken, så att du kan hämta tjänsterna på flera datorer med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="445d0-114">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="445d0-115">Följande kommando hämtar till exempel tjänsterna på den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="445d0-115">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="445d0-116">Hämtar nödvändiga och beroende tjänster</span><span class="sxs-lookup"><span data-stu-id="445d0-116">Getting Required and Dependent Services</span></span>

<span data-ttu-id="445d0-117">Get-Service-cmdlet har två parametrar som är mycket användbara i tjänst administration.</span><span class="sxs-lookup"><span data-stu-id="445d0-117">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="445d0-118">Parametern DependentServices hämtar tjänster som är beroende av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="445d0-118">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="445d0-119">Parametern RequiredServices hämtar tjänster som den här tjänsten är beroende av.</span><span class="sxs-lookup"><span data-stu-id="445d0-119">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="445d0-120">Dessa parametrar visar bara värdena för egenskaperna DependentServices och ServicesDependedOn (alias = RequiredServices) för objektet system. ServiceProcess. ServiceController som Get-Service returnerar, men de fören klar kommandona och gör att den här informationen blir mycket enklare.</span><span class="sxs-lookup"><span data-stu-id="445d0-120">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="445d0-121">Följande kommando hämtar de tjänster som LanmanWorkstation-tjänsten kräver.</span><span class="sxs-lookup"><span data-stu-id="445d0-121">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="445d0-122">Följande kommando hämtar de tjänster som kräver LanmanWorkstation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="445d0-122">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="445d0-123">Du kan till och med hämta alla tjänster som har beroenden.</span><span class="sxs-lookup"><span data-stu-id="445d0-123">You can even get all services that have dependencies.</span></span> <span data-ttu-id="445d0-124">Följande kommando gör bara det och använder sedan Format-Table-cmdlet för att visa egenskaperna status, Name, RequiredServices och DependentServices för tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="445d0-124">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="445d0-125">Stoppa, starta, pausa och starta om tjänster</span><span class="sxs-lookup"><span data-stu-id="445d0-125">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="445d0-126">Alla tjänst-cmdletar har samma generella form.</span><span class="sxs-lookup"><span data-stu-id="445d0-126">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="445d0-127">Tjänster kan anges med eget namn eller visnings namn och ta listor och jokertecken som värden.</span><span class="sxs-lookup"><span data-stu-id="445d0-127">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="445d0-128">Om du vill stoppa utskrifts hanteraren använder du:</span><span class="sxs-lookup"><span data-stu-id="445d0-128">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="445d0-129">Starta utskrifts hanteraren när den har stoppats genom att använda:</span><span class="sxs-lookup"><span data-stu-id="445d0-129">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="445d0-130">Om du vill pausa utskrifts hanteraren använder du:</span><span class="sxs-lookup"><span data-stu-id="445d0-130">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="445d0-131">`Restart-Service`Cmdleten fungerar på samma sätt som de andra tjänst-cmdletarna, men vi kommer att visa några mer komplexa exempel för den.</span><span class="sxs-lookup"><span data-stu-id="445d0-131">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="445d0-132">I den enklaste användningen anger du namnet på tjänsten:</span><span class="sxs-lookup"><span data-stu-id="445d0-132">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="445d0-133">Du ser att du får ett upprepande varnings meddelande om utskrifts hanteraren startar.</span><span class="sxs-lookup"><span data-stu-id="445d0-133">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="445d0-134">När du utför en tjänst åtgärd som tar en stund meddelar Windows PowerShell dig att den fortfarande försöker utföra uppgiften.</span><span class="sxs-lookup"><span data-stu-id="445d0-134">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="445d0-135">Om du vill starta om flera tjänster kan du hämta en lista över tjänster, filtrera dem och sedan utföra omstarten:</span><span class="sxs-lookup"><span data-stu-id="445d0-135">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

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

<span data-ttu-id="445d0-136">Dessa tjänst-cmdletar har ingen ComputerName-parameter, men du kan köra dem på en fjärrdator med hjälp av Invoke-Command-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="445d0-136">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="445d0-137">Följande kommando startar till exempel om Spooler-tjänsten på fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="445d0-137">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="445d0-138">Ställer in tjänst egenskaper</span><span class="sxs-lookup"><span data-stu-id="445d0-138">Setting Service Properties</span></span>

<span data-ttu-id="445d0-139">`Set-Service`Cmdleten ändrar egenskaperna för en tjänst på en lokal eller fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="445d0-139">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="445d0-140">Eftersom tjänstens status är en egenskap kan du använda denna cmdlet för att starta, stoppa och pausa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="445d0-140">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="445d0-141">Set-Service cmdlet har också en Startuptype tjänst-parameter som låter dig ändra tjänstens starttyp.</span><span class="sxs-lookup"><span data-stu-id="445d0-141">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="445d0-142">Om du vill använda `Set-Service` i Windows Vista och senare versioner av Windows öppnar du Windows PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="445d0-142">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="445d0-143">Mer information finns i [set-service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span><span class="sxs-lookup"><span data-stu-id="445d0-143">For more information, see [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span></span>

## <a name="see-also"></a><span data-ttu-id="445d0-144">Se även</span><span class="sxs-lookup"><span data-stu-id="445d0-144">See Also</span></span>

- [<span data-ttu-id="445d0-145">Get-Service</span><span class="sxs-lookup"><span data-stu-id="445d0-145">Get-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [<span data-ttu-id="445d0-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="445d0-146">Set-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [<span data-ttu-id="445d0-147">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="445d0-147">Restart-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [<span data-ttu-id="445d0-148">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="445d0-148">Suspend-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
