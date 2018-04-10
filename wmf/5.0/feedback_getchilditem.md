---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
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