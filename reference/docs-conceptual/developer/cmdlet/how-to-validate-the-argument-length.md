---
title: Så här verifierar du argument längden | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356268"
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

[ValidateLength-Attribute-deklaration](./validatelength-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
