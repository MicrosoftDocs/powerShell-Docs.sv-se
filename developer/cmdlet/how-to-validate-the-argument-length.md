---
title: Hur du verifierar Argumentlängd | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847602"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="52d63-102">Verifiera argumentlängden</span><span class="sxs-lookup"><span data-stu-id="52d63-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="52d63-103">Det här exemplet visar hur du anger en valideringsregel som Windows PowerShell-runtime kan använda för att kontrollera antalet tecken (tecken) för Parameterargumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="52d63-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="52d63-104">Du kan ange den här valideringsregel genom att deklarera ValidateLength-attributet.</span><span class="sxs-lookup"><span data-stu-id="52d63-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="52d63-105">Läs mer om den klass som definierar det här attributet [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="52d63-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="52d63-106">Att verifiera Argumentlängd</span><span class="sxs-lookup"><span data-stu-id="52d63-106">To validate the argument length</span></span>

- <span data-ttu-id="52d63-107">Lägg till attributet verifiera enligt följande kod.</span><span class="sxs-lookup"><span data-stu-id="52d63-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="52d63-108">Det här exemplet anger att längden på argumentet ska ha en längd på 0 och 10 tecken.</span><span class="sxs-lookup"><span data-stu-id="52d63-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="52d63-109">Läs mer om hur du deklarera det här attributet [ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="52d63-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="52d63-110">Se även</span><span class="sxs-lookup"><span data-stu-id="52d63-110">See Also</span></span>

[<span data-ttu-id="52d63-111">Deklaration av ValidateLength attribut</span><span class="sxs-lookup"><span data-stu-id="52d63-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="52d63-112">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="52d63-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
