---
ms.date: 09/13/2016
ms.topic: reference
title: Lägga till en cmdlet-beskrivning
description: Lägga till en cmdlet-beskrivning
ms.openlocfilehash: 08d21a281881678423bbe3c382279875ed2868db
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651216"
---
# <a name="how-to-add-a-cmdlet-description"></a>Lägga till en cmdlet-beskrivning

I det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnittet **Beskrivning** i cmdlet-hjälpen. I Hjälp filen läggs det här innehållet till i **kommando** -noden för varje cmdlet.

> [!NOTE]
> Om du vill se en fullständig vy över en hjälpfil öppnar du en av `dll-Help.xml` filerna som finns i installations katalogen för PowerShell. Filen innehåller till exempel `Microsoft.PowerShell.Commands.Management.dll-Help.xml` innehåll för flera av PowerShell-cmdletarna.

### <a name="to-add-a-description"></a>Lägga till en beskrivning

- Börja med att förklara de grundläggande funktionerna i cmdleten mer detaljerat. I många fall kan du förklara de termer som används i cmdlet-namnet och illustrera okända begrepp med ett exempel. Om till exempel cmdleten lägger till data i en fil, förklarar du att den lägger till data i slutet av en befintlig fil.

- Om du vill hitta alla funktioner i cmdleten granskar du parameter listan. Beskriv den primära funktionen i cmdleten och ta sedan med andra funktioner och funktioner. Om till exempel huvud funktionen för cmdlet: en är att ändra en egenskap, men cmdleten kan ändra alla egenskaper, så i den detaljerade beskrivningen. Om cmdlet-parametrarna gör det möjligt för användarna att begära information på olika sätt, förklarar du det.

- Ta med information om hur användarna kan använda cmdleten, förutom den uppenbara användningen. Du kan till exempel använda objektet som `Get-Host` cmdleten hämtar för att ändra färg på text i Windows PowerShell-kommando fönstret.

  Exempel: " `Get-Acl` cmdleten hämtar objekt som representerar säkerhets beskrivningen för en fil eller resurs. Säkerhets beskrivningen innehåller åtkomst kontrol listorna (ACL) för resursen. ACL: en anger de behörigheter som användare och användar grupper har åtkomst till resursen. "

- Den detaljerade beskrivningen ska beskriva cmdleten, men den bör inte beskriva de begrepp som cmdleten använder. Placera koncept definitioner i ytterligare anteckningar.

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
