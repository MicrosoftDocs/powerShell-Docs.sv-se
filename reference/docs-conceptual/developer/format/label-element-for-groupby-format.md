---
title: Etikett element för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07b4d037472a9dd2329e94576ec10f5b82f46b34
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785786"
---
# <a name="label-element-for-groupby-format"></a>Label-element för GroupBy (format)

Anger en etikett som visas när en ny grupp påträffas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för visnings-(format) etikett element för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `Label` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-element för View (format)](./groupby-element-for-view-format.md)|Definierar hur en ny grupp av objekt visas.|

## <a name="text-value"></a>Textvärde

Ange texten som visas när Windows PowerShell påträffar en ny egenskap eller ett nytt skript värde.

## <a name="remarks"></a>Kommentarer

Utöver den text som anges av det här elementet visar Windows PowerShell det nya värdet som startar gruppen och lägger till en tom rad före och efter gruppen.

## <a name="example"></a>Exempel

I följande exempel visas etiketten för en ny grupp. Den visade etiketten ser ut ungefär så här: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Ett exempel på en hel format fil som innehåller det här elementet finns i [wide View (groupby)](./wide-view-groupby.md).

## <a name="see-also"></a>Se även

[GroupBy-element för View (format)](./groupby-element-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
