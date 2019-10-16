---
title: SelectionSetName-element för ViewSelectedBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358817"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>SelectionSetName-element för ViewSelectedBy (format)

Anger en uppsättning .NET-objekt som visas i vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `SelectionSetName`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ViewSelectedBy-element (format)](./viewselectedby-element-format.md)|Definierar de .NET-objekt som visas i vyn.|

## <a name="text-value"></a>Text värde

Ange namnet på den markerings uppsättning som definieras av `Name`-elementet för urvals uppsättningen.

## <a name="remarks"></a>Anmärkningar

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

[Definiera urvals uppsättningar](./defining-selection-sets.md)

[ViewSelectedBy-element (format)](./viewselectedby-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
