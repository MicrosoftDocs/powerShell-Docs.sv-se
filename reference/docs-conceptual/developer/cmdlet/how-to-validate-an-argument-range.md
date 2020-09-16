---
title: Så här verifierar du ett argument intervall | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange attribute, example
ms.openlocfilehash: b48b1b87425add51e855c48ec700c78c3ae296c1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782080"
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
