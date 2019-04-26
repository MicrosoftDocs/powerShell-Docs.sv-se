---
title: TypeName-Element för SelectionCondition för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083951"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>TypeName-element för SelectionCondition för Controls för Configuration (format)

Anger ett .NET-typ som utlöser villkoret. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för kontroller för (Format) CustomEntry konfigurationselement för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för (Format) SelectionCondition konfigurationselement för EntrySelectedBy för CustomEntry för (Format) TypeName konfigurationselement för SelectionCondition för kontroller för konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` Element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för CustomEntry för konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[SelectionCondition Element för EntrySelectedBy för CustomEntry för konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
