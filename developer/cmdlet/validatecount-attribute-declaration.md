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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067186"
---
# <a name="validatecount-attribute-declaration"></a>Deklaration av attributet ValidateCount

Attributet ValidateCount anger minsta och största antalet argument som tillåts för en cmdlet-parameter.

## <a name="syntax"></a>Syntax

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametrar

`MinLength` ([System.Int32][]) krävs. Anger det minsta antalet argument.

`MaxLength`([System.Int32][]) krävs. Anger det maximala antalet argument.

## <a name="remarks"></a>Anmärkningar

- Läs mer om hur du deklarera det här attributet [hur du validerar en argumentantal][].

- När det här attributet inte har anropats kan motsvarande cmdlet-parameter ha valfritt antal argument.

- Windows PowerShell-runtime genererar ett fel under följande förhållanden:

    - Den `MinLength` och `MaxLength` attributet parametrar inte är av typen [System.Int32][].

    - Värdet för den `MaxLength` attribut parameter är mindre än värdet för den `MinLength` attributet parameter.

- Attributet ValidateCount definieras av den [System.Management.Automation.ValidateCountAttribute][] klass.

## <a name="see-also"></a>Se även

[System.Management.Automation.ValidateCountAttribute][]

[Hur du validerar en argumentantal][]

[Skriva en Windows PowerShell-Cmdlet][]

[Hur du validerar en argumentantal]: how-to-validate-an-argument-count.md
[Skriva en Windows PowerShell-Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
