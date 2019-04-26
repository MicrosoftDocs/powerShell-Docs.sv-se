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
# <a name="how-to-declare-dynamic-parameters"></a>Deklarera dynamiska parametrar

Det här exemplet visar hur du definierar dynamiska parametrar som läggs till i cmdleten vid körning. I det här exemplet på `Department` parametern har lagts till i cmdleten när användaren anger den `Employee` växla parametern. Mer information om dynamiska parametrar finns i [dynamiska parametrar för cmdleten](./cmdlet-dynamic-parameters.md).

## <a name="to-define-dynamic-parameters"></a>Definiera dynamiska parametrar

1. Lägg till i klassdeklarationen cmdlet den [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) gränssnitt som visas.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Anropa den [System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) metod som returnerar det objekt som dynamiska parametrar har definierats. I det här exemplet metoden anropas när den `Employee` parameter har angetts.

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

3. Deklarera en klass som definierar de dynamiska parametrarna som ska läggas till. Du kan använda de attribut som du använde för att deklarera statiska cmdlet-parametrarna för att deklarera dynamiska parametrar.

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

## <a name="example"></a>Exempel

I det här exemplet på `Department` parameter läggs när användaren anger den `Employee` parametern. Den `Department` parameter är en valfri parameter och ValidateSet attributet används för att ange tillåtna argument.

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

## <a name="see-also"></a>Se även

[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Cmdlet dynamiska parametrar](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)