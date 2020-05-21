---
title: Lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: ecd23d3eb722137bdda0498fc71e0e966c57a589
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561197"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="2a65c-102">Lägga till Windows PowerShell-aktiviteter till Visual Studio Toolbox</span><span class="sxs-lookup"><span data-stu-id="2a65c-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="2a65c-103">Innan du skapar ett PowerShell-arbetsflöde med hjälp av arbetsflödesdesigner måste du först lägga till PowerShell-aktiviteter i verktygs lådan i ett program projekt i Visual Studio Workflow Console.</span><span class="sxs-lookup"><span data-stu-id="2a65c-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="2a65c-104">Följande procedur visar hur du lägger till aktiviteter från sammansättningen Microsoft. PowerShell. Core. Activities i Visual Studio-verktygslådan.</span><span class="sxs-lookup"><span data-stu-id="2a65c-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="2a65c-105">Lägga till Windows PowerShell-aktiviteter i verktygs lådan</span><span class="sxs-lookup"><span data-stu-id="2a65c-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="2a65c-106">Skapa ett nytt program projekt i arbets flödes konsolen i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a65c-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="2a65c-107">I menyn **Visa** klickar du på **verktygs låda**.</span><span class="sxs-lookup"><span data-stu-id="2a65c-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="2a65c-108">Lägg till en ny flik i verktygs lådan genom att högerklicka i verktygs lådan och klicka på **fliken Lägg till**och ge den nya fliken ett namn som "PowerShell-aktiviteter".</span><span class="sxs-lookup"><span data-stu-id="2a65c-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="2a65c-109">Genom att lägga till en flik kan du gruppera PowerShell-aktiviteterna separat från andra verktyg i verktygs lådan.</span><span class="sxs-lookup"><span data-stu-id="2a65c-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="2a65c-110">Klicka på Välj objekt på fliken nytt verktygs låda **..**.. Dialog rutan **Välj objekt i verktygs lådan** visas.</span><span class="sxs-lookup"><span data-stu-id="2a65c-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="2a65c-111">I dialog rutan **Välj verktygs objekt** klickar du på fliken **system. Activities** .</span><span class="sxs-lookup"><span data-stu-id="2a65c-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="2a65c-112">Klicka på **Browse** (Bläddra).</span><span class="sxs-lookup"><span data-stu-id="2a65c-112">Click **Browse**.</span></span>

7. <span data-ttu-id="2a65c-113">Gå till mappen%WINDIR%\Microsoft.NET\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e och dubbelklicka på Microsoft. PowerShell. Core. Activities. dll.</span><span class="sxs-lookup"><span data-stu-id="2a65c-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="2a65c-114">Klicka på **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a65c-114">Click **OK**.</span></span> <span data-ttu-id="2a65c-115">Aktiviteterna som definieras av sammansättningen Microsoft. PowerShell. Core. Activities är nu tillgängliga i verktygs lådan.</span><span class="sxs-lookup"><span data-stu-id="2a65c-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a65c-116">Se även</span><span class="sxs-lookup"><span data-stu-id="2a65c-116">See Also</span></span>

[<span data-ttu-id="2a65c-117">Skriva ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="2a65c-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="2a65c-118">Skapa ett arbetsflöde med Windows PowerShell-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="2a65c-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)
