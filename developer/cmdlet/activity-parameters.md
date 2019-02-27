---
title: Parametrarna för aktiviteten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 32e2b8acf33bc733c5e4cab94a721076ff46225d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849093"
---
# <a name="activity-parameters"></a><span data-ttu-id="e5d5d-102">Aktivitetsparametrar</span><span class="sxs-lookup"><span data-stu-id="e5d5d-102">Activity Parameters</span></span>

<span data-ttu-id="e5d5d-103">I följande tabell visas de rekommenderade namn och de funktioner för parametrarna för aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-103">The following table lists the recommended names and functionality for activity parameters.</span></span>

<span data-ttu-id="e5d5d-104">Lägg till datatypen: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-104">Append Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-105">Implementera den här parametern så att användaren kan lägga till innehåll i slutet av en resurs när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-105">Implement this parameter so that the user can add content to the end of a resource when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-106">CaseSensitive datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-106">CaseSensitive Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-107">Implementera den här parametern så att användaren kan kräva skiftlägeskänslighet när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-107">Implement this parameter so the user can require case sensitivity when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-108">Kommandot datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="e5d5d-108">Command Data type: String</span></span>

<span data-ttu-id="e5d5d-109">Implementera den här parametern så att användaren kan ange en kommandosträng ska köras.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-109">Implement this parameter so the user can specify a command string to run.</span></span>

<span data-ttu-id="e5d5d-110">CompatibleVersion datatyp: System.Version object</span><span class="sxs-lookup"><span data-stu-id="e5d5d-110">CompatibleVersion Data type: System.Version object</span></span>

<span data-ttu-id="e5d5d-111">Implementera den här parametern så att användaren kan ange semantik som cmdlet: en måste vara kompatibel med för kompatibilitet med tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-111">Implement this parameter so the user can specify the semantics that the cmdlet must be compatible with for compatibility with previous versions.</span></span>

<span data-ttu-id="e5d5d-112">Komprimera datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-112">Compress Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-113">Implementera den här parametern så att datakomprimering används när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-113">Implement this parameter so that data compression is used when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-114">Komprimera datatyp: Nyckelord</span><span class="sxs-lookup"><span data-stu-id="e5d5d-114">Compress Data type: Keyword</span></span>

<span data-ttu-id="e5d5d-115">Implementera den här parametern så att användaren kan ange algoritmen som ska användas för komprimering.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-115">Implement this parameter so that the user can specify the algorithm to use for data compression.</span></span>

<span data-ttu-id="e5d5d-116">Kontinuerlig datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-116">Continuous Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-117">Implementera den här parametern så att data har bearbetats tills användaren avslutar cmdleten när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-117">Implement this parameter so that data is processed until the user terminates the cmdlet when the parameter is specified.</span></span> <span data-ttu-id="e5d5d-118">Om parametern inte anges, cmdleten bearbetar en fördefinierad mängd data och avbryter åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-118">If the parameter is not specified, the cmdlet processes a predefined amount of data and then terminates the operation.</span></span>

<span data-ttu-id="e5d5d-119">Skapa datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-119">Create Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-120">Implementera den här parametern om du vill ange att en resurs skapas om det inte redan finns när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-120">Implement this parameter to indicate that a resource is created if one does not already exist when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-121">Ta bort datatypen: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-121">Delete Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-122">Implementera den här parametern så att resurser tas bort när cmdleten har slutförts åtgärden när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-122">Implement this parameter so that resources are deleted when the cmdlet has completed its operation when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-123">Tömma datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-123">Drain Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-124">Implementera den här parametern om du vill ange att återstående arbetsuppgifter bearbetas innan cmdleten bearbetar nya data när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-124">Implement this parameter to indicate that outstanding work items are processed before the cmdlet processes new data when the parameter is specified.</span></span> <span data-ttu-id="e5d5d-125">Om parametern inte anges, behandlas arbetsobjekt direkt.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-125">If the parameter is not specified, the work items are processed immediately.</span></span>

<span data-ttu-id="e5d5d-126">Radera datatyp: Int32</span><span class="sxs-lookup"><span data-stu-id="e5d5d-126">Erase Data type: Int32</span></span>

