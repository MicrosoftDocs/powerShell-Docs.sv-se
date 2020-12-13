---
ms.date: 09/13/2016
ms.topic: reference
title: Deklarera dynamiska parametrar
description: Deklarera dynamiska parametrar
ms.openlocfilehash: 0f5a8f249b414663aa9702a908ea5c8ca24755ff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667087"
---
# <a name="how-to-declare-dynamic-parameters"></a>Deklarera dynamiska parametrar

Det här exemplet visar hur du definierar dynamiska parametrar som läggs till i cmdleten vid körning. I det här exemplet `Department` läggs parametern till i cmdleten när användaren anger `Employee` växlings parametern. Mer information om dynamiska parametrar finns i [cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).

## <a name="to-define-dynamic-parameters"></a>Definiera dynamiska parametrar

1. I cmdlet-klassens deklaration lägger du till gränssnittet [system. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) enligt vad som visas.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Anropa metoden [system. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) som returnerar det objekt där dynamiska parametrar har definierats. I det här exemplet anropas metoden när `Employee` parametern anges.

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

3. Deklarera en klass som definierar de dynamiska parametrar som ska läggas till. Du kan använda de attribut som du använde för att deklarera de statiska cmdlet-parametrarna för att deklarera dynamiska parametrar.

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

I det här exemplet `Department` läggs parametern till när användaren anger `Employee` parametern. `Department`Parametern är en valfri parameter och ValidateSet-attributet används för att ange tillåtna argument.

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

[System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Dynamiska cmdlet-parametrar](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
