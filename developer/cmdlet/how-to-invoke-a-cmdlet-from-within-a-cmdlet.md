---
title: Hur du anropar en Cmdlet från inom en Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055911"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Anropa en cmdlet inifrån en cmdlet

Det här exemplet visar hur du anropar en cmdlet från inom en annan cmdlet, där du kan lägga till funktioner för anropade cmdlet: en till den cmdlet som du utvecklar. I det här exemplet på `Get-Process` cmdlet anropas för att få de processer som körs på den lokala datorn. Anropet till den `Get-Process` cmdlet är likvärdiga med följande kommando. Detta kommando hämtar alla processer med namn som börjar med tecknen ”a” till ”t”.

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Du kan anropa dessa cmdlets som härleds direkt från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klass. Du kan inte anropa en cmdlet som härleds från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klass.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Anropa en cmdlet från inom en cmdlet

1. Se till att sammansättningen som definierar cmdlet anropas refereras och att rätt `using` instruktionen har lagts till. I det här exemplet läggs följande namnrymder.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Skapa en ny instans av cmdlet anropas i den inkommande metoden-cmdlet: ens bearbetades. I det här exemplet, ett objekt av typen [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) skapas tillsammans med den sträng som innehåller de argument som används när cmdleten har anropats.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Anropa den [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metoden för att anropa den `Get-Process` cmdlet.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Exempel

I det här exemplet på `Get-Process` cmdlet anropas inifrån den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -metoden för en cmdlet.

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

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
