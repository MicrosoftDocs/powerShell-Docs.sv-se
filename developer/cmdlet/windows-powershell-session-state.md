---
title: Windows PowerShell-sessionstillstånd | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: 5d4effb508c9f2544832dad557671520cb0a7ac7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851704"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="b5f23-102">Windows PowerShell-sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="b5f23-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="b5f23-103">Sessionstillstånd refererar till den aktuella konfigurationen för en Windows PowerShell-session eller modulen.</span><span class="sxs-lookup"><span data-stu-id="b5f23-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="b5f23-104">En Windows PowerShell-session är den driftsmiljö som ska användas interaktivt av kommandoradsverktyget användaren eller via programmering med ett program.</span><span class="sxs-lookup"><span data-stu-id="b5f23-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="b5f23-105">Sessionstillstånd för en session kallas för det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="b5f23-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="b5f23-106">En Windows PowerShell-session avser tiden mellan när en värdapp öppnas en Windows PowerShell-körningsutrymme och när den stängs körningsutrymmet från en utvecklares perspektiv.</span><span class="sxs-lookup"><span data-stu-id="b5f23-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="b5f23-107">Sessionen är har tittat på ett annat sätt, livslängden för en instans av Windows PowerShell-motorn som anropas när körningsutrymmet finns.</span><span class="sxs-lookup"><span data-stu-id="b5f23-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="b5f23-108">Modulen sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="b5f23-108">Module Session State</span></span>

<span data-ttu-id="b5f23-109">Modulen sessionstillstånd skapas när modulen eller något av dess kapslade moduler importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="b5f23-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="b5f23-110">När en modul exporterar ett element, till exempel en cmdlet, en funktion eller ett skript, läggs en referens till det elementet till det globala sessionstillståndet sessionen.</span><span class="sxs-lookup"><span data-stu-id="b5f23-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="b5f23-111">När elementet körs, är det köras inom sessionstillstånd i modulen.</span><span class="sxs-lookup"><span data-stu-id="b5f23-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="b5f23-112">Sessionslägesdata</span><span class="sxs-lookup"><span data-stu-id="b5f23-112">Session-State Data</span></span>

<span data-ttu-id="b5f23-113">Sessionstillståndet anger data kan vara offentliga eller privata.</span><span class="sxs-lookup"><span data-stu-id="b5f23-113">Session state data can be public or private.</span></span> <span data-ttu-id="b5f23-114">Offentliga data är tillgängliga för anrop från utanför sessionstillståndet medan privata data är endast tillgängligt för inifrån sessionens tillstånd.</span><span class="sxs-lookup"><span data-stu-id="b5f23-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="b5f23-115">En modul kan till exempel ha en privat-funktion som kan anropas endast av modulen eller endast internt av en offentlig elementet som har exporterats.</span><span class="sxs-lookup"><span data-stu-id="b5f23-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="b5f23-116">Detta liknar de privata och offentliga medlemmarna av en .NET Framework-typen.</span><span class="sxs-lookup"><span data-stu-id="b5f23-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="b5f23-117">Sessionstillståndsdata lagras av den aktuella instansen av motorn för körning inom ramen för den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b5f23-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="b5f23-118">Sessionslägesdata består av följande objekt:</span><span class="sxs-lookup"><span data-stu-id="b5f23-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="b5f23-119">Information om sökvägen</span><span class="sxs-lookup"><span data-stu-id="b5f23-119">Path information</span></span>

- <span data-ttu-id="b5f23-120">Enhetsinformationen</span><span class="sxs-lookup"><span data-stu-id="b5f23-120">Drive information</span></span>

- <span data-ttu-id="b5f23-121">Information om Windows PowerShell-provider</span><span class="sxs-lookup"><span data-stu-id="b5f23-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="b5f23-122">Information om de importerade moduler och referenser till modulen elementen (till exempel-cmdlet: ar, funktioner och skript) som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="b5f23-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="b5f23-123">Den här informationen och dessa referenser är för endast globala sessionens tillstånd.</span><span class="sxs-lookup"><span data-stu-id="b5f23-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="b5f23-124">Sessionstillstånd Variabelinformation</span><span class="sxs-lookup"><span data-stu-id="b5f23-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="b5f23-125">Åtkomst till sessionslägesdata lagras i cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="b5f23-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="b5f23-126">Cmdlet: ar kan få åtkomst till sessionslägesdata lagras antingen indirekt, via den [System.Management.Automation.Pscmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) egenskap i klassen cmdlet eller direkt via den [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klass.</span><span class="sxs-lookup"><span data-stu-id="b5f23-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.Pscmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="b5f23-127">Den [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klassen innehåller egenskaper som kan användas för att undersöka olika typer av sessionstillståndsdata.</span><span class="sxs-lookup"><span data-stu-id="b5f23-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5f23-128">Se även</span><span class="sxs-lookup"><span data-stu-id="b5f23-128">See Also</span></span>

[<span data-ttu-id="b5f23-129">System.Management.Automation.Pscmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="b5f23-129">System.Management.Automation.Pscmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="b5f23-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="b5f23-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="b5f23-131">Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b5f23-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="b5f23-132">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b5f23-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="b5f23-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="b5f23-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
