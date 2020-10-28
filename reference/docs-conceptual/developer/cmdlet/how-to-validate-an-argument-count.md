---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera argumentantal
description: Verifiera argumentantal
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666951"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="4ff66-103">Verifiera argumentantal</span><span class="sxs-lookup"><span data-stu-id="4ff66-103">How to Validate an Argument Count</span></span>

<span data-ttu-id="4ff66-104">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera antalet argument (antalet) som en parameter accepterar innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="4ff66-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="4ff66-105">Du ställer in den här validerings regeln genom att deklarera ValidateCount-attributet.</span><span class="sxs-lookup"><span data-stu-id="4ff66-105">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="4ff66-106">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="4ff66-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="4ff66-107">Verifiera ett argument antal</span><span class="sxs-lookup"><span data-stu-id="4ff66-107">To validate an argument count</span></span>

- <span data-ttu-id="4ff66-108">Lägg till attributet validate som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="4ff66-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="4ff66-109">I det här exemplet anger du att parametern ska acceptera ett argument eller så många som tre argument.</span><span class="sxs-lookup"><span data-stu-id="4ff66-109">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

<span data-ttu-id="4ff66-110">Mer information om hur du deklarerar det här attributet finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4ff66-110">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ff66-111">Se även</span><span class="sxs-lookup"><span data-stu-id="4ff66-111">See Also</span></span>

[<span data-ttu-id="4ff66-112">Deklaration av attributet ValidateCount</span><span class="sxs-lookup"><span data-stu-id="4ff66-112">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="4ff66-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="4ff66-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
