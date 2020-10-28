---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera argumentantal
description: Verifiera argumentantal
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666951"
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
