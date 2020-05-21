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
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Lägga till Windows PowerShell-aktiviteter till Visual Studio Toolbox

Innan du skapar ett PowerShell-arbetsflöde med hjälp av arbetsflödesdesigner måste du först lägga till PowerShell-aktiviteter i verktygs lådan i ett program projekt i Visual Studio Workflow Console. Följande procedur visar hur du lägger till aktiviteter från sammansättningen Microsoft. PowerShell. Core. Activities i Visual Studio-verktygslådan.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Lägga till Windows PowerShell-aktiviteter i verktygs lådan

1. Skapa ett nytt program projekt i arbets flödes konsolen i Visual Studio.

2. I menyn **Visa** klickar du på **verktygs låda**.

3. Lägg till en ny flik i verktygs lådan genom att högerklicka i verktygs lådan och klicka på **fliken Lägg till**och ge den nya fliken ett namn som "PowerShell-aktiviteter".

   Genom att lägga till en flik kan du gruppera PowerShell-aktiviteterna separat från andra verktyg i verktygs lådan.

4. Klicka på Välj objekt på fliken nytt verktygs låda **..**.. Dialog rutan **Välj objekt i verktygs lådan** visas.

5. I dialog rutan **Välj verktygs objekt** klickar du på fliken **system. Activities** .

6. Klicka på **Browse** (Bläddra).

7. Gå till mappen%WINDIR%\Microsoft.NET\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e och dubbelklicka på Microsoft. PowerShell. Core. Activities. dll.

8. Klicka på **OK**. Aktiviteterna som definieras av sammansättningen Microsoft. PowerShell. Core. Activities är nu tillgängliga i verktygs lådan.

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-arbetsflöde](./writing-a-windows-powershell-workflow.md)

[Skapa ett arbetsflöde med Windows PowerShell-aktiviteter](./creating-a-workflow-with-windows-powershell-activities.md)
