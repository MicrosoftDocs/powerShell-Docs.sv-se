---
ms.date: 09/13/2016
ms.topic: reference
title: Anropa en cmdlet inifrån en cmdlet
description: Anropa en cmdlet inifrån en cmdlet
ms.openlocfilehash: d137ac895f66000329de76a2c16a74b02c0e82ca
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667053"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Anropa en cmdlet inifrån en cmdlet

Det här exemplet visar hur du anropar en cmdlet från en annan cmdlet, vilket gör att du kan lägga till funktionerna i den anropade cmdleten till den cmdlet som du utvecklar. I det här exemplet `Get-Process` anropas cmdleten för att hämta de processer som körs på den lokala datorn. Anropet till `Get-Process` cmdleten motsvarar följande kommando. Det här kommandot hämtar alla processer vars namn börjar med tecknen "a" till "t".

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Du kan bara anropa de cmdlet: ar som härleds direkt från klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . Det går inte att anropa en cmdlet som härleds från klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Anropa en cmdlet inifrån en cmdlet

1. Kontrol lera att sammansättningen som definierar den cmdlet som ska anropas refereras och att lämplig `using` instruktion läggs till. I det här exemplet läggs följande namn områden till.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Skapa en ny instans av cmdleten som ska anropas i den ingångs bearbetnings metoden för cmdleten. I det här exemplet skapas ett objekt av typen [Microsoft. PowerShell. commands. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) tillsammans med strängen som innehåller de argument som används när cmdleten anropas.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Anropa metoden [system. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) för att anropa `Get-Process` cmdleten.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Exempel

I det här exemplet `Get-Process` anropas cmdleten i metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) för en cmdlet.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

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

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
