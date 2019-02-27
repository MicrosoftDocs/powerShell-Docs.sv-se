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
ms.openlocfilehash: 6e1c8a4709988adfa59bda14eb3af52b0a79f1df
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847063"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="78c32-102">Självstudie om StopProc</span><span class="sxs-lookup"><span data-stu-id="78c32-102">StopProc Tutorial</span></span>

<span data-ttu-id="78c32-103">Det här avsnittet innehåller en självstudie för att skapa cmdlet Stop-processen, som liknar den [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78c32-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="78c32-104">Den här självstudien innehåller delar av kod som illustrerar hur cmdletar implementeras och en förklaring av koden.</span><span class="sxs-lookup"><span data-stu-id="78c32-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>
<span data-ttu-id="78c32-105">Det här avsnittet innehåller en självstudie för att skapa cmdlet Stop-processen, som liknar den [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78c32-105">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="78c32-106">Den här självstudien innehåller delar av kod som illustrerar hur cmdletar implementeras och en förklaring av koden.</span><span class="sxs-lookup"><span data-stu-id="78c32-106">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="78c32-107">Avsnitt i den här självstudien</span><span class="sxs-lookup"><span data-stu-id="78c32-107">Topics in this Tutorial</span></span>

<span data-ttu-id="78c32-108">Ämnena i den här självstudien är avsedda att läsas sekventiellt, med varje avsnitt som bygger på vad som beskrevs i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="78c32-108">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="78c32-109">[Skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md) i det här avsnittet beskriver hur du skapar en cmdlet som stöder system ändringar, som att stoppa en process som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="78c32-109">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="78c32-110">[Att lägga till meddelanden för användare i din Cmdlet](./adding-user-messages-to-your-cmdlet.md) det här avsnittet beskrivs hur du lägger till möjligheten att skriva meddelanden för användare, felsökningsmeddelanden, varningsmeddelanden och statusinformation i cmdlet:.</span><span class="sxs-lookup"><span data-stu-id="78c32-110">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="78c32-111">[Att lägga till alias och jokertecken Expansion och bidra till att Cmdlet-parametrarna](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) i det här avsnittet beskriver hur du skapar en cmdlet som stöder parameteralias, hjälp och jokertecken expansion.</span><span class="sxs-lookup"><span data-stu-id="78c32-111">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="78c32-112">[Att lägga till parametern anger cmdletar](./adding-parameter-sets-to-a-cmdlet.md) det här avsnittet beskrivs hur du lägger till parametern anger att en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="78c32-112">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="78c32-113">Parameteruppsättningar kan cmdleten ska fungera på olika sätt beroende på vilka parametrar som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="78c32-113">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="78c32-114">Se även</span><span class="sxs-lookup"><span data-stu-id="78c32-114">See Also</span></span>

[<span data-ttu-id="78c32-115">Skapa en Cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="78c32-115">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="78c32-116">Meddelanden för att lägga till användare i cmdlet:</span><span class="sxs-lookup"><span data-stu-id="78c32-116">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="78c32-117">Att lägga till alias och jokertecken Expansion och bidra till att Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="78c32-117">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="78c32-118">Att lägga till parametern anger till cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="78c32-118">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="78c32-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="78c32-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
