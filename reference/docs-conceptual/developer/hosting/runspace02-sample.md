---
title: Runspace02-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353104"
---
# <a name="runspace02-sample"></a>Runspace02 – exempel

Det här exemplet visar hur du kan använda-cmdlet: arna [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och [sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) med hjälp av klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) . Cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) returnerar [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objekt för varje process som körs på den lokala datorn och `Sort-Object` sorterar objekten baserat på deras [system.Diagnostics.process.ID *](/dotnet/api/System.Diagnostics.Process.Id) -egenskap. Resultatet av dessa kommandon visas med hjälp av en [system. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -kontroll.

## <a name="requirements"></a>Krav

Det här exemplet kräver Windows PowerShell 2,0.

## <a name="demonstrates"></a>Visat

Det här exemplet demonstrerar följande.

- Skapar ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt för att köra kommandon.

- Lägger till kommandon i pipelinen för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Köra kommandona synkront.

- Med hjälp av en [system. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -kontroll för att visa resultatet av kommandona i ett Windows Forms-program.

## <a name="example"></a>Exempel

I det här exemplet körs cmdletarna [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och [sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) synkront i standard-körnings utrymme som tillhandahålls av Windows PowerShell. Utdata visas i ett formulär med hjälp av en [system. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -kontroll.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-värdprogram](./writing-a-windows-powershell-host-application.md)