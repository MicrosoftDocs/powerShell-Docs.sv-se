---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058989"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="04913-102">Enhetlig och konsekvent tillstånds- och statusrepresentation</span><span class="sxs-lookup"><span data-stu-id="04913-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="04913-103">Ett antal förbättringar har gjorts i den här versionen för arbetsflöden som bygger LCM-tillstånd och status för DSC.</span><span class="sxs-lookup"><span data-stu-id="04913-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="04913-104">Dessa inkluderar enhetlig och konsekvent tillstånd och status visning hanterbara datetime-egenskap för statusobjekt som returneras av `Get-DscConfigurationStatus` tillstånd information-egenskapen som returneras av cmdlet och förbättrad LCM `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04913-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="04913-105">En representation av LCM-tillstånd och status för DSC revisited och enhetlig enligt följande regler:</span><span class="sxs-lookup"><span data-stu-id="04913-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="04913-106">Notprocessed resource påverkar inte LCM-tillstånd och status för DSC.</span><span class="sxs-lookup"><span data-stu-id="04913-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="04913-107">LCM stoppa ytterligare bearbetningsresurser när den stöter på en resurs som begär omstart.</span><span class="sxs-lookup"><span data-stu-id="04913-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="04913-108">En resurs som begär omstart är inte i önskat läge tills omstart faktiskt händer.</span><span class="sxs-lookup"><span data-stu-id="04913-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="04913-109">Efter en resurs som misslyckas, ser till att MGM bearbeta ytterligare resurser så länge de inte är beroende av ett fel.</span><span class="sxs-lookup"><span data-stu-id="04913-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="04913-110">Den övergripande statusen som returneras av `Get-DscConfigurationStatus` cmdlet är den överordnade uppsättningen status för alla resurser.</span><span class="sxs-lookup"><span data-stu-id="04913-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="04913-111">PendingReboot tillståndet är en supermängd PendingConfiguration tillstånd.</span><span class="sxs-lookup"><span data-stu-id="04913-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="04913-112">I tabellen nedan visas resulterande tillstånd och status relaterade egenskaper under några vanliga scenarier.</span><span class="sxs-lookup"><span data-stu-id="04913-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="04913-113">Scenario</span><span class="sxs-lookup"><span data-stu-id="04913-113">Scenario</span></span>                        | <span data-ttu-id="04913-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="04913-114">LCMState</span></span>             | <span data-ttu-id="04913-115">Status</span><span class="sxs-lookup"><span data-stu-id="04913-115">Status</span></span>     | <span data-ttu-id="04913-116">Omstart har begärts</span><span class="sxs-lookup"><span data-stu-id="04913-116">Reboot Requested</span></span> | <span data-ttu-id="04913-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="04913-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="04913-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="04913-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="04913-119">S<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="04913-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="04913-120">Inaktiv</span><span class="sxs-lookup"><span data-stu-id="04913-120">Idle</span></span>                 | <span data-ttu-id="04913-121">Klart</span><span class="sxs-lookup"><span data-stu-id="04913-121">Success</span></span>    | <span data-ttu-id="04913-122">$false</span><span class="sxs-lookup"><span data-stu-id="04913-122">$false</span></span>        | <span data-ttu-id="04913-123">S</span><span class="sxs-lookup"><span data-stu-id="04913-123">S</span></span>                            | <span data-ttu-id="04913-124">$null</span><span class="sxs-lookup"><span data-stu-id="04913-124">$null</span></span>                          |
| <span data-ttu-id="04913-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="04913-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="04913-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="04913-126">PendingConfiguration</span></span> | <span data-ttu-id="04913-127">Fel</span><span class="sxs-lookup"><span data-stu-id="04913-127">Failure</span></span>    | <span data-ttu-id="04913-128">$false</span><span class="sxs-lookup"><span data-stu-id="04913-128">$false</span></span>        | <span data-ttu-id="04913-129">$null</span><span class="sxs-lookup"><span data-stu-id="04913-129">$null</span></span>                        | <span data-ttu-id="04913-130">F</span><span class="sxs-lookup"><span data-stu-id="04913-130">F</span></span>                              |
| <span data-ttu-id="04913-131">S,F</span><span class="sxs-lookup"><span data-stu-id="04913-131">S,F</span></span>                             | <span data-ttu-id="04913-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="04913-132">PendingConfiguration</span></span> | <span data-ttu-id="04913-133">Fel</span><span class="sxs-lookup"><span data-stu-id="04913-133">Failure</span></span>    | <span data-ttu-id="04913-134">$false</span><span class="sxs-lookup"><span data-stu-id="04913-134">$false</span></span>        | <span data-ttu-id="04913-135">S</span><span class="sxs-lookup"><span data-stu-id="04913-135">S</span></span>                            | <span data-ttu-id="04913-136">F</span><span class="sxs-lookup"><span data-stu-id="04913-136">F</span></span>                              |
| <span data-ttu-id="04913-137">F,S</span><span class="sxs-lookup"><span data-stu-id="04913-137">F,S</span></span>                             | <span data-ttu-id="04913-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="04913-138">PendingConfiguration</span></span> | <span data-ttu-id="04913-139">Fel</span><span class="sxs-lookup"><span data-stu-id="04913-139">Failure</span></span>    | <span data-ttu-id="04913-140">$false</span><span class="sxs-lookup"><span data-stu-id="04913-140">$false</span></span>        | <span data-ttu-id="04913-141">S</span><span class="sxs-lookup"><span data-stu-id="04913-141">S</span></span>                            | <span data-ttu-id="04913-142">F</span><span class="sxs-lookup"><span data-stu-id="04913-142">F</span></span>                              |
| <span data-ttu-id="04913-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="04913-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="04913-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="04913-144">PendingConfiguration</span></span> | <span data-ttu-id="04913-145">Fel</span><span class="sxs-lookup"><span data-stu-id="04913-145">Failure</span></span>    | <span data-ttu-id="04913-146">$false</span><span class="sxs-lookup"><span data-stu-id="04913-146">$false</span></span>        | <span data-ttu-id="04913-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="04913-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="04913-148">F</span><span class="sxs-lookup"><span data-stu-id="04913-148">F</span></span>                              |
| <span data-ttu-id="04913-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="04913-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="04913-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="04913-150">PendingConfiguration</span></span> | <span data-ttu-id="04913-151">Fel</span><span class="sxs-lookup"><span data-stu-id="04913-151">Failure</span></span>    | <span data-ttu-id="04913-152">$false</span><span class="sxs-lookup"><span data-stu-id="04913-152">$false</span></span>        | <span data-ttu-id="04913-153">S</span><span class="sxs-lookup"><span data-stu-id="04913-153">S</span></span>                            | <span data-ttu-id="04913-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="04913-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="04913-155">S, r</span><span class="sxs-lookup"><span data-stu-id="04913-155">S, r</span></span>                            | <span data-ttu-id="04913-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="04913-156">PendingReboot</span></span>        | <span data-ttu-id="04913-157">Klart</span><span class="sxs-lookup"><span data-stu-id="04913-157">Success</span></span>    | <span data-ttu-id="04913-158">$true</span><span class="sxs-lookup"><span data-stu-id="04913-158">$true</span></span>         | <span data-ttu-id="04913-159">S</span><span class="sxs-lookup"><span data-stu-id="04913-159">S</span></span>                            | <span data-ttu-id="04913-160">R</span><span class="sxs-lookup"><span data-stu-id="04913-160">r</span></span>                              |
| <span data-ttu-id="04913-161">F, r</span><span class="sxs-lookup"><span data-stu-id="04913-161">F, r</span></span>                            | <span data-ttu-id="04913-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="04913-162">PendingReboot</span></span>        | <span data-ttu-id="04913-163">Fel</span><span class="sxs-lookup"><span data-stu-id="04913-163">Failure</span></span>    | <span data-ttu-id="04913-164">$true</span><span class="sxs-lookup"><span data-stu-id="04913-164">$true</span></span>         | <span data-ttu-id="04913-165">$null</span><span class="sxs-lookup"><span data-stu-id="04913-165">$null</span></span>                        | <span data-ttu-id="04913-166">F, r</span><span class="sxs-lookup"><span data-stu-id="04913-166">F, r</span></span>                           |
| <span data-ttu-id="04913-167">r, S</span><span class="sxs-lookup"><span data-stu-id="04913-167">r, S</span></span>                            | <span data-ttu-id="04913-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="04913-168">PendingReboot</span></span>        | <span data-ttu-id="04913-169">Klart</span><span class="sxs-lookup"><span data-stu-id="04913-169">Success</span></span>    | <span data-ttu-id="04913-170">$true</span><span class="sxs-lookup"><span data-stu-id="04913-170">$true</span></span>         | <span data-ttu-id="04913-171">$null</span><span class="sxs-lookup"><span data-stu-id="04913-171">$null</span></span>                        | <span data-ttu-id="04913-172">R</span><span class="sxs-lookup"><span data-stu-id="04913-172">r</span></span>                              |
| <span data-ttu-id="04913-173">r, F</span><span class="sxs-lookup"><span data-stu-id="04913-173">r, F</span></span>                            | <span data-ttu-id="04913-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="04913-174">PendingReboot</span></span>        | <span data-ttu-id="04913-175">Klart</span><span class="sxs-lookup"><span data-stu-id="04913-175">Success</span></span>    | <span data-ttu-id="04913-176">$true</span><span class="sxs-lookup"><span data-stu-id="04913-176">$true</span></span>         | <span data-ttu-id="04913-177">$null</span><span class="sxs-lookup"><span data-stu-id="04913-177">$null</span></span>                        | <span data-ttu-id="04913-178">R</span><span class="sxs-lookup"><span data-stu-id="04913-178">r</span></span>                              |

