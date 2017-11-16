---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
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

