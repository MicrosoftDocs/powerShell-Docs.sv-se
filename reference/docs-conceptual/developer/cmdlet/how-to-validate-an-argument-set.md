---
title: Verifiera en argument uppsättning | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateSet attribute, example
ms.openlocfilehash: 6173f1380583f5b27e2b188990a5ea041f447c57
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782012"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="d3aed-102">Verifiera en argumentuppsättning</span><span class="sxs-lookup"><span data-stu-id="d3aed-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="d3aed-103">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="d3aed-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="d3aed-104">Den här verifierings regeln innehåller en uppsättning giltiga värden för parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="d3aed-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="d3aed-105">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="d3aed-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="d3aed-106">Verifiera en argument uppsättning</span><span class="sxs-lookup"><span data-stu-id="d3aed-106">To validate an argument set</span></span>

- <span data-ttu-id="d3aed-107">Lägg till attributet ValidateSet som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="d3aed-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="d3aed-108">I det här exemplet anges en uppsättning av tre möjliga värden för `UserName` parametern.</span><span class="sxs-lookup"><span data-stu-id="d3aed-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="d3aed-109">Mer information om hur du deklarerar det här attributet finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d3aed-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d3aed-110">Se även</span><span class="sxs-lookup"><span data-stu-id="d3aed-110">See Also</span></span>

[<span data-ttu-id="d3aed-111">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="d3aed-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="d3aed-112">Deklaration av attributet ValidateSet</span><span class="sxs-lookup"><span data-stu-id="d3aed-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="d3aed-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="d3aed-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
