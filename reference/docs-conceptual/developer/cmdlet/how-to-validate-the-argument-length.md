---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera argumentlängden
description: Verifiera argumentlängden
ms.openlocfilehash: 460aedbe6847033f976cb7bf70b6c77ac5a3a3c9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652625"
---
# <a name="how-to-validate-the-argument-length"></a>Verifiera argumentlängden

Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera antalet tecken (längden) för parameter argumentet innan cmdleten körs. Du ställer in den här validerings regeln genom att deklarera ValidateLength-attributet.

> [!NOTE]
> Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Verifiera argument längden

- Lägg till attributet validate som det visas i följande kod. I det här exemplet anger du att argumentets längd ska innehålla en längd på 0 till 10 tecken.

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Mer information om hur du deklarerar det här attributet finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Deklaration av attributet ValidateLength](./validatelength-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
