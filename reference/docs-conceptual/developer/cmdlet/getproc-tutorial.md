---
ms.date: 09/13/2016
ms.topic: reference
title: Självstudie om GetProc
description: Självstudie om GetProc
ms.openlocfilehash: 9379e791dd5361fcf5b79061bf0a601ebeb84f42
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652780"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="4db95-103">Självstudie om GetProc</span><span class="sxs-lookup"><span data-stu-id="4db95-103">GetProc Tutorial</span></span>

<span data-ttu-id="4db95-104">Det här avsnittet innehåller en själv studie kurs om hur du skapar en Get-Proc-cmdlet som liknar cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4db95-104">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="4db95-105">Den här självstudien innehåller fragment med kod som illustrerar hur cmdlets implementeras och en förklaring av koden.</span><span class="sxs-lookup"><span data-stu-id="4db95-105">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="4db95-106">Avsnitt i den här självstudien</span><span class="sxs-lookup"><span data-stu-id="4db95-106">Topics in this Tutorial</span></span>

<span data-ttu-id="4db95-107">Avsnitten i den här självstudien är utformade för att läsas sekventiellt, med varje ämne som bygger på vad som diskuterades i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="4db95-107">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="4db95-108">[Skapa en cmdlet utan parametrar](./creating-a-cmdlet-without-parameters.md) I det här avsnittet beskrivs hur du skapar en-cmdlet som hämtar information från den lokala datorn utan att använda parametrar, och sedan skriver informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4db95-108">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="4db95-109">[Lägga till parametrar som bearbetar Command-Line-Indatatyp](./adding-parameters-that-process-command-line-input.md) I det här avsnittet beskrivs hur du lägger till en parameter i Get-Proc cmdlet så att cmdleten kan bearbeta indatatyper baserat på explicita objekt som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4db95-109">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="4db95-110">Implementeringen som beskrivs här hämtar processer baserat på deras namn och skriver sedan informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4db95-110">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="4db95-111">[Lägga till parametrar som bearbetar pipeline-inflöden](./adding-parameters-that-process-pipeline-input.md) I det här avsnittet beskrivs hur du lägger till en parameter i Get-Proc-cmdleten så att cmdleten kan bearbeta objekt som skickas till den via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4db95-111">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="4db95-112">Implementerings-cmdleten som beskrivs här hämtar processer baserat på objekt som skickas till cmdleten och skriver sedan informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4db95-112">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="4db95-113">[Lägga till fel rapportering som inte avslutas till din cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) I det här avsnittet beskrivs hur du lägger till fel rapportering som inte avslutas till en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4db95-113">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="4db95-114">Implementeringen som beskrivs här identifierar fel som inträffar när indata bearbetas och en felpost skrivs till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="4db95-114">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="4db95-115">Se även</span><span class="sxs-lookup"><span data-stu-id="4db95-115">See Also</span></span>

[<span data-ttu-id="4db95-116">Skapa en cmdlet utan parametrar</span><span class="sxs-lookup"><span data-stu-id="4db95-116">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="4db95-117">Lägga till parametrar som bearbetar Command-Line-Indatatyp</span><span class="sxs-lookup"><span data-stu-id="4db95-117">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="4db95-118">Lägga till parametrar som bearbetar pipelineindata</span><span class="sxs-lookup"><span data-stu-id="4db95-118">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="4db95-119">Lägga till fel rapportering som inte avslutas till din cmdlet</span><span class="sxs-lookup"><span data-stu-id="4db95-119">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="4db95-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4db95-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
