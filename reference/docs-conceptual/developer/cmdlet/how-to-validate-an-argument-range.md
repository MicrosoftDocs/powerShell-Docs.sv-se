---
title: Så här verifierar du ett argument intervall | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange attribute, example
ms.openlocfilehash: b48b1b87425add51e855c48ec700c78c3ae296c1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782080"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="76656-102">Verifiera ett argumentintervall</span><span class="sxs-lookup"><span data-stu-id="76656-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="76656-103">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera de lägsta och högsta värdena för parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="76656-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="76656-104">Du ställer in den här validerings regeln genom att deklarera ValidateRange-attributet.</span><span class="sxs-lookup"><span data-stu-id="76656-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="76656-105">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="76656-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="76656-106">Verifiera ett argument intervall</span><span class="sxs-lookup"><span data-stu-id="76656-106">To validate an argument range</span></span>

- <span data-ttu-id="76656-107">Lägg till attributet ValidateRange som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="76656-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="76656-108">I det här exemplet anges ett intervall på 0 till 5 för `InputData` parametern.</span><span class="sxs-lookup"><span data-stu-id="76656-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="76656-109">Mer information om hur du deklarerar det här attributet finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="76656-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="76656-110">Se även</span><span class="sxs-lookup"><span data-stu-id="76656-110">See Also</span></span>

[<span data-ttu-id="76656-111">Deklaration av attributet ValidateRange</span><span class="sxs-lookup"><span data-stu-id="76656-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="76656-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="76656-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
