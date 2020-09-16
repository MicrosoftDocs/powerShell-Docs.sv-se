---
title: Så här skriver du en enkel cmdlet | Microsoft Docs
ms.date: 01/15/2019
ms.openlocfilehash: 2ff0b47454804c9becd6f03ac521946b9596bb8b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784069"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="5f8e8-102">Så här skriver du en cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f8e8-102">How to write a cmdlet</span></span>

<span data-ttu-id="5f8e8-103">Den här artikeln visar hur du skriver en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f8e8-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="5f8e8-104">`Send-Greeting`Cmdlet: en använder ett enda användar namn som indata och skriver sedan en hälsning till användaren.</span><span class="sxs-lookup"><span data-stu-id="5f8e8-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="5f8e8-105">Även om cmdleten inte fungerar mycket, visar det här exemplet de viktigaste avsnitten i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f8e8-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="5f8e8-106">Steg för att skriva en cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f8e8-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="5f8e8-107">Om du vill deklarera klassen som en-cmdlet använder du **cmdlet** -attributet.</span><span class="sxs-lookup"><span data-stu-id="5f8e8-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="5f8e8-108">**Cmdlet** -attributet anger verbet och Substantiv för cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="5f8e8-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="5f8e8-109">Mer information om **cmdlet** -attributet finns i [CmdletAttribute-deklaration](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5f8e8-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="5f8e8-110">Ange namnet på klassen.</span><span class="sxs-lookup"><span data-stu-id="5f8e8-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="5f8e8-111">Ange att cmdleten härleds från någon av följande klasser:</span><span class="sxs-lookup"><span data-stu-id="5f8e8-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="5f8e8-112">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f8e8-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="5f8e8-113">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="5f8e8-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="5f8e8-114">Om du vill definiera parametrarna för cmdleten använder du attributet **parameter** .</span><span class="sxs-lookup"><span data-stu-id="5f8e8-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="5f8e8-115">I det här fallet anges bara en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="5f8e8-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="5f8e8-116">Mer information om attributet **parameter** finns i ParameterAttribute- [deklaration](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5f8e8-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="5f8e8-117">Åsidosätt den metod för bearbetning av indata som bearbetar indata.</span><span class="sxs-lookup"><span data-stu-id="5f8e8-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="5f8e8-118">I det här fallet åsidosätts metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="5f8e8-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="5f8e8-119">Om du vill skriva hälsningen använder du metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="5f8e8-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="5f8e8-120">Hälsningen visas i följande format:</span><span class="sxs-lookup"><span data-stu-id="5f8e8-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="5f8e8-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="5f8e8-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="5f8e8-122">Se även</span><span class="sxs-lookup"><span data-stu-id="5f8e8-122">See also</span></span>

[<span data-ttu-id="5f8e8-123">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f8e8-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="5f8e8-124">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="5f8e8-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="5f8e8-125">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="5f8e8-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="5f8e8-126">System. Management. Automation. cmdlet. WriteObject</span><span class="sxs-lookup"><span data-stu-id="5f8e8-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="5f8e8-127">CmdletAttribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="5f8e8-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="5f8e8-128">ParameterAttribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="5f8e8-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="5f8e8-129">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f8e8-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
