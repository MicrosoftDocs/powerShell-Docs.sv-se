---
title: Deklaration av ValidateLength attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855147"
---
# <a name="validatelength-attribute-declaration"></a>Deklaration av attributet ValidateLength

Attributet ValidateLength anger minsta och högsta antalet tillåtna tecken för en cmdlet-argument för parametern. Det här attributet kan också användas i Windows PowerShell-funktioner.

## <a name="syntax"></a>Syntax

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametrar

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required. Anger det minsta antalet tecken som tillåts.

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required. Anger det maximala antalet tecken som tillåts.

## <a name="remarks"></a>Anmärkningar

- Läs mer om hur du deklarera det här attributet [så deklarera indata valideringsregler](./how-to-validate-parameter-input.md).

- När det här attributet inte används, kan motsvarande Parameterargumentet vara av valfri längd.

- Windows PowerShell-runtime genererar ett fel under följande förhållanden:

    - När värdet för den `MaxLength` attribut parameter är mindre än värdet för den `MinLength` attributet parameter.

    - När den `MaxLength` attributet parametern anges till 0.

    - När argumentet är inte en sträng.

- Attributet ValidateLength definieras av den [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klass.

## <a name="see-also"></a>Se även

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
