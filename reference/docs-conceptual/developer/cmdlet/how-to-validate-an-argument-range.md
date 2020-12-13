---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera ett argumentintervall
description: Verifiera ett argumentintervall
ms.openlocfilehash: 1c1c53d43350a38beb2193200de3bd6b689366a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666934"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="22bbd-103">Verifiera ett argumentintervall</span><span class="sxs-lookup"><span data-stu-id="22bbd-103">How to Validate an Argument Range</span></span>

<span data-ttu-id="22bbd-104">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera de lägsta och högsta värdena för parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="22bbd-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="22bbd-105">Du ställer in den här validerings regeln genom att deklarera ValidateRange-attributet.</span><span class="sxs-lookup"><span data-stu-id="22bbd-105">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="22bbd-106">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="22bbd-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="22bbd-107">Verifiera ett argument intervall</span><span class="sxs-lookup"><span data-stu-id="22bbd-107">To validate an argument range</span></span>

- <span data-ttu-id="22bbd-108">Lägg till attributet ValidateRange som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="22bbd-108">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="22bbd-109">I det här exemplet anges ett intervall på 0 till 5 för `InputData` parametern.</span><span class="sxs-lookup"><span data-stu-id="22bbd-109">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="22bbd-110">Mer information om hur du deklarerar det här attributet finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="22bbd-110">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="22bbd-111">Se även</span><span class="sxs-lookup"><span data-stu-id="22bbd-111">See Also</span></span>

[<span data-ttu-id="22bbd-112">Deklaration av attributet ValidateRange</span><span class="sxs-lookup"><span data-stu-id="22bbd-112">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="22bbd-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="22bbd-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
