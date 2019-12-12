---
title: Elementet TypeName för SelectionCondition för CustomControl för vyn (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c65171-4d4c-46a9-a545-591df058acd1
caps.latest.revision: 7
ms.openlocfilehash: 00e9ae0916dd6d22602b99b201c9c4b7e549dc48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353538"
---
# <a name="typename-element-for-selectioncondition-for-customcontrol-for-view--format"></a>TypeName-element för SelectionCondition för CustomControl för View  (format)

Anger en .NET-typ som utlöser villkoret. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View Format) CustomItem-element för CustomEntry för CustomControl för View (format) SelectionCondition-element för EntrySelectedBy för CustomControl för View (format) TypeName-element för SelectionCondition för View (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `TypeName`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
