---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 32f8e20889ddc526def4b925e8d0761a2e851e19
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="cf929-102">Enhetlig och konsekvent tillstånd och Status Representation</span><span class="sxs-lookup"><span data-stu-id="cf929-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="cf929-103">Ett antal förbättringar har gjorts i den här versionen för automatiseringar inbyggda MGM tillstånd och DSC-status.</span><span class="sxs-lookup"><span data-stu-id="cf929-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="cf929-104">Dessa inkluderar enhetlig och konsekvent tillstånd och status garantier, hanterbara datetime-egenskap för status-objekt som returneras av Get-DscConfigurationStatus cmdlet och förbättrad MGM tillstånd information egenskap returnerades av Get-DscLocalConfigurationManager cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cf929-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by Get-DscConfigurationStatus cmdlet and enhanced LCM state details property returned by Get-DscLocalConfigurationManager cmdlet.</span></span>

<span data-ttu-id="cf929-105">Representation av MGM tillstånd och DSC Åtgärdsstatus revisited och enhetlig enligt följande regler:</span><span class="sxs-lookup"><span data-stu-id="cf929-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>
1.  <span data-ttu-id="cf929-106">Notprocessed resurs påverkar inte MGM tillstånd och DSC-status.</span><span class="sxs-lookup"><span data-stu-id="cf929-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2.  <span data-ttu-id="cf929-107">MGM stoppa ytterligare bearbetningsresurser när den stöter på en resurs som kräver omstart.</span><span class="sxs-lookup"><span data-stu-id="cf929-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3.  <span data-ttu-id="cf929-108">En resurs som begär omstart är inte status som önskas förrän omstart i själva verket inträffar.</span><span class="sxs-lookup"><span data-stu-id="cf929-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4.  <span data-ttu-id="cf929-109">Efter en resurs som misslyckas, håller MGM bearbetningsresurser ytterligare så länge de inte är beroende av ett fel.</span><span class="sxs-lookup"><span data-stu-id="cf929-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5.  <span data-ttu-id="cf929-110">Den allmänna statusen som returneras av Get-DscConfigurationStatus cmdlet är den överordnade uppsättningen status för alla resurser.</span><span class="sxs-lookup"><span data-stu-id="cf929-110">The overall status returned by Get-DscConfigurationStatus cmdlet is the super set of all resources’ status.</span></span>
6.  <span data-ttu-id="cf929-111">PendingReboot tillstånd är en supermängd PendingConfiguration tillstånd.</span><span class="sxs-lookup"><span data-stu-id="cf929-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="cf929-112">I tabellen nedan visas resulterande tillstånd och status relaterade egenskaper under några vanliga scenarier.</span><span class="sxs-lookup"><span data-stu-id="cf929-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="cf929-113">**Scenario**</span><span class="sxs-lookup"><span data-stu-id="cf929-113">**Scenario**</span></span>                    | <span data-ttu-id="cf929-114">**LCMState\***</span><span class="sxs-lookup"><span data-stu-id="cf929-114">**LCMState\***</span></span>       | <span data-ttu-id="cf929-115">**Status**</span><span class="sxs-lookup"><span data-stu-id="cf929-115">**Status**</span></span> | <span data-ttu-id="cf929-116">**Omstart begärdes**</span><span class="sxs-lookup"><span data-stu-id="cf929-116">**Reboot Requested**</span></span>  | <span data-ttu-id="cf929-117">**ResourcesInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="cf929-117">**ResourcesInDesiredState**</span></span>  | <span data-ttu-id="cf929-118">**ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="cf929-118">**ResourcesNotInDesiredState**</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="cf929-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="cf929-119">S**^**</span></span>                          | <span data-ttu-id="cf929-120">Inaktiv</span><span class="sxs-lookup"><span data-stu-id="cf929-120">Idle</span></span>                 | <span data-ttu-id="cf929-121">Klart</span><span class="sxs-lookup"><span data-stu-id="cf929-121">Success</span></span>    | <span data-ttu-id="cf929-122">$false</span><span class="sxs-lookup"><span data-stu-id="cf929-122">$false</span></span>        | <span data-ttu-id="cf929-123">S</span><span class="sxs-lookup"><span data-stu-id="cf929-123">S</span></span>                            | <span data-ttu-id="cf929-124">$null</span><span class="sxs-lookup"><span data-stu-id="cf929-124">$null</span></span>                          |
| <span data-ttu-id="cf929-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="cf929-125">F**^**</span></span>                          | <span data-ttu-id="cf929-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf929-126">PendingConfiguration</span></span> | <span data-ttu-id="cf929-127">Fel</span><span class="sxs-lookup"><span data-stu-id="cf929-127">Failure</span></span>    | <span data-ttu-id="cf929-128">$false</span><span class="sxs-lookup"><span data-stu-id="cf929-128">$false</span></span>        | <span data-ttu-id="cf929-129">$null</span><span class="sxs-lookup"><span data-stu-id="cf929-129">$null</span></span>                        | <span data-ttu-id="cf929-130">F</span><span class="sxs-lookup"><span data-stu-id="cf929-130">F</span></span>                              |
| <span data-ttu-id="cf929-131">S, F</span><span class="sxs-lookup"><span data-stu-id="cf929-131">S,F</span></span>                             | <span data-ttu-id="cf929-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf929-132">PendingConfiguration</span></span> | <span data-ttu-id="cf929-133">Fel</span><span class="sxs-lookup"><span data-stu-id="cf929-133">Failure</span></span>    | <span data-ttu-id="cf929-134">$false</span><span class="sxs-lookup"><span data-stu-id="cf929-134">$false</span></span>        | <span data-ttu-id="cf929-135">S</span><span class="sxs-lookup"><span data-stu-id="cf929-135">S</span></span>                            | <span data-ttu-id="cf929-136">F</span><span class="sxs-lookup"><span data-stu-id="cf929-136">F</span></span>                              |
| <span data-ttu-id="cf929-137">F, S</span><span class="sxs-lookup"><span data-stu-id="cf929-137">F,S</span></span>                             | <span data-ttu-id="cf929-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf929-138">PendingConfiguration</span></span> | <span data-ttu-id="cf929-139">Fel</span><span class="sxs-lookup"><span data-stu-id="cf929-139">Failure</span></span>    | <span data-ttu-id="cf929-140">$false</span><span class="sxs-lookup"><span data-stu-id="cf929-140">$false</span></span>        | <span data-ttu-id="cf929-141">S</span><span class="sxs-lookup"><span data-stu-id="cf929-141">S</span></span>                            | <span data-ttu-id="cf929-142">F</span><span class="sxs-lookup"><span data-stu-id="cf929-142">F</span></span>                              |
| <span data-ttu-id="cf929-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="cf929-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="cf929-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf929-144">PendingConfiguration</span></span> | <span data-ttu-id="cf929-145">Fel</span><span class="sxs-lookup"><span data-stu-id="cf929-145">Failure</span></span>    | <span data-ttu-id="cf929-146">$false</span><span class="sxs-lookup"><span data-stu-id="cf929-146">$false</span></span>        | <span data-ttu-id="cf929-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="cf929-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="cf929-148">F</span><span class="sxs-lookup"><span data-stu-id="cf929-148">F</span></span>                              |
| <span data-ttu-id="cf929-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="cf929-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="cf929-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf929-150">PendingConfiguration</span></span> | <span data-ttu-id="cf929-151">Fel</span><span class="sxs-lookup"><span data-stu-id="cf929-151">Failure</span></span>    | <span data-ttu-id="cf929-152">$false</span><span class="sxs-lookup"><span data-stu-id="cf929-152">$false</span></span>        | <span data-ttu-id="cf929-153">S</span><span class="sxs-lookup"><span data-stu-id="cf929-153">S</span></span>                            | <span data-ttu-id="cf929-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="cf929-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="cf929-155">S, r</span><span class="sxs-lookup"><span data-stu-id="cf929-155">S, r</span></span>                            | <span data-ttu-id="cf929-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="cf929-156">PendingReboot</span></span>        | <span data-ttu-id="cf929-157">Klart</span><span class="sxs-lookup"><span data-stu-id="cf929-157">Success</span></span>    | <span data-ttu-id="cf929-158">$true</span><span class="sxs-lookup"><span data-stu-id="cf929-158">$true</span></span>         | <span data-ttu-id="cf929-159">S</span><span class="sxs-lookup"><span data-stu-id="cf929-159">S</span></span>                            | <span data-ttu-id="cf929-160">R</span><span class="sxs-lookup"><span data-stu-id="cf929-160">r</span></span>                              |
| <span data-ttu-id="cf929-161">F, r</span><span class="sxs-lookup"><span data-stu-id="cf929-161">F, r</span></span>                            | <span data-ttu-id="cf929-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="cf929-162">PendingReboot</span></span>        | <span data-ttu-id="cf929-163">Fel</span><span class="sxs-lookup"><span data-stu-id="cf929-163">Failure</span></span>    | <span data-ttu-id="cf929-164">$true</span><span class="sxs-lookup"><span data-stu-id="cf929-164">$true</span></span>         | <span data-ttu-id="cf929-165">$null</span><span class="sxs-lookup"><span data-stu-id="cf929-165">$null</span></span>                        | <span data-ttu-id="cf929-166">F, r</span><span class="sxs-lookup"><span data-stu-id="cf929-166">F, r</span></span>                           |
| <span data-ttu-id="cf929-167">r, S</span><span class="sxs-lookup"><span data-stu-id="cf929-167">r, S</span></span>                            | <span data-ttu-id="cf929-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="cf929-168">PendingReboot</span></span>        | <span data-ttu-id="cf929-169">Klart</span><span class="sxs-lookup"><span data-stu-id="cf929-169">Success</span></span>    | <span data-ttu-id="cf929-170">$true</span><span class="sxs-lookup"><span data-stu-id="cf929-170">$true</span></span>         | <span data-ttu-id="cf929-171">$null</span><span class="sxs-lookup"><span data-stu-id="cf929-171">$null</span></span>                        | <span data-ttu-id="cf929-172">R</span><span class="sxs-lookup"><span data-stu-id="cf929-172">r</span></span>                              |
| <span data-ttu-id="cf929-173">r, F</span><span class="sxs-lookup"><span data-stu-id="cf929-173">r, F</span></span>                            | <span data-ttu-id="cf929-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="cf929-174">PendingReboot</span></span>        | <span data-ttu-id="cf929-175">Klart</span><span class="sxs-lookup"><span data-stu-id="cf929-175">Success</span></span>    | <span data-ttu-id="cf929-176">$true</span><span class="sxs-lookup"><span data-stu-id="cf929-176">$true</span></span>         | <span data-ttu-id="cf929-177">$null</span><span class="sxs-lookup"><span data-stu-id="cf929-177">$null</span></span>                        | <span data-ttu-id="cf929-178">R</span><span class="sxs-lookup"><span data-stu-id="cf929-178">r</span></span>                              |

