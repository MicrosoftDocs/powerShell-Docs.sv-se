---
title: Hur du deklarera dynamiska parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067934"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="6fe98-102">Deklarera dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="6fe98-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="6fe98-103">Det här exemplet visar hur du definierar dynamiska parametrar som läggs till i cmdleten vid körning.</span><span class="sxs-lookup"><span data-stu-id="6fe98-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="6fe98-104">I det här exemplet på `Department` parametern har lagts till i cmdleten när användaren anger den `Employee` växla parametern.</span><span class="sxs-lookup"><span data-stu-id="6fe98-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="6fe98-105">Mer information om dynamiska parametrar finns i [dynamiska parametrar för cmdleten](./cmdlet-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6fe98-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="6fe98-106">Definiera dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="6fe98-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="6fe98-107">Lägg till i klassdeklarationen cmdlet den [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) gränssnitt som visas.</span><span class="sxs-lookup"><span data-stu-id="6fe98-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="6fe98-108">Anropa den [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) metod som returnerar det objekt som dynamiska parametrar har definierats.</span><span class="sxs-lookup"><span data-stu-id="6fe98-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="6fe98-109">I det här exemplet metoden anropas när den `Employee` parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="6fe98-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

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

3. <span data-ttu-id="6fe98-110">Deklarera en klass som definierar de dynamiska parametrarna som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="6fe98-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="6fe98-111">Du kan använda de attribut som du använde för att deklarera statiska cmdlet-parametrarna för att deklarera dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="6fe98-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

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

## <a name="example"></a><span data-ttu-id="6fe98-112">Exempel</span><span class="sxs-lookup"><span data-stu-id="6fe98-112">Example</span></span>

<span data-ttu-id="6fe98-113">I det här exemplet på `Department` parameter läggs när användaren anger den `Employee` parametern.</span><span class="sxs-lookup"><span data-stu-id="6fe98-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="6fe98-114">Den `Department` parameter är en valfri parameter och ValidateSet attributet används för att ange tillåtna argument.</span><span class="sxs-lookup"><span data-stu-id="6fe98-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6fe98-115">Se även</span><span class="sxs-lookup"><span data-stu-id="6fe98-115">See Also</span></span>

[<span data-ttu-id="6fe98-116">System.Management.Automation.Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="6fe98-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="6fe98-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="6fe98-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="6fe98-118">Cmdlet dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="6fe98-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="6fe98-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6fe98-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)