---
title: Så här verifierar du ett argument antal | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356296"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="d47d9-102">Verifiera argumentantal</span><span class="sxs-lookup"><span data-stu-id="d47d9-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="d47d9-103">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera antalet argument (antalet) som en parameter accepterar innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="d47d9-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="d47d9-104">Du ställer in den här validerings regeln genom att deklarera ValidateCount-attributet.</span><span class="sxs-lookup"><span data-stu-id="d47d9-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="d47d9-105">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="d47d9-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="d47d9-106">Verifiera ett argument antal</span><span class="sxs-lookup"><span data-stu-id="d47d9-106">To validate an argument count</span></span>

- <span data-ttu-id="d47d9-107">Lägg till attributet validate som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="d47d9-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="d47d9-108">I det här exemplet anger du att parametern ska acceptera ett argument eller så många som tre argument.</span><span class="sxs-lookup"><span data-stu-id="d47d9-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="d47d9-109">Mer information om hur du deklarerar det här attributet finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d47d9-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d47d9-110">Se även</span><span class="sxs-lookup"><span data-stu-id="d47d9-110">See Also</span></span>

[<span data-ttu-id="d47d9-111">ValidateCount-Attribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="d47d9-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="d47d9-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="d47d9-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
