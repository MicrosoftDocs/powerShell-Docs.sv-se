---
title: GetProc självstudien | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068104"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="bab45-102">Självstudie om GetProc</span><span class="sxs-lookup"><span data-stu-id="bab45-102">GetProc Tutorial</span></span>

<span data-ttu-id="bab45-103">Det här avsnittet innehåller en självstudie för att skapa en cmdlet Get-processen som liknar den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bab45-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="bab45-104">Den här självstudien innehåller delar av kod som illustrerar hur cmdletar implementeras och en förklaring av koden.</span><span class="sxs-lookup"><span data-stu-id="bab45-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="bab45-105">Avsnitt i den här självstudien</span><span class="sxs-lookup"><span data-stu-id="bab45-105">Topics in this Tutorial</span></span>

<span data-ttu-id="bab45-106">Ämnena i den här självstudien är avsedda att läsas sekventiellt, med varje avsnitt som bygger på vad som beskrevs i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="bab45-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="bab45-107">[Skapa en Cmdlet utan parametrar](./creating-a-cmdlet-without-parameters.md) i det här avsnittet beskriver hur du skapar en cmdlet som hämtar information från den lokala datorn utan att använda parametrar och skriver informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="bab45-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="bab45-108">[Att lägga till parametrar som processen Command-Line inkommande](./adding-parameters-that-process-command-line-input.md) det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-processen så att cmdleten kan bearbeta indata som baseras på explicita objekt skickades till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="bab45-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="bab45-109">Implementeringen som beskrivs hämtar här processer baserat på deras namn och skriver informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="bab45-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="bab45-110">[Att lägga till parametrar som indata från Pipeline processen](./adding-parameters-that-process-pipeline-input.md) det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-processen så att cmdleten kan bearbeta objekt som skickas till den via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="bab45-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="bab45-111">Cmdleten implementeringen som beskrivs hämtar här processer baserat på objekt som överförs till cmdlet: en och skriver informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="bab45-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="bab45-112">[Att lägga till oändliga felrapportering i din Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) det här avsnittet beskrivs hur du lägger till oändliga fel som rapporterar till en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bab45-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="bab45-113">Implementeringen som beskrivs här identifierar oändliga fel som inträffar när indata och skriver en Felpost till felströmmen.</span><span class="sxs-lookup"><span data-stu-id="bab45-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="bab45-114">Se även</span><span class="sxs-lookup"><span data-stu-id="bab45-114">See Also</span></span>

[<span data-ttu-id="bab45-115">Skapa en Cmdlet utan parametrar</span><span class="sxs-lookup"><span data-stu-id="bab45-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="bab45-116">Att lägga till parametrar som bearbetar av kommandoraden</span><span class="sxs-lookup"><span data-stu-id="bab45-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="bab45-117">Att lägga till parametrar som indata för Process-pipelinen</span><span class="sxs-lookup"><span data-stu-id="bab45-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="bab45-118">Att lägga till oändliga felrapportering i cmdlet:</span><span class="sxs-lookup"><span data-stu-id="bab45-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="bab45-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="bab45-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
