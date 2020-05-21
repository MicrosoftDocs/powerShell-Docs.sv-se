---
title: Skapa ett arbets flöde med hjälp av ett Windows PowerShell-skript | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: cc613240e056e8443b075019cbff6dd15da3716f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557456"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="09260-102">Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="09260-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="09260-103">Du kan skapa ett arbets flöde genom att skriva ett Windows PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="09260-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="09260-104">Om du vill skapa ett arbets flöde använder du arbets flödets nyckelord följt av ett namn för arbets flödet före bröd texten i skriptet.</span><span class="sxs-lookup"><span data-stu-id="09260-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="09260-105">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="09260-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="09260-106">Du hittar arbets flödet på samma sätt som med andra Windows PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="09260-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="09260-107">Implementera parallell och sekvens</span><span class="sxs-lookup"><span data-stu-id="09260-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="09260-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) stöder körning av aktiviteter parallellt.</span><span class="sxs-lookup"><span data-stu-id="09260-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) supports execution of activities in parallel.</span></span> <span data-ttu-id="09260-109">Om du vill implementera den här funktionen i ett Windows PowerShell-skript använder du `parallel` nyckelordet framför ett skript block.</span><span class="sxs-lookup"><span data-stu-id="09260-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="09260-110">Du kan också använda `foreach -parallel` byggnaden för att iterera genom en samling objekt parallellt.</span><span class="sxs-lookup"><span data-stu-id="09260-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="09260-111">Om du vill köra en grupp med aktiviteter i nummerordning i ett parallellt block, omger du den gruppen med aktiviteter i ett-skript block och föregår blocket med nyckelordet Sequence.</span><span class="sxs-lookup"><span data-stu-id="09260-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="09260-112">Ansluta datorer till en domän</span><span class="sxs-lookup"><span data-stu-id="09260-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="09260-113">Följande skript skapar ett arbets flöde som kontrollerar domän status för en grupp med användardefinierade datorer, kopplar dem till en domän om de inte redan är anslutna och kontrollerar sedan statusen igen.</span><span class="sxs-lookup"><span data-stu-id="09260-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>
<span data-ttu-id="09260-114">Det här är en skript version av XAML-arbetsflödet som beskrivs i [skapa ett arbets flöde med Windows PowerShell-aktiviteter](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="09260-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```
