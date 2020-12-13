---
ms.date: 01/15/2019
ms.topic: reference
title: Skriva en enkel cmdlet
description: Skriva en enkel cmdlet
ms.openlocfilehash: 59dce5d797f80647e0b70a1f80faf67198652082
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646499"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="6b62e-103">Så här skriver du en cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b62e-103">How to write a cmdlet</span></span>

<span data-ttu-id="6b62e-104">Den här artikeln visar hur du skriver en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b62e-104">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="6b62e-105">`Send-Greeting`Cmdlet: en använder ett enda användar namn som indata och skriver sedan en hälsning till användaren.</span><span class="sxs-lookup"><span data-stu-id="6b62e-105">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="6b62e-106">Även om cmdleten inte fungerar mycket, visar det här exemplet de viktigaste avsnitten i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b62e-106">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="6b62e-107">Steg för att skriva en cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b62e-107">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="6b62e-108">Om du vill deklarera klassen som en-cmdlet använder du **cmdlet** -attributet.</span><span class="sxs-lookup"><span data-stu-id="6b62e-108">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="6b62e-109">**Cmdlet** -attributet anger verbet och Substantiv för cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="6b62e-109">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="6b62e-110">Mer information om **cmdlet** -attributet finns i [CmdletAttribute-deklaration](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b62e-110">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="6b62e-111">Ange namnet på klassen.</span><span class="sxs-lookup"><span data-stu-id="6b62e-111">Specify the name of the class.</span></span>

3. <span data-ttu-id="6b62e-112">Ange att cmdleten härleds från någon av följande klasser:</span><span class="sxs-lookup"><span data-stu-id="6b62e-112">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="6b62e-113">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b62e-113">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="6b62e-114">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="6b62e-114">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="6b62e-115">Om du vill definiera parametrarna för cmdleten använder du attributet **parameter** .</span><span class="sxs-lookup"><span data-stu-id="6b62e-115">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="6b62e-116">I det här fallet anges bara en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="6b62e-116">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="6b62e-117">Mer information om attributet **parameter** finns i ParameterAttribute- [deklaration](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b62e-117">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="6b62e-118">Åsidosätt den metod för bearbetning av indata som bearbetar indata.</span><span class="sxs-lookup"><span data-stu-id="6b62e-118">Override the input processing method that processes the input.</span></span> <span data-ttu-id="6b62e-119">I det här fallet åsidosätts metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="6b62e-119">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="6b62e-120">Om du vill skriva hälsningen använder du metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="6b62e-120">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="6b62e-121">Hälsningen visas i följande format:</span><span class="sxs-lookup"><span data-stu-id="6b62e-121">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="6b62e-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="6b62e-122">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6b62e-123">Se även</span><span class="sxs-lookup"><span data-stu-id="6b62e-123">See also</span></span>

[<span data-ttu-id="6b62e-124">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b62e-124">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="6b62e-125">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="6b62e-125">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="6b62e-126">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="6b62e-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="6b62e-127">System. Management. Automation. cmdlet. WriteObject</span><span class="sxs-lookup"><span data-stu-id="6b62e-127">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="6b62e-128">CmdletAttribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="6b62e-128">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="6b62e-129">ParameterAttribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="6b62e-129">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="6b62e-130">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b62e-130">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
