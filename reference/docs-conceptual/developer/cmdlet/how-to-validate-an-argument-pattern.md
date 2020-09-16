---
title: Så här verifierar du ett argument mönster | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidatePattern attribute, example
ms.openlocfilehash: 35104e786d4b809a711d97fea52ae0e348dd5ca3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782097"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="092e7-102">Verifiera ett argumentmönster</span><span class="sxs-lookup"><span data-stu-id="092e7-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="092e7-103">Det här exemplet visar hur du anger en validerings regel som Windows PowerShell-körningsmiljön kan använda för att kontrol lera tecknen i parameter argumentet innan cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="092e7-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="092e7-104">Du ställer in den här validerings regeln genom att deklarera ValidatePattern-attributet.</span><span class="sxs-lookup"><span data-stu-id="092e7-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="092e7-105">Mer information om klassen som definierar det här attributet finns i [system. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="092e7-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="092e7-106">Validera ett argument mönster</span><span class="sxs-lookup"><span data-stu-id="092e7-106">To validate an argument pattern</span></span>

- <span data-ttu-id="092e7-107">Lägg till attributet validate som det visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="092e7-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="092e7-108">I det här exemplet anges ett mönster med fyra siffror där varje siffra har värdet 0 till 9.</span><span class="sxs-lookup"><span data-stu-id="092e7-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="092e7-109">Mer information om hur du deklarerar det här attributet finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="092e7-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="092e7-110">Se även</span><span class="sxs-lookup"><span data-stu-id="092e7-110">See Also</span></span>

[<span data-ttu-id="092e7-111">Deklaration av attributet ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="092e7-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="092e7-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="092e7-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
