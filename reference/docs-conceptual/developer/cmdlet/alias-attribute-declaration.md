---
title: Deklaration av alias-attribut | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359486"
---
# <a name="alias-attribute-declaration"></a>Deklaration av attributet Alias

Attributet alias gör att användaren kan ange olika namn för en cmdlet-parameter. Alias kan användas för att ange genvägar för ett parameter namn, eller så kan de ange olika namn som passar för olika scenarier.

## <a name="syntax"></a>Syntax

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parametrar

`aliasName` (sträng []) krävs. Anger en uppsättning kommaavgränsade aliasnamn för cmdlet-parametern.

## <a name="remarks"></a>Anmärkningar

- Attributet alias används med attributet parameter när du anger en cmdlet-parameter. Mer information om hur du deklarerar dessa attribut finns i [så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).

- Varje aliasnamn måste vara unikt inom en-cmdlet. Windows PowerShell söker inte efter dubbla aliasnamn.

- Attributet alias används en gång för varje parameter i en cmdlet.

- Attributet alias definieras av klassen [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .

## <a name="see-also"></a>Se även

[Parameter-alias](./parameter-aliases.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
