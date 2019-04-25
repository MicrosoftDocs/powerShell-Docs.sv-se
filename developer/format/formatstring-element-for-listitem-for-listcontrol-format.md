---
title: FormatString-Element för ListItem för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065634"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>FormatString-element för ListItem för ListControl  (format)

Anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListControl (Format) ListItems som finns Element för ListControl (Format) ListItem Element för ListControl (Format) FormatString-elementet för ListItem för ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `FormatString` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skript som vars värde visas i en rad i listvyn.|

## <a name="text-value"></a>Textvärde

Ange mönstret som används för att formatera data. Du kan till exempel använda det här mönstret ska formateras värdet för en egenskap som är av typen [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Anmärkningar

Formatsträngar kan användas när du skapar tabellvyer, listvyer, brett vyer eller anpassade vyer. Mer information om hur du formaterar ett värde som visas i en vy finns i [formatering visas Data](./formatting-displayed-data.md).

Läs mer om hur du använder formatsträngar i listvyer [skapar listvyn](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skriva ett Windows PowerShell formatering och skriver fil](./writing-a-powershell-formatting-file.md)
