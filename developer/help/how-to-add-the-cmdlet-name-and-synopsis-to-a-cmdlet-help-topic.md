---
title: Hur du lägger till Cmdlet-namn och sammanfattning för en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850892"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="f89db-102">Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="f89db-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="f89db-103">Det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnitten namn och en sammanfattning av cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="f89db-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="f89db-104">Det här innehållet har lagts till noden kommando för varje cmdlet i hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="f89db-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="f89db-105">För en fullständig överblick över en hjälpfilen, öppna en av dll-Help.xml-filerna finns i installationskatalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f89db-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="f89db-106">Till exempel innehåller filen Microsoft.PowerShell.Commands.Management.dll Help.xml innehåll för flera av Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f89db-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="f89db-107">Du lägger till Cmdlet-namn och en sammanfattning</span><span class="sxs-lookup"><span data-stu-id="f89db-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="f89db-108">Cmdlet: en hjälp kan visa två beskrivningar för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f89db-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="f89db-109">Första beskrivningen är en kort beskrivning som kallas sammanfattning.</span><span class="sxs-lookup"><span data-stu-id="f89db-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="f89db-110">Andra beskrivningen är en mer detaljerad beskrivning som diskuteras i [att lägga till den detaljerade beskrivningen för en Cmdlet-hjälpavsnittet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="f89db-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="f89db-111">Båda dessa beskrivningar ska skrivas som en enda punkt.</span><span class="sxs-lookup"><span data-stu-id="f89db-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="f89db-112">I sammanfattning Upprepa inte cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="f89db-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="f89db-113">Informera användaren att cmdleten Get-Server hämtar en server är kort, men inte informativt.</span><span class="sxs-lookup"><span data-stu-id="f89db-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="f89db-114">I stället använda synonymer och Lägg till information i beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="f89db-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="f89db-115">Exempel: ”Hämtar ett objekt som representerar en lokal eller fjärransluten dator”.</span><span class="sxs-lookup"><span data-stu-id="f89db-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="f89db-116">Använd enkla verb som ”hämta”, ”skapa” och ”ändra” i sammanfattning.</span><span class="sxs-lookup"><span data-stu-id="f89db-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="f89db-117">Undvik att använda ”Ange” eftersom det är vaga och avancerad ord som ”ändra”.</span><span class="sxs-lookup"><span data-stu-id="f89db-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="f89db-118">Exempel: ”Hämtar information om Authenticode-signaturen i en fil”.</span><span class="sxs-lookup"><span data-stu-id="f89db-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="f89db-119">Skriv i aktiva rösten.</span><span class="sxs-lookup"><span data-stu-id="f89db-119">Write in active voice.</span></span> <span data-ttu-id="f89db-120">Till exempel ”använda objektet TimeSpan...” är mycket tydligare än ”TimeSpan-objektet kan användas till att...”</span><span class="sxs-lookup"><span data-stu-id="f89db-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="f89db-121">Undvik att verb ”visa” att beskriva cmdletar som hämta objekt.</span><span class="sxs-lookup"><span data-stu-id="f89db-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="f89db-122">Även om Windows PowerShell visar cmdlet data, är det viktigt att introducera användare till konceptet som cmdleten returnerar .NET Framework-objekt vars data inte visas.</span><span class="sxs-lookup"><span data-stu-id="f89db-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="f89db-123">Om du betona visningen kanske användaren inte tänka på att cmdlet: en kan ha returnerat många andra användbara egenskaper och metoder som inte visas.</span><span class="sxs-lookup"><span data-stu-id="f89db-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f89db-124">Se även</span><span class="sxs-lookup"><span data-stu-id="f89db-124">See Also</span></span>

 [<span data-ttu-id="f89db-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f89db-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)