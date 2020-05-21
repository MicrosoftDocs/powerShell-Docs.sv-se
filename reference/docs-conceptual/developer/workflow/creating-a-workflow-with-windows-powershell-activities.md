---
title: Skapa ett arbets flöde med Windows PowerShell-aktiviteter | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 12b0b246b78142f3811f9f566cd94e4dabd40cc9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557473"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="d9981-102">Skapa ett arbetsflöde med Windows PowerShell-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="d9981-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="d9981-103">Du kan skapa ett Windows PowerShell-arbetsflöde genom att välja aktiviteter från Visual Studio-verktygslådan och dra dem till arbetsflödesdesigners fönstret.</span><span class="sxs-lookup"><span data-stu-id="d9981-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="d9981-104">Information om hur du lägger till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan finns i [lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="d9981-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="d9981-105">Följande procedurer beskriver hur du skapar ett arbets flöde som kontrollerar domän status för en grupp av användardefinierade datorer, kopplar dem till en domän om de inte redan är anslutna och sedan kontrollerar statusen igen.</span><span class="sxs-lookup"><span data-stu-id="d9981-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="d9981-106">Konfigurerar projektet</span><span class="sxs-lookup"><span data-stu-id="d9981-106">Setting up the Project</span></span>

1. <span data-ttu-id="d9981-107">Följ proceduren i [lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) för att skapa ett arbets flödes projekt och lägga till aktiviteterna från sammansättningarna [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) och [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) i verktygs lådan.</span><span class="sxs-lookup"><span data-stu-id="d9981-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="d9981-108">Lägg till system. Management. Automation, Microsoft. PowerShell. Activities, system. Management, Microsoft. PowerShell. Management. Activities och Microsoft. PowerShell. commands. Management för projektet som referens sammansättningar.</span><span class="sxs-lookup"><span data-stu-id="d9981-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="d9981-109">Lägga till aktiviteter i arbets flödet</span><span class="sxs-lookup"><span data-stu-id="d9981-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="d9981-110">Lägg till en **sekvens** -aktivitet i arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="d9981-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="d9981-111">Skapa ett argument `ComputerName` med namnet med en argument typ `String[]` .</span><span class="sxs-lookup"><span data-stu-id="d9981-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="d9981-112">Det här argumentet representerar namnen på de datorer som ska kontrol leras och anslutas.</span><span class="sxs-lookup"><span data-stu-id="d9981-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="d9981-113">Skapa ett argument med namnet `DomainCred` av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="d9981-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="d9981-114">Det här argumentet representerar domänautentiseringsuppgifter för ett domän konto som har behörighet att ansluta en dator till domänen.</span><span class="sxs-lookup"><span data-stu-id="d9981-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="d9981-115">Skapa ett argument med namnet `MachineCred` av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="d9981-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="d9981-116">Det här argumentet representerar autentiseringsuppgifterna för en administratör på de datorer som ska kontrol leras och anslutas.</span><span class="sxs-lookup"><span data-stu-id="d9981-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="d9981-117">Lägg till en **ParallelForEach** -aktivitet i **sekvens** -aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="d9981-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="d9981-118">Ange `comp` och `ComputerName` i text rutorna så att loopen upprepas genom elementen i `ComputerName` matrisen.</span><span class="sxs-lookup"><span data-stu-id="d9981-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="d9981-119">Lägg till en **sekvens** -aktivitet i bröd texten i **ParallelForEach** -aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="d9981-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="d9981-120">Ange egenskapen **DisplayName** för sekvensen till `JoinDomain` .</span><span class="sxs-lookup"><span data-stu-id="d9981-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="d9981-121">Lägg till en **GetWmiObject** -aktivitet i **JoinDomain** -sekvensen.</span><span class="sxs-lookup"><span data-stu-id="d9981-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="d9981-122">Redigera egenskaperna för **GetWmiObject** -aktiviteten enligt följande.</span><span class="sxs-lookup"><span data-stu-id="d9981-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="d9981-123">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d9981-123">Property</span></span>|<span data-ttu-id="d9981-124">Värde</span><span class="sxs-lookup"><span data-stu-id="d9981-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="d9981-125">**Klass**</span><span class="sxs-lookup"><span data-stu-id="d9981-125">**Class**</span></span>|<span data-ttu-id="d9981-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="d9981-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="d9981-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="d9981-127">**PSComputerName**</span></span>|<span data-ttu-id="d9981-128">fysiskt</span><span class="sxs-lookup"><span data-stu-id="d9981-128">{comp}</span></span>|
   |<span data-ttu-id="d9981-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="d9981-129">**PSCredential**</span></span>|<span data-ttu-id="d9981-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="d9981-130">MachineCred</span></span>|