<span data-ttu-id="e5d5d-127">Implementera den här parametern så att användaren kan ange hur många gånger som en resurs tas bort innan de tas bort.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-127">Implement this parameter so that the user can specify the number of times a resource is erased before it is deleted.</span></span>

<span data-ttu-id="e5d5d-128">ErrorLevel datatyp: Int32</span><span class="sxs-lookup"><span data-stu-id="e5d5d-128">ErrorLevel Data type: Int32</span></span>

<span data-ttu-id="e5d5d-129">Implementera den här parametern så att användaren kan ange nivån av fel till rapporten.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-129">Implement this parameter so that the user can specify the level of errors to report.</span></span>

<span data-ttu-id="e5d5d-130">Exkludera datatyp: String[]</span><span class="sxs-lookup"><span data-stu-id="e5d5d-130">Exclude Data type: String[]</span></span>

<span data-ttu-id="e5d5d-131">Implementera den här parametern så att användaren kan utesluta något från en aktivitet.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-131">Implement this parameter so that the user can exclude something from an activity.</span></span> <span data-ttu-id="e5d5d-132">Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e5d5d-132">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="e5d5d-133">Filtrera datatyp: Nyckelord</span><span class="sxs-lookup"><span data-stu-id="e5d5d-133">Filter Data type: Keyword</span></span>

<span data-ttu-id="e5d5d-134">Implementera den här parametern så att användaren kan ange ett filter som väljs de resurser som du vill utföra cmdlet-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-134">Implement this parameter so that the user can specify a filter that selects the resources upon which to perform the cmdlet action.</span></span> <span data-ttu-id="e5d5d-135">Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e5d5d-135">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="e5d5d-136">Följ datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-136">Follow Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-137">Implementera den här parametern så att förloppet spåras när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-137">Implement this parameter so that progress is tracked when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-138">Tvinga datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-138">Force Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-139">Implementera den här parametern för att ange att användaren kan utföra en åtgärd även om begränsningar uppstår när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-139">Implement this parameter to indicate that the user can perform an action even if restrictions are encountered when the parameter is specified.</span></span> <span data-ttu-id="e5d5d-140">Parametern tillåter inte att säkerheten äventyras.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-140">The parameter does not allow security to be compromised.</span></span> <span data-ttu-id="e5d5d-141">Den här parametern kan till exempel en användare skriver över en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-141">For example, this parameter lets a user overwrite a read-only file.</span></span>

<span data-ttu-id="e5d5d-142">Med datatypen: String[]</span><span class="sxs-lookup"><span data-stu-id="e5d5d-142">Include Data type: String[]</span></span>

<span data-ttu-id="e5d5d-143">Implementera den här parametern så att användaren kan innehålla något i en aktivitet.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-143">Implement this parameter so that the user can include something in an activity.</span></span> <span data-ttu-id="e5d5d-144">Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e5d5d-144">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="e5d5d-145">Inkrementell datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-145">Incremental Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-146">Implementera den här parametern om du vill ange att bearbetning utförs stegvis när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-146">Implement this parameter to indicate that processing is performed incrementally when the parameter is specified.</span></span> <span data-ttu-id="e5d5d-147">Den här parametern kan till exempel en användare att utföra inkrementella säkerhetskopieringar som säkerhetskopierar filer endast sedan den senaste säkerhetskopieringen.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-147">For example, this parameter lets a user perform incremental backups that back up files only since the last backup.</span></span>

<span data-ttu-id="e5d5d-148">InputObject datatyp: Objekt</span><span class="sxs-lookup"><span data-stu-id="e5d5d-148">InputObject Data type: Object</span></span>

