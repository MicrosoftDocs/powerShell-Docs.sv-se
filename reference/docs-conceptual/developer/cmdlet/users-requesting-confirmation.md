---
title: Användare som begär bekräftelse | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f0effb35a110f33248a582fab874e3ab95c7df4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786347"
---
# <a name="users-requesting-confirmation"></a>Användare som begär bekräftelse

När du anger ett värde för `true` `SupportsShouldProcess` parametern för cmdlet-attributets deklaration, kan användarna ange `Confirm` parametern i kommando tolken.

I Standard miljön kan användarna ange `Confirm` parametern eller `"-Confirm:$true` så att bekräftelse begärs när metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas. Detta kringgår [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bekräftelse förfrågningar, även för åtgärder med hög påverkan.

Om `Confirm` inte anges bekräftelser anropen [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) om `$ConfirmPreference` Preference-variabeln är lika med eller större än `ConfirmImpact` inställningen för cmdleten eller providern. Standardinställningen `$ConfirmPreference` är hög. I Standard miljön är det därför bara-cmdletar och-providers som anger en bekräftelse av åtgärden som kräver hög påverkan.

Om `Confirm` har värdet False eller om `"-Confirm:$false` har angetts, begär anropet [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) från användaren och Shell- `$ConfirmPreference` variabeln ignoreras.

## <a name="remarks"></a>Kommentarer

- För-cmdletar och-providers som anger `SupportsShouldProcess` , men inte `ConfirmImpact` , hanteras dessa åtgärder som "medelhög påverkan"-åtgärder och de kommer inte att fråga som standard. Deras effekt nivå är mindre än standardinställningen för `$ConfirmPreference` variabeln Preference.

- Om användaren anger `Verbose` parametern kommer de att meddelas om åtgärden även om de inte behöver bekräftas.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
