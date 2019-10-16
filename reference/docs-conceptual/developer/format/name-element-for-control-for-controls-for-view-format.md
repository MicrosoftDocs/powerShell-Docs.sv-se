---
title: Namn element för kontroll för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355995"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Name-element för Control för Controls för View (format)

Anger kontrollens namn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för att visa (format)-elementet för kontroll av visnings namn (format)

## <a name="syntax"></a>Syntax

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `Name`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontroll element för kontroller för vy (format)](./control-element-for-controls-for-view-format.md)|Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.|

## <a name="text-value"></a>Text värde

Ange det namn som ska användas för att referera till kontrollen.

## <a name="remarks"></a>Anmärkningar

Namnet som anges här kan användas i följande element för att referera till den här kontrollen.

- När du skapar en tabell, lista, bred eller anpassad flikkontroll, kan kontrollen anges med följande element: [groupby-element för vy (format)](./groupby-element-for-view-format.md)

- När du skapar en annan kontroll som kan användas av en vy, kan den här kontrollen anges av följande element: [ExpressionBinding-element för CustomItem för kontroller för visning (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)

[ExpressionBinding-element för CustomItem för kontroller för vy (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Kontroll element för kontroller för vy (format)](./control-element-for-controls-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
