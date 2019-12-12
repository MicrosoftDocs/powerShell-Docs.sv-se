---
title: ValidateSet-Attribute-deklaration | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355421"
---
# <a name="validateset-attribute-declaration"></a>Deklaration av attributet ValidateSet

Attributet ValidateSetAttribute anger en uppsättning möjliga värden för ett cmdlet parameter argument. Det här attributet kan också användas av Windows PowerShell-funktioner.

När det här attributet anges avgör Windows PowerShell-körningsmiljön om det angivna argumentet för cmdlet-parametern matchar ett element i den angivna element uppsättningen. Cmdleten körs bara om parameter argumentet matchar ett element i mängden. Om ingen matchning hittas uppstår ett fel i Windows PowerShell-körningsmiljön.

## <a name="syntax"></a>Syntax

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parametrar

`ValidValues` ([system. String](/dotnet/api/System.String)) krävs. Anger giltiga parameter element värden. I följande exempel visas hur du anger ett eller flera element.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. Standardvärdet för `true` indikerar att Skift läget ignoreras. Värdet `false` gör cmdleten Skift läges känslig.

## <a name="remarks"></a>Anmärkningar

- Det här attributet kan bara användas en gång per parameter.

- Om parametervärdet är en matris måste varje element i matrisen matcha ett element i attribut uppsättningen.

- Attributet ValidateSetAttribute definieras av klassen [system. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
