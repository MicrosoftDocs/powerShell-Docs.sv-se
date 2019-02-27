---
title: Hur du lägger till en beskrivning för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851431"
---
# <a name="how-to-add-a-cmdlet-description"></a>Lägga till en cmdlet-beskrivning

Det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnittet beskrivning i cmdlet-hjälpen. Det här innehållet har lagts till noden kommando för varje cmdlet i hjälpfilen.

> [!NOTE]
> För en fullständig överblick över en hjälpfilen, öppna en av dll-Help.xml-filerna finns i installationskatalogen för Windows PowerShell. Till exempel innehåller filen Microsoft.PowerShell.Commands.Management.dll Help.xml innehåll för flera av Windows PowerShell-cmdlets.

### <a name="to-add-a-description"></a>Att lägga till en beskrivning

- Börja genom att förklara de grundläggande funktionerna i cmdlet: en i detalj. I många fall kan du förklara termer som används i cmdlet-namn och illustrera begrepp som är bekant med ett exempel. Om cmdlet: en lägger till data till en fil, till exempel, förklara det lägger till data i slutet av en befintlig fil.

- Granska listan över för att hitta alla funktioner i cmdleten. Beskriver den främsta uppgiften för cmdlet: en och sedan inkludera andra funktioner och funktioner. Anta exempelvis att om Huvudsyftet med cmdlet: en är att ändra en egenskap, men cmdlet: en kan ändra alla egenskaper, så i den detaljerade beskrivningen. Om cmdlet-parametrarna låter användarna begära information på olika sätt, förklara det.

- Innehåller information om hur användare kan använda cmdlet: en, förutom uppenbara används. Du kan till exempel använda objektet som den `Get-Host` cmdlet: en hämtar om du vill ändra färgen på texten i Windows PowerShell-kommandofönster.

  Exempel:  ”Den `Get-Acl` cmdlet hämtar objekt som representerar säkerhetsbeskrivningen för en fil eller resurs. Säkerhetsbeskrivningen innehåller åtkomstkontrollistor (ACL) för resursen. ACL: Anger de behörigheter som användare och användargrupper som har åtkomst till resursen ”.

- Den detaljerade beskrivningen bör beskriva cmdleten, men det bör inte beskriver begrepp som använder cmdlet: en. Placera konceptet definitioner i ytterligare information.

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