<span data-ttu-id="e5d5d-149">Implementera den här parametern när cmdlet: en hämtar indata från andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-149">Implement this parameter when the cmdlet takes input from other cmdlets.</span></span> <span data-ttu-id="e5d5d-150">När du definierar en `InputObject` parametern alltid ange den `ValueFromPipeline` nyckelord när du deklarerar den **parametern** attribut.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-150">When you define an `InputObject` parameter, always specify the `ValueFromPipeline` keyword when you declare the **Parameter** attribute.</span></span> <span data-ttu-id="e5d5d-151">Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e5d5d-151">For more information about using input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="e5d5d-152">Infoga datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-152">Insert Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-153">Implementera den här parametern så att cmdleten infogar ett objekt när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-153">Implement this parameter so that the cmdlet inserts an item when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-154">Interaktiv datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-154">Interactive Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-155">Implementera den här parametern så att cmdleten fungerar interaktivt med användaren när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-155">Implement this parameter so that the cmdlet works interactively with the user when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-156">Intervalltyp för Data: Hash-tabell</span><span class="sxs-lookup"><span data-stu-id="e5d5d-156">Interval Data type: HashTable</span></span>

<span data-ttu-id="e5d5d-157">Implementera den här parametern så att användaren kan ange en hash-tabell över nyckelord som innehåller värdena.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-157">Implement this parameter so that the user can specify a hash table of keywords that contains the values.</span></span> <span data-ttu-id="e5d5d-158">I följande exempel visar exempelvärden för den `Interval` parameter: `-interval @{ResumeScan=15; Retry=3}`.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-158">The following example shows sample values for the `Interval` parameter: `-interval @{ResumeScan=15; Retry=3}`.</span></span>

<span data-ttu-id="e5d5d-159">Loggdata skriver du: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-159">Log Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-160">Implementera den här parametern granskning av cmdlet: en när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-160">Implement this parameter audit the actions of the cmdlet when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-161">NoClobber datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-161">NoClobber Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-162">Implementera den här parametern så att resursen inte ska skrivas över när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-162">Implement this parameter so that the resource will not be overwritten when the parameter is specified.</span></span> <span data-ttu-id="e5d5d-163">Den här parametern gäller vanligtvis för cmdletar som skapar nya objekt så att de kan förhindras från att skriva över befintliga objekt med samma namn.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-163">This parameter generally applies to cmdlets that create new objects so that they can be prevented from overwriting existing objects with the same name.</span></span>

<span data-ttu-id="e5d5d-164">Meddela datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-164">Notify Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-165">Implementera den här parametern så att användaren ska meddelas att aktiviteten har slutförts när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-165">Implement this parameter so that the user will be notified that the activity is complete when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-166">NotifyAddress datatyp: E-postadress</span><span class="sxs-lookup"><span data-stu-id="e5d5d-166">NotifyAddress Data type: E-mail address</span></span>

<span data-ttu-id="e5d5d-167">Implementera den här parametern så att användaren kan ange den e-postadressen du använder för att skicka ett meddelande när den `Notify` parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-167">Implement this parameter so that the user can specify the e-mail address to use to send a notification when the `Notify` parameter is specified.</span></span>

<span data-ttu-id="e5d5d-168">Skriv över datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-168">Overwrite Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-169">Implementera den här parametern så att cmdleten skriver över befintliga data när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-169">Implement this parameter so that the cmdlet overwrites any existing data when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-170">Fråga datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="e5d5d-170">Prompt Data type: String</span></span>

<span data-ttu-id="e5d5d-171">Implementera den här parametern så att användaren kan ange en prompt som ber cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-171">Implement this parameter so that the user can specify a prompt for the cmdlet.</span></span>

<span data-ttu-id="e5d5d-172">Tyst datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-172">Quiet Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-173">Implementera den här parametern så att cmdleten Undertrycker Användarfeedback under dess åtgärder när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-173">Implement this parameter so that the cmdlet suppresses user feedback during its actions when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-174">Recurse datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-174">Recurse Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-175">Implementera den här parametern så att cmdlet-rekursivt utför dess åtgärder på resurser när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-175">Implement this parameter so that the cmdlet recursively performs its actions on resources when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-176">Reparera datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-176">Repair Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-177">Implementera den här parametern så att cmdleten ska försöka korrigera något från skadas när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-177">Implement this parameter so that the cmdlet will attempt to correct something from a broken state when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-178">RepairString datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="e5d5d-178">RepairString Data type: String</span></span>

<span data-ttu-id="e5d5d-179">Implementera den här parametern så att användaren kan ange en sträng som ska användas när den `Repair` parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-179">Implement this parameter so that the user can specify a string to use when the `Repair` parameter is specified.</span></span>

<span data-ttu-id="e5d5d-180">Gör om-datatypen: Int32</span><span class="sxs-lookup"><span data-stu-id="e5d5d-180">Retry Data type: Int32</span></span>

<span data-ttu-id="e5d5d-181">Implementera den här parametern så att användaren kan ange hur många gånger som cmdleten försöker en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-181">Implement this parameter so the user can specify the number of times the cmdlet will attempt an action.</span></span>

<span data-ttu-id="e5d5d-182">Välj typ av Data: Nyckelordet matris</span><span class="sxs-lookup"><span data-stu-id="e5d5d-182">Select Data type: Keyword array</span></span>

<span data-ttu-id="e5d5d-183">Implementera den här parametern så att användaren kan ange en matris med vilka typer av objekt.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-183">Implement this parameter so that the user can specify an array of the types of items.</span></span>

<span data-ttu-id="e5d5d-184">Stream-datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-184">Stream Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-185">Implementera den här parametern så att användaren kan strömma flera utdata objekt genom pipelinen när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-185">Implement this parameter so the user can stream multiple output objects through the pipeline when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-186">Strikt datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-186">Strict Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-187">Implementera den här parametern så att alla fel hanteras som avslutande fel när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-187">Implement this parameter so that all errors are handled as terminating errors when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-188">TempLocation datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="e5d5d-188">TempLocation Data type: String</span></span>

<span data-ttu-id="e5d5d-189">Implementera den här parametern så att användaren kan ange platsen för tillfälliga data som används under driften av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-189">Implement this parameter so the user can specify the location of temporary data that is used during the operation of the cmdlet.</span></span>

<span data-ttu-id="e5d5d-190">Tidsgräns för datatyp: Int32</span><span class="sxs-lookup"><span data-stu-id="e5d5d-190">Timeout Data type: Int32</span></span>

<span data-ttu-id="e5d5d-191">Implementera den här parametern så att användaren kan ange timeout-intervall (i millisekunder).</span><span class="sxs-lookup"><span data-stu-id="e5d5d-191">Implement this parameter so that the user can specify the timeout interval (in milliseconds).</span></span>

<span data-ttu-id="e5d5d-192">Trunkera datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-192">Truncate Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-193">Implementera den här parametern så att cmdleten trunkerar dess åtgärder när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-193">Implement this parameter so that the cmdlet will truncate its actions when the parameter is specified.</span></span> <span data-ttu-id="e5d5d-194">Om parametern inte anges, utför cmdlet: en annan åtgärd.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-194">If the parameter is not specified, the cmdlet performs another action.</span></span>

<span data-ttu-id="e5d5d-195">Kontrollera typ av Data: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-195">Verify Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-196">Implementera den här parametern så att cmdleten kommer att testa för att avgöra om en åtgärd har uppstått när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-196">Implement this parameter so that the cmdlet will test to determine whether an action has occurred when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-197">Vänta datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e5d5d-197">Wait Data type: SwitchParameter</span></span>

<span data-ttu-id="e5d5d-198">Implementera den här parametern så att cmdleten väntar på indata från användaren innan du fortsätter när parametern har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-198">Implement this parameter so that the cmdlet will wait for user input before continuing when the parameter is specified.</span></span>

<span data-ttu-id="e5d5d-199">Väntetid datatyp: Int32</span><span class="sxs-lookup"><span data-stu-id="e5d5d-199">WaitTime Data type: Int32</span></span>

<span data-ttu-id="e5d5d-200">Implementera den här parametern så att användaren kan ange varaktighet (i sekunder) att cmdleten ska vänta tills användaren ange när den `Wait` parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="e5d5d-200">Implement this parameter so that the user can specify the duration (in seconds) that the cmdlet will wait for user input when the `Wait` parameter is specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5d5d-201">Se även</span><span class="sxs-lookup"><span data-stu-id="e5d5d-201">See Also</span></span>

[<span data-ttu-id="e5d5d-202">Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="e5d5d-202">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="e5d5d-203">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5d5d-203">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="e5d5d-204">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e5d5d-204">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
