---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera argumentlängden
description: Verifiera argumentlängden
ms.openlocfilehash: 460aedbe6847033f976cb7bf70b6c77ac5a3a3c9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652625"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="89c28-103">Verifiera argumentlängden</span><span class="sxs-lookup"><span data-stu-id="89c28-103">How to Validate the Argument Length</span></span>

<span data-ttu-id="89c28-104">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera antalet tecken (längden) för parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="89c28-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="89c28-105">Du ställer in den här validerings regeln genom att deklarera ValidateLength-attributet.</span><span class="sxs-lookup"><span data-stu-id="89c28-105">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="89c28-106">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="89c28-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="89c28-107">Verifiera argument längden</span><span class="sxs-lookup"><span data-stu-id="89c28-107">To validate the argument length</span></span>

- <span data-ttu-id="89c28-108">Lägg till attributet validate som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="89c28-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="89c28-109">I det här exemplet anger du att argumentets längd ska innehålla en längd på 0 till 10 tecken.</span><span class="sxs-lookup"><span data-stu-id="89c28-109">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="89c28-110">Mer information om hur du deklarerar det här attributet finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="89c28-110">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89c28-111">Se även</span><span class="sxs-lookup"><span data-stu-id="89c28-111">See Also</span></span>

[<span data-ttu-id="89c28-112">Deklaration av attributet ValidateLength</span><span class="sxs-lookup"><span data-stu-id="89c28-112">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="89c28-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="89c28-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
