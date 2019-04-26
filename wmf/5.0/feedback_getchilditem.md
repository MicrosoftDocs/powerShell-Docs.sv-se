---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085308"
---
# <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem har parametern - Depth
**Get-ChildItem** har nu en **– djup** parameter som du använder med **– Recurse** att begränsa rekursion:

PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 0

Katalog: C:\\användare\\slee\\hämtar\\exempel

Läget LastWriteTime längd namn

---- ------------- ------ ----

d---4/14/2015 17:36:00 Depth0

-a---4/14/2015 1:19 PM 0 File1.txt

-a---4/14/2015 1:19 PM 0 File2.txt

-a---4/14/2015 1:19 PM 0 File3.txt

PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 1

Katalog: C:\\användare\\slee\\hämtar\\exempel

Läget LastWriteTime längd namn

---- ------------- ------ ----

d---4/14/2015 17:36:00 Depth0

-a---4/14/2015 1:19 PM 0 File1.txt

-a---4/14/2015 1:19 PM 0 File2.txt

-a---4/14/2015 1:19 PM 0 File3.txt

Katalog: C:\\användare\\slee\\hämtar\\exempel\\Depth0

Läget LastWriteTime längd namn

---- ------------- ------ ----

d---4/14/2015 5:33 PM Depth1
