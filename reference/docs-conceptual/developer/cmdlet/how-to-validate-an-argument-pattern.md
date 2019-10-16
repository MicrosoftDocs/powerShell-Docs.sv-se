---
title: Så här verifierar du ett argument mönster | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356317"
---
# <a name="how-to-validate-an-argument-pattern"></a>Verifiera ett argumentmönster

Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera tecknen i parameter argumentet innan cmdleten körs. Du ställer in den här validerings regeln genom att deklarera ValidatePattern-attributet.

> [!NOTE]
> Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Validera ett argument mönster

- Lägg till attributet validate som det visas i följande kod. I det här exemplet anges ett mönster med fyra siffror där varje siffra har värdet 0 till 9.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

Mer information om hur du deklarerar det här attributet finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Se även

[ValidatePattern-Attribute-deklaration](./validatepattern-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
