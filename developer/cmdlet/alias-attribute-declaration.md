---
title: Alias attributet deklarationen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846146"
---
# <a name="alias-attribute-declaration"></a>Deklaration av attributet Alias

Attributet Alias gör att användaren att ange olika namn för en cmdlet-parameter. Alias kan användas för att tillhandahålla genvägar för ett parameternamn och de kan tillhandahålla olika namn som är lämpliga för olika scenarier.

## <a name="syntax"></a>Syntax

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parametrar

`aliasName` (String[]) Krävs. Anger en uppsättning med CSV-aliasnamn för cmdlet-parameter.

## <a name="remarks"></a>Anmärkningar

- Alias-attributet används med attributet Parameter när du anger en cmdlet-parameter. Mer information om hur du deklarera dessa attribut finns i [så deklarera Cmdlet-parametrarna](./how-to-declare-cmdlet-parameters.md).

- Varje aliasnamn måste vara unika inom en cmdlet. Windows PowerShell kontrollerar inte om duplicerade aliasnamn.

- Alias-attributet används en gång för varje parameter i en cmdlet.

- Alias-attributet definieras av den [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) klass.

## <a name="see-also"></a>Se även

[Parameteralias](./parameter-aliases.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
