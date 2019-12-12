---
title: Verifiera en argument uppsättning | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356282"
---
# <a name="how-to-validate-an-argument-set"></a>Verifiera en argumentuppsättning

Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera parameter argumentet innan cmdleten körs. Den här verifierings regeln innehåller en uppsättning giltiga värden för parameter argumentet.

> [!NOTE]
> Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Verifiera en argument uppsättning

- Lägg till attributet ValidateSet som det visas i följande kod. I det här exemplet anges en uppsättning av tre möjliga värden för parametern `UserName`.

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

[ValidateSet-Attribute-deklaration](./validateset-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
