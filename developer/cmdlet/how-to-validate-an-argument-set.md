---
title: Hur du validerar en uppsättning Argument | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850570"
---
# <a name="how-to-validate-an-argument-set"></a>Verifiera en argumentuppsättning

Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera Parameterargumentet innan cmdleten körs. Den här valideringsregel innehåller en uppsättning med giltiga värden för Parameterargumentet.

> [!NOTE]
> Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Validera en uppsättning argument

- Lägg till attributet ValidateSet som visas i följande kod. Det här exemplet anger en uppsättning med tre möjliga värden för den `UserName` parametern.

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

Läs mer om hur du deklarera det här attributet [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Se även

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Deklaration av ValidateSet attribut](./validateset-attribute-declaration.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
