---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera en argumentuppsättning
description: Verifiera en argumentuppsättning
ms.openlocfilehash: 50ec0a48277893584d896e14ad6aa843682a28cc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650364"
---
# <a name="how-to-validate-an-argument-set"></a>Verifiera en argumentuppsättning

Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera parameter argumentet innan cmdleten körs. Den här verifierings regeln innehåller en uppsättning giltiga värden för parameter argumentet.

> [!NOTE]
> Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Verifiera en argument uppsättning

- Lägg till attributet ValidateSet som det visas i följande kod. I det här exemplet anges en uppsättning av tre möjliga värden för `UserName` parametern.

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

Mer information om hur du deklarerar det här attributet finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Se även

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Deklaration av attributet ValidateSet](./validateset-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
