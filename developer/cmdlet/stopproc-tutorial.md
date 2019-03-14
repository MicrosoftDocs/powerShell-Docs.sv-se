---
title: StopProc självstudien | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794407"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="7824b-102">Självstudie om StopProc</span><span class="sxs-lookup"><span data-stu-id="7824b-102">StopProc Tutorial</span></span>

<span data-ttu-id="7824b-103">Det här avsnittet innehåller en självstudie för att skapa cmdlet Stop-processen, som liknar den [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7824b-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="7824b-104">Den här självstudien innehåller delar av kod som illustrerar hur cmdletar implementeras och en förklaring av koden.</span><span class="sxs-lookup"><span data-stu-id="7824b-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="7824b-105">Avsnitt i den här självstudien</span><span class="sxs-lookup"><span data-stu-id="7824b-105">Topics in this Tutorial</span></span>

<span data-ttu-id="7824b-106">Ämnena i den här självstudien är avsedda att läsas sekventiellt, med varje avsnitt som bygger på vad som beskrevs i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="7824b-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="7824b-107">[Skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md) i det här avsnittet beskriver hur du skapar en cmdlet som stöder system ändringar, som att stoppa en process som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="7824b-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="7824b-108">[Att lägga till meddelanden för användare i din Cmdlet](./adding-user-messages-to-your-cmdlet.md) det här avsnittet beskrivs hur du lägger till möjligheten att skriva meddelanden för användare, felsökningsmeddelanden, varningsmeddelanden och statusinformation i cmdlet:.</span><span class="sxs-lookup"><span data-stu-id="7824b-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="7824b-109">[Att lägga till alias och jokertecken Expansion och bidra till att Cmdlet-parametrarna](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) i det här avsnittet beskriver hur du skapar en cmdlet som stöder parameteralias, hjälp och jokertecken expansion.</span><span class="sxs-lookup"><span data-stu-id="7824b-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="7824b-110">[Att lägga till parametern anger cmdletar](./adding-parameter-sets-to-a-cmdlet.md) det här avsnittet beskrivs hur du lägger till parametern anger att en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7824b-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="7824b-111">Parameteruppsättningar kan cmdleten ska fungera på olika sätt beroende på vilka parametrar som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="7824b-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="7824b-112">Se även</span><span class="sxs-lookup"><span data-stu-id="7824b-112">See Also</span></span>

[<span data-ttu-id="7824b-113">Skapa en Cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="7824b-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="7824b-114">Meddelanden för att lägga till användare i cmdlet:</span><span class="sxs-lookup"><span data-stu-id="7824b-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="7824b-115">Att lägga till alias och jokertecken Expansion och bidra till att Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="7824b-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="7824b-116">Att lägga till parametern anger till cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="7824b-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="7824b-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7824b-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
