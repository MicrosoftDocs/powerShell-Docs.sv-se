---
title: Skapa ett arbetsflöde med Windows PowerShell aktiviteter | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080450"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="90a15-102">Skapa ett arbetsflöde med Windows PowerShell-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="90a15-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="90a15-103">Du kan skapa ett Windows PowerShell-arbetsflöde genom att välja aktiviteter i verktygslådan för Visual Studio och dra dem till Workflow Designer-fönstret.</span><span class="sxs-lookup"><span data-stu-id="90a15-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="90a15-104">Information om att lägga till Windows PowerShell-aktiviteter i verktygslådan för Visual Studio finns i [att lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="90a15-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="90a15-105">Följande procedurer beskriver hur du skapar ett arbetsflöde som kontrollerar domänen för en grupp användardefinierade datorer och kopplar dem till en domän om de inte redan är ansluten och kontrollerar status igen.</span><span class="sxs-lookup"><span data-stu-id="90a15-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="90a15-106">Konfigurera projektet</span><span class="sxs-lookup"><span data-stu-id="90a15-106">Setting up the Project</span></span>

1. <span data-ttu-id="90a15-107">Följ proceduren i [att lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) att skapa ett arbetsflöde-projekt och lägga till aktiviteter från den [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) och [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) sammansättningar i verktygslådan.</span><span class="sxs-lookup"><span data-stu-id="90a15-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="90a15-108">Lägg till System.Management.Automation, Microsoft.PowerShell.Activities, av System.Management, Microsoft.PowerShell.Management.Activities och Microsoft.PowerShell.Commands.Management om projektet som referenssammansättningar.</span><span class="sxs-lookup"><span data-stu-id="90a15-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="90a15-109">Att lägga till aktiviteter i arbetsflödet</span><span class="sxs-lookup"><span data-stu-id="90a15-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="90a15-110">Lägg till en **sekvens** aktivitet i arbetsflödet.</span><span class="sxs-lookup"><span data-stu-id="90a15-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="90a15-111">Skapa ett argument som heter `ComputerName` med ett argument av typen `String[]`.</span><span class="sxs-lookup"><span data-stu-id="90a15-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="90a15-112">Det här argumentet representerar namnen på datorerna för att kontrollera och ansluta till.</span><span class="sxs-lookup"><span data-stu-id="90a15-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="90a15-113">Skapa ett argument som heter `DomainCred` av typen [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="90a15-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="90a15-114">Det här argumentet representerar domänautentiseringsuppgifter för ett domänkonto som har behörighet att ansluta en dator till domänen.</span><span class="sxs-lookup"><span data-stu-id="90a15-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="90a15-115">Skapa ett argument som heter `MachineCred` av typen [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="90a15-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="90a15-116">Det här argumentet representerar autentiseringsuppgifter för administratör på datorerna för att kontrollera och ansluta till.</span><span class="sxs-lookup"><span data-stu-id="90a15-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="90a15-117">Lägg till en **ParallelForEach** aktivitet i den **sekvens** aktivitet.</span><span class="sxs-lookup"><span data-stu-id="90a15-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="90a15-118">Ange `comp` och `ComputerName` i textrutor så att loopen upprepas elementen i den `ComputerName` matris.</span><span class="sxs-lookup"><span data-stu-id="90a15-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="90a15-119">Lägg till en **sekvens** aktivitet och i brödtexten för den **ParallelForEach** aktivitet.</span><span class="sxs-lookup"><span data-stu-id="90a15-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="90a15-120">Ange den **DisplayName** egenskapen för aktivitetssekvensen ska `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="90a15-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="90a15-121">Lägg till en **GetWmiObject** aktivitet för att den **JoinDomain** sekvens.</span><span class="sxs-lookup"><span data-stu-id="90a15-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="90a15-122">Redigera egenskaperna för den **GetWmiObject** aktivitet på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="90a15-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="90a15-123">Egenskap</span><span class="sxs-lookup"><span data-stu-id="90a15-123">Property</span></span>|<span data-ttu-id="90a15-124">Värde</span><span class="sxs-lookup"><span data-stu-id="90a15-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="90a15-125">**Klass**</span><span class="sxs-lookup"><span data-stu-id="90a15-125">**Class**</span></span>|<span data-ttu-id="90a15-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="90a15-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="90a15-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="90a15-127">**PSComputerName**</span></span>|<span data-ttu-id="90a15-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="90a15-128">{comp}</span></span>|
   |<span data-ttu-id="90a15-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="90a15-129">**PSCredential**</span></span>|<span data-ttu-id="90a15-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="90a15-130">MachineCred</span></span>|

9. <span data-ttu-id="90a15-131">Lägg till en **AddComputer** aktivitet för att den **JoinDomain** aktivitetssekvensen efter den **GetWmiObject** aktivitet.</span><span class="sxs-lookup"><span data-stu-id="90a15-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="90a15-132">Redigera egenskaperna för den **AddComputer** aktivitet på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="90a15-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="90a15-133">Egenskap</span><span class="sxs-lookup"><span data-stu-id="90a15-133">Property</span></span>|<span data-ttu-id="90a15-134">Värde</span><span class="sxs-lookup"><span data-stu-id="90a15-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="90a15-135">**Datornamn**</span><span class="sxs-lookup"><span data-stu-id="90a15-135">**ComputerName**</span></span>|<span data-ttu-id="90a15-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="90a15-136">{comp}</span></span>|
    |<span data-ttu-id="90a15-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="90a15-137">**DomainCredential**</span></span>|<span data-ttu-id="90a15-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="90a15-138">DomainCred</span></span>|

11. <span data-ttu-id="90a15-139">Lägg till en **RestartComputer** aktivitet för att den **JoinDomain** aktivitetssekvensen efter den **AddComputer** aktivitet.</span><span class="sxs-lookup"><span data-stu-id="90a15-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="90a15-140">Redigera egenskaperna för den **RestartComputer** aktivitet på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="90a15-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="90a15-141">Egenskap</span><span class="sxs-lookup"><span data-stu-id="90a15-141">Property</span></span>|<span data-ttu-id="90a15-142">Värde</span><span class="sxs-lookup"><span data-stu-id="90a15-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="90a15-143">**Datornamn**</span><span class="sxs-lookup"><span data-stu-id="90a15-143">**ComputerName**</span></span>|<span data-ttu-id="90a15-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="90a15-144">{comp}</span></span>|
    |<span data-ttu-id="90a15-145">**Autentiseringsuppgifter**</span><span class="sxs-lookup"><span data-stu-id="90a15-145">**Credential**</span></span>|<span data-ttu-id="90a15-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="90a15-146">MachineCred</span></span>|
    |<span data-ttu-id="90a15-147">**för**</span><span class="sxs-lookup"><span data-stu-id="90a15-147">**For**</span></span>|<span data-ttu-id="90a15-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="90a15-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="90a15-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="90a15-149">**Force**</span></span>|<span data-ttu-id="90a15-150">Sant</span><span class="sxs-lookup"><span data-stu-id="90a15-150">True</span></span>|
    |<span data-ttu-id="90a15-151">Vänta</span><span class="sxs-lookup"><span data-stu-id="90a15-151">Wait</span></span>|<span data-ttu-id="90a15-152">Sant</span><span class="sxs-lookup"><span data-stu-id="90a15-152">True</span></span>|
    |<span data-ttu-id="90a15-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="90a15-153">PSComputerName</span></span>|<span data-ttu-id="90a15-154">{""}</span><span class="sxs-lookup"><span data-stu-id="90a15-154">{""}</span></span>|

13. <span data-ttu-id="90a15-155">Lägg till en **GetWmiObject** aktivitet för att den **JoinDomain** aktivitetssekvensen efter den **RestartComputer** aktivitet.</span><span class="sxs-lookup"><span data-stu-id="90a15-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="90a15-156">Redigera dess egenskaper för att vara samma som föregående **GetWmiObject** aktivitet.</span><span class="sxs-lookup"><span data-stu-id="90a15-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="90a15-157">När du är klar med följande arbetsflöde design-fönstret bör se ut så här.</span><span class="sxs-lookup"><span data-stu-id="90a15-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="90a15-158">![JoinDomain XAML i arbetsflödesdesigner](../media/joindomainworkflow.png)
    ![JoinDomain XAML i arbetsflödesdesigner](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="90a15-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>