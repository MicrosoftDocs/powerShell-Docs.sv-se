---
title: Sessionstillstånd för Windows PowerShell | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.openlocfilehash: 7436e3ebd0e099ead81f9fea01a0a2994b982213
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783950"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="1dc18-102">Windows PowerShell-sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="1dc18-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="1dc18-103">Sessionstillstånd refererar till den aktuella konfigurationen av en Windows PowerShell-session eller-modul.</span><span class="sxs-lookup"><span data-stu-id="1dc18-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="1dc18-104">En Windows PowerShell-session är den drifts miljö som används interaktivt av kommando rads användaren eller program mässigt av ett värd program.</span><span class="sxs-lookup"><span data-stu-id="1dc18-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="1dc18-105">Sessionens tillstånd för en session kallas för det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="1dc18-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="1dc18-106">Från ett utvecklings perspektiv refererar en Windows PowerShell-session till tiden mellan när ett värd program öppnar en Windows PowerShell-körnings utrymme och när körnings utrymme stängs.</span><span class="sxs-lookup"><span data-stu-id="1dc18-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="1dc18-107">På ett annat sätt är sessionen livs längden för en instans av Windows PowerShell-motorn som anropas medan körnings utrymme finns.</span><span class="sxs-lookup"><span data-stu-id="1dc18-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="1dc18-108">Sessionstillstånd för modul</span><span class="sxs-lookup"><span data-stu-id="1dc18-108">Module Session State</span></span>

<span data-ttu-id="1dc18-109">Sessionstillstånd för modulen skapas när modulen eller en av dess kapslade moduler importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="1dc18-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="1dc18-110">När en modul exporterar ett element, till exempel en cmdlet, en funktion eller ett skript, läggs en referens till det elementet till i sessionens globala sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="1dc18-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="1dc18-111">Men när elementet körs körs det inom modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="1dc18-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="1dc18-112">Data för sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="1dc18-112">Session-State Data</span></span>

<span data-ttu-id="1dc18-113">Session State-data kan vara offentliga eller privata.</span><span class="sxs-lookup"><span data-stu-id="1dc18-113">Session state data can be public or private.</span></span> <span data-ttu-id="1dc18-114">Offentliga data är tillgängliga för anrop från utanför sessionstillståndet, medan privata data bara är tillgängliga för anrop inifrån sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="1dc18-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="1dc18-115">En modul kan till exempel ha en privat funktion som bara kan anropas av modulen eller bara internt av ett offentligt element som har exporter ATS.</span><span class="sxs-lookup"><span data-stu-id="1dc18-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="1dc18-116">Detta liknar privata och offentliga medlemmar av en .NET Framework typ.</span><span class="sxs-lookup"><span data-stu-id="1dc18-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="1dc18-117">Data för sessionstillstånd lagras av den aktuella instansen av körnings motorn inom kontexten för den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="1dc18-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="1dc18-118">Data för sessionstillstånd består av följande objekt:</span><span class="sxs-lookup"><span data-stu-id="1dc18-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="1dc18-119">Sök vägs information</span><span class="sxs-lookup"><span data-stu-id="1dc18-119">Path information</span></span>

- <span data-ttu-id="1dc18-120">Enhets information</span><span class="sxs-lookup"><span data-stu-id="1dc18-120">Drive information</span></span>

- <span data-ttu-id="1dc18-121">Information om Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="1dc18-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="1dc18-122">Information om importerade moduler och referenser till modulens element (till exempel cmdlets, Functions och scripts) som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="1dc18-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="1dc18-123">Den här informationen och dessa referenser gäller endast för det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="1dc18-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="1dc18-124">Variabel information för sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="1dc18-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="1dc18-125">Åtkomst till sessionens tillstånds data inom cmdletar</span><span class="sxs-lookup"><span data-stu-id="1dc18-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="1dc18-126">-Cmdletar har åtkomst till sessionstillstånd antingen indirekt via egenskapen [system. Management. Automation. PSCmdlet. sessionState \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) för cmdlet-klassen eller direkt via klassen [system. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) .</span><span class="sxs-lookup"><span data-stu-id="1dc18-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="1dc18-127">Klassen [system. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) innehåller egenskaper som kan användas för att undersöka olika typer av sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="1dc18-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="1dc18-128">Se även</span><span class="sxs-lookup"><span data-stu-id="1dc18-128">See Also</span></span>

[<span data-ttu-id="1dc18-129">System. Management. Automation. PSCmdlet. sessionState</span><span class="sxs-lookup"><span data-stu-id="1dc18-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="1dc18-130">System. Management. Automation. sessionState? Displayproperty = FullName</span><span class="sxs-lookup"><span data-stu-id="1dc18-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="1dc18-131">Windows PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="1dc18-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="1dc18-132">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="1dc18-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="1dc18-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="1dc18-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
