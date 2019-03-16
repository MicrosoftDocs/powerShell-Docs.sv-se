---
title: Cmdlet-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058053"
---
# <a name="cmdlet-samples"></a><span data-ttu-id="8b76f-102">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="8b76f-102">Cmdlet Samples</span></span>

<span data-ttu-id="8b76f-103">Det här avsnittet beskrivs exempelkod som har angetts i Windows PowerShell 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="8b76f-103">This section describes sample code that is provided in the Windows PowerShell 2.0 SDK.</span></span> <span data-ttu-id="8b76f-104">Du kan kopiera koden från avsnitten i det här avsnittet eller öppna källfilerna som installeras med SDK: N.</span><span class="sxs-lookup"><span data-stu-id="8b76f-104">You can copy code from the topics in this section, or open the source files installed with the SDK.</span></span> <span data-ttu-id="8b76f-105">Den [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) tillhandahåller ReadMe-filerna, källfiler och Visual Studio projektfiler för varje exempel.</span><span class="sxs-lookup"><span data-stu-id="8b76f-105">The [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) provides ReadMe files, source files, and Visual Studio project files for each sample.</span></span> <span data-ttu-id="8b76f-106">Med SDK för installerat kan du hitta exempel under den `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` mapp.</span><span class="sxs-lookup"><span data-stu-id="8b76f-106">With the SDK installed, you can find the samples under the `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folder.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8b76f-107">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="8b76f-107">In This Section</span></span>

<span data-ttu-id="8b76f-108">[GetProcessSample01 exempel](./getprocesssample01-sample.md) det här exemplet visas hur du skriver en cmdlet som hämtar processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8b76f-108">[GetProcessSample01 Sample](./getprocesssample01-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span>

<span data-ttu-id="8b76f-109">[GetProcessSample02 exempel](./getprocesssample02-sample.md) det här exemplet visas hur du skriver en cmdlet som hämtar processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8b76f-109">[GetProcessSample02 Sample](./getprocesssample02-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="8b76f-110">Det ger en namnparameter som kan användas för att ange processerna som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="8b76f-110">It provides a Name parameter that can be used to specify the processes to be retrieved.</span></span>

<span data-ttu-id="8b76f-111">[GetProcessSample03 exempel](./getprocesssample03-sample.md) det här exemplet visas hur du skriver en cmdlet som hämtar processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8b76f-111">[GetProcessSample03 Sample](./getprocesssample03-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="8b76f-112">Det ger en namnparameter som kan ta emot ett objekt från pipelinen eller ett värde från en egenskap för ett objekt vars egenskapsnamnet är samma som parameternamnet.</span><span class="sxs-lookup"><span data-stu-id="8b76f-112">It provides a Name parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span>

<span data-ttu-id="8b76f-113">[GetProcessSample04 exempel](./getprocesssample04-sample.md) det här exemplet visas hur du skriver en cmdlet som hämtar processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8b76f-113">[GetProcessSample04 Sample](./getprocesssample04-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="8b76f-114">Den genererar en oändliga fel om ett fel inträffar vid hämtning av en process.</span><span class="sxs-lookup"><span data-stu-id="8b76f-114">It generates a nonterminating error if an error occurs while retrieving a process.</span></span>

<span data-ttu-id="8b76f-115">[GetProcessSample05 exempel](./getprocesssample05-sample.md) detta exempel visar en fullständig version av cmdleten Get-processen.</span><span class="sxs-lookup"><span data-stu-id="8b76f-115">[GetProcessSample05 Sample](./getprocesssample05-sample.md) This sample shows a complete version of the Get-Proc cmdlet.</span></span>

<span data-ttu-id="8b76f-116">[StopProcessSample01 exempel](./stopprocesssample01-sample.md) i det här exemplet visar hur du skriver en cmdlet som efterfrågar feedback från användaren innan den försöker stoppa en process och hur du implementerar en `PassThru` parameter som anger att användaren vill cmdleten returnerar en objekt.</span><span class="sxs-lookup"><span data-stu-id="8b76f-116">[StopProcessSample01 Sample](./stopprocesssample01-sample.md) This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object.</span></span>

<span data-ttu-id="8b76f-117">[StopProcessSample02 exempel](./stopprocesssample02-sample.md) det här exemplet visas hur du skriver en cmdlet som skriver utförlig, felsökning och varningsmeddelanden när processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8b76f-117">[StopProcessSample02 Sample](./stopprocesssample02-sample.md) This sample shows how to write a cmdlet that writes debug, verbose, and warning messages while stopping processes on the local computer.</span></span>

<span data-ttu-id="8b76f-118">[StopProcessSample03 exempel](./stopprocesssample03-sample.md) det här exemplet visas hur du skriver en cmdlet vars parametrar har alias och som stöd för jokertecken.</span><span class="sxs-lookup"><span data-stu-id="8b76f-118">[StopProcessSample03 Sample](./stopprocesssample03-sample.md) This sample shows how to write a cmdlet whose parameters have aliases and that support wildcard characters.</span></span>

<span data-ttu-id="8b76f-119">[StopProcessSample04 exempel](./stopprocesssample04-sample.md) det här exemplet visas hur du skriver en cmdlet som deklarerar parameteruppsättningar, anger standardparametern anger och kan acceptera en indataobjektet.</span><span class="sxs-lookup"><span data-stu-id="8b76f-119">[StopProcessSample04 Sample](./stopprocesssample04-sample.md) This sample shows how to write a cmdlet that declares parameter sets, specifies the default parameter set, and can accept an input object.</span></span>

<span data-ttu-id="8b76f-120">[Events01 exempel](./events01-sample.md) i det här exemplet visar hur du skapar en cmdlet som används att registrera dig för händelser som skapats av [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="8b76f-120">[Events01 Sample](./events01-sample.md) This sample shows how to create a cmdlet that allows the user to register for events raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="8b76f-121">Med denna cmdlet kan användarna till exempel registrera en åtgärd som ska köras när en fil skapas under en viss katalog.</span><span class="sxs-lookup"><span data-stu-id="8b76f-121">With this cmdlet users can, for example, register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="8b76f-122">Det här exemplet kommer från den [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) basklassen.</span><span class="sxs-lookup"><span data-stu-id="8b76f-122">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b76f-123">Se även</span><span class="sxs-lookup"><span data-stu-id="8b76f-123">See Also</span></span>

[<span data-ttu-id="8b76f-124">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8b76f-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