- <span data-ttu-id="04913-179">S<sub>i</sub>: Ett antal resurser som har tillämpats</span><span class="sxs-lookup"><span data-stu-id="04913-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="04913-180">F<sub>i</sub>: Ett antal resurser som används med fel</span><span class="sxs-lookup"><span data-stu-id="04913-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="04913-181">r: En resurs som kräver omstart</span><span class="sxs-lookup"><span data-stu-id="04913-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="04913-182">Förbättring i Get-DscConfigurationStatus cmdlet</span><span class="sxs-lookup"><span data-stu-id="04913-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="04913-183">Några förbättringar har gjorts `Get-DscConfigurationStatus` cmdlet i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="04913-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="04913-184">Tidigare är StartDate-egenskapen för objekt som returneras av cmdlet: en av typen sträng.</span><span class="sxs-lookup"><span data-stu-id="04913-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="04913-185">Nu är av typen Datetime, vilket gör att komplexa att välja och filtrera utifrån enklare inbäddade egenskaperna för ett Datetime-objekt.</span><span class="sxs-lookup"><span data-stu-id="04913-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="04913-186">I följande exempel returneras alla DSC-åtgärdsposter som inträffat på samma dag i veckan som den aktuella dagen.</span><span class="sxs-lookup"><span data-stu-id="04913-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="04913-187">Poster med åtgärder som inte du göra ändringar i nodens konfiguration (d.v.s. läsåtgärder endast) elimineras.</span><span class="sxs-lookup"><span data-stu-id="04913-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="04913-188">Därför `Test-DscConfiguration`, `Get-DscConfiguration` åtgärder är inte längre uppblandat i returnerade objekt från `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04913-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="04913-189">Poster i meta configuration frö läggs till i avkastningen på `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04913-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="04913-190">Följande är ett exempel på resultatet som returneras från `Get-DscConfigurationStatus –All` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04913-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="04913-191">Förbättring i cmdleten Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="04913-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="04913-192">Ett nytt fält av LCMStateDetail har lagts till i objektet som returnerades från `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04913-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="04913-193">Det här fältet fylls när LCMState är ”upptagen”.</span><span class="sxs-lookup"><span data-stu-id="04913-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="04913-194">Den kan hämtas med följande cmdlet:</span><span class="sxs-lookup"><span data-stu-id="04913-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="04913-195">Följande är ett exempel på utdata för en kontinuerlig övervakning av en konfiguration som kräver två omstarter på en fjärransluten nod.</span><span class="sxs-lookup"><span data-stu-id="04913-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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
