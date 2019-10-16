---
title: Så här verifierar du ett argument antal | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356296"
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

[ValidateCount-Attribute-deklaration](./validatecount-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
