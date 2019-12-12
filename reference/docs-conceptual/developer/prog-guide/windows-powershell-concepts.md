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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357101"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="823b6-102">Begrepp relaterade till Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="823b6-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="823b6-103">Det här avsnittet innehåller konceptuell information som hjälper dig att förstå PowerShell från en utvecklares synvinkel.</span><span class="sxs-lookup"><span data-stu-id="823b6-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="823b6-104">Ämnes namn</span><span class="sxs-lookup"><span data-stu-id="823b6-104">Topic Name</span></span>|<span data-ttu-id="823b6-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="823b6-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="823b6-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="823b6-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="823b6-107">Beskrivning av PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="823b6-107">Description of PowerShell objects.</span></span> <span data-ttu-id="823b6-108">Mer information finns i [om att skapa objekt](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="823b6-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="823b6-109">Skapar körnings utrymmen</span><span class="sxs-lookup"><span data-stu-id="823b6-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="823b6-110">De drift miljöer där kommandon bearbetas.</span><span class="sxs-lookup"><span data-stu-id="823b6-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="823b6-111">Mer information finns i [körnings utrymme-klass](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="823b6-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="823b6-112">Utöka utdata-objekt</span><span class="sxs-lookup"><span data-stu-id="823b6-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="823b6-113">Utöka PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="823b6-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="823b6-114">Mer information finns i [About types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="823b6-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="823b6-115">Registrerar cmdletar</span><span class="sxs-lookup"><span data-stu-id="823b6-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="823b6-116">Så här gör du moduler och snapin-moduler tillgängliga i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="823b6-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="823b6-117">Mer information finns i [moduler och snapin-moduler](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="823b6-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="823b6-118">Begär bekräftelse från cmdletar</span><span class="sxs-lookup"><span data-stu-id="823b6-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="823b6-119">Hur cmdlets och providers begär feedback från användaren innan en åtgärd vidtas.</span><span class="sxs-lookup"><span data-stu-id="823b6-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="823b6-120">RuntimeDefinedParameter-klass</span><span class="sxs-lookup"><span data-stu-id="823b6-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="823b6-121">Parameter deklarationer för körning.</span><span class="sxs-lookup"><span data-stu-id="823b6-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="823b6-122">System. Management. Automation-namnrymd</span><span class="sxs-lookup"><span data-stu-id="823b6-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="823b6-123">Översikt över PowerShell API-namnområden.</span><span class="sxs-lookup"><span data-stu-id="823b6-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="823b6-124">Översikt över Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="823b6-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="823b6-125">Översikt över PowerShell-leverantörer som används för att komma åt data lager.</span><span class="sxs-lookup"><span data-stu-id="823b6-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="823b6-126">Skriva hjälp för PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="823b6-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="823b6-127">Så här skriver du PowerShell-cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="823b6-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="823b6-128">Se även</span><span class="sxs-lookup"><span data-stu-id="823b6-128">See also</span></span>

[<span data-ttu-id="823b6-129">PowerShell-klass</span><span class="sxs-lookup"><span data-stu-id="823b6-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="823b6-130">PowerShell Core API-referens</span><span class="sxs-lookup"><span data-stu-id="823b6-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="823b6-131">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="823b6-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="823b6-132">Skriva hjälp för Windows PowerShell-moduler</span><span class="sxs-lookup"><span data-stu-id="823b6-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="823b6-133">Skriva en Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="823b6-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="823b6-134">Windows PowerShell API-referens</span><span class="sxs-lookup"><span data-stu-id="823b6-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="823b6-135">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="823b6-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)