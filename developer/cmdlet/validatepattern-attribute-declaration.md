---
title: Deklaration av ValidatePattern attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067135"
---
# <a name="validatepattern-attribute-declaration"></a>Deklaration av attributet ValidatePattern

Attributet ValidatePattern anger ett mönster för reguljärt uttryck som validerar argumentet för en cmdlet-parameter. Det här attributet kan också användas i Windows PowerShell-funktioner.

När ValidatePattern anropas i en cmdlet, Windows PowerShell-runtime Konverterar argumentet för cmdlet-parameter till en sträng och sedan jämförs strängen i mönstret som tillhandahålls av ValidatePattern-attributet. Cmdleten körs bara om den konvertera strängrepresentationen av argumentet och det angivna mönstren matchar. Om de inte matchar genereras ett fel av Windows PowerShell-körningen.

## <a name="syntax"></a>Syntax

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parametrar

`RegexString` ([System.String](/dotnet/api/System.String)) krävs. Anger ett reguljärt uttryck som validerar Parameterargumentet.

Alternativ ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) valfritt med namnet parametern. Anger en bitvis kombination av [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flaggor som anger alternativ för reguljärt uttryck.

## <a name="remarks"></a>Anmärkningar

- Det här attributet kan användas endast en gång per parametern.

- Du kan använda den `Option` parametern för attributet för att definiera ytterligare mönstret. Exempelvis kan göra du mönstret skiftlägeskänsligt.

- Om det här attributet används för en samling, måste varje element i samlingen matcha mönstret.

- Attributet ValidatePattern definieras av den [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) klass.

## <a name="see-also"></a>Se även

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
