---
title: Deklaration av ValidateRange attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067118"
---
# <a name="validaterange-attribute-declaration"></a>Deklaration av attributet ValidateRange

Attributet ValidateRange anger de minsta och högsta värden (intervall) för cmdlet-argument för parametern. Det här attributet kan också användas i Windows PowerShell-funktioner.

## <a name="syntax"></a>Syntax

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parametrar

`MinRange` ([System.Object](/dotnet/api/system.object)) krävs. Anger det minsta tillåtna värdet.

`MaxRange` ([System.Object](/dotnet/api/system.object)) krävs. Anger det högsta tillåtna värdet.

## <a name="remarks"></a>Anmärkningar

- Windows PowerShell-runtime genererar en konstruktion fel när värdet för den `MinRange` parametern är större än värdet för den `MaxRange` parametern.

- Windows PowerShell-runtime genererar ett valideringsfel under följande förhållanden:

    - När värdet för argumentet är mindre än värdet `MinRange` gränsen med eller större än den `MaxRange` gränsen.

    - När argumentet är inte av samma typ som den `MinRange` och `MaxRange` parametrar.

- Attributet ValidateRange definieras av den [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) klass.

## <a name="see-also"></a>Se även

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
