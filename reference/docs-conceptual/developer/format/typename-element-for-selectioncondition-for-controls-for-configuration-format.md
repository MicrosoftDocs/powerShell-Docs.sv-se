---
title: Elementet TypeName för SelectionCondition för kontroller för konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353552"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>TypeName-element för SelectionCondition för Controls för Configuration (format)

Anger en .NET-typ som utlöser villkoret. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för kontroller för Konfiguration (format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy-element för CustomEntry for Controls for Configuration (format) SelectionCondition-element för EntrySelectedBy för CustomEntry för Konfigurations element (format) för SelectionCondition för kontroll av konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `TypeName`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för CustomEntry för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Text värde

Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för CustomEntry för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