<span data-ttu-id="cf929-179">^ S<sub>jag</sub>: ett antal resurser som har tillämpats F<sub>jag</sub>: ett antal resurser som tillämpats fel r: en resurs som kräver omstart\*</span><span class="sxs-lookup"><span data-stu-id="cf929-179">^ S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="cf929-180">Förbättring i Get-DscConfigurationStatus cmdlet</span><span class="sxs-lookup"><span data-stu-id="cf929-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="cf929-181">Några förbättringar har gjorts till Get-DscConfigurationStatus cmdlet i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="cf929-181">A few enhancements have been made to Get-DscConfigurationStatus cmdlet in this release.</span></span> <span data-ttu-id="cf929-182">Tidigare är egenskapen StartDate för objekt som returnerats av cmdleten av typen String.</span><span class="sxs-lookup"><span data-stu-id="cf929-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="cf929-183">Nu är av typen Datetime, vilket gör att komplicerade att välja och filtrering lättare baserat på inbyggda egenskaper för ett Datetime-objekt.</span><span class="sxs-lookup"><span data-stu-id="cf929-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="cf929-184">Följande är ett exempel som returnerar alla poster för DSC-åtgärden som inträffat på samma dag i veckan som idag.</span><span class="sxs-lookup"><span data-stu-id="cf929-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="cf929-185">Posterna för åtgärder som inte du göra ändringar i nodens konfiguration (d.v.s. läsåtgärder endast) elimineras.</span><span class="sxs-lookup"><span data-stu-id="cf929-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="cf929-186">Därför Test-DscConfiguration Get-DscConfiguration åtgärder är inte längre uppblandat i returnerade objekt från Get-DscConfigurationStatus cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cf929-186">Therefore, Test-DscConfiguration, Get-DscConfiguration operations are no longer adulterated in returned objects from Get-DscConfigurationStatus cmdlet.</span></span>
<span data-ttu-id="cf929-187">Poster med meta configuration inställningen åtgärden läggs till av Get-DscConfigurationStatus cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cf929-187">Records of meta configuration setting operation is added to the return of Get-DscConfigurationStatus cmdlet.</span></span>

