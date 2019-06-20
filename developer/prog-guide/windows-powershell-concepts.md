---
title: Windows PowerShell-koncept | Microsoft Docs
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263862"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="d5c39-102">Begrepp relaterade till Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5c39-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="d5c39-103">Det här avsnittet innehåller begreppsrelaterad information som hjälper dig förstå PowerShell från en utvecklare synvinkel.</span><span class="sxs-lookup"><span data-stu-id="d5c39-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="d5c39-104">Ämnesnamn</span><span class="sxs-lookup"><span data-stu-id="d5c39-104">Topic Name</span></span>|<span data-ttu-id="d5c39-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d5c39-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="d5c39-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="d5c39-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="d5c39-107">Beskrivning av PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="d5c39-107">Description of PowerShell objects.</span></span> <span data-ttu-id="d5c39-108">Mer information finns i [om Objektskapande](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="d5c39-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="d5c39-109">Skapa Körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="d5c39-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="d5c39-110">Av driftmiljöerna där kommandon bearbetas.</span><span class="sxs-lookup"><span data-stu-id="d5c39-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="d5c39-111">Mer information finns i [Körningsutrymme klass](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="d5c39-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="d5c39-112">Utöka utdata objekt</span><span class="sxs-lookup"><span data-stu-id="d5c39-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="d5c39-113">Hur du utökar PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="d5c39-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="d5c39-114">Mer information finns i [om Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="d5c39-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="d5c39-115">Registrera cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="d5c39-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="d5c39-116">Hur du gör moduler och snapin-moduler som är tillgängliga i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5c39-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="d5c39-117">Mer information finns i [moduler och snapin-moduler](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="d5c39-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="d5c39-118">Begär bekräftelse från cmdletar</span><span class="sxs-lookup"><span data-stu-id="d5c39-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="d5c39-119">Hur cmdlets och providers begäran feedback till användaren innan en åtgärd utförs.</span><span class="sxs-lookup"><span data-stu-id="d5c39-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="d5c39-120">RuntimeDefinedParameter-klass</span><span class="sxs-lookup"><span data-stu-id="d5c39-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="d5c39-121">Runtime-parameterdeklarationer.</span><span class="sxs-lookup"><span data-stu-id="d5c39-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="d5c39-122">System.Management.Automation Namespace</span><span class="sxs-lookup"><span data-stu-id="d5c39-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="d5c39-123">Översikt över PowerShell-API-namnområdena.</span><span class="sxs-lookup"><span data-stu-id="d5c39-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="d5c39-124">Översikt för Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="d5c39-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="d5c39-125">Översikt över hur PowerShell-providers som används för att komma åt data lagras.</span><span class="sxs-lookup"><span data-stu-id="d5c39-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="d5c39-126">Skriva hjälp för PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="d5c39-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="d5c39-127">Hur du skriver hjälp för PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5c39-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d5c39-128">Se även</span><span class="sxs-lookup"><span data-stu-id="d5c39-128">See also</span></span>

[<span data-ttu-id="d5c39-129">PowerShell-klass</span><span class="sxs-lookup"><span data-stu-id="d5c39-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="d5c39-130">PowerShell Core API-referens</span><span class="sxs-lookup"><span data-stu-id="d5c39-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="d5c39-131">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5c39-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d5c39-132">Skrivhjälp för Windows PowerShell-moduler</span><span class="sxs-lookup"><span data-stu-id="d5c39-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="d5c39-133">Skriva ett Windows Powershell-providern</span><span class="sxs-lookup"><span data-stu-id="d5c39-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="d5c39-134">API-referens för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5c39-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="d5c39-135">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="d5c39-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)