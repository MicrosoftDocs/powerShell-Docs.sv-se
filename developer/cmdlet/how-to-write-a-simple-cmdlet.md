---
title: Hur du skriver en enkel Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 2fc1a3947ca6076387ea85d7f8ba9018ed7385a0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849534"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="905b5-102">Hur du skriver en cmdlet</span><span class="sxs-lookup"><span data-stu-id="905b5-102">How to write a cmdlet</span></span>

<span data-ttu-id="905b5-103">Den här artikeln visar hur du skriver en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="905b5-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="905b5-104">Den **skicka hälsning** cmdlet tar ett enda användarnamn som indata och sedan skriver en hälsning för denna användare.</span><span class="sxs-lookup"><span data-stu-id="905b5-104">The **Send-Greeting** cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="905b5-105">Även om cmdleten inte gör mycket arbete visar det här exemplet de viktigaste avsnitten av en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="905b5-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="905b5-106">Steg för att skriva en cmdlet</span><span class="sxs-lookup"><span data-stu-id="905b5-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="905b5-107">Du kan deklarera klassen som en cmdlet genom att använda den **Cmdlet** attribut.</span><span class="sxs-lookup"><span data-stu-id="905b5-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="905b5-108">Den **Cmdlet** attributet anger verb och substantiv för cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="905b5-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="905b5-109">Mer information om den **Cmdlet** attributet, se [CmdletAttribute deklarationen](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="905b5-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="905b5-110">Ange namnet på klassen.</span><span class="sxs-lookup"><span data-stu-id="905b5-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="905b5-111">Ange att cmdleten härleds från någon av följande klasser:</span><span class="sxs-lookup"><span data-stu-id="905b5-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="905b5-112">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="905b5-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="905b5-113">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="905b5-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="905b5-114">Om du vill definiera parametrar för cmdleten använda det **parametern** attribut.</span><span class="sxs-lookup"><span data-stu-id="905b5-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="905b5-115">I det här fallet krävs bara en parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="905b5-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="905b5-116">Mer information om den **parametern** attributet, se [ParameterAttribute deklarationen](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="905b5-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="905b5-117">Åsidosätta indata metoden som bearbetar indata bearbetades.</span><span class="sxs-lookup"><span data-stu-id="905b5-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="905b5-118">I det här fallet den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden åsidosätts.</span><span class="sxs-lookup"><span data-stu-id="905b5-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="905b5-119">Om du vill skriva hälsningen använder-metoden [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="905b5-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="905b5-120">Hälsningen visas i följande format:</span><span class="sxs-lookup"><span data-stu-id="905b5-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="905b5-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="905b5-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify and
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

## <a name="see-also"></a><span data-ttu-id="905b5-122">Se även</span><span class="sxs-lookup"><span data-stu-id="905b5-122">See also</span></span>

[<span data-ttu-id="905b5-123">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="905b5-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="905b5-124">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="905b5-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="905b5-125">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="905b5-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="905b5-126">System.Management.Automation.Cmdlet.WriteObject</span><span class="sxs-lookup"><span data-stu-id="905b5-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="905b5-127">CmdletAttribute deklaration</span><span class="sxs-lookup"><span data-stu-id="905b5-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="905b5-128">ParameterAttribute deklaration</span><span class="sxs-lookup"><span data-stu-id="905b5-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="905b5-129">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="905b5-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
