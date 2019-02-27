---
title: Bakgrundsjobb | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: 9aff23647e55e8c9c41c54e5b62cedc15fb28a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847630"
---
# <a name="background-jobs"></a><span data-ttu-id="eae90-102">Bakgrundsjobb</span><span class="sxs-lookup"><span data-stu-id="eae90-102">Background Jobs</span></span>

<span data-ttu-id="eae90-103">Cmdlet: ar kan utföra sina åtgärder internt eller som ett Windows PowerShell*bakgrundsjobbet*.</span><span class="sxs-lookup"><span data-stu-id="eae90-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="eae90-104">När en cmdlet körs i bakgrunden på arbetet utförs asynkront i en egen separat från den pipeline-tråden med hjälp av cmdlet: en tråd.</span><span class="sxs-lookup"><span data-stu-id="eae90-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="eae90-105">Ur användare när en cmdlet körs i bakgrunden, returnerar Kommandotolken omedelbart även om jobbet tar längre tid att slutföra och användaren kan fortsätta utan avbrott medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="eae90-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="eae90-106">Bakgrundsjobb, underordnade jobb och jobbet databasen</span><span class="sxs-lookup"><span data-stu-id="eae90-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="eae90-107">Objektet som returneras av cmdlet: ar som stöder bakgrundsjobb definierar jobbet.</span><span class="sxs-lookup"><span data-stu-id="eae90-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="eae90-108">(Den [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet även returnerar ett jobbobjekt.) Namnet på jobbet, en identifierare som används för att ange jobbet, tillståndsinformationen och det underordnade jobbet ingår i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="eae90-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="eae90-109">Jobbet utför inte någon av arbetet.</span><span class="sxs-lookup"><span data-stu-id="eae90-109">The job does not perform any of the work.</span></span> <span data-ttu-id="eae90-110">Varje bakgrundsjobbet har minst ett underordnat jobb eftersom underordnat jobb utför det faktiska arbetet.</span><span class="sxs-lookup"><span data-stu-id="eae90-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="eae90-111">När du kör en cmdlet så att arbetet utförs i bakgrunden, cmdlet: en måste lägga till jobbet och det underordnade jobbet till en gemensam databas, kallas de *jobbet databasen*.</span><span class="sxs-lookup"><span data-stu-id="eae90-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>
<span data-ttu-id="eae90-112">Objektet som returneras av cmdlet: ar som stöder bakgrundsjobb definierar jobbet.</span><span class="sxs-lookup"><span data-stu-id="eae90-112">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="eae90-113">(Den [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet även returnerar ett jobbobjekt.) Namnet på jobbet, en identifierare som används för att ange jobbet, tillståndsinformationen och det underordnade jobbet ingår i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="eae90-113">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="eae90-114">Jobbet utför inte någon av arbetet.</span><span class="sxs-lookup"><span data-stu-id="eae90-114">The job does not perform any of the work.</span></span> <span data-ttu-id="eae90-115">Varje bakgrundsjobbet har minst ett underordnat jobb eftersom underordnat jobb utför det faktiska arbetet.</span><span class="sxs-lookup"><span data-stu-id="eae90-115">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="eae90-116">När du kör en cmdlet så att arbetet utförs i bakgrunden, cmdlet: en måste lägga till jobbet och det underordnade jobbet till en gemensam databas, kallas de *jobbet databasen*.</span><span class="sxs-lookup"><span data-stu-id="eae90-116">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="eae90-117">Mer information om hur bakgrundsjobb hanteras på kommandoraden finns i följande:</span><span class="sxs-lookup"><span data-stu-id="eae90-117">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="eae90-118">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="eae90-118">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="eae90-119">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="eae90-119">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="eae90-120">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="eae90-120">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="eae90-121">Skriva en Cmdlet som körs i bakgrunden</span><span class="sxs-lookup"><span data-stu-id="eae90-121">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="eae90-122">Om du vill skriva en cmdlet som kan köras i bakgrunden, måste du utföra följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="eae90-122">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="eae90-123">Definiera en `asJob` växla parametern så att användaren kan välja om du vill köra cmdleten i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="eae90-123">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="eae90-124">Skapa ett objekt som härleds från den [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) klass.</span><span class="sxs-lookup"><span data-stu-id="eae90-124">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="eae90-125">Det här objektet kan vara en anpassad jobbobjektet eller ett jobbobjekt som tillhandahålls av Windows PowerShell, till exempel en [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objekt.</span><span class="sxs-lookup"><span data-stu-id="eae90-125">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="eae90-126">I en post bearbetning av-metoden lägger du till en `if` -instruktion som identifierar om cmdleten ska köras i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="eae90-126">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="eae90-127">Implementera klassen jobb för anpassade jobbobjekt.</span><span class="sxs-lookup"><span data-stu-id="eae90-127">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="eae90-128">Returnera de lämpliga objekt, beroende på om cmdleten körs i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="eae90-128">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="eae90-129">Finns ett kodexempel i [så Support jobb](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="eae90-129">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="eae90-130">Bakgrund jobbrelaterade API: er</span><span class="sxs-lookup"><span data-stu-id="eae90-130">Background Job-Related APIs</span></span>

<span data-ttu-id="eae90-131">Följande API: er tillhandahålls av Windows PowerShell för att hantera bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="eae90-131">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="eae90-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) härleds anpassade jobbobjekt.</span><span class="sxs-lookup"><span data-stu-id="eae90-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="eae90-133">Det här är en abstrakt klass.</span><span class="sxs-lookup"><span data-stu-id="eae90-133">This is an abstract class.</span></span>

<span data-ttu-id="eae90-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) hanterar och ger information om de aktuella aktiva bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="eae90-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="eae90-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definierar tillståndet för bakgrundsjobbet.</span><span class="sxs-lookup"><span data-stu-id="eae90-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="eae90-136">Tillstånd är igång, körs och stoppad.</span><span class="sxs-lookup"><span data-stu-id="eae90-136">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="eae90-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) innehåller information om tillståndet för ett bakgrundsjobb och, om det senaste tillståndet ändrar orsakades av ett fel, orsak som jobbet har angett det aktuella tillståndet.</span><span class="sxs-lookup"><span data-stu-id="eae90-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="eae90-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) ger argumenten för en händelse som utlöses när ett bakgrundsjobb ändrar tillstånd.</span><span class="sxs-lookup"><span data-stu-id="eae90-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="eae90-139">Windows PowerShell-Job-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="eae90-139">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="eae90-140">Följande cmdletar tillhandahålls av Windows PowerShell för att hantera bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="eae90-140">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="eae90-141">Get-Job</span><span class="sxs-lookup"><span data-stu-id="eae90-141">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="eae90-142">Hämtar Windows PowerShell-bakgrundsjobb som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="eae90-142">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="eae90-143">Ta emot jobb</span><span class="sxs-lookup"><span data-stu-id="eae90-143">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="eae90-144">Hämtar resultaten av Windows PowerShell-bakgrundsjobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="eae90-144">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="eae90-145">Ta bort jobb</span><span class="sxs-lookup"><span data-stu-id="eae90-145">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="eae90-146">Tar bort ett Windows PowerShell-bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="eae90-146">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="eae90-147">Starta jobb</span><span class="sxs-lookup"><span data-stu-id="eae90-147">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="eae90-148">Startar ett Windows PowerShell-bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="eae90-148">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="eae90-149">Stoppa jobb</span><span class="sxs-lookup"><span data-stu-id="eae90-149">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="eae90-150">Stoppar ett Windows PowerShell-bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="eae90-150">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="eae90-151">Wait-jobb</span><span class="sxs-lookup"><span data-stu-id="eae90-151">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="eae90-152">Undertrycker Kommandotolken förrän en eller alla av Windows PowerShell-bakgrundsjobb som körs i sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="eae90-152">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="eae90-153">Se även</span><span class="sxs-lookup"><span data-stu-id="eae90-153">See Also</span></span>

[<span data-ttu-id="eae90-154">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eae90-154">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
