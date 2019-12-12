---
title: Så här verifierar du ett argument intervall | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356289"
---
# <a name="how-to-validate-an-argument-range"></a>Verifiera ett argumentintervall

Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera de lägsta och högsta värdena för parameter argumentet innan cmdleten körs. Du ställer in den här validerings regeln genom att deklarera ValidateRange-attributet.

> [!NOTE]
> Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Verifiera ett argument intervall

- Lägg till attributet ValidateRange som det visas i följande kod. I det här exemplet anges ett intervall på 0 till 5 för parametern `InputData`.

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

Mer information om hur du deklarerar det här attributet finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Se även

[ValidateRange-Attribute-deklaration](./validaterange-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
