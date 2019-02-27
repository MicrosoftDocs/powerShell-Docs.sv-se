---
title: Hur du validerar en argumentantal | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849009"
---
# <a name="how-to-validate-an-argument-count"></a>Verifiera argumentantal

Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera antalet argument (antal) som accepterar en parameter innan cmdleten körs. Du kan ange den här valideringsregel genom att deklarera ValidateCount-attributet.

> [!NOTE]
> Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Validera en argumentantal

- Lägg till attributet verifiera enligt följande kod. Det här exemplet anger att parametern accepterar ett argument eller upp till tre argument.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

Läs mer om hur du deklarera det här attributet [ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Deklaration av ValidateCount attribut](./validatecount-attribute-declaration.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
