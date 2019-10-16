---
title: GetProc-självstudie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355533"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="a858a-102">Självstudie om GetProc</span><span class="sxs-lookup"><span data-stu-id="a858a-102">GetProc Tutorial</span></span>

<span data-ttu-id="a858a-103">Det här avsnittet innehåller en själv studie kurs om hur du skapar en get-proc-cmdlet som liknar cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a858a-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="a858a-104">Den här självstudien innehåller fragment med kod som illustrerar hur cmdlets implementeras och en förklaring av koden.</span><span class="sxs-lookup"><span data-stu-id="a858a-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="a858a-105">Avsnitt i den här självstudien</span><span class="sxs-lookup"><span data-stu-id="a858a-105">Topics in this Tutorial</span></span>

<span data-ttu-id="a858a-106">Avsnitten i den här självstudien är utformade för att läsas sekventiellt, med varje ämne som bygger på vad som diskuterades i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="a858a-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="a858a-107">[Skapa en cmdlet utan parametrar](./creating-a-cmdlet-without-parameters.md) I det här avsnittet beskrivs hur du skapar en-cmdlet som hämtar information från den lokala datorn utan att använda parametrar, och sedan skriver informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a858a-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="a858a-108">[Lägga till parametrar som bearbetar kommando rads indatatyper](./adding-parameters-that-process-command-line-input.md) I det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-proc så att cmdleten kan bearbeta indatatyper baserat på explicita objekt som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a858a-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="a858a-109">Implementeringen som beskrivs här hämtar processer baserat på deras namn och skriver sedan informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a858a-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="a858a-110">[Lägga till parametrar som bearbetar pipeline-inflöden](./adding-parameters-that-process-pipeline-input.md) I det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-proc så att cmdleten kan bearbeta objekt som skickas till den via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a858a-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="a858a-111">Implementerings-cmdleten som beskrivs här hämtar processer baserat på objekt som skickas till cmdleten och skriver sedan informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a858a-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="a858a-112">[Lägga till fel rapportering som inte avslutas till din cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) I det här avsnittet beskrivs hur du lägger till fel rapportering som inte avslutas till en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a858a-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="a858a-113">Implementeringen som beskrivs här identifierar fel som inträffar när indata bearbetas och en felpost skrivs till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="a858a-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="a858a-114">Se även</span><span class="sxs-lookup"><span data-stu-id="a858a-114">See Also</span></span>

[<span data-ttu-id="a858a-115">Skapa en cmdlet utan parametrar</span><span class="sxs-lookup"><span data-stu-id="a858a-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="a858a-116">Lägga till parametrar som bearbetar kommando rads indatatyper</span><span class="sxs-lookup"><span data-stu-id="a858a-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="a858a-117">Lägga till parametrar som bearbetar pipeline-inflöden</span><span class="sxs-lookup"><span data-stu-id="a858a-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="a858a-118">Lägga till fel rapportering som inte avslutas till din cmdlet</span><span class="sxs-lookup"><span data-stu-id="a858a-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="a858a-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a858a-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
