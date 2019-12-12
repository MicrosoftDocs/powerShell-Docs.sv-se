---
title: Så här verifierar du argument längden | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356268"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="ad9ef-102">Verifiera argumentlängden</span><span class="sxs-lookup"><span data-stu-id="ad9ef-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="ad9ef-103">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera antalet tecken (längden) för parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="ad9ef-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="ad9ef-104">Du ställer in den här validerings regeln genom att deklarera ValidateLength-attributet.</span><span class="sxs-lookup"><span data-stu-id="ad9ef-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="ad9ef-105">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="ad9ef-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="ad9ef-106">Verifiera argument längden</span><span class="sxs-lookup"><span data-stu-id="ad9ef-106">To validate the argument length</span></span>

- <span data-ttu-id="ad9ef-107">Lägg till attributet validate som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="ad9ef-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="ad9ef-108">I det här exemplet anger du att argumentets längd ska innehålla en längd på 0 till 10 tecken.</span><span class="sxs-lookup"><span data-stu-id="ad9ef-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="ad9ef-109">Mer information om hur du deklarerar det här attributet finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ad9ef-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad9ef-110">Se även</span><span class="sxs-lookup"><span data-stu-id="ad9ef-110">See Also</span></span>

[<span data-ttu-id="ad9ef-111">ValidateLength-Attribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="ad9ef-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="ad9ef-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="ad9ef-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
