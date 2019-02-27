---
title: Lägga till en Se även avsnittet i ett hjälpavsnitt för providern | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848456"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="58984-102">Lägga till ett ”Se även”-avsnitt i ett hjälpavsnitt för providers</span><span class="sxs-lookup"><span data-stu-id="58984-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="58984-103">Det här avsnittet beskrivs hur du fyller i **Se även** delen av ett hjälpavsnitt för providern.</span><span class="sxs-lookup"><span data-stu-id="58984-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="58984-104">Den **Se även** avsnittet består av en lista över ämnen som är relaterade till providern eller kan hjälpa dig att du bättre förstå och använda providern.</span><span class="sxs-lookup"><span data-stu-id="58984-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="58984-105">Avsnittet listan kan innehålla cmdlet-hjälpen, provider hjälp och konceptuella (”information”) hjälpavsnitten i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58984-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="58984-106">Den kan även innehålla referenser till böcker, faktablad och online ämnen, t.ex. en onlineversionen av hjälpavsnittet för providern.</span><span class="sxs-lookup"><span data-stu-id="58984-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="58984-107">När du refererar till online ämnen, ange URI: N eller en sökterm i oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="58984-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="58984-108">Den `Get-Help` cmdlet inte länka eller omdirigera till något av ämnena i listan.</span><span class="sxs-lookup"><span data-stu-id="58984-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="58984-109">Dessutom den `Online` -parametern för den `Get-Help` cmdlet fungerar inte med hjälp av providern.</span><span class="sxs-lookup"><span data-stu-id="58984-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="58984-110">Se även skapas från den `RelatedLinks` element och taggar som den innehåller.</span><span class="sxs-lookup"><span data-stu-id="58984-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="58984-111">Följande XML-koden visar hur du lägger till taggar.</span><span class="sxs-lookup"><span data-stu-id="58984-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="58984-112">Att lägga till ”Se även” ämnen</span><span class="sxs-lookup"><span data-stu-id="58984-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="58984-113">I den *AssemblyName*.dll-help.xml filen i den `providerHelp` element, lägga till en `RelatedLinks` element.</span><span class="sxs-lookup"><span data-stu-id="58984-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="58984-114">Den `RelatedLinks` elementet ska vara det sista elementet i den `providerHelp` element.</span><span class="sxs-lookup"><span data-stu-id="58984-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="58984-115">Endast en `RelatedLinks` element tillåts i varje hjälpavsnitt för providern.</span><span class="sxs-lookup"><span data-stu-id="58984-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="58984-116">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="58984-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="58984-117">För varje avsnitt i den **Se även** avsnittet i den `RelatedLinks` element, lägga till en `navigationLink` element.</span><span class="sxs-lookup"><span data-stu-id="58984-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="58984-118">Sedan, i varje `navigationLink` element, lägga till en `linkText` element och en `uri` element.</span><span class="sxs-lookup"><span data-stu-id="58984-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="58984-119">Om du inte använder den `uri` element, du kan lägga till det som ett tomt element (\<uri / >).</span><span class="sxs-lookup"><span data-stu-id="58984-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="58984-120">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="58984-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="58984-121">Skriv namnet på ämnet mellan den `linkText` taggar.</span><span class="sxs-lookup"><span data-stu-id="58984-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="58984-122">Om du tillhandahåller en URI, skriver du det mellan den `uri` taggar.</span><span class="sxs-lookup"><span data-stu-id="58984-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="58984-123">Att ange onlineversionen av hjälpavsnittet i providern mellan den `linkText` , skriver ”onlineversion”: i stället för namnet på ämnet.</span><span class="sxs-lookup"><span data-stu-id="58984-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="58984-124">Normalt den ”onlineversion”: länk är det första avsnittet i avsnittet Se även listan.</span><span class="sxs-lookup"><span data-stu-id="58984-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="58984-125">I följande exempel innehåller tre Se även avsnitt.</span><span class="sxs-lookup"><span data-stu-id="58984-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="58984-126">Först avser online-versionen av det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="58984-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="58984-127">Andra refererar till ett hjälpavsnitt för Windows PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="58984-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="58984-128">Tredje refererar till en annan onlineavsnittet.</span><span class="sxs-lookup"><span data-stu-id="58984-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```