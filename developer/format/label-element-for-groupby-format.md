---
title: Etikettera Element för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065418"
---
# <a name="label-element-for-groupby-format"></a>Label-element för GroupBy (format)

Anger en etikett som visas när en ny grupp har påträffats.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) etikett elementet för GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `Label` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)|Definierar hur en ny grupp med objekt visas.|

## <a name="text-value"></a>Textvärde

Ange vilken text som visas när en ny egenskap eller skriptvärdet uppstår med hjälp av Windows PowerShell.

## <a name="remarks"></a>Anmärkningar

Förutom den text som anges av det här elementet, visar det nya värdet som startar gruppen och lägger till en tom rad före och efter gruppen i Windows PowerShell.

## <a name="example"></a>Exempel

I följande exempel visar etiketten för en ny grupp. Visas etiketten skulle se ut ungefär så här: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Ett exempel på en fullständig formatering fil som innehåller det här elementet finns [bred vy (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Se även

[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
