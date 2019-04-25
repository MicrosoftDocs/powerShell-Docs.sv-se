---
title: Hur du verifierar ett mönster för argumentet | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067781"
---
# <a name="how-to-validate-an-argument-pattern"></a>Verifiera ett argumentmönster

Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera mönstret tecken på Parameterargumentet innan cmdleten körs. Du kan ange den här valideringsregel genom att deklarera ValidatePattern-attributet.

> [!NOTE]
> Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Att validera ett argument-mönster

- Lägg till attributet verifiera enligt följande kod. Det här exemplet anger ett mönster med fyra siffror, där varje siffra har värdet 0 till 9.

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

Läs mer om hur du deklarera det här attributet [ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Deklaration av ValidatePattern attribut](./validatepattern-attribute-declaration.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
