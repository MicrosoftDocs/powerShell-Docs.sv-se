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
ms.openlocfilehash: 997b1d6841ff014093ba54bf7a1db7b0b7d746b8
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564814"
---
# <a name="runspace02-sample"></a><span data-ttu-id="0a7c9-102">Runspace02 – exempel</span><span class="sxs-lookup"><span data-stu-id="0a7c9-102">Runspace02 Sample</span></span>

<span data-ttu-id="0a7c9-103">Det här exemplet visar hur du kan använda-cmdlet: arna [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och [sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) med hjälp av klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="0a7c9-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="0a7c9-104">Cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) returnerar [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objekt för varje process som körs på den lokala datorn och `Sort-Object` sorterar objekten baserat på deras [system.Diagnostics.process.ID \*](/dotnet/api/System.Diagnostics.Process.Id) -egenskap.</span><span class="sxs-lookup"><span data-stu-id="0a7c9-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="0a7c9-105">Resultatet av dessa kommandon visas med hjälp av en [system. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -kontroll.</span><span class="sxs-lookup"><span data-stu-id="0a7c9-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a7c9-106">Krav</span><span class="sxs-lookup"><span data-stu-id="0a7c9-106">Requirements</span></span>

<span data-ttu-id="0a7c9-107">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="0a7c9-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0a7c9-108">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="0a7c9-108">Demonstrates</span></span>

<span data-ttu-id="0a7c9-109">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="0a7c9-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="0a7c9-110">Skapar ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt för att köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="0a7c9-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="0a7c9-111">Lägger till kommandon i pipelinen för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="0a7c9-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="0a7c9-112">Köra kommandona synkront.</span><span class="sxs-lookup"><span data-stu-id="0a7c9-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="0a7c9-113">Med hjälp av en [system. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -kontroll för att visa resultatet av kommandona i ett Windows Forms-program.</span><span class="sxs-lookup"><span data-stu-id="0a7c9-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="0a7c9-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="0a7c9-114">Example</span></span>

<span data-ttu-id="0a7c9-115">I det här exemplet körs cmdletarna [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och [sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) synkront i standard-körnings utrymme som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0a7c9-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="0a7c9-116">Utdata visas i ett formulär med hjälp av en [system. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -kontroll.</span><span class="sxs-lookup"><span data-stu-id="0a7c9-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0a7c9-117">Se även</span><span class="sxs-lookup"><span data-stu-id="0a7c9-117">See Also</span></span>

[<span data-ttu-id="0a7c9-118">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="0a7c9-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
