---
title: Så här lägger du till en cmdlet-Beskrivning | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353321"
---
# <a name="how-to-add-a-cmdlet-description"></a>Lägga till en cmdlet-beskrivning

I det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnittet Beskrivning i cmdlet-hjälpen. I Hjälp filen läggs det här innehållet till i kommando-noden för varje cmdlet.

> [!NOTE]
> Om du vill se en fullständig vy över en hjälpfil öppnar du en av dll-Help. XML-filerna som finns i installations katalogen för Windows PowerShell. Till exempel innehåller filen Microsoft. PowerShell. commands. Management. dll-Help. XML innehåll för flera av Windows PowerShell-cmdlets.

### <a name="to-add-a-description"></a>Lägga till en beskrivning

- Börja med att förklara de grundläggande funktionerna i cmdleten mer detaljerat. I många fall kan du förklara de termer som används i cmdlet-namnet och illustrera okända begrepp med ett exempel. Om till exempel cmdleten lägger till data i en fil, förklarar du att den lägger till data i slutet av en befintlig fil.

- Om du vill hitta alla funktioner i cmdleten granskar du parameter listan. Beskriv den primära funktionen i cmdleten och ta sedan med andra funktioner och funktioner. Om till exempel huvud funktionen för cmdlet: en är att ändra en egenskap, men cmdleten kan ändra alla egenskaper, så i den detaljerade beskrivningen. Om cmdlet-parametrarna gör det möjligt för användarna att begära information på olika sätt, förklarar du det.

- Ta med information om hur användarna kan använda cmdleten, förutom den uppenbara användningen. Du kan till exempel använda objektet som `Get-Host` cmdleten hämtar för att ändra färg på text i Windows PowerShell-kommando fönstret.

  Exempel: "`Get-Acl`-cmdleten hämtar objekt som representerar säkerhets beskrivningen för en fil eller resurs. Säkerhets beskrivningen innehåller åtkomst kontrol listorna (ACL) för resursen. ACL: en anger de behörigheter som användare och användar grupper har åtkomst till resursen. "

- Den detaljerade beskrivningen ska beskriva cmdleten, men den bör inte beskriva de begrepp som cmdleten använder. Placera koncept definitioner i ytterligare anteckningar.

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
