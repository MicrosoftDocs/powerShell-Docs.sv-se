---
ms.date: 09/13/2016
ms.topic: reference
title: Självstudie om StopProc
description: Självstudie om StopProc
ms.openlocfilehash: 95229ee3c4905d295bd6991fe8ccf8c9840c3cdd
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646431"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="0069f-103">Självstudie om StopProc</span><span class="sxs-lookup"><span data-stu-id="0069f-103">StopProc Tutorial</span></span>

<span data-ttu-id="0069f-104">Det här avsnittet innehåller en själv studie kurs om hur du skapar Stop-Proc-cmdleten, som liknar cmdleten för [Stop-processen](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0069f-104">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="0069f-105">Den här självstudien innehåller fragment med kod som illustrerar hur cmdlets implementeras och en förklaring av koden.</span><span class="sxs-lookup"><span data-stu-id="0069f-105">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="0069f-106">Avsnitt i den här självstudien</span><span class="sxs-lookup"><span data-stu-id="0069f-106">Topics in this Tutorial</span></span>

<span data-ttu-id="0069f-107">Avsnitten i den här självstudien är utformade för att läsas sekventiellt, med varje ämne som bygger på vad som diskuterades i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="0069f-107">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="0069f-108">[Skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md) I det här avsnittet beskrivs hur du skapar en-cmdlet som stöder system ändringar, till exempel att stoppa en process som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="0069f-108">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="0069f-109">[Lägga till användar meddelanden i din cmdlet](./adding-user-messages-to-your-cmdlet.md) I det här avsnittet beskrivs hur du lägger till möjligheten att skriva användar meddelanden, felsöka meddelanden, varnings meddelanden och statusinformation till din cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0069f-109">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="0069f-110">[Lägga till alias, expansion med jokertecken och hjälp till cmdlet-parametrar](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) I det här avsnittet beskrivs hur du skapar en-cmdlet som stöder parameter-alias, hjälp och expansion med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="0069f-110">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="0069f-111">[Lägga till parameter uppsättningar till cmdletar](./adding-parameter-sets-to-a-cmdlet.md) I det här avsnittet beskrivs hur du lägger till parameter uppsättningar i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0069f-111">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="0069f-112">Parameter uppsättningar tillåter att cmdleten fungerar på olika sätt beroende på vilka parametrar som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="0069f-112">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="0069f-113">Se även</span><span class="sxs-lookup"><span data-stu-id="0069f-113">See Also</span></span>

[<span data-ttu-id="0069f-114">Skapa en cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="0069f-114">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="0069f-115">Lägga till användarmeddelanden i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="0069f-115">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="0069f-116">Lägga till alias, jokerteckenexpansion och hjälp i cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="0069f-116">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="0069f-117">Lägga till parameter uppsättningar till cmdletar</span><span class="sxs-lookup"><span data-stu-id="0069f-117">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="0069f-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0069f-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
