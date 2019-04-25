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
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068697"
---
# <a name="background-jobs"></a><span data-ttu-id="48d79-102">Bakgrundsjobb</span><span class="sxs-lookup"><span data-stu-id="48d79-102">Background Jobs</span></span>

<span data-ttu-id="48d79-103">Cmdlet: ar kan utföra sina åtgärder internt eller som ett Windows PowerShell*bakgrundsjobbet*.</span><span class="sxs-lookup"><span data-stu-id="48d79-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="48d79-104">När en cmdlet körs i bakgrunden på arbetet utförs asynkront i en egen separat från den pipeline-tråden med hjälp av cmdlet: en tråd.</span><span class="sxs-lookup"><span data-stu-id="48d79-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="48d79-105">Ur användare när en cmdlet körs i bakgrunden, returnerar Kommandotolken omedelbart även om jobbet tar längre tid att slutföra och användaren kan fortsätta utan avbrott medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="48d79-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="48d79-106">Bakgrundsjobb, underordnade jobb och jobbet databasen</span><span class="sxs-lookup"><span data-stu-id="48d79-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="48d79-107">Objektet som returneras av cmdlet: ar som stöder bakgrundsjobb definierar jobbet.</span><span class="sxs-lookup"><span data-stu-id="48d79-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="48d79-108">(Den [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet även returnerar ett jobbobjekt.) Namnet på jobbet, en identifierare som används för att ange jobbet, tillståndsinformationen och det underordnade jobbet ingår i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="48d79-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="48d79-109">Jobbet utför inte någon av arbetet.</span><span class="sxs-lookup"><span data-stu-id="48d79-109">The job does not perform any of the work.</span></span> <span data-ttu-id="48d79-110">Varje bakgrundsjobbet har minst ett underordnat jobb eftersom underordnat jobb utför det faktiska arbetet.</span><span class="sxs-lookup"><span data-stu-id="48d79-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="48d79-111">När du kör en cmdlet så att arbetet utförs i bakgrunden, cmdlet: en måste lägga till jobbet och det underordnade jobbet till en gemensam databas, kallas de *jobbet databasen*.</span><span class="sxs-lookup"><span data-stu-id="48d79-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="48d79-112">Mer information om hur bakgrundsjobb hanteras på kommandoraden finns i följande:</span><span class="sxs-lookup"><span data-stu-id="48d79-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="48d79-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="48d79-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="48d79-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="48d79-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="48d79-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="48d79-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="48d79-116">Skriva en Cmdlet som körs i bakgrunden</span><span class="sxs-lookup"><span data-stu-id="48d79-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="48d79-117">Om du vill skriva en cmdlet som kan köras i bakgrunden, måste du utföra följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="48d79-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="48d79-118">Definiera en `asJob` växla parametern så att användaren kan välja om du vill köra cmdleten i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="48d79-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="48d79-119">Skapa ett objekt som härleds från den [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) klass.</span><span class="sxs-lookup"><span data-stu-id="48d79-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="48d79-120">Det här objektet kan vara en anpassad jobbobjektet eller ett jobbobjekt som tillhandahålls av Windows PowerShell, till exempel en [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objekt.</span><span class="sxs-lookup"><span data-stu-id="48d79-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="48d79-121">I en post bearbetning av-metoden lägger du till en `if` -instruktion som identifierar om cmdleten ska köras i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="48d79-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="48d79-122">Implementera klassen jobb för anpassade jobbobjekt.</span><span class="sxs-lookup"><span data-stu-id="48d79-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="48d79-123">Returnera de lämpliga objekt, beroende på om cmdleten körs i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="48d79-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="48d79-124">Finns ett kodexempel i [så Support jobb](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="48d79-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="48d79-125">Bakgrund jobbrelaterade API: er</span><span class="sxs-lookup"><span data-stu-id="48d79-125">Background Job-Related APIs</span></span>

<span data-ttu-id="48d79-126">Följande API: er tillhandahålls av Windows PowerShell för att hantera bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="48d79-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="48d79-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) härleds anpassade jobbobjekt.</span><span class="sxs-lookup"><span data-stu-id="48d79-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="48d79-128">Det här är en abstrakt klass.</span><span class="sxs-lookup"><span data-stu-id="48d79-128">This is an abstract class.</span></span>

<span data-ttu-id="48d79-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) hanterar och ger information om de aktuella aktiva bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="48d79-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="48d79-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definierar tillståndet för bakgrundsjobbet.</span><span class="sxs-lookup"><span data-stu-id="48d79-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="48d79-131">Tillstånd är igång, körs och stoppad.</span><span class="sxs-lookup"><span data-stu-id="48d79-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="48d79-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) innehåller information om tillståndet för ett bakgrundsjobb och, om det senaste tillståndet ändrar orsakades av ett fel, orsak som jobbet har angett det aktuella tillståndet.</span><span class="sxs-lookup"><span data-stu-id="48d79-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="48d79-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) ger argumenten för en händelse som utlöses när ett bakgrundsjobb ändrar tillstånd.</span><span class="sxs-lookup"><span data-stu-id="48d79-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="48d79-134">Windows PowerShell-Job-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="48d79-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="48d79-135">Följande cmdletar tillhandahålls av Windows PowerShell för att hantera bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="48d79-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="48d79-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="48d79-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="48d79-137">Hämtar Windows PowerShell-bakgrundsjobb som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="48d79-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="48d79-138">Ta emot jobb</span><span class="sxs-lookup"><span data-stu-id="48d79-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="48d79-139">Hämtar resultaten av Windows PowerShell-bakgrundsjobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="48d79-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="48d79-140">Ta bort jobb</span><span class="sxs-lookup"><span data-stu-id="48d79-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="48d79-141">Tar bort ett Windows PowerShell-bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="48d79-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="48d79-142">Starta jobb</span><span class="sxs-lookup"><span data-stu-id="48d79-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="48d79-143">Startar ett Windows PowerShell-bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="48d79-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="48d79-144">Stoppa jobb</span><span class="sxs-lookup"><span data-stu-id="48d79-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="48d79-145">Stoppar ett Windows PowerShell-bakgrundsjobb.</span><span class="sxs-lookup"><span data-stu-id="48d79-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="48d79-146">Wait-jobb</span><span class="sxs-lookup"><span data-stu-id="48d79-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="48d79-147">Undertrycker Kommandotolken förrän en eller alla av Windows PowerShell-bakgrundsjobb som körs i sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="48d79-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="48d79-148">Se även</span><span class="sxs-lookup"><span data-stu-id="48d79-148">See Also</span></span>

[<span data-ttu-id="48d79-149">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="48d79-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
