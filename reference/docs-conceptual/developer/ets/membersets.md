---
title: Medlems uppsättningar för utökade typ system
ms.date: 07/09/2020
ms.openlocfilehash: 3f4e44ed7b498bb7c4a71f7b131270ed4f2ef981
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786262"
---
# <a name="ets-member-sets"></a>ETS medlems uppsättningar

Med medlems uppsättningar kan du partitionera medlemmar av **PSObject** -objektet i två del mängder så att medlemmar i under uppsättningarna kan refereras till tillsammans med deras delmängds namn. De två typerna av del mängder inkluderar egenskaps uppsättningar och medlems uppsättningar. Ett exempel på hur PowerShell använder medlems uppsättningar finns i en viss egenskaps uppsättning med namnet **DefaultDisplayPropertySet** som används för att fastställa, vid körning, vilka egenskaper som ska visas för ett angivet **PSObject** -objekt.

## <a name="property-sets"></a>Egenskaps uppsättningar

Egenskaps uppsättningar kan innehålla valfritt antal egenskaper för en **PSObject** -typ. I allmänhet kan en egenskaps uppsättning användas när en samling egenskaper (av samma typ) behövs. Egenskaps uppsättningen skapas genom att anropa `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` konstruktorn med namnet på egenskaps uppsättningen och namnen på de refererade egenskaperna. Det skapade **PSPropertySet** -objektet kan sedan användas som ett alias som pekar på egenskaperna i uppsättningen. [PSPropertySet](/dotnet/api/system.management.automation.pspropertyset) -klassen har följande egenskaper och metoder.

- **IsInstance** -egenskap: hämtar ett **booleskt** värde som anger egenskapens källa.
- **MemberType** -egenskap: hämtar typ av egenskaper i egenskaps uppsättningen.
- **Namn** egenskap: hämtar namnet på egenskaps uppsättningen.
- **ReferencedPropertyNames** -egenskap: hämtar namnen på egenskaperna i egenskaps uppsättningen.
- **TypeNameOfValue** -egenskap: hämtar en **PropertySet** Enumeration-konstant som definierar den här uppsättningen som en egenskaps uppsättning.
- **Value** -egenskap: hämtar eller anger **PSPropertySet** -objektet.
- `PSPropertySet.Copy` metod: gör en exakt kopia av **PSPropertySet** -objektet.
- `PSMemberSet.ToString` metod: konverterar **PSPropertySet** -objektet till en sträng.

## <a name="member-sets"></a>Medlems uppsättningar

Medlems uppsättningar kan innehålla valfritt antal utökade medlemmar av vilken typ som helst. Medlems uppsättningen skapas genom att anropar `PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`
konstruktor med namnet på medlems uppsättningen och namnen på de medlemmar som refereras till. Det skapade **PSPropertySet** -objektet kan sedan användas som ett alias som pekar på medlemmarna i uppsättningen. [PSMemberSet](/dotnet/api/system.management.automation.psmemberset) -klassen har följande egenskaper och metoder.

- **IsInstance** -egenskap: hämtar ett **booleskt** värde som anger medlemmens källa.
- **Medlems egenskap:** hämtar alla medlemmar i medlems uppsättningen.
- **MemberType** -egenskap: hämtar en **MemberSet** -uppräknings konstant som definierar den här uppsättningen som en medlems uppsättning.
- Egenskapen **metoder** : hämtar de metoder som ingår i medlems uppsättningen.
- **Egenskaps egenskap:** hämtar egenskaperna som ingår i medlems uppsättningen.
- **TypeNameOfValue** -egenskap: hämtar en **MemberSet** -uppräknings konstant som definierar den här uppsättningen som en medlems uppsättning.
- **Värde** egenskap: hämtar **PSMemberSet** -objektet.
- `PSMemberSet.Copy` metod: gör en exakt kopia av **PSMemberSet** -objektet.
- `PSMemberSet.ToString` metod: konverterar **PSMemberSet** -objektet till en sträng.
