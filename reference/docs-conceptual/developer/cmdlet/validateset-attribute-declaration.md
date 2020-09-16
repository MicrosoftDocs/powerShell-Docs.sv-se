---
title: ValidateSet-Attribute-deklaration | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.openlocfilehash: 0b6833efb0ce8e9474e9d91049fd201fc845cbea
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787775"
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

`ValidValues` ([System. String](/dotnet/api/System.String)) krävs. Anger giltiga parameter element värden. I följande exempel visas hur du anger ett eller flera element.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter. Standardvärdet för `true` anger att Case ignoreras. Värdet `false` gör cmdlet Skift läges känsligt.

## <a name="remarks"></a>Kommentarer

- Det här attributet kan bara användas en gång per parameter.

- Om parametervärdet är en matris måste varje element i matrisen matcha ett element i attribut uppsättningen.

- Attributet ValidateSetAttribute definieras av klassen [system. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .

## <a name="see-also"></a>Se även

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
