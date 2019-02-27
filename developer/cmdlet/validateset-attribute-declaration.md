---
title: Deklaration av ValidateSet attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850458"
---
# <a name="validateset-attribute-declaration"></a>Deklaration av attributet ValidateSet

Attributet ValidateSetAttribute anger en uppsättning möjliga värden för en cmdlet-argument för parametern. Det här attributet kan också användas i Windows PowerShell-funktioner.

När det här attributet anges avgör Windows PowerShell-körningen om det angivna argumentet för cmdlet-parameter matchar ett element i den angivna element uppsättningen. Cmdleten körs bara om Parameterargumentet matchar ett element i mängden. Om ingen matchning hittas returneras ett fel av Windows PowerShell-körningen.

## <a name="syntax"></a>Syntax

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parametrar

`ValidValues` ([System.String](/dotnet/api/System.String)) krävs. Anger de giltiga parametervärdena för elementet. I följande exempel visas hur du anger en eller flera element.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern. Standardvärdet för `true` anger att inte är skiftlägeskänsliga. Värdet `false` gör cmdleten skiftlägeskänsliga.

## <a name="remarks"></a>Anmärkningar

- Det här attributet kan användas endast en gång per parametern.

- Om värdet för parametern är en matris, måste varje element i matrisen matcha ett element i attributuppsättningen.

- Attributet ValidateSetAttribute definieras av den [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) klass.

## <a name="see-also"></a>Se även

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
