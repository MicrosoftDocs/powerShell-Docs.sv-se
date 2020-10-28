---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace01 (VB.NET) – kodexempel
description: Runspace01 (VB.NET) – kodexempel
ms.openlocfilehash: 69211662c166c40e6e99e287083f7bd53f9f536f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653860"
---
# <a name="runspace01-vbnet-code-sample"></a>Runspace01 (VB.NET) – kodexempel

Här är kod exemplen för körnings utrymme som beskrivs i [skapa ett konsol program som kör ett angivet kommando](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program). För att göra detta anropar programmet en körnings utrymme och anropar sedan ett kommando. (Observera att det här programmet inte anger körnings utrymme konfigurations information eller inte uttryckligen skapar en pipeline.) Kommandot som anropas är `Get-Process` cmdleten.

## <a name="code-sample"></a>Kod exempel

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Module Runspace01
        ' <summary>
        ' This sample uses the RunspaceInvoke class to execute
        ' the get-process cmdlet synchronously. The name and
        ' handlecount are then extracted from  the PSObjects
        ' returned and displayed.
        ' </summary>
        ' <param name="args">Unused</param>
        ' <remarks>
        ' This sample demonstrates the following:
        ' 1. Creating an instance of the RunspaceInvoke class.
        ' 2. Using this instance to invoke a PowerShell command.
        ' 3. Using PSObject to extract properties from the objects
        '    returned by this command.
        ' </remarks>
        Sub Main()
            ' Create an instance of the RunspaceInvoke class.
            ' This takes care of all building all of the other
            ' data structures needed...
            Dim invoker As RunspaceInvoke = New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            For Each result As PSObject In invoker.Invoke("get-process")
                Console.WriteLine("{0,-20} {1}", _
                    result.Members("ProcessName").Value, _
                    result.Members("HandleCount").Value)
            Next
            System.Console.WriteLine("Hit any key to exit...")
            System.Console.ReadKey()
        End Sub
    End Module
End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace01.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace01.vb#L09-L53 "Runspace01.vb")] -->

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
