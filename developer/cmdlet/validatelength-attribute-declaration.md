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
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794339"
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

- Läs mer om hur du deklarera det här attributet [så deklarera indata valideringsregler](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- När det här attributet inte används, kan motsvarande Parameterargumentet vara av valfri längd.

- Windows PowerShell-runtime genererar ett fel under följande förhållanden:

    - När värdet för den `MaxLength` attribut parameter är mindre än värdet för den `MinLength` attributet parameter.

    - När den `MaxLength` attributet parametern anges till 0.

    - När argumentet är inte en sträng.

- Attributet ValidateLength definieras av den [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klass.

## <a name="see-also"></a>Se även

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)