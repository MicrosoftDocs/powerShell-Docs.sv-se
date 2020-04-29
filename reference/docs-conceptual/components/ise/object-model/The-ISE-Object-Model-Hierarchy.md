---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISE-objektmodellhierarkin
ms.openlocfilehash: 1ec5810fc5e7b765c2a08af83bce0415dd61a54b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737040"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="751ee-103">ISE-objektmodellhierarkin</span><span class="sxs-lookup"><span data-stu-id="751ee-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="751ee-104">I det här avsnittet visas hierarkin för objekt som ingår i Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="751ee-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="751ee-105">Windows PowerShell ISE ingår i Windows PowerShell 3,0, 4,0 och 5,1.</span><span class="sxs-lookup"><span data-stu-id="751ee-105">Windows PowerShell ISE is included in Windows PowerShell 3.0, 4.0, and 5.1.</span></span> <span data-ttu-id="751ee-106">Klicka på ett objekt för att ta dig till referens dokumentationen för den klass som definierar objektet.</span><span class="sxs-lookup"><span data-stu-id="751ee-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="751ee-107">$psISE objekt</span><span class="sxs-lookup"><span data-stu-id="751ee-107">$psISE Object</span></span>

<span data-ttu-id="751ee-108">`$psISE` Objektet är [rotobjektet](The-ObjectModelRoot-Object.md) för den Windows PowerShell ISE Object-hierarkin.</span><span class="sxs-lookup"><span data-stu-id="751ee-108">The `$psISE` object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="751ee-109">På den översta nivån gör den följande objekt tillgängliga för skript:</span><span class="sxs-lookup"><span data-stu-id="751ee-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfile"></a>[<span data-ttu-id="751ee-110">$psISE. CurrentFile</span><span class="sxs-lookup"><span data-stu-id="751ee-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="751ee-111">`$psISE.CurrentFile` Objektet är en instans av klassen [ISEFile](The-ISEFile-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="751ee-111">The `$psISE.CurrentFile` object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltab"></a>[<span data-ttu-id="751ee-112">$psISE. CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="751ee-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="751ee-113">`$psISE.CurrentPowerShellTab` Objektet är en instans av klassen [PowerShellTab](The-PowerShellTab-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="751ee-113">The `$psISE.CurrentPowerShellTab` object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="751ee-114">$psISE. CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="751ee-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="751ee-115">`$psISE.CurrentVisibleHorizontalTool` Objektet är en instans av klassen [ISEAddOnTool](The-ISEAddOnTool-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="751ee-115">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="751ee-116">Den representerar det installerade tilläggs verktyget som för närvarande är dockat till den övre kanten i Windows PowerShell ISEs fönstret.</span><span class="sxs-lookup"><span data-stu-id="751ee-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="751ee-117">$psISE. CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="751ee-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="751ee-118">`$psISE.CurrentVisibleHorizontalTool` Objektet är en instans av klassen [ISEAddOnTool](The-ISEAddOnTool-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="751ee-118">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="751ee-119">Den representerar det installerade tilläggs verktyget som för närvarande är dockat till den högra kanten i Windows PowerShell ISEs fönstret.</span><span class="sxs-lookup"><span data-stu-id="751ee-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptions"></a>[<span data-ttu-id="751ee-120">$psISE. alternativ</span><span class="sxs-lookup"><span data-stu-id="751ee-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="751ee-121">`$psISE.Options` Objektet är en instans av klassen [ISEOptions](The-ISEOptions-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="751ee-121">The `$psISE.Options` object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span> <span data-ttu-id="751ee-122">Objektet ISEOptions representerar olika inställningar för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="751ee-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="751ee-123">Det är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="751ee-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabs"></a>[<span data-ttu-id="751ee-124">$psISE. PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="751ee-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="751ee-125">`$psISE.PowerShellTabs` Objektet är en instans av klassen [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="751ee-125">The `$psISE.PowerShellTabs` object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="751ee-126">Det är en samling av alla öppna PowerShell-flikar som representerar de tillgängliga Windows PowerShell-körnings miljöerna på den lokala datorn eller på anslutna fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="751ee-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="751ee-127">Varje medlem i samlingen är en instans av klassen [PowerShellTab](The-PowerShellTab-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="751ee-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="751ee-128">Se även</span><span class="sxs-lookup"><span data-stu-id="751ee-128">See Also</span></span>

- [<span data-ttu-id="751ee-129">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="751ee-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="751ee-130">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="751ee-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