9. <span data-ttu-id="d9981-131">Lägg till en **AddComputer** -aktivitet i **JoinDomain** -sekvensen efter **GetWmiObject** -aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="d9981-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="d9981-132">Redigera egenskaperna för **AddComputer** -aktiviteten enligt följande.</span><span class="sxs-lookup"><span data-stu-id="d9981-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="d9981-133">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d9981-133">Property</span></span>|<span data-ttu-id="d9981-134">Värde</span><span class="sxs-lookup"><span data-stu-id="d9981-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="d9981-135">**Namnet**</span><span class="sxs-lookup"><span data-stu-id="d9981-135">**ComputerName**</span></span>|<span data-ttu-id="d9981-136">fysiskt</span><span class="sxs-lookup"><span data-stu-id="d9981-136">{comp}</span></span>|
    |<span data-ttu-id="d9981-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="d9981-137">**DomainCredential**</span></span>|<span data-ttu-id="d9981-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="d9981-138">DomainCred</span></span>|

11. <span data-ttu-id="d9981-139">Lägg till en **RestartComputer** -aktivitet i **JoinDomain** -sekvensen efter **AddComputer** -aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="d9981-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="d9981-140">Redigera egenskaperna för **RestartComputer** -aktiviteten enligt följande.</span><span class="sxs-lookup"><span data-stu-id="d9981-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="d9981-141">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d9981-141">Property</span></span>|<span data-ttu-id="d9981-142">Värde</span><span class="sxs-lookup"><span data-stu-id="d9981-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="d9981-143">**Namnet**</span><span class="sxs-lookup"><span data-stu-id="d9981-143">**ComputerName**</span></span>|<span data-ttu-id="d9981-144">fysiskt</span><span class="sxs-lookup"><span data-stu-id="d9981-144">{comp}</span></span>|
    |<span data-ttu-id="d9981-145">**Autentiseringsuppgift**</span><span class="sxs-lookup"><span data-stu-id="d9981-145">**Credential**</span></span>|<span data-ttu-id="d9981-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="d9981-146">MachineCred</span></span>|
    |<span data-ttu-id="d9981-147">**Söker**</span><span class="sxs-lookup"><span data-stu-id="d9981-147">**For**</span></span>|<span data-ttu-id="d9981-148">Microsoft. PowerShell. commands. WaitForServiceTypes. PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9981-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="d9981-149">**Inför**</span><span class="sxs-lookup"><span data-stu-id="d9981-149">**Force**</span></span>|<span data-ttu-id="d9981-150">Sant</span><span class="sxs-lookup"><span data-stu-id="d9981-150">True</span></span>|
    |<span data-ttu-id="d9981-151">Vänta</span><span class="sxs-lookup"><span data-stu-id="d9981-151">Wait</span></span>|<span data-ttu-id="d9981-152">Sant</span><span class="sxs-lookup"><span data-stu-id="d9981-152">True</span></span>|
    |<span data-ttu-id="d9981-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="d9981-153">PSComputerName</span></span>|<span data-ttu-id="d9981-154">{""}</span><span class="sxs-lookup"><span data-stu-id="d9981-154">{""}</span></span>|

13. <span data-ttu-id="d9981-155">Lägg till en **GetWmiObject** -aktivitet i **JoinDomain** -sekvensen efter **RestartComputer** -aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="d9981-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="d9981-156">Redigera egenskaperna så att de är samma som föregående **GetWmiObject** -aktivitet.</span><span class="sxs-lookup"><span data-stu-id="d9981-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="d9981-157">När du är färdig med procedurerna bör fönstret arbets flödes design se ut så här.</span><span class="sxs-lookup"><span data-stu-id="d9981-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="d9981-158">![JoinDomain XAML i Workflow Designer ](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
     ![JoinDomain XAML i arbetsflödesdesignern](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="d9981-158">![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span></span>
