---
title: TypeName-Element för EntrySelectedBy för CustomEntry för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083985"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>TypeName-element för EntrySelectedBy för CustomEntry för View (format)

Anger ett .NET-typ som använder den här definitionen av vyn anpassad kontroll. Det finns ingen gräns för hur många typer som kan anges för en Definitionsuppdatering.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för EntrySelectedBy vy (Format) Element för CustomEntry för vyn (Format) TypeName-elementet för EntrySelectedBy för CustomEntry för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för CustomEntry för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar vilka typer av .NET som använder den här anpassade kontrollen vydefinitionen eller villkor som måste finnas för den här definitionen som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

Varje anpassad kontroll vydefinitionen måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.

Mer information om komponenter för en anpassad kontroll vy finns i [skapar anpassade kontroller](./creating-custom-controls.md).

## <a name="see-also"></a>Se även

[Skapa anpassade kontroller](./creating-custom-controls.md)

[EntrySelectedBy Element för CustomEntry för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
