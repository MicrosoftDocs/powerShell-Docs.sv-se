---
ms.date: 09/13/2016
ms.topic: reference
title: Verifiera en argumentuppsättning
description: Verifiera en argumentuppsättning
ms.openlocfilehash: 50ec0a48277893584d896e14ad6aa843682a28cc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650364"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="1c325-103">Verifiera en argumentuppsättning</span><span class="sxs-lookup"><span data-stu-id="1c325-103">How to Validate an Argument Set</span></span>

<span data-ttu-id="1c325-104">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="1c325-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="1c325-105">Den här verifierings regeln innehåller en uppsättning giltiga värden för parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="1c325-105">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="1c325-106">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="1c325-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="1c325-107">Verifiera en argument uppsättning</span><span class="sxs-lookup"><span data-stu-id="1c325-107">To validate an argument set</span></span>

- <span data-ttu-id="1c325-108">Lägg till attributet ValidateSet som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="1c325-108">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="1c325-109">I det här exemplet anges en uppsättning av tre möjliga värden för `UserName` parametern.</span><span class="sxs-lookup"><span data-stu-id="1c325-109">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="1c325-110">Mer information om hur du deklarerar det här attributet finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1c325-110">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c325-111">Se även</span><span class="sxs-lookup"><span data-stu-id="1c325-111">See Also</span></span>

[<span data-ttu-id="1c325-112">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="1c325-112">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="1c325-113">Deklaration av attributet ValidateSet</span><span class="sxs-lookup"><span data-stu-id="1c325-113">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="1c325-114">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c325-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
