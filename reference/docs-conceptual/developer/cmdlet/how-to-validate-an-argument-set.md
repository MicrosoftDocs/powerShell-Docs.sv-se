---
title: Verifiera en argument uppsättning | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356282"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="b52ef-102">Verifiera en argumentuppsättning</span><span class="sxs-lookup"><span data-stu-id="b52ef-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="b52ef-103">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="b52ef-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="b52ef-104">Den här verifierings regeln innehåller en uppsättning giltiga värden för parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="b52ef-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="b52ef-105">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="b52ef-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="b52ef-106">Verifiera en argument uppsättning</span><span class="sxs-lookup"><span data-stu-id="b52ef-106">To validate an argument set</span></span>

- <span data-ttu-id="b52ef-107">Lägg till attributet ValidateSet som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="b52ef-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="b52ef-108">I det här exemplet anges en uppsättning av tre möjliga värden för parametern `UserName`.</span><span class="sxs-lookup"><span data-stu-id="b52ef-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="b52ef-109">Mer information om hur du deklarerar det här attributet finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="b52ef-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b52ef-110">Se även</span><span class="sxs-lookup"><span data-stu-id="b52ef-110">See Also</span></span>

[<span data-ttu-id="b52ef-111">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="b52ef-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="b52ef-112">ValidateSet-Attribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="b52ef-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="b52ef-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="b52ef-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
