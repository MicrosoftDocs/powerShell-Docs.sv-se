---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera ett argumentmönster
description: Verifiera ett argumentmönster
ms.openlocfilehash: ab5777c918a53c0a3900f87c52e7f14f9cb9b726
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666917"
---
# <a name="how-to-validate-an-argument-pattern"></a>Verifiera ett argumentmönster

Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera tecknen i parameter argumentet innan cmdleten körs. Du ställer in den här validerings regeln genom att deklarera ValidatePattern-attributet.

> [!NOTE]
> Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Validera ett argument mönster

- Lägg till attributet validate som det visas i följande kod. I det här exemplet anges ett mönster med fyra siffror där varje siffra har värdet 0 till 9.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

Mer information om hur du deklarerar det här attributet finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Deklaration av attributet ValidatePattern](./validatepattern-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
