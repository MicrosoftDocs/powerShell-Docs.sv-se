---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Modellen objekthierarkin ISE
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="ec265-103">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="ec265-103">The ISE Object Model Hierarchy</span></span>
<span data-ttu-id="ec265-104">Det här avsnittet visar hierarkin med objekt som är en del av Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="ec265-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="ec265-105">Windows PowerShell ISE ingår i Windows PowerShell 3.0 och Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="ec265-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="ec265-106">Klicka på ett objekt för att ta dig till referensdokumentationen för den klass som definierar objektet.</span><span class="sxs-lookup"><span data-stu-id="ec265-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="ec265-107">$psISE objekt</span><span class="sxs-lookup"><span data-stu-id="ec265-107">$psISE Object</span></span>

<span data-ttu-id="ec265-108">Den **$psISE** objektet är den [rotobjektet](The-ObjectModelRoot-Object.md) i hierarkin för Windows PowerShell ISE-objektet.</span><span class="sxs-lookup"><span data-stu-id="ec265-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="ec265-109">Finns på den översta nivån är följande objekt tillgängliga för skript:</span><span class="sxs-lookup"><span data-stu-id="ec265-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="ec265-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="ec265-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="ec265-111">Den **$psISE.CurrentFile** objekt är en instans av den [ISEFile](The-ISEFile-Object.md) klass.</span><span class="sxs-lookup"><span data-stu-id="ec265-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="ec265-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="ec265-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="ec265-113">Den **$psISE.CurrentPowerShellTab** objekt är en instans av den [PowerShellTab](The-PowerShellTab-Object.md) klass.</span><span class="sxs-lookup"><span data-stu-id="ec265-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="ec265-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="ec265-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="ec265-115">Den **$psISE.CurrentVisibleHorizontalTool** objekt är en instans av den [ISEAddOnTool](The-ISEAddOnTool-Object.md) klass.</span><span class="sxs-lookup"><span data-stu-id="ec265-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="ec265-116">Verktyget installerat tillägg som för närvarande är dockad representerar mot överkanten i fönstret Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ec265-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="ec265-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="ec265-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="ec265-118">Den **$psISE.CurrentVisibleHorizontalTool** objekt är en instans av den [ISEAddOnTool](The-ISEAddOnTool-Object.md) klass.</span><span class="sxs-lookup"><span data-stu-id="ec265-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="ec265-119">Verktyget installerat tillägg som för närvarande är dockad representerar fönstret Windows PowerShell ISE högra kant.</span><span class="sxs-lookup"><span data-stu-id="ec265-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="ec265-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="ec265-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="ec265-121">Den **$psISE.Options** objekt är en instans av den [ISEOptions](The-ISEOptions-Object.md) klass.</span><span class="sxs-lookup"><span data-stu-id="ec265-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="ec265-122">ISEOptions-objektet representerar olika inställningar för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ec265-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="ec265-123">Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="ec265-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="ec265-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="ec265-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="ec265-125">Den **$psISE.PowerShellTabs** objekt är en instans av den [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klass.</span><span class="sxs-lookup"><span data-stu-id="ec265-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="ec265-126">Det är en samling av alla öppna PowerShell flikar som representerar tillgängliga Windows PowerShell kör miljöer på den lokala datorn eller på anslutna fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="ec265-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="ec265-127">Varje medlem i samlingen är en instans av den [PowerShellTab](The-PowerShellTab-Object.md) klass.</span><span class="sxs-lookup"><span data-stu-id="ec265-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec265-128">Se även</span><span class="sxs-lookup"><span data-stu-id="ec265-128">See Also</span></span>
- [<span data-ttu-id="ec265-129">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="ec265-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ec265-130">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="ec265-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