<span data-ttu-id="cf929-188">Följande är ett exempel på resultat som returneras från Get-DscConfigurationStatus – alla cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cf929-188">Following is an example of result returned from Get-DscConfigurationStatus –All cmdlet.</span></span>
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="cf929-189">Förbättring i Get-DscLocalConfigurationManager cmdlet</span><span class="sxs-lookup"><span data-stu-id="cf929-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>
<span data-ttu-id="cf929-190">Ett nytt fält av LCMStateDetail har lagts till i objektet som returnerades från Get-DscLocalConfigurationManager cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cf929-190">A new field of LCMStateDetail is added to the object returned from Get-DscLocalConfigurationManager cmdlet.</span></span> <span data-ttu-id="cf929-191">Det här fältet fylls när LCMState är ”upptagen”.</span><span class="sxs-lookup"><span data-stu-id="cf929-191">This field is populated when LCMState is “Busy”.</span></span> <span data-ttu-id="cf929-192">De kan hämtas av följande cmdlet:</span><span class="sxs-lookup"><span data-stu-id="cf929-192">It can be retrieved by following cmdlet:</span></span>
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="cf929-193">Följande är ett exempel på utdata för en kontinuerlig övervakning av en konfiguration som kräver två omstarter på en fjärr-nod.</span><span class="sxs-lookup"><span data-stu-id="cf929-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>
```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```

