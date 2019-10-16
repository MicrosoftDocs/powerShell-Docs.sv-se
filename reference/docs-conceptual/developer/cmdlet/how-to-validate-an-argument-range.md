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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356289"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="1b563-102">Verifiera ett argumentintervall</span><span class="sxs-lookup"><span data-stu-id="1b563-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="1b563-103">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera de lägsta och högsta värdena för parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="1b563-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="1b563-104">Du ställer in den här validerings regeln genom att deklarera ValidateRange-attributet.</span><span class="sxs-lookup"><span data-stu-id="1b563-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="1b563-105">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="1b563-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="1b563-106">Verifiera ett argument intervall</span><span class="sxs-lookup"><span data-stu-id="1b563-106">To validate an argument range</span></span>

- <span data-ttu-id="1b563-107">Lägg till attributet ValidateRange som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="1b563-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="1b563-108">I det här exemplet anges ett intervall på 0 till 5 för parametern `InputData`.</span><span class="sxs-lookup"><span data-stu-id="1b563-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="1b563-109">Mer information om hur du deklarerar det här attributet finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1b563-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b563-110">Se även</span><span class="sxs-lookup"><span data-stu-id="1b563-110">See Also</span></span>

[<span data-ttu-id="1b563-111">ValidateRange-Attribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="1b563-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="1b563-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="1b563-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
