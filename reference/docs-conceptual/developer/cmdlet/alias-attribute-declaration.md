---
title: Deklaration av alias-attribut | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782420"
---
# <a name="alias-attribute-declaration"></a>Deklaration av attributet Alias

Attributet alias gör att användaren kan ange olika namn för en cmdlet-parameter. Alias kan användas för att ange genvägar för ett parameter namn, eller så kan de ange olika namn som passar för olika scenarier.

## <a name="syntax"></a>Syntax

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parametrar

`aliasName` (Sträng []) Kunna. Anger en uppsättning kommaavgränsade aliasnamn för cmdlet-parametern.

## <a name="remarks"></a>Kommentarer

- Attributet alias används med attributet parameter när du anger en cmdlet-parameter. Mer information om hur du deklarerar dessa attribut finns i [så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).

- Varje aliasnamn måste vara unikt inom en-cmdlet. Windows PowerShell söker inte efter dubbla aliasnamn.

- Attributet alias används en gång för varje parameter i en cmdlet.

- Attributet alias definieras av klassen [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .

## <a name="see-also"></a>Se även

[Parameteralias](./parameter-aliases.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
