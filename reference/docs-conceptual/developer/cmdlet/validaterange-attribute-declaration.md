---
title: ValidateRange-Attribute-deklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 560fa105ac3f93ae6334df0112f5290dfa20576c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692005"
---
# <a name="validaterange-attribute-declaration"></a>Deklaration av attributet ValidateRange

Attributet ValidateRange anger det lägsta och högsta värdet (intervallet) för argumentet cmdlet-parameter. Det här attributet kan också användas av Windows PowerShell-funktioner.

## <a name="syntax"></a>Syntax

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parametrar

`MinRange`([System. Object](/dotnet/api/system.object)) krävs. Anger det lägsta tillåtna värdet.

`MaxRange`([System. Object](/dotnet/api/system.object)) krävs. Anger det högsta tillåtna värdet.

## <a name="remarks"></a>Kommentarer

- Windows PowerShell-körningsmiljön genererar ett konstruktions fel när värdet för `MinRange` parametern är större än värdet för `MaxRange` parametern.

- Windows PowerShell-körningsmiljön genererar ett verifierings fel under följande förhållanden:

  - När värdet för argumentet är mindre än `MinRange` gränsen eller större än `MaxRange` gränsen.

  - Om argumentet inte är av samma typ som `MinRange` `MaxRange` parametrarna och.

- Attributet ValidateRange definieras av klassen [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
