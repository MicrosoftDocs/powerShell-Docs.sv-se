---
title: Hur du validerar en uppsättning Argument | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850570"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="fcc8d-102">Verifiera en argumentuppsättning</span><span class="sxs-lookup"><span data-stu-id="fcc8d-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="fcc8d-103">Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera Parameterargumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="fcc8d-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="fcc8d-104">Den här valideringsregel innehåller en uppsättning med giltiga värden för Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="fcc8d-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="fcc8d-105">Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="fcc8d-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="fcc8d-106">Validera en uppsättning argument</span><span class="sxs-lookup"><span data-stu-id="fcc8d-106">To validate an argument set</span></span>

- <span data-ttu-id="fcc8d-107">Lägg till attributet ValidateSet som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="fcc8d-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="fcc8d-108">Det här exemplet anger en uppsättning med tre möjliga värden för den `UserName` parametern.</span><span class="sxs-lookup"><span data-stu-id="fcc8d-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="fcc8d-109">Läs mer om hur du deklarera det här attributet [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="fcc8d-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcc8d-110">Se även</span><span class="sxs-lookup"><span data-stu-id="fcc8d-110">See Also</span></span>

[<span data-ttu-id="fcc8d-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="fcc8d-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="fcc8d-112">Deklaration av ValidateSet attribut</span><span class="sxs-lookup"><span data-stu-id="fcc8d-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="fcc8d-113">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fcc8d-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
