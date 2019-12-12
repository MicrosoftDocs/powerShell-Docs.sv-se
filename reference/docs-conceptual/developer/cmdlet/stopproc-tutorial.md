---
title: StopProc-självstudie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359228"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="cbf2f-102">Självstudie om StopProc</span><span class="sxs-lookup"><span data-stu-id="cbf2f-102">StopProc Tutorial</span></span>

<span data-ttu-id="cbf2f-103">Det här avsnittet innehåller en själv studie kurs om hur du skapar cmdleten Stop-proc, som påminner om cmdleten för [stopp processen](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cbf2f-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="cbf2f-104">Den här självstudien innehåller fragment med kod som illustrerar hur cmdlets implementeras och en förklaring av koden.</span><span class="sxs-lookup"><span data-stu-id="cbf2f-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="cbf2f-105">Avsnitt i den här självstudien</span><span class="sxs-lookup"><span data-stu-id="cbf2f-105">Topics in this Tutorial</span></span>

<span data-ttu-id="cbf2f-106">Avsnitten i den här självstudien är utformade för att läsas sekventiellt, med varje ämne som bygger på vad som diskuterades i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="cbf2f-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="cbf2f-107">[Skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md) I det här avsnittet beskrivs hur du skapar en-cmdlet som stöder system ändringar, till exempel att stoppa en process som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="cbf2f-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="cbf2f-108">[Lägga till användar meddelanden i din cmdlet](./adding-user-messages-to-your-cmdlet.md) I det här avsnittet beskrivs hur du lägger till möjligheten att skriva användar meddelanden, felsöka meddelanden, varnings meddelanden och statusinformation till din cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cbf2f-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="cbf2f-109">[Lägga till alias, expansion med jokertecken och hjälp till cmdlet-parametrar](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) I det här avsnittet beskrivs hur du skapar en-cmdlet som stöder parameter-alias, hjälp och expansion med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="cbf2f-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="cbf2f-110">[Lägga till parameter uppsättningar till cmdletar](./adding-parameter-sets-to-a-cmdlet.md) I det här avsnittet beskrivs hur du lägger till parameter uppsättningar i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cbf2f-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="cbf2f-111">Parameter uppsättningar tillåter att cmdleten fungerar på olika sätt beroende på vilka parametrar som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="cbf2f-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbf2f-112">Se även</span><span class="sxs-lookup"><span data-stu-id="cbf2f-112">See Also</span></span>

[<span data-ttu-id="cbf2f-113">Skapa en cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="cbf2f-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="cbf2f-114">Lägga till användar meddelanden i din cmdlet</span><span class="sxs-lookup"><span data-stu-id="cbf2f-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="cbf2f-115">Lägga till alias, expansion med jokertecken och hjälp till cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="cbf2f-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="cbf2f-116">Lägga till parameter uppsättningar till cmdletar</span><span class="sxs-lookup"><span data-stu-id="cbf2f-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="cbf2f-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cbf2f-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
