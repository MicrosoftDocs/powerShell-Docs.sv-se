---
title: Så här deklarerar du dynamiska parametrar | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8839aa8841bf94a9b7f8f930ca315fe0ccedb30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784188"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="2835f-102">Deklarera dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="2835f-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="2835f-103">Det här exemplet visar hur du definierar dynamiska parametrar som läggs till i cmdleten vid körning.</span><span class="sxs-lookup"><span data-stu-id="2835f-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="2835f-104">I det här exemplet `Department` läggs parametern till i cmdleten när användaren anger `Employee` växlings parametern.</span><span class="sxs-lookup"><span data-stu-id="2835f-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="2835f-105">Mer information om dynamiska parametrar finns i [cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2835f-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="2835f-106">Definiera dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="2835f-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="2835f-107">I cmdlet-klassens deklaration lägger du till gränssnittet [system. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) enligt vad som visas.</span><span class="sxs-lookup"><span data-stu-id="2835f-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="2835f-108">Anropa metoden [system. Management. Automation. Idynamicparameters. Getdynamicparameters \*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) som returnerar det objekt där dynamiska parametrar har definierats.</span><span class="sxs-lookup"><span data-stu-id="2835f-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="2835f-109">I det här exemplet anropas metoden när `Employee` parametern anges.</span><span class="sxs-lookup"><span data-stu-id="2835f-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="2835f-110">Deklarera en klass som definierar de dynamiska parametrar som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="2835f-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="2835f-111">Du kan använda de attribut som du använde för att deklarera de statiska cmdlet-parametrarna för att deklarera dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="2835f-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="2835f-112">Exempel</span><span class="sxs-lookup"><span data-stu-id="2835f-112">Example</span></span>

<span data-ttu-id="2835f-113">I det här exemplet `Department` läggs parametern till när användaren anger `Employee` parametern.</span><span class="sxs-lookup"><span data-stu-id="2835f-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="2835f-114">`Department`Parametern är en valfri parameter och ValidateSet-attributet används för att ange tillåtna argument.</span><span class="sxs-lookup"><span data-stu-id="2835f-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="2835f-115">Se även</span><span class="sxs-lookup"><span data-stu-id="2835f-115">See Also</span></span>

[<span data-ttu-id="2835f-116">System. Management. Automation. Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="2835f-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="2835f-117">System. Management. Automation. Idynamicparameters. Getdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="2835f-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="2835f-118">Dynamiska cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="2835f-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="2835f-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2835f-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
