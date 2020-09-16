---
title: Verifiera en argument uppsättning | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateSet attribute, example
ms.openlocfilehash: 6173f1380583f5b27e2b188990a5ea041f447c57
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782012"
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
