---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Använd flikexpansion
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 437c1e3c04352f2c5c3aba4c67b542821975f739
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229428"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="3dbd1-103">Använd flikexpansion</span><span class="sxs-lookup"><span data-stu-id="3dbd1-103">Using Tab Expansion</span></span>

<span data-ttu-id="3dbd1-104">Kommandoradsverktyget gränssnitt är ett sätt att slutföra namnen på lång filer eller kommandon automatiskt, ofta snabbare kommandot posten och ge tips.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="3dbd1-105">PowerShell kan du fylla i filnamn och cmdlet-namnen genom att trycka på den <kbd>fliken</kbd> nyckel.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-105">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="3dbd1-106">Flikexpansion styrs av funktionen intern TabExpansion eller TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="3dbd1-107">Eftersom den här funktionen kan ändras eller åsidosätts, är den här diskussionen en guide i beteendet hos PowerShell standardkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="3dbd1-108">Om du vill fylla i ett filnamn eller sökväg från de olika alternativen automatiskt skriver en del av namn och tryck på den <kbd>fliken</kbd> nyckel.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-108">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="3dbd1-109">PowerShell kommer automatiskt att expandera namnet till den första matchningen som hittas.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="3dbd1-110">Att trycka på den <kbd>fliken</kbd> nyckel upprepade gånger ska gå igenom alla tillgängliga alternativ.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-110">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="3dbd1-111">Flikexpansion av cmdlet-namnen är något annorlunda.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="3dbd1-112">Om du vill använda flikexpansion på en cmdlet-namn, skriver du hela första delen av namn (verb) och bindestreck som kommer efter.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="3dbd1-113">Du kan fylla i mer i namnet på en partiell matchning.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="3dbd1-114">Exempel: Om du skriver `get-co` och tryck sedan på den <kbd>fliken</kbd> nyckel, PowerShell kommer automatiskt att expandera den till den `Get-Command` cmdlet (Observera att även ändras i fallet med bokstäver i sina standard formulär).</span><span class="sxs-lookup"><span data-stu-id="3dbd1-114">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="3dbd1-115">Om du trycker på <kbd>fliken</kbd> viktiga igen, PowerShell ersätter det med det bara andra matchande cmdlet-namnet, `Get-Content`.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-115">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="3dbd1-116">Du kan använda flikexpansion upprepade gånger på samma rad.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="3dbd1-117">Du kan till exempel använda flikexpansion på namnet på den `Get-Content` cmdlet genom att ange:</span><span class="sxs-lookup"><span data-stu-id="3dbd1-117">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="3dbd1-118">När du trycker på den <kbd>fliken</kbd> nyckel, kommandot expanderar till:</span><span class="sxs-lookup"><span data-stu-id="3dbd1-118">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="3dbd1-119">Sedan kan du delvis anger du sökvägen till aktiva installationens loggfil och Använd flikexpansion igen:</span><span class="sxs-lookup"><span data-stu-id="3dbd1-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="3dbd1-120">När du trycker på den <kbd>fliken</kbd> nyckel, kommandot expanderar till:</span><span class="sxs-lookup"><span data-stu-id="3dbd1-120">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="3dbd1-121">En begränsning med fliken expansionsprocessen är att tolkas alltid flikar som försöker slutföra ett ord.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="3dbd1-122">Om du kopierar och klistrar in kommandoexempel i en PowerShell-konsol, kontrollerar du att exemplet inte innehåller flikar; i annat fall resultatet blir oförutsägbara och kommer sannolikt inte som du tänkt.</span><span class="sxs-lookup"><span data-stu-id="3dbd1-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>