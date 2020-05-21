---
title: ValidateCount-Attribute-deklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 3cae95fab30a4abe4e544ed5cb7dadc9f4debf02
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692371"
---
# <a name="validatecount-attribute-declaration"></a>Deklaration av attributet ValidateCount

Attributet ValidateCount anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.

## <a name="syntax"></a>Syntax

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametrar

`MinLength`([System. Int32][]) krävs. Anger det minsta antalet argument.

`MaxLength`([System. Int32][]) krävs. Anger det maximala antalet argument.

## <a name="remarks"></a>Kommentarer

- Mer information om hur du deklarerar det här attributet finns i [så här verifierar du ett argument antal][].

- När det här attributet inte anropas kan motsvarande cmdlet-parameter ha valfritt antal argument.

- Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:

  - `MinLength`Parametrarna och `MaxLength` är inte av typen [system. Int32][].

  - Värdet för `MaxLength` attributet Attribute är mindre än värdet för `MinLength` parametern Attribute.

- Attributet ValidateCount definieras av klassen [system. Management. Automation. ValidateCountAttribute][] .

## <a name="see-also"></a>Se även

[System. Management. Automation. ValidateCountAttribute][]

[Verifiera argumentantal][]

[Skriva en Windows PowerShell-cmdlet][]

[Verifiera argumentantal]: how-to-validate-an-argument-count.md
[Skriva en Windows PowerShell-cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
