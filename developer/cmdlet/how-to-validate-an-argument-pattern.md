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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846160"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="41922-102">Verifiera ett argumentmönster</span><span class="sxs-lookup"><span data-stu-id="41922-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="41922-103">Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera mönstret tecken på Parameterargumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="41922-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="41922-104">Du kan ange den här valideringsregel genom att deklarera ValidatePattern-attributet.</span><span class="sxs-lookup"><span data-stu-id="41922-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="41922-105">Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="41922-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="41922-106">Att validera ett argument-mönster</span><span class="sxs-lookup"><span data-stu-id="41922-106">To validate an argument pattern</span></span>

- <span data-ttu-id="41922-107">Lägg till attributet verifiera enligt följande kod.</span><span class="sxs-lookup"><span data-stu-id="41922-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="41922-108">Det här exemplet anger ett mönster med fyra siffror, där varje siffra har värdet 0 till 9.</span><span class="sxs-lookup"><span data-stu-id="41922-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="41922-109">Läs mer om hur du deklarera det här attributet [ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="41922-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41922-110">Se även</span><span class="sxs-lookup"><span data-stu-id="41922-110">See Also</span></span>

[<span data-ttu-id="41922-111">Deklaration av ValidatePattern attribut</span><span class="sxs-lookup"><span data-stu-id="41922-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="41922-112">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="41922-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
