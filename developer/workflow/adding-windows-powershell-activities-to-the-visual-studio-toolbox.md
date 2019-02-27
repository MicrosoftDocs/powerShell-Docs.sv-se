---
title: Att lägga till Windows PowerShell-aktiviteter i verktygslådan Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852110"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="b8fb9-102">Lägga till Windows PowerShell-aktiviteter till Visual Studio Toolbox</span><span class="sxs-lookup"><span data-stu-id="b8fb9-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="b8fb9-103">Innan du skapar ett PowerShell-arbetsflöde med Workflow Designer måste du först lägga till PowerShell-aktiviteter i verktygslådan i ett arbetsflöde för Visual Studio-konsolprogramprojekt.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="b8fb9-104">Följande procedur visar hur du lägger till aktiviteter från Microsoft.PowerShell.Core.Activities-sammansättningen i Visual Studio-verktygslådan.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="b8fb9-105">Att lägga till Windows PowerShell-aktiviteter i verktygslådan</span><span class="sxs-lookup"><span data-stu-id="b8fb9-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="b8fb9-106">Skapa ett nytt arbetsflöde konsolprogramprojektet i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="b8fb9-107">På den **visa** -menyn klickar du på **verktygslådan**.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="b8fb9-108">Lägg till en ny flik i verktygslådan genom att högerklicka någonstans i verktygslådan och klicka på **lägger du till fliken**, och ge den nya fliken ett namn, till exempel ”PowerShell aktiviteter”.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="b8fb9-109">Att lägga till en flik kan du gruppera de PowerShell-aktiviteter som är separat från andra verktyg i verktygslådan.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="b8fb9-110">På fliken nya verktygslådan **Välj objekt...** . Den **väljer verktygslådan objekt** dialogruta.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="b8fb9-111">I den **väljer verktygslådan objekt** dialogrutan klickar du på den **System.Activities** fliken.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="b8fb9-112">Klicka på **Bläddra**.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-112">Click **Browse**.</span></span>

7. <span data-ttu-id="b8fb9-113">Navigera till mappen %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e och dubbelklicka på Microsoft.PowerShell.Core.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="b8fb9-114">Klicka på **OK**.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-114">Click **OK**.</span></span> <span data-ttu-id="b8fb9-115">De aktiviteter som definierats av Microsoft.PowerShell.Core.Activities-sammansättningen är nu tillgängliga i verktygslådan.</span><span class="sxs-lookup"><span data-stu-id="b8fb9-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8fb9-116">Se även</span><span class="sxs-lookup"><span data-stu-id="b8fb9-116">See Also</span></span>

[<span data-ttu-id="b8fb9-117">Skriva ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="b8fb9-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="b8fb9-118">Skapa ett arbetsflöde med Windows PowerShell-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="b8fb9-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)