---
title: Etikett element för GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356065"
---
# <a name="label-element-for-groupby-format"></a>Label-element för GroupBy (format)

Anger en etikett som visas när en ny grupp påträffas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för visnings-(format) etikett element för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Label`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)|Definierar hur en ny grupp av objekt visas.|

## <a name="text-value"></a>Textvärde

Ange texten som visas när Windows PowerShell påträffar en ny egenskap eller ett nytt skript värde.

## <a name="remarks"></a>Anmärkningar

Utöver den text som anges av det här elementet visar Windows PowerShell det nya värdet som startar gruppen och lägger till en tom rad före och efter gruppen.

## <a name="example"></a>Exempel

I följande exempel visas etiketten för en ny grupp. Etiketten som visas ser ut ungefär så här: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Ett exempel på en hel format fil som innehåller det här elementet finns i [wide View (groupby)](./wide-view-groupby.md).

## <a name="see-also"></a>Se även

[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
