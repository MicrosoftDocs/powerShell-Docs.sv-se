---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för ViewSelectedBy (format)
description: SelectionSetName-element för ViewSelectedBy (format)
ms.openlocfilehash: a1a1816761715a138bcb3c2bd4cb9dbbb2f9cb92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654915"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>SelectionSetName-element för ViewSelectedBy (format)

Anger en uppsättning .NET-objekt som visas i vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `SelectionSetName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ViewSelectedBy-element (format)](./viewselectedby-element-format.md)|Definierar de .NET-objekt som visas i vyn.|

## <a name="text-value"></a>Textvärde

Ange namnet på den markerings uppsättning som definieras av `Name` elementet för urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv. Mer information om hur du definierar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger en urvals uppsättning för en listvy. Samma schema används för tabeller, breda och anpassade vyer.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Se även

[Definiera valuppsättningar](./defining-selection-sets.md)

[ViewSelectedBy-element (format)](./viewselectedby-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
