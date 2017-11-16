---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Med fliken expanderades
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 8412bd97a95719f07b16c6671d3b8801bbfab8e3
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2017
---
# <a name="using-tab-expansion"></a><span data-ttu-id="b41b4-103">Med fliken expanderades</span><span class="sxs-lookup"><span data-stu-id="b41b4-103">Using Tab Expansion</span></span>
<span data-ttu-id="b41b4-104">Kommandoradsverktyget tankar tillhandahåller ofta ett sätt att slutföra namnen på långa filer eller kommandon automatiskt, snabba på kommando-post och ge.</span><span class="sxs-lookup"><span data-stu-id="b41b4-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing .</span></span> <span data-ttu-id="b41b4-105">Windows PowerShell kan du fylla i namn på filen och cmdlet genom att trycka på **fliken** nyckel.</span><span class="sxs-lookup"><span data-stu-id="b41b4-105">Windows PowerShell allows you to fill in file names and cmdlet names by pressing the **Tab** key.</span></span>

> [!NOTE]
> <span data-ttu-id="b41b4-106">Fliken expansion styrs av funktionen interna TabExpansion eller TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="b41b4-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="b41b4-107">Eftersom den här funktionen kan ändras eller åsidosätts, är den här diskussionen en guide som beteendet för PowerShell standardkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b41b4-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="b41b4-108">Om du vill fylla i ett filnamn eller sökväg från de tillgängliga alternativen automatiskt skriver en del av namn och klicka på den **fliken** nyckel.</span><span class="sxs-lookup"><span data-stu-id="b41b4-108">To fill in a filename or path from the available choices automatically, type part of the name and press the **Tab** key.</span></span> <span data-ttu-id="b41b4-109">PowerShell kommer automatiskt att expandera namnet till den första matchningen som hittas.</span><span class="sxs-lookup"><span data-stu-id="b41b4-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="b41b4-110">När du trycker på den **fliken** nyckel upprepade gånger att växla mellan alla tillgängliga alternativ.</span><span class="sxs-lookup"><span data-stu-id="b41b4-110">Pressing the **Tab** key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="b41b4-111">Fliken expandering av cmdlet-namnen är något annorlunda.</span><span class="sxs-lookup"><span data-stu-id="b41b4-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="b41b4-112">För att använda fliken expansion på en cmdlet-namn, skriver du hela första delen av namn (verb) och bindestreck som följer den.</span><span class="sxs-lookup"><span data-stu-id="b41b4-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="b41b4-113">Du kan fylla i flera namn för en delvis matchning.</span><span class="sxs-lookup"><span data-stu-id="b41b4-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="b41b4-114">Om du skriver till exempel **get-co** och tryck sedan på den **fliken** nyckeln, PowerShell kommer automatiskt att expandera den till den **Get-Command** cmdlet (Observera att ändrar du även fallet för att deras standardformulär).</span><span class="sxs-lookup"><span data-stu-id="b41b4-114">For example, if you type **get-co** and then press the **Tab** key, PowerShell will automatically expand this to the **Get-Command** cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="b41b4-115">Om du trycker på **fliken** nyckeln igen och PowerShell ersätter det med endast andra matchande namn, **Get-innehåll**.</span><span class="sxs-lookup"><span data-stu-id="b41b4-115">If you press **Tab** key again, PowerShell replaces this with the only other matching cmdlet name, **Get-Content**.</span></span>

<span data-ttu-id="b41b4-116">Du kan använda fliken expansion upprepade gånger på samma linje.</span><span class="sxs-lookup"><span data-stu-id="b41b4-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="b41b4-117">Du kan till exempel använda fliken expansion på namnet på den **Get-innehåll** cmdlet genom att ange:</span><span class="sxs-lookup"><span data-stu-id="b41b4-117">For example, you can use tab expansion on the name of the **Get-Content** cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="b41b4-118">När du trycker på den **fliken** nyckeln, kommandot expanderar till:</span><span class="sxs-lookup"><span data-stu-id="b41b4-118">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="b41b4-119">Du kan sedan delvis ange sökvägen till loggfilen Active Setup och använda fliken expansion igen:</span><span class="sxs-lookup"><span data-stu-id="b41b4-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="b41b4-120">När du trycker på den **fliken** nyckeln, kommandot expanderar till:</span><span class="sxs-lookup"><span data-stu-id="b41b4-120">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="b41b4-121">En begränsning med den flik utvidgas är flikar tolkas alltid som försöker slutföra ett ord.</span><span class="sxs-lookup"><span data-stu-id="b41b4-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="b41b4-122">Om du kopierar och klistrar in kommandoexempel i PowerShell-konsolen, kontrollera att provet inte innehåller flikar. Om resultatet blir oförutsägbara och sannolikt inte som du tänkt.</span><span class="sxs-lookup"><span data-stu-id="b41b4-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>

