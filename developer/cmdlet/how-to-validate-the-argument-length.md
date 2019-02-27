---
title: Hur du verifierar Argumentlängd | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847602"
---
# <a name="how-to-validate-the-argument-length"></a>Verifiera argumentlängden

Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera antalet tecken (tecken) för Parameterargumentet innan cmdleten körs. Du kan ange den här valideringsregel genom att deklarera ValidateLength-attributet.

> [!NOTE]
> Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Att verifiera Argumentlängd

- Lägg till attributet verifiera enligt följande kod. Det här exemplet anger att längden på argumentet ska ha en längd på 0 och 10 tecken.

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

Läs mer om hur du deklarera det här attributet [ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Deklaration av ValidateLength attribut](./validatelength-attribute-declaration.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
