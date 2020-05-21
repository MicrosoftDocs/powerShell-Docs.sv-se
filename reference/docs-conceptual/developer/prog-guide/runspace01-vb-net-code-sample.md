---
title: Kod exempel för Runspace01 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12ee5382-95ba-41c7-8291-7f69a6f63514
caps.latest.revision: 7
ms.openlocfilehash: ce6bdec379a7ba9bf9b088c79a08ad5cef5da80b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560312"
---
# <a name="runspace01-vbnet-code-sample"></a><span data-ttu-id="cfe54-102">Runspace01 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="cfe54-102">Runspace01 (VB.NET) Code Sample</span></span>

<span data-ttu-id="cfe54-103">Här är kod exemplen för körnings utrymme som beskrivs i [skapa ett konsol program som kör ett angivet kommando](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="cfe54-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="cfe54-104">För att göra detta anropar programmet en körnings utrymme och anropar sedan ett kommando.</span><span class="sxs-lookup"><span data-stu-id="cfe54-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="cfe54-105">(Observera att det här programmet inte anger körnings utrymme konfigurations information eller inte uttryckligen skapar en pipeline.) Kommandot som anropas är `Get-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cfe54-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline.) The command that is invoked is the `Get-Process` cmdlet.</span></span>

## <a name="code-sample"></a><span data-ttu-id="cfe54-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="cfe54-106">Code Sample</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cfe54-107">Se även</span><span class="sxs-lookup"><span data-stu-id="cfe54-107">See Also</span></span>

[<span data-ttu-id="cfe54-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cfe54-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
