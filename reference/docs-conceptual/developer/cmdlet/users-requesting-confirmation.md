---
ms.date: 09/13/2016
ms.topic: reference
title: Användare som begär bekräftelse
description: Användare som begär bekräftelse
ms.openlocfilehash: 58dbe27635ca38886b728f585fec063645b3597e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646299"
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
