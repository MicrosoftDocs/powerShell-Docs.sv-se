---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera ett argumentintervall
description: Verifiera ett argumentintervall
ms.openlocfilehash: 1c1c53d43350a38beb2193200de3bd6b689366a4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666934"
---
# <a name="how-to-validate-an-argument-range"></a>Verifiera ett argumentintervall

Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera de lägsta och högsta värdena för parameter argumentet innan cmdleten körs. Du ställer in den här validerings regeln genom att deklarera ValidateRange-attributet.

> [!NOTE]
> Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Verifiera ett argument intervall

- Lägg till attributet ValidateRange som det visas i följande kod. I det här exemplet anges ett intervall på 0 till 5 för `InputData` parametern.

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

Mer information om hur du deklarerar det här attributet finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Deklaration av attributet ValidateRange](./validaterange-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
