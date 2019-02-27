---
title: Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844746"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="99347-102">Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="99347-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="99347-103">Du kan skapa ett arbetsflöde genom att skriva ett Windows PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="99347-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="99347-104">Använd nyckelord för arbetsflöde följt av ett namn för arbetsflödet innan innehållet i skriptet för att skapa ett arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="99347-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="99347-105">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="99347-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="99347-106">Du hittar arbetsflödet i på samma sätt som andra Windows PowerShell-kommando.</span><span class="sxs-lookup"><span data-stu-id="99347-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="99347-107">Implementera parallell- och</span><span class="sxs-lookup"><span data-stu-id="99347-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="99347-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) stöder körning av aktiviteter parallellt.</span><span class="sxs-lookup"><span data-stu-id="99347-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="99347-109">För att implementera den här funktionen i ett Windows PowerShell-skript, använda den `parallel` nyckelordet framför ett skriptblock.</span><span class="sxs-lookup"><span data-stu-id="99347-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="99347-110">Du kan också använda den `foreach -parallel` konstruktion att gå igenom en uppsättning objekt parallellt.</span><span class="sxs-lookup"><span data-stu-id="99347-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="99347-111">Ange den gruppen med aktiviteter inom ett skriptblock och föregå blocket med nyckelordet sekvens för att köra en grupp med aktiviteter i sekventiell ordning inom en parallell block.</span><span class="sxs-lookup"><span data-stu-id="99347-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="99347-112">Ansluta datorer till en domän</span><span class="sxs-lookup"><span data-stu-id="99347-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="99347-113">Följande skript skapar ett arbetsflöde som kontrollerar domänen för en grupp användardefinierade datorer och kopplar dem till en domän om de inte redan är ansluten och kontrollerar status igen.</span><span class="sxs-lookup"><span data-stu-id="99347-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="99347-114">Det här är en skriptversion av XAML-arbetsflödet som beskrivs i [skapar ett arbetsflöde med Windows PowerShell aktiviteter](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="99347-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

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