---
title: Att lägga till och anropa kommandon | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083033"
---
# <a name="adding-and-invoking-commands"></a>Lägga till och anropa kommandon

När du har skapat ett körningsutrymme, kan du lägga till Windows PowerShellcommands och skript för en pipeline och sedan anropa pipelinen synkront eller asynkront.

## <a name="creating-a-pipeline"></a>Skapa en pipeline

 Den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klassen innehåller flera metoder för att lägga till kommandon, parametrar och skript till pipelinen. Du kan anropa pipelinen synkront genom att anropa en överlagring för den [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metoden eller asynkront genom att anropa en överlagring för den [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) och sedan den [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metod.

### <a name="addcommand"></a>AddCommand

1. Skapa en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Lägg till det kommando som du vill köra.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Anropa kommandot.

   ```csharp
   ps.Invoke();
   ```

 Om du anropar den [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metod som är mer än en gång innan du anropar den [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metod, resultatet av den första kommandot skickas till andra och så vidare. Om du inte vill skicka resultatet av en föregående kommando för att ett kommando lägger du till den genom att anropa den [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) i stället.

### <a name="addparameter"></a>AddParameter

 Föregående exempel körs ett enda kommando utan några parametrar. Du kan lägga till parametrar i kommandot med hjälp av den [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metod till exempel följande kod hämtar en lista över alla processer som namnges `PowerShell` som körs på den datorn.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Du kan lägga till ytterligare parametrar genom att anropa [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) upprepade gånger.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 Du kan också lägga till en ordlista över parameternamn och värden som genom att anropa den [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) metod.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Du kan simulera batchbearbetning med hjälp av den [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metod, som lägger till en ytterligare instruktion i slutet av din pipeline för följande kod hämtar en lista över processer som körs med namnet `PowerShell`, och sedan hämtar listan över aktiva tjänster.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Du kan köra ett befintligt skript genom att anropa den [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metod. I följande exempel lägger till ett skript till pipelinen och kör den. Det här exemplet förutsätter att det finns redan ett skript som heter `MyScript.ps1` i en mapp med namnet `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Det finns också en version av den [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metod som tar en boolesk parameter som heter `useLocalScope`. Om den här parametern anges till `true`, och sedan skriptet körs i det lokala scopet. Följande kod körs skriptet i det lokala scopet.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Anropa en pipeline synkront

 När du lägger till element i pipelinen anropar den. Om du vill anropa pipelinen synkront du anropar en överlagring för den [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metod. I följande exempel visar hur du synkroniserat anropa en pipeline.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>Anropa en pipeline asynkront

 Du anropar en pipeline asynkront genom att anropa en överlagring för den [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) att skapa en [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) objektet och sedan anropa den [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metod.

 I följande exempel visas hur du anropar en pipeline asynkront.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>Se även

 [Skapa en InitialSessionState](./creating-an-initialsessionstate.md)

 [Skapa en begränsad körningsutrymme](./creating-a-constrained-runspace.md)
