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
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Lägga till Windows PowerShell-aktiviteter till Visual Studio Toolbox

Innan du skapar ett PowerShell-arbetsflöde med Workflow Designer måste du först lägga till PowerShell-aktiviteter i verktygslådan i ett arbetsflöde för Visual Studio-konsolprogramprojekt. Följande procedur visar hur du lägger till aktiviteter från Microsoft.PowerShell.Core.Activities-sammansättningen i Visual Studio-verktygslådan.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Att lägga till Windows PowerShell-aktiviteter i verktygslådan

1. Skapa ett nytt arbetsflöde konsolprogramprojektet i Visual Studio.

2. På den **visa** -menyn klickar du på **verktygslådan**.

3. Lägg till en ny flik i verktygslådan genom att högerklicka någonstans i verktygslådan och klicka på **lägger du till fliken**, och ge den nya fliken ett namn, till exempel ”PowerShell aktiviteter”.

   Att lägga till en flik kan du gruppera de PowerShell-aktiviteter som är separat från andra verktyg i verktygslådan.

4. På fliken nya verktygslådan **Välj objekt...** . Den **väljer verktygslådan objekt** dialogruta.

5. I den **väljer verktygslådan objekt** dialogrutan klickar du på den **System.Activities** fliken.

6. Klicka på **Bläddra**.

7. Navigera till mappen %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e och dubbelklicka på Microsoft.PowerShell.Core.Activities.dll.

8. Klicka på **OK**. De aktiviteter som definierats av Microsoft.PowerShell.Core.Activities-sammansättningen är nu tillgängliga i verktygslådan.

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-arbetsflöde](./writing-a-windows-powershell-workflow.md)

[Skapa ett arbetsflöde med Windows PowerShell-aktiviteter](./creating-a-workflow-with-windows-powershell-activities.md)