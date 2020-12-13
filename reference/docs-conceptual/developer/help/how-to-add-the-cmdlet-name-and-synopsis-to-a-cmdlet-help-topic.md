---
ms.date: 09/13/2016
ms.topic: reference
title: Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt
description: Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt
ms.openlocfilehash: aeeb0cdd1d6d17b88067928ff952dc57a9441917
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659063"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="82ff7-103">Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="82ff7-103">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="82ff7-104">I det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnitten **namn** och **Sammanfattning** i cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="82ff7-104">This section describes how to add content that is displayed in the **NAME** and **SYNOPSIS** sections of the cmdlet help.</span></span> <span data-ttu-id="82ff7-105">I Hjälp filen läggs det här innehållet till i kommando-noden för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="82ff7-105">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="82ff7-106">Om du vill se en fullständig vy över en hjälpfil öppnar du en av `dll-Help.xml` filerna som finns i installations katalogen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82ff7-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="82ff7-107">Filen innehåller till exempel `Microsoft.PowerShell.Commands.Management.dll-Help.xml` innehåll för flera av PowerShell-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="82ff7-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="82ff7-108">Lägga till cmdlet-namn och en sammanfattning</span><span class="sxs-lookup"><span data-stu-id="82ff7-108">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="82ff7-109">Cmdlet-hjälpen kan visa två beskrivningar för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82ff7-109">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="82ff7-110">Den första beskrivningen är en kort beskrivning som kallas för sammanfattning.</span><span class="sxs-lookup"><span data-stu-id="82ff7-110">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="82ff7-111">Den andra beskrivningen är en mer detaljerad beskrivning som beskrivs i [avsnittet lägga till detaljerad beskrivning i en cmdlet-hjälpfil](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="82ff7-111">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>
  <span data-ttu-id="82ff7-112">Båda dessa beskrivningar ska vara skrivna som ett enda stycke.</span><span class="sxs-lookup"><span data-stu-id="82ff7-112">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="82ff7-113">I sammanfattningen upprepar du inte cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="82ff7-113">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="82ff7-114">Informerar användaren om att `Get-Server` cmdleten hämtar en server, men inte informativ.</span><span class="sxs-lookup"><span data-stu-id="82ff7-114">Informing the user that the `Get-Server` cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="82ff7-115">Använd i stället synonymer och Lägg till information i beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="82ff7-115">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="82ff7-116">Exempel: "hämtar ett objekt som representerar en lokal dator eller fjärrdator."</span><span class="sxs-lookup"><span data-stu-id="82ff7-116">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="82ff7-117">Använd enkla verb som "Get", "Create" och "Change" i sammanfattningen.</span><span class="sxs-lookup"><span data-stu-id="82ff7-117">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="82ff7-118">Undvik att använda "Set" eftersom det är vagt och snygga ord som "ändra".</span><span class="sxs-lookup"><span data-stu-id="82ff7-118">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="82ff7-119">Exempel: "hämtar information om Authenticode-signaturen i en fil."</span><span class="sxs-lookup"><span data-stu-id="82ff7-119">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="82ff7-120">Skriv i aktiv röst.</span><span class="sxs-lookup"><span data-stu-id="82ff7-120">Write in active voice.</span></span> <span data-ttu-id="82ff7-121">Exempel: "Använd TimeSpan-objektet..." är mycket tydligare än "TimeSpan-objektet kan användas för..."</span><span class="sxs-lookup"><span data-stu-id="82ff7-121">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="82ff7-122">Undvik verbet "Visa" när du beskriver cmdletar som hämtar objekt.</span><span class="sxs-lookup"><span data-stu-id="82ff7-122">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="82ff7-123">Även om Windows PowerShell visar cmdlet-data är det viktigt att introducera användare till det begrepp som cmdleten returnerar .NET Framework objekt vars data inte kan visas.</span><span class="sxs-lookup"><span data-stu-id="82ff7-123">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="82ff7-124">Om du betonar visningen kanske inte användaren inser att cmdleten kan ha returnerat många andra användbara egenskaper och metoder som inte visas.</span><span class="sxs-lookup"><span data-stu-id="82ff7-124">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="82ff7-125">Se även</span><span class="sxs-lookup"><span data-stu-id="82ff7-125">See Also</span></span>

[<span data-ttu-id="82ff7-126">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="82ff7-126">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
