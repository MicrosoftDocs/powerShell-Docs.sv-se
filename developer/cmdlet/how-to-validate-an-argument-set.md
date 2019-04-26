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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067730"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="e5c16-102">Verifiera en argumentuppsättning</span><span class="sxs-lookup"><span data-stu-id="e5c16-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="e5c16-103">Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera Parameterargumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="e5c16-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="e5c16-104">Den här valideringsregel innehåller en uppsättning med giltiga värden för Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="e5c16-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c16-105">Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="e5c16-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="e5c16-106">Validera en uppsättning argument</span><span class="sxs-lookup"><span data-stu-id="e5c16-106">To validate an argument set</span></span>

- <span data-ttu-id="e5c16-107">Lägg till attributet ValidateSet som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="e5c16-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="e5c16-108">Det här exemplet anger en uppsättning med tre möjliga värden för den `UserName` parametern.</span><span class="sxs-lookup"><span data-stu-id="e5c16-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="e5c16-109">Läs mer om hur du deklarera det här attributet [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e5c16-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5c16-110">Se även</span><span class="sxs-lookup"><span data-stu-id="e5c16-110">See Also</span></span>

[<span data-ttu-id="e5c16-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="e5c16-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="e5c16-112">Deklaration av ValidateSet attribut</span><span class="sxs-lookup"><span data-stu-id="e5c16-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="e5c16-113">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5c16-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
