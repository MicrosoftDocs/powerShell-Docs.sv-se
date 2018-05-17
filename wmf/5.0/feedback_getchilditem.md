---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem har - djup parameter
**Get-ChildItem** har nu en **– djup** parameter som du använder med **– Recurse** att begränsa rekursion:

PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 0

Katalog: C:\\användare\\slee\\hämtar\\exempel

Läge LastWriteTime längd namn

---- ------------- ------ ----

d – 4-14/2015 17:36:00 Depth0

-a – 4-14/2015 1:19 PM 0 File1.txt

-a – 4-14/2015 1:19 PM 0 File2.txt

-a – 4-14/2015 1:19 PM 0 File3.txt

PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 1

Katalog: C:\\användare\\slee\\hämtar\\exempel

Läge LastWriteTime längd namn

---- ------------- ------ ----

d – 4-14/2015 17:36:00 Depth0

-a – 4-14/2015 1:19 PM 0 File1.txt

-a – 4-14/2015 1:19 PM 0 File2.txt

-a – 4-14/2015 1:19 PM 0 File3.txt

Katalog: C:\\användare\\slee\\hämtar\\exempel\\Depth0

Läge LastWriteTime längd namn

---- ------------- ------ ----

d – 4-14/2015 5:33 PM Depth1
