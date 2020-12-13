---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell-sessionstillstånd
description: Windows PowerShell-sessionstillstånd
ms.openlocfilehash: 51de92f1f392f708cf49c7ccb4a6808fd628076c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668141"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="300bf-103">Windows PowerShell-sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="300bf-103">Windows PowerShell Session State</span></span>

<span data-ttu-id="300bf-104">Sessionstillstånd refererar till den aktuella konfigurationen av en Windows PowerShell-session eller-modul.</span><span class="sxs-lookup"><span data-stu-id="300bf-104">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="300bf-105">En Windows PowerShell-session är den drifts miljö som används interaktivt av kommando rads användaren eller program mässigt av ett värd program.</span><span class="sxs-lookup"><span data-stu-id="300bf-105">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="300bf-106">Sessionens tillstånd för en session kallas för det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="300bf-106">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="300bf-107">Från ett utvecklings perspektiv refererar en Windows PowerShell-session till tiden mellan när ett värd program öppnar en Windows PowerShell-körnings utrymme och när körnings utrymme stängs.</span><span class="sxs-lookup"><span data-stu-id="300bf-107">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="300bf-108">På ett annat sätt är sessionen livs längden för en instans av Windows PowerShell-motorn som anropas medan körnings utrymme finns.</span><span class="sxs-lookup"><span data-stu-id="300bf-108">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="300bf-109">Sessionstillstånd för modul</span><span class="sxs-lookup"><span data-stu-id="300bf-109">Module Session State</span></span>

<span data-ttu-id="300bf-110">Sessionstillstånd för modulen skapas när modulen eller en av dess kapslade moduler importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="300bf-110">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="300bf-111">När en modul exporterar ett element, till exempel en cmdlet, en funktion eller ett skript, läggs en referens till det elementet till i sessionens globala sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="300bf-111">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="300bf-112">Men när elementet körs körs det inom modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="300bf-112">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="300bf-113">Session-State data</span><span class="sxs-lookup"><span data-stu-id="300bf-113">Session-State Data</span></span>

<span data-ttu-id="300bf-114">Session State-data kan vara offentliga eller privata.</span><span class="sxs-lookup"><span data-stu-id="300bf-114">Session state data can be public or private.</span></span> <span data-ttu-id="300bf-115">Offentliga data är tillgängliga för anrop från utanför sessionstillståndet, medan privata data bara är tillgängliga för anrop inifrån sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="300bf-115">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="300bf-116">En modul kan till exempel ha en privat funktion som bara kan anropas av modulen eller bara internt av ett offentligt element som har exporter ATS.</span><span class="sxs-lookup"><span data-stu-id="300bf-116">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="300bf-117">Detta liknar privata och offentliga medlemmar av en .NET Framework typ.</span><span class="sxs-lookup"><span data-stu-id="300bf-117">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="300bf-118">Data för sessionstillstånd lagras av den aktuella instansen av körnings motorn inom kontexten för den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="300bf-118">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="300bf-119">Data för sessionstillstånd består av följande objekt:</span><span class="sxs-lookup"><span data-stu-id="300bf-119">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="300bf-120">Sök vägs information</span><span class="sxs-lookup"><span data-stu-id="300bf-120">Path information</span></span>

- <span data-ttu-id="300bf-121">Enhets information</span><span class="sxs-lookup"><span data-stu-id="300bf-121">Drive information</span></span>

- <span data-ttu-id="300bf-122">Information om Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="300bf-122">Windows PowerShell provider information</span></span>

- <span data-ttu-id="300bf-123">Information om importerade moduler och referenser till modulens element (till exempel cmdlets, Functions och scripts) som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="300bf-123">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="300bf-124">Den här informationen och dessa referenser gäller endast för det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="300bf-124">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="300bf-125">Variabel information för sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="300bf-125">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="300bf-126">Åtkomst till Session-State data inom cmdletar</span><span class="sxs-lookup"><span data-stu-id="300bf-126">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="300bf-127">-Cmdletar har åtkomst till sessionstillstånd antingen indirekt via egenskapen [system. Management. Automation. PSCmdlet. sessionState \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) för cmdlet-klassen eller direkt via klassen [system. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) .</span><span class="sxs-lookup"><span data-stu-id="300bf-127">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="300bf-128">Klassen [system. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) innehåller egenskaper som kan användas för att undersöka olika typer av sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="300bf-128">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="300bf-129">Se även</span><span class="sxs-lookup"><span data-stu-id="300bf-129">See Also</span></span>

[<span data-ttu-id="300bf-130">System. Management. Automation. PSCmdlet. sessionState</span><span class="sxs-lookup"><span data-stu-id="300bf-130">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="300bf-131">System. Management. Automation. sessionState? Displayproperty = FullName</span><span class="sxs-lookup"><span data-stu-id="300bf-131">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="300bf-132">Windows PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="300bf-132">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="300bf-133">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="300bf-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="300bf-134">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="300bf-134">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
