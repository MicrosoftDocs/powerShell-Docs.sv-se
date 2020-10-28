---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera ett argumentmönster
description: Verifiera ett argumentmönster
ms.openlocfilehash: ab5777c918a53c0a3900f87c52e7f14f9cb9b726
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666917"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="f3da4-103">Verifiera ett argumentmönster</span><span class="sxs-lookup"><span data-stu-id="f3da4-103">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="f3da4-104">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera tecknen i parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="f3da4-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="f3da4-105">Du ställer in den här validerings regeln genom att deklarera ValidatePattern-attributet.</span><span class="sxs-lookup"><span data-stu-id="f3da4-105">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="f3da4-106">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="f3da4-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="f3da4-107">Validera ett argument mönster</span><span class="sxs-lookup"><span data-stu-id="f3da4-107">To validate an argument pattern</span></span>

- <span data-ttu-id="f3da4-108">Lägg till attributet validate som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="f3da4-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="f3da4-109">I det här exemplet anges ett mönster med fyra siffror där varje siffra har värdet 0 till 9.</span><span class="sxs-lookup"><span data-stu-id="f3da4-109">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="f3da4-110">Mer information om hur du deklarerar det här attributet finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f3da4-110">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3da4-111">Se även</span><span class="sxs-lookup"><span data-stu-id="f3da4-111">See Also</span></span>

[<span data-ttu-id="f3da4-112">Deklaration av attributet ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="f3da4-112">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="f3da4-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f3da4-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
