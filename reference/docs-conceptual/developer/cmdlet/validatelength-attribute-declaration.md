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
ms.openlocfilehash: a1a494534169b2da470286020dfacfa8e9084839
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692319"
---
# <a name="validatelength-attribute-declaration"></a>Deklaration av attributet ValidateLength

Attributet ValidateLength anger det lägsta och högsta antalet tecken för ett cmdlet parameter argument. Det här attributet kan också användas av Windows PowerShell-funktioner.

## <a name="syntax"></a>Syntax

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametrar

`MinLength`([System. Int32](/dotnet/api/System.Int32)) krävs. Anger det minsta antalet tecken som tillåts.

`MaxLength`([System. Int32](/dotnet/api/System.Int32)) krävs. Anger det maximala antalet tecken som tillåts.

## <a name="remarks"></a>Kommentarer

- Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du validerings regler för indata](./how-to-validate-parameter-input.md).

- Om det här attributet inte används kan motsvarande parameter argument vara en valfri längd.

- Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:

  - När värdet för `MaxLength` attributet Attribute är mindre än värdet för `MinLength` parametern Attribute.

  - När `MaxLength` parametern Attribute anges till 0.

  - Om argumentet inte är en sträng.

- Attributet ValidateLength definieras av klassen [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
