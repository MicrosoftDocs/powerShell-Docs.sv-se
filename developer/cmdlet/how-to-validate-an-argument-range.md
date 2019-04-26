---
title: Hur du verifierar ett Argument adressintervall | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067798"
---
# <a name="how-to-validate-an-argument-range"></a>Verifiera ett argumentintervall

Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera lägsta och högsta värden för Parameterargumentet innan cmdleten körs. Du kan ange den här valideringsregel genom att deklarera ValidateRange-attributet.

> [!NOTE]
> Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Att validera ett argument-adressintervall

- Lägg till attributet ValidateRange som visas i följande kod. Det här exemplet anger ett intervall på 0 till 5 för de `InputData` parametern.

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

Läs mer om hur du deklarera det här attributet [ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Se även

[Deklaration av ValidateRange attribut](./validaterange-attribute-declaration.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
