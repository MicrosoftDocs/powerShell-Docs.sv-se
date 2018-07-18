---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: b279d388754c5ee42215f21317f7b3d8089b7608
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093889"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="6fd1d-102">Enhetlig och konsekvent tillstånds- och statusrepresentation</span><span class="sxs-lookup"><span data-stu-id="6fd1d-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="6fd1d-103">Ett antal förbättringar har gjorts i den här versionen för arbetsflöden som bygger LCM-tillstånd och status för DSC.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="6fd1d-104">Dessa inkluderar enhetlig och konsekvent tillstånd och status visning hanterbara datetime-egenskap för statusobjekt som returneras av `Get-DscConfigurationStatus` tillstånd information-egenskapen som returneras av cmdlet och förbättrad LCM `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="6fd1d-105">En representation av LCM-tillstånd och status för DSC revisited och enhetlig enligt följande regler:</span><span class="sxs-lookup"><span data-stu-id="6fd1d-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="6fd1d-106">Notprocessed resource påverkar inte LCM-tillstånd och status för DSC.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
1. <span data-ttu-id="6fd1d-107">LCM stoppa ytterligare bearbetningsresurser när den stöter på en resurs som begär omstart.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
1. <span data-ttu-id="6fd1d-108">En resurs som begär omstart är inte i önskat läge tills omstart faktiskt händer.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
1. <span data-ttu-id="6fd1d-109">Efter en resurs som misslyckas, ser till att MGM bearbeta ytterligare resurser så länge de inte är beroende av ett fel.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
1. <span data-ttu-id="6fd1d-110">Den övergripande statusen som returneras av `Get-DscConfigurationStatus` cmdlet är den överordnade uppsättningen status för alla resurser.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
1. <span data-ttu-id="6fd1d-111">PendingReboot tillståndet är en supermängd PendingConfiguration tillstånd.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

   <span data-ttu-id="6fd1d-112">I tabellen nedan visas resulterande tillstånd och status relaterade egenskaper under några vanliga scenarier.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

   | <span data-ttu-id="6fd1d-113">Scenario</span><span class="sxs-lookup"><span data-stu-id="6fd1d-113">Scenario</span></span>                    | <span data-ttu-id="6fd1d-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="6fd1d-114">LCMState</span></span>       | <span data-ttu-id="6fd1d-115">Status</span><span class="sxs-lookup"><span data-stu-id="6fd1d-115">Status</span></span> | <span data-ttu-id="6fd1d-116">Omstart har begärts</span><span class="sxs-lookup"><span data-stu-id="6fd1d-116">Reboot Requested</span></span>  | <span data-ttu-id="6fd1d-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="6fd1d-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="6fd1d-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="6fd1d-118">ResourcesNotInDesiredState</span></span> |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | <span data-ttu-id="6fd1d-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="6fd1d-119">S**^**</span></span>                          | <span data-ttu-id="6fd1d-120">Inaktiv</span><span class="sxs-lookup"><span data-stu-id="6fd1d-120">Idle</span></span>                 | <span data-ttu-id="6fd1d-121">Klart</span><span class="sxs-lookup"><span data-stu-id="6fd1d-121">Success</span></span>    | <span data-ttu-id="6fd1d-122">$false</span><span class="sxs-lookup"><span data-stu-id="6fd1d-122">$false</span></span>        | <span data-ttu-id="6fd1d-123">S</span><span class="sxs-lookup"><span data-stu-id="6fd1d-123">S</span></span>                            | <span data-ttu-id="6fd1d-124">$null</span><span class="sxs-lookup"><span data-stu-id="6fd1d-124">$null</span></span>                          |
   | <span data-ttu-id="6fd1d-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="6fd1d-125">F**^**</span></span>                          | <span data-ttu-id="6fd1d-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fd1d-126">PendingConfiguration</span></span> | <span data-ttu-id="6fd1d-127">Fel</span><span class="sxs-lookup"><span data-stu-id="6fd1d-127">Failure</span></span>    | <span data-ttu-id="6fd1d-128">$false</span><span class="sxs-lookup"><span data-stu-id="6fd1d-128">$false</span></span>        | <span data-ttu-id="6fd1d-129">$null</span><span class="sxs-lookup"><span data-stu-id="6fd1d-129">$null</span></span>                        | <span data-ttu-id="6fd1d-130">F</span><span class="sxs-lookup"><span data-stu-id="6fd1d-130">F</span></span>                              |
   | <span data-ttu-id="6fd1d-131">S, F</span><span class="sxs-lookup"><span data-stu-id="6fd1d-131">S,F</span></span>                             | <span data-ttu-id="6fd1d-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fd1d-132">PendingConfiguration</span></span> | <span data-ttu-id="6fd1d-133">Fel</span><span class="sxs-lookup"><span data-stu-id="6fd1d-133">Failure</span></span>    | <span data-ttu-id="6fd1d-134">$false</span><span class="sxs-lookup"><span data-stu-id="6fd1d-134">$false</span></span>        | <span data-ttu-id="6fd1d-135">S</span><span class="sxs-lookup"><span data-stu-id="6fd1d-135">S</span></span>                            | <span data-ttu-id="6fd1d-136">F</span><span class="sxs-lookup"><span data-stu-id="6fd1d-136">F</span></span>                              |
   | <span data-ttu-id="6fd1d-137">F-S</span><span class="sxs-lookup"><span data-stu-id="6fd1d-137">F,S</span></span>                             | <span data-ttu-id="6fd1d-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fd1d-138">PendingConfiguration</span></span> | <span data-ttu-id="6fd1d-139">Fel</span><span class="sxs-lookup"><span data-stu-id="6fd1d-139">Failure</span></span>    | <span data-ttu-id="6fd1d-140">$false</span><span class="sxs-lookup"><span data-stu-id="6fd1d-140">$false</span></span>        | <span data-ttu-id="6fd1d-141">S</span><span class="sxs-lookup"><span data-stu-id="6fd1d-141">S</span></span>                            | <span data-ttu-id="6fd1d-142">F</span><span class="sxs-lookup"><span data-stu-id="6fd1d-142">F</span></span>                              |
   | <span data-ttu-id="6fd1d-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="6fd1d-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="6fd1d-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fd1d-144">PendingConfiguration</span></span> | <span data-ttu-id="6fd1d-145">Fel</span><span class="sxs-lookup"><span data-stu-id="6fd1d-145">Failure</span></span>    | <span data-ttu-id="6fd1d-146">$false</span><span class="sxs-lookup"><span data-stu-id="6fd1d-146">$false</span></span>        | <span data-ttu-id="6fd1d-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="6fd1d-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="6fd1d-148">F</span><span class="sxs-lookup"><span data-stu-id="6fd1d-148">F</span></span>                              |
   | <span data-ttu-id="6fd1d-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="6fd1d-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="6fd1d-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fd1d-150">PendingConfiguration</span></span> | <span data-ttu-id="6fd1d-151">Fel</span><span class="sxs-lookup"><span data-stu-id="6fd1d-151">Failure</span></span>    | <span data-ttu-id="6fd1d-152">$false</span><span class="sxs-lookup"><span data-stu-id="6fd1d-152">$false</span></span>        | <span data-ttu-id="6fd1d-153">S</span><span class="sxs-lookup"><span data-stu-id="6fd1d-153">S</span></span>                            | <span data-ttu-id="6fd1d-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="6fd1d-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
   | <span data-ttu-id="6fd1d-155">S, r</span><span class="sxs-lookup"><span data-stu-id="6fd1d-155">S, r</span></span>                            | <span data-ttu-id="6fd1d-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="6fd1d-156">PendingReboot</span></span>        | <span data-ttu-id="6fd1d-157">Klart</span><span class="sxs-lookup"><span data-stu-id="6fd1d-157">Success</span></span>    | <span data-ttu-id="6fd1d-158">$true</span><span class="sxs-lookup"><span data-stu-id="6fd1d-158">$true</span></span>         | <span data-ttu-id="6fd1d-159">S</span><span class="sxs-lookup"><span data-stu-id="6fd1d-159">S</span></span>                            | <span data-ttu-id="6fd1d-160">r</span><span class="sxs-lookup"><span data-stu-id="6fd1d-160">r</span></span>                              |
   | <span data-ttu-id="6fd1d-161">F-, r</span><span class="sxs-lookup"><span data-stu-id="6fd1d-161">F, r</span></span>                            | <span data-ttu-id="6fd1d-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="6fd1d-162">PendingReboot</span></span>        | <span data-ttu-id="6fd1d-163">Fel</span><span class="sxs-lookup"><span data-stu-id="6fd1d-163">Failure</span></span>    | <span data-ttu-id="6fd1d-164">$true</span><span class="sxs-lookup"><span data-stu-id="6fd1d-164">$true</span></span>         | <span data-ttu-id="6fd1d-165">$null</span><span class="sxs-lookup"><span data-stu-id="6fd1d-165">$null</span></span>                        | <span data-ttu-id="6fd1d-166">F-, r</span><span class="sxs-lookup"><span data-stu-id="6fd1d-166">F, r</span></span>                           |
   | <span data-ttu-id="6fd1d-167">r, S</span><span class="sxs-lookup"><span data-stu-id="6fd1d-167">r, S</span></span>                            | <span data-ttu-id="6fd1d-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="6fd1d-168">PendingReboot</span></span>        | <span data-ttu-id="6fd1d-169">Klart</span><span class="sxs-lookup"><span data-stu-id="6fd1d-169">Success</span></span>    | <span data-ttu-id="6fd1d-170">$true</span><span class="sxs-lookup"><span data-stu-id="6fd1d-170">$true</span></span>         | <span data-ttu-id="6fd1d-171">$null</span><span class="sxs-lookup"><span data-stu-id="6fd1d-171">$null</span></span>                        | <span data-ttu-id="6fd1d-172">r</span><span class="sxs-lookup"><span data-stu-id="6fd1d-172">r</span></span>                              |
   | <span data-ttu-id="6fd1d-173">r, F</span><span class="sxs-lookup"><span data-stu-id="6fd1d-173">r, F</span></span>                            | <span data-ttu-id="6fd1d-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="6fd1d-174">PendingReboot</span></span>        | <span data-ttu-id="6fd1d-175">Klart</span><span class="sxs-lookup"><span data-stu-id="6fd1d-175">Success</span></span>    | <span data-ttu-id="6fd1d-176">$true</span><span class="sxs-lookup"><span data-stu-id="6fd1d-176">$true</span></span>         | <span data-ttu-id="6fd1d-177">$null</span><span class="sxs-lookup"><span data-stu-id="6fd1d-177">$null</span></span>                        | <span data-ttu-id="6fd1d-178">r</span><span class="sxs-lookup"><span data-stu-id="6fd1d-178">r</span></span>                              |

   <span data-ttu-id="6fd1d-179">^
   S<sub>jag</sub>: ett antal resurser som har tillämpats F<sub>jag</sub>: ett antal resurser som har inte tillämpats r: en resurs som kräver omstart \*</span><span class="sxs-lookup"><span data-stu-id="6fd1d-179">^
   S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="6fd1d-180">Förbättring i Get-DscConfigurationStatus cmdlet</span><span class="sxs-lookup"><span data-stu-id="6fd1d-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="6fd1d-181">Några förbättringar har gjorts `Get-DscConfigurationStatus` cmdlet i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-181">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="6fd1d-182">Tidigare är StartDate-egenskapen för objekt som returneras av cmdlet: en av typen sträng.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="6fd1d-183">Nu är av typen Datetime, vilket gör att komplexa att välja och filtrera utifrån enklare inbäddade egenskaperna för ett Datetime-objekt.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *
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

<span data-ttu-id="6fd1d-184">Följande är ett exempel som returnerar alla poster för DSC-åtgärden som inträffat på samma dag i veckan som idag.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="6fd1d-185">Poster med åtgärder som inte du göra ändringar i nodens konfiguration (d.v.s. läsåtgärder endast) elimineras.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="6fd1d-186">Därför `Test-DscConfiguration`, `Get-DscConfiguration` åtgärder är inte längre uppblandat i returnerade objekt från `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-186">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span>
<span data-ttu-id="6fd1d-187">Poster i meta configuration frö läggs till i avkastningen på `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-187">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="6fd1d-188">Följande är ett exempel på resultatet som returneras från `Get-DscConfigurationStatus` – alla cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-188">Following is an example of result returned from `Get-DscConfigurationStatus` –All cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="6fd1d-189">Förbättring i cmdleten Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6fd1d-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="6fd1d-190">Ett nytt fält av LCMStateDetail har lagts till i objektet som returnerades från `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-190">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="6fd1d-191">Det här fältet fylls när LCMState är ”upptagen”.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="6fd1d-192">Den kan hämtas med följande cmdlet:</span><span class="sxs-lookup"><span data-stu-id="6fd1d-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="6fd1d-193">Följande är ett exempel på utdata för en kontinuerlig övervakning av en konfiguration som kräver två omstarter på en fjärransluten nod.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
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