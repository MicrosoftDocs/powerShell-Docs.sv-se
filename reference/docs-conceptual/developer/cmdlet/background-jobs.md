---
title: Bakgrunds jobb | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354917"
---
# <a name="background-jobs"></a><span data-ttu-id="0b298-102">Bakgrundsjobb</span><span class="sxs-lookup"><span data-stu-id="0b298-102">Background Jobs</span></span>

<span data-ttu-id="0b298-103">Cmdlets kan utföra sina åtgärder internt eller som ett*bakgrunds jobb*i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b298-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="0b298-104">När en cmdlet körs som ett bakgrunds jobb utförs arbetet asynkront i sin egen tråd separat från pipeline-tråden som cmdleten använder.</span><span class="sxs-lookup"><span data-stu-id="0b298-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="0b298-105">När en cmdlet körs som ett bakgrunds jobb i användar perspektivet returnerar kommando tolken omedelbart även om jobbet tar en längre tid att slutföra, och användaren kan fortsätta utan avbrott medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="0b298-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="0b298-106">Bakgrunds jobb, underordnade jobb och jobb databasen</span><span class="sxs-lookup"><span data-stu-id="0b298-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="0b298-107">Jobbobjektet som returneras av de cmdletar som har stöd för bakgrunds jobb definierar jobbet.</span><span class="sxs-lookup"><span data-stu-id="0b298-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="0b298-108">(Cmdleten [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) returnerar också ett Job-objekt.) Namnet på jobbet, en identifierare som används för att ange jobbet, tillståndsinformation och de underordnade jobben ingår i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="0b298-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="0b298-109">Jobbet utför inget arbete.</span><span class="sxs-lookup"><span data-stu-id="0b298-109">The job does not perform any of the work.</span></span> <span data-ttu-id="0b298-110">Varje bakgrunds jobb har minst ett underordnat jobb eftersom det underordnade jobbet utför det faktiska arbetet.</span><span class="sxs-lookup"><span data-stu-id="0b298-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="0b298-111">När du kör en cmdlet så att arbetet utförs som ett bakgrunds jobb måste cmdleten lägga till jobbet och de underordnade jobben till en gemensam lagrings plats, som kallas *jobbets lagrings plats*.</span><span class="sxs-lookup"><span data-stu-id="0b298-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="0b298-112">Mer information om hur bakgrunds jobb hanteras på kommando raden finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="0b298-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="0b298-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="0b298-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="0b298-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="0b298-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="0b298-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="0b298-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="0b298-116">Skriva en cmdlet som körs som ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="0b298-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="0b298-117">Om du vill skriva en-cmdlet som kan köras som ett bakgrunds jobb måste du utföra följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="0b298-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="0b298-118">Definiera en `asJob` växel parameter så att användaren kan bestämma om du vill köra cmdleten som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="0b298-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="0b298-119">Skapa ett objekt som härleds från klassen [system. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) .</span><span class="sxs-lookup"><span data-stu-id="0b298-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="0b298-120">Objektet kan vara ett anpassat jobb objekt eller ett jobb objekt som tillhandahålls av Windows PowerShell, till exempel ett [system. Management. Automation. Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) -objekt.</span><span class="sxs-lookup"><span data-stu-id="0b298-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="0b298-121">I en post bearbetnings metod lägger du till en `if`-instruktion som identifierar om cmdleten ska köras som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="0b298-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="0b298-122">Implementera jobb klassen för anpassade jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="0b298-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="0b298-123">Returnera lämpliga objekt, beroende på om cmdleten körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="0b298-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="0b298-124">Ett kod exempel finns i [så här stöder du jobb](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="0b298-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="0b298-125">API: er för bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="0b298-125">Background Job-Related APIs</span></span>

<span data-ttu-id="0b298-126">Följande API: er tillhandahålls av Windows PowerShell för att hantera bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="0b298-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="0b298-127">[System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) härleder anpassade jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="0b298-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="0b298-128">Detta är en abstrakt klass.</span><span class="sxs-lookup"><span data-stu-id="0b298-128">This is an abstract class.</span></span>

<span data-ttu-id="0b298-129">[System. Management. Automation. Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) hanterar och ger information om de aktuella aktiva bakgrunds jobben.</span><span class="sxs-lookup"><span data-stu-id="0b298-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="0b298-130">[System. Management. Automation. JobState](/dotnet/api/System.Management.Automation.JobState) definierar status för bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="0b298-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="0b298-131">Tillstånd är igång, körs och stoppas.</span><span class="sxs-lookup"><span data-stu-id="0b298-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="0b298-132">[System. Management. Automation. Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) innehåller information om tillståndet för ett bakgrunds jobb och, om den senaste tillstånds ändringen orsakades av ett fel, varför jobbet skrevs i det aktuella tillståndet.</span><span class="sxs-lookup"><span data-stu-id="0b298-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="0b298-133">[System. Management. Automation. Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) innehåller argument för en händelse som aktive ras när ett bakgrunds jobb ändrar tillstånd.</span><span class="sxs-lookup"><span data-stu-id="0b298-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="0b298-134">Windows PowerShell-jobb-cmdletar</span><span class="sxs-lookup"><span data-stu-id="0b298-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="0b298-135">Följande cmdletar tillhandahålls av Windows PowerShell för att hantera bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="0b298-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="0b298-136">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="0b298-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="0b298-137">Hämtar bakgrunds jobb i Windows PowerShell som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0b298-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="0b298-138">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="0b298-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="0b298-139">Hämtar resultatet av bakgrunds jobben för Windows PowerShell i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0b298-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="0b298-140">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="0b298-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="0b298-141">Tar bort ett bakgrunds jobb i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b298-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="0b298-142">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="0b298-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="0b298-143">Startar ett bakgrunds jobb i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b298-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="0b298-144">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="0b298-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="0b298-145">Stoppar ett bakgrunds jobb i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b298-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="0b298-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="0b298-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="0b298-147">Ignorerar kommando tolken tills en eller flera av de Windows PowerShell-bakgrunds jobb som körs i sessionen är slutförda.</span><span class="sxs-lookup"><span data-stu-id="0b298-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b298-148">Se även</span><span class="sxs-lookup"><span data-stu-id="0b298-148">See Also</span></span>

[<span data-ttu-id="0b298-149">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b298-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
