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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067235"
---
# <a name="users-requesting-confirmation"></a>Användare som begär bekräftelse

När du anger ett värde av `true` för den `SupportsShouldProcess` parametern för cmdleten attributet deklarationen som användarna kan ange den `Confirm` parameter i Kommandotolken.

Användare kan ange i standardmiljön, den `Confirm` parametern eller `"-Confirm:$true` så att bekräftelse begärs när den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoden anropas. Detta kringgår [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bekräftelse begäranden, även för hög inverkan åtgärder.

Om `Confirm` inte anges i [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anrop begär bekräftelse om den `$ConfirmPreference` inställningsvariabeln är lika med eller större än den `ConfirmImpact` inställningen för den cmdlet eller providern. Standardinställningen för `$ConfirmPreference` är hög. Därför i standardmiljön begär endast-cmdlets och providers som anger en hög inverkan åtgärd bekräftelse.

Om `Confirm` är false eller om `"-Confirm:$false` anges den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anrop begär bekräftelse från användaren, och `$ConfirmPreference` gränssnittsvariabeln ignoreras.

## <a name="remarks"></a>Anmärkningar

- För cmdlets och providers som anger `SupportsShouldProcess`, men inte `ConfirmImpact`dessa åtgärder hanteras som ”medelstor inverkan”-åtgärder och de uppmanas inte som standard. Deras inverkan är lägre än standardinställningen för den `$ConfirmPreference` inställningsvariabeln.

- Om användaren anger den `Verbose` parameter, de kommer att meddelas om åtgärden även om de inte uppmanas att bekräfta.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
