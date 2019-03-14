---
title: Deklaration av ValidateCount attribut | Microsoft Docs
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
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794457"
---
# <a name="validatecount-attribute-declaration"></a>Deklaration av attributet ValidateCount

Attributet ValidateCount anger minsta och största antalet argument som tillåts för en cmdlet-parameter.

## <a name="syntax"></a>Syntax

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametrar

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) krävs. Anger det minsta antalet argument.

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) krävs. Anger det maximala antalet argument.

## <a name="remarks"></a>Anmärkningar

- Läs mer om hur du deklarera det här attributet [så deklarera indata valideringsregler](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- När det här attributet inte har anropats kan motsvarande cmdlet-parameter ha valfritt antal argument.

- Windows PowerShell-runtime genererar ett fel under följande förhållanden:

    - Den `MinLength` och `MaxLength` attributet parametrar inte är av typen [System.Int32](/dotnet/api/System.Int32).

    - Värdet för den `MaxLength` attribut parameter är mindre än värdet för den `MinLength` attributet parameter.

- Attributet ValidateCount definieras av den [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) klass.

## <a name="see-also"></a>Se även

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[Hur du deklarera verifiering av indata-regler](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
