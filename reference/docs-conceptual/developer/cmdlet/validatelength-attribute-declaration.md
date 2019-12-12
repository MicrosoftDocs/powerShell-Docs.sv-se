---
title: ValidateLength-Attribute-deklaration | Microsoft Docs
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
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359148"
---
# <a name="validatelength-attribute-declaration"></a>Deklaration av attributet ValidateLength

Attributet ValidateLength anger det lägsta och högsta antalet tecken för ett cmdlet parameter argument. Det här attributet kan också användas av Windows PowerShell-funktioner.

## <a name="syntax"></a>Syntax

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametrar

`MinLength` ([system. Int32](/dotnet/api/System.Int32)) krävs. Anger det minsta antalet tecken som tillåts.

`MaxLength` ([system. Int32](/dotnet/api/System.Int32)) krävs. Anger det maximala antalet tecken som tillåts.

## <a name="remarks"></a>Anmärkningar

- Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du validerings regler för indata](./how-to-validate-parameter-input.md).

- Om det här attributet inte används kan motsvarande parameter argument vara en valfri längd.

- Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:

    - När värdet för parametern `MaxLength` attribut är mindre än värdet för parametern `MinLength` attribut.

    - När parametern `MaxLength` attribut anges till 0.

    - Om argumentet inte är en sträng.

- Attributet ValidateLength definieras av klassen [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
