---
title: Lägga till ett ”Se även”-avsnitt i ett hjälpavsnitt för providers
ms.date: 09/12/2016
ms.openlocfilehash: 54adf4bb941888583eb749b7b5322b27d84c7af7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893483"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="4c537-102">Lägga till ett ”Se även”-avsnitt i ett hjälpavsnitt för providers</span><span class="sxs-lookup"><span data-stu-id="4c537-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="4c537-103">I det här avsnittet beskrivs hur du fyller i avsnittet **Se även** i en providers hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="4c537-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="4c537-104">Avsnittet **Se även** består av en lista med ämnen som är relaterade till leverantören eller kan hjälpa användaren att förstå och använda providern.</span><span class="sxs-lookup"><span data-stu-id="4c537-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="4c537-105">Ämnes listan kan innehålla hjälp avsnitten om cmdlet-hjälpen, providerns hjälp och konceptuellhet ("om") i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c537-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="4c537-106">Det kan även innehålla referenser till böcker, papper och online-ämnen, inklusive en online-version av hjälp avsnittet aktuell Provider.</span><span class="sxs-lookup"><span data-stu-id="4c537-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="4c537-107">När du refererar till online-ämnen ska du ange URI: n eller en sökterm som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="4c537-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="4c537-108">`Get-Help`Cmdlet: en länkar eller omdirigerar inte till något av ämnena i listan.</span><span class="sxs-lookup"><span data-stu-id="4c537-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="4c537-109">`Online`Parametern för `Get-Help` cmdleten fungerar inte heller med leverantörs hjälpen.</span><span class="sxs-lookup"><span data-stu-id="4c537-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="4c537-110">Avsnittet **Se även** skapas från `RelatedLinks` elementet och de taggar som det innehåller.</span><span class="sxs-lookup"><span data-stu-id="4c537-110">The **See Also** section is created from the `RelatedLinks` element and the tags that it contains.</span></span>
<span data-ttu-id="4c537-111">Följande XML visar hur du lägger till taggarna.</span><span class="sxs-lookup"><span data-stu-id="4c537-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="4c537-112">För att lägga till se även ämnen</span><span class="sxs-lookup"><span data-stu-id="4c537-112">To Add SEE ALSO Topics</span></span>

1. <span data-ttu-id="4c537-113">`<AssemblyName>.dll-help.xml` `providerHelp` Lägg till ett-element i-filen i-elementet `RelatedLinks` .</span><span class="sxs-lookup"><span data-stu-id="4c537-113">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="4c537-114">`RelatedLinks`Elementet ska vara det sista elementet i `providerHelp` elementet.</span><span class="sxs-lookup"><span data-stu-id="4c537-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="4c537-115">Endast ett- `RelatedLinks` element tillåts i varje leverantörs hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="4c537-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="4c537-116">Exempel:</span><span class="sxs-lookup"><span data-stu-id="4c537-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. <span data-ttu-id="4c537-117">För varje ämne i avsnittet **Se även** , `RelatedLinks` Lägg till ett-element i elementet `navigationLink` .</span><span class="sxs-lookup"><span data-stu-id="4c537-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="4c537-118">`navigationLink`Lägg sedan till ett- `linkText` element och ett-element inom varje element `uri` .</span><span class="sxs-lookup"><span data-stu-id="4c537-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="4c537-119">Om du inte använder `uri` -elementet kan du lägga till det som ett tomt element ( \<uri/> ).</span><span class="sxs-lookup"><span data-stu-id="4c537-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="4c537-120">Exempel:</span><span class="sxs-lookup"><span data-stu-id="4c537-120">For example:</span></span>

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

1. <span data-ttu-id="4c537-121">Skriv ämnes namnet mellan `linkText` taggarna.</span><span class="sxs-lookup"><span data-stu-id="4c537-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="4c537-122">Om du tillhandahåller en URI, anger du den mellan `uri` taggarna.</span><span class="sxs-lookup"><span data-stu-id="4c537-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="4c537-123">Om du vill ange onlineversionen av hjälp avsnittet för aktuell Provider, mellan `linkText` taggarna, skriver du "online version:" i stället för ämnes namnet.</span><span class="sxs-lookup"><span data-stu-id="4c537-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="4c537-124">Normalt är länken "online version:" den första artikeln i listan se även.</span><span class="sxs-lookup"><span data-stu-id="4c537-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="4c537-125">I följande exempel ingår tre Se även ämnen.</span><span class="sxs-lookup"><span data-stu-id="4c537-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="4c537-126">Det första refererar till online-versionen av det aktuella avsnittet.</span><span class="sxs-lookup"><span data-stu-id="4c537-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="4c537-127">Den andra hänvisar till ett hjälp avsnitt för Windows PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c537-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="4c537-128">Den tredje refererar till ett annat online-ämne.</span><span class="sxs-lookup"><span data-stu-id="4c537-128">The third refers to another online topic.</span></span>

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
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
