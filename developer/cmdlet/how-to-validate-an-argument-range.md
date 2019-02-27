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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849429"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="a36aa-102">Verifiera ett argumentintervall</span><span class="sxs-lookup"><span data-stu-id="a36aa-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="a36aa-103">Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera lägsta och högsta värden för Parameterargumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="a36aa-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="a36aa-104">Du kan ange den här valideringsregel genom att deklarera ValidateRange-attributet.</span><span class="sxs-lookup"><span data-stu-id="a36aa-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="a36aa-105">Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="a36aa-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="a36aa-106">Att validera ett argument-adressintervall</span><span class="sxs-lookup"><span data-stu-id="a36aa-106">To validate an argument range</span></span>

- <span data-ttu-id="a36aa-107">Lägg till attributet ValidateRange som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="a36aa-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="a36aa-108">Det här exemplet anger ett intervall på 0 till 5 för de `InputData` parametern.</span><span class="sxs-lookup"><span data-stu-id="a36aa-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="a36aa-109">Läs mer om hur du deklarera det här attributet [ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a36aa-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a36aa-110">Se även</span><span class="sxs-lookup"><span data-stu-id="a36aa-110">See Also</span></span>

[<span data-ttu-id="a36aa-111">Deklaration av ValidateRange attribut</span><span class="sxs-lookup"><span data-stu-id="a36aa-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="a36aa-112">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a36aa-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
