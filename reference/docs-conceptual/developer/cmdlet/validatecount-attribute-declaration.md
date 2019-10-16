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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359167"
---
# <a name="validatecount-attribute-declaration"></a>Deklaration av attributet ValidateCount

Attributet ValidateCount anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.

## <a name="syntax"></a>Syntax

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametrar

`MinLength` ([system. Int32][]) krävs. Anger det minsta antalet argument.

`MaxLength` ([system. Int32][]) krävs. Anger det maximala antalet argument.

## <a name="remarks"></a>Anmärkningar

- Mer information om hur du deklarerar det här attributet finns i [så här verifierar du ett argument antal][].

- När det här attributet inte anropas kan motsvarande cmdlet-parameter ha valfritt antal argument.

- Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:

    - Attributen för parametern `MinLength` och `MaxLength` är inte av typen [system. Int32][].

    - Värdet för attributet `MaxLength` är mindre än värdet för parametern `MinLength`.

- Attributet ValidateCount definieras av klassen [system. Management. Automation. ValidateCountAttribute][] .

## <a name="see-also"></a>Se även

[System. Management. Automation. ValidateCountAttribute][]

[Så här verifierar du ett argument antal][]

[Skriva en Windows PowerShell-cmdlet][]

[Så här verifierar du ett argument antal]: how-to-validate-an-argument-count.md
[Skriva en Windows PowerShell-cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
