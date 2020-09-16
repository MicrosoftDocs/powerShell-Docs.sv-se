---
title: Så här verifierar du ett argument antal | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateCount attribute, example
ms.openlocfilehash: e7c0eb364a6975cec089b984c2100d476631a12d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782131"
---
# <a name="how-to-validate-an-argument-count"></a>Verifiera argumentantal

Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera antalet argument (antalet) som en parameter accepterar innan cmdleten körs. Du ställer in den här validerings regeln genom att deklarera ValidateCount-attributet.

> [!NOTE]
> Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Verifiera ett argument antal

- Lägg till attributet validate som det visas i följande kod. I det här exemplet anger du att parametern ska acceptera ett argument eller så många som tre argument.

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

Mer information om hur du deklarerar det här attributet finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Deklaration av attributet ValidateCount](./validatecount-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
