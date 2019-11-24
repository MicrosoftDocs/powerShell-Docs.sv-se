---
title: Användare som begär bekräftelse | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359155"
---
# <a name="users-requesting-confirmation"></a>Användare som begär bekräftelse

När du anger ett värde för `true` för `SupportsShouldProcess`-parametern för cmdlet-attributets deklaration, kan användarna ange `Confirm`-parametern i kommando tolken.

I Standard miljön kan användare ange `Confirm` parameter eller `"-Confirm:$true` så att en bekräftelse begärs när metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas. Detta kringgår [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bekräftelse förfrågningar, även för åtgärder med hög påverkan.

Om `Confirm` inte anges bekräftar [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anrops begär Anden om inställningen `$ConfirmPreference` är lika med eller större än `ConfirmImpact` inställningen för cmdleten eller providern. Standardinställningen för `$ConfirmPreference` är hög. I Standard miljön är det därför bara-cmdletar och-providers som anger en bekräftelse av åtgärden som kräver hög påverkan.

Om `Confirm` är falskt eller om `"-Confirm:$false` anges, begär [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) förfrågningar från användaren och `$ConfirmPreference` Shell-variabeln ignoreras.

## <a name="remarks"></a>Kommentarer

- För cmdlets och providers som anger `SupportsShouldProcess`, men inte `ConfirmImpact`, hanteras dessa åtgärder som "medelhög påverkan"-åtgärder och de kommer inte att fråga som standard. Deras effekt nivå är mindre än standardinställningen för variabeln `$ConfirmPreference`.

- Om användaren anger parametern `Verbose` kommer de att meddelas om åtgärden även om de inte uppmanas att bekräfta.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
