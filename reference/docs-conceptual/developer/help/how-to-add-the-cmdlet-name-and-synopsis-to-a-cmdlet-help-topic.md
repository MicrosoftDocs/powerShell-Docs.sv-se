---
title: Så här lägger du till cmdlet-namnet och sammanfattningen i ett hjälp avsnitt för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: 5b4c04a14c3d86c7a3b94b768e8fb59116d8c6f5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560635"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="d5442-102">Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="d5442-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="d5442-103">I det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnitten namn och sammanfattning i cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="d5442-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="d5442-104">I Hjälp filen läggs det här innehållet till i kommando-noden för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5442-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="d5442-105">Om du vill se en fullständig vy över en hjälpfil öppnar du en av dll-Help. XML-filerna som finns i installations katalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5442-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="d5442-106">Till exempel innehåller filen Microsoft. PowerShell. commands. Management. dll-Help. XML innehåll för flera av Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d5442-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="d5442-107">Lägga till cmdlet-namn och en sammanfattning</span><span class="sxs-lookup"><span data-stu-id="d5442-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="d5442-108">Cmdlet-hjälpen kan visa två beskrivningar för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d5442-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="d5442-109">Den första beskrivningen är en kort beskrivning som kallas för sammanfattning.</span><span class="sxs-lookup"><span data-stu-id="d5442-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="d5442-110">Den andra beskrivningen är en mer detaljerad beskrivning som beskrivs i [avsnittet lägga till detaljerad beskrivning i en cmdlet-hjälpfil](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="d5442-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="d5442-111">Båda dessa beskrivningar ska vara skrivna som ett enda stycke.</span><span class="sxs-lookup"><span data-stu-id="d5442-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="d5442-112">I sammanfattningen upprepar du inte cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="d5442-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="d5442-113">Informerar användaren om att cmdleten Get-server hämtar en server, men inte informativ.</span><span class="sxs-lookup"><span data-stu-id="d5442-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="d5442-114">Använd i stället synonymer och Lägg till information i beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="d5442-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="d5442-115">Exempel: "hämtar ett objekt som representerar en lokal dator eller fjärrdator."</span><span class="sxs-lookup"><span data-stu-id="d5442-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="d5442-116">Använd enkla verb som "Get", "Create" och "Change" i sammanfattningen.</span><span class="sxs-lookup"><span data-stu-id="d5442-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="d5442-117">Undvik att använda "Set" eftersom det är vagt och snygga ord som "ändra".</span><span class="sxs-lookup"><span data-stu-id="d5442-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="d5442-118">Exempel: "hämtar information om Authenticode-signaturen i en fil."</span><span class="sxs-lookup"><span data-stu-id="d5442-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="d5442-119">Skriv i aktiv röst.</span><span class="sxs-lookup"><span data-stu-id="d5442-119">Write in active voice.</span></span> <span data-ttu-id="d5442-120">Exempel: "Använd TimeSpan-objektet..." är mycket tydligare än "TimeSpan-objektet kan användas för..."</span><span class="sxs-lookup"><span data-stu-id="d5442-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="d5442-121">Undvik verbet "Visa" när du beskriver cmdletar som hämtar objekt.</span><span class="sxs-lookup"><span data-stu-id="d5442-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="d5442-122">Även om Windows PowerShell visar cmdlet-data är det viktigt att introducera användare till det begrepp som cmdleten returnerar .NET Framework objekt vars data inte kan visas.</span><span class="sxs-lookup"><span data-stu-id="d5442-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="d5442-123">Om du betonar visningen kanske inte användaren inser att cmdleten kan ha returnerat många andra användbara egenskaper och metoder som inte visas.</span><span class="sxs-lookup"><span data-stu-id="d5442-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5442-124">Se även</span><span class="sxs-lookup"><span data-stu-id="d5442-124">See Also</span></span>

 [<span data-ttu-id="d5442-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d5442-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
