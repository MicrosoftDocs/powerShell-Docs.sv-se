---
title: Så här skriver du en enkel cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 9bd72e8f97c194c98adb1049f5a966549113fd12
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563896"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="cdf75-102">Så här skriver du en cmdlet</span><span class="sxs-lookup"><span data-stu-id="cdf75-102">How to write a cmdlet</span></span>

<span data-ttu-id="cdf75-103">Den här artikeln visar hur du skriver en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cdf75-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="cdf75-104">`Send-Greeting`Cmdlet: en använder ett enda användar namn som indata och skriver sedan en hälsning till användaren.</span><span class="sxs-lookup"><span data-stu-id="cdf75-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="cdf75-105">Även om cmdleten inte fungerar mycket, visar det här exemplet de viktigaste avsnitten i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cdf75-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="cdf75-106">Steg för att skriva en cmdlet</span><span class="sxs-lookup"><span data-stu-id="cdf75-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="cdf75-107">Om du vill deklarera klassen som en-cmdlet använder du **cmdlet** -attributet.</span><span class="sxs-lookup"><span data-stu-id="cdf75-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="cdf75-108">**Cmdlet** -attributet anger verbet och Substantiv för cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="cdf75-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="cdf75-109">Mer information om **cmdlet** -attributet finns i [CmdletAttribute-deklaration](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="cdf75-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="cdf75-110">Ange namnet på klassen.</span><span class="sxs-lookup"><span data-stu-id="cdf75-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="cdf75-111">Ange att cmdleten härleds från någon av följande klasser:</span><span class="sxs-lookup"><span data-stu-id="cdf75-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="cdf75-112">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="cdf75-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="cdf75-113">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="cdf75-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="cdf75-114">Om du vill definiera parametrarna för cmdleten använder du attributet **parameter** .</span><span class="sxs-lookup"><span data-stu-id="cdf75-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="cdf75-115">I det här fallet anges bara en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="cdf75-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="cdf75-116">Mer information om attributet **parameter** finns i ParameterAttribute- [deklaration](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="cdf75-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="cdf75-117">Åsidosätt den metod för bearbetning av indata som bearbetar indata.</span><span class="sxs-lookup"><span data-stu-id="cdf75-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="cdf75-118">I det här fallet åsidosätts metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="cdf75-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="cdf75-119">Om du vill skriva hälsningen använder du metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="cdf75-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="cdf75-120">Hälsningen visas i följande format:</span><span class="sxs-lookup"><span data-stu-id="cdf75-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="cdf75-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="cdf75-121">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cdf75-122">Se även</span><span class="sxs-lookup"><span data-stu-id="cdf75-122">See also</span></span>

[<span data-ttu-id="cdf75-123">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="cdf75-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="cdf75-124">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="cdf75-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="cdf75-125">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="cdf75-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="cdf75-126">System. Management. Automation. cmdlet. WriteObject</span><span class="sxs-lookup"><span data-stu-id="cdf75-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="cdf75-127">CmdletAttribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="cdf75-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="cdf75-128">ParameterAttribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="cdf75-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="cdf75-129">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="cdf75-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
