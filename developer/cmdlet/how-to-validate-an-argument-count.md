---
title: Hur du validerar en argumentantal | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849009"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="310be-102">Verifiera argumentantal</span><span class="sxs-lookup"><span data-stu-id="310be-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="310be-103">Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera antalet argument (antal) som accepterar en parameter innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="310be-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="310be-104">Du kan ange den här valideringsregel genom att deklarera ValidateCount-attributet.</span><span class="sxs-lookup"><span data-stu-id="310be-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="310be-105">Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="310be-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="310be-106">Validera en argumentantal</span><span class="sxs-lookup"><span data-stu-id="310be-106">To validate an argument count</span></span>

- <span data-ttu-id="310be-107">Lägg till attributet verifiera enligt följande kod.</span><span class="sxs-lookup"><span data-stu-id="310be-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="310be-108">Det här exemplet anger att parametern accepterar ett argument eller upp till tre argument.</span><span class="sxs-lookup"><span data-stu-id="310be-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="310be-109">Läs mer om hur du deklarera det här attributet [ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="310be-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="310be-110">Se även</span><span class="sxs-lookup"><span data-stu-id="310be-110">See Also</span></span>

[<span data-ttu-id="310be-111">Deklaration av ValidateCount attribut</span><span class="sxs-lookup"><span data-stu-id="310be-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="310be-112">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="310be-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
