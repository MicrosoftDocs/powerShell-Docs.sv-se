---
title: Lägga till och anropa kommandon | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357759"
---
# <a name="adding-and-invoking-commands"></a>Lägga till och anropa kommandon

När du har skapat en körnings utrymme kan du lägga till Windows-PowerShellcommands och skript i en pipeline och sedan anropa pipelinen synkront eller asynkront.

## <a name="creating-a-pipeline"></a>Skapa en pipeline

 Klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) innehåller flera metoder för att lägga till kommandon, parametrar och skript i pipelinen. Du kan anropa pipelinen synkront genom att anropa en överlagring av metoden [system. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) eller asynkront genom att anropa en överlagring av [system. Management. Automation. PowerShell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) och sedan metoden [system. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

### <a name="addcommand"></a>AddCommand

1. Skapa ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Lägg till kommandot som du vill köra.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Anropa kommandot.

   ```csharp
   ps.Invoke();
   ```

 Om du anropar metoden [system. Management. Automation. PowerShell. Addcommand *](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) mer än en gång innan du anropar metoden [system. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) är resultatet av det första kommandot skickas till det andra, och så vidare. Om du inte vill skicka vidare resultatet av ett tidigare kommando till ett kommando lägger du till det genom att anropa [system. Management. Automation. PowerShell. Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) i stället.

### <a name="addparameter"></a>AddParameter

 I föregående exempel körs ett enda kommando utan några parametrar. Du kan lägga till parametrar till kommandot med hjälp av metoden [system. Management. Automation. Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) , exempel: följande kod hämtar en lista över alla processer som heter `PowerShell` körs på datorn.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Du kan lägga till ytterligare parametrar genom att anropa [system. Management. Automation. Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) upprepade gånger.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 Du kan också lägga till en ord lista med parameter namn och värden genom att anropa metoden [system. Management. Automation. PowerShell. AddParameters *](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Du kan simulera batching med hjälp av metoden [system. Management. Automation. PowerShell. Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , som lägger till ytterligare en instruktion i slutet av pipelinen. följande kod hämtar en lista över processer som körs med namnet `PowerShell`och hämtar sedan listan över tjänster som körs.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Du kan köra ett befintligt skript genom att anropa metoden [system. Management. Automation. PowerShell. Addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) . I följande exempel läggs ett skript till i pipelinen och körs. Det här exemplet förutsätter att det redan finns ett skript med namnet `MyScript.ps1` i en mapp med namnet `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Det finns också en version av metoden [system. Management. Automation. PowerShell. Addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) som tar en boolesk parameter med namnet `useLocalScope`. Om den här parametern är inställd på `true`körs skriptet i det lokala omfånget. Följande kod kommer att köra skriptet i det lokala omfånget.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Anropa en pipeline synkront

 När du har lagt till element i pipelinen anropar du det. Om du vill anropa pipelinen synkront anropar du en överlagring av metoden [system. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) . I följande exempel visas hur du synkront anropar en pipeline.

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

 Du anropar en pipeline asynkront genom att anropa en överlagring av [system. Management. Automation. PowerShell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) för att skapa ett [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) -objekt och sedan anropa metoden [system. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

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

 [Skapa en begränsad körnings utrymme](./creating-a-constrained-runspace.md)
