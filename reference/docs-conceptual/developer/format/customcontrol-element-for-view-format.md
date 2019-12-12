---
title: CustomControl-element för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354777"
---
# <a name="customcontrol-element-for-view-format"></a>CustomControl-element för View (format)

Definierar ett anpassat kontroll format för vyn.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element (format)

## <a name="syntax"></a>Syntax

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomControl`-elementet. Du måste ange ett underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries-element för CustomControl för vy (format)](./customentries-element-for-customcontrol-for-view-format.md)|Nödvändigt element.<br /><br /> Innehåller definitionerna för vyn anpassad kontroll.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa element (format)](./view-element-format.md)|Definierar en vy som används för att visa ett eller flera .NET-objekt.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall krävs bara en definition för varje kontroll, men det är möjligt att ange flera definitioner om du vill använda samma vy för att visa olika .NET-objekt. I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomEntries-element för CustomControl för vy (format)](./customentries-element-for-customcontrol-for-view-format.md)

[Visa element (format)](./view-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
