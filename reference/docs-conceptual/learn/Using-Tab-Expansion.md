---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Använd flikexpansion
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436507"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="9389a-103">Använd flikexpansion</span><span class="sxs-lookup"><span data-stu-id="9389a-103">Using Tab Expansion</span></span>

<span data-ttu-id="9389a-104">Kommando rads gränssnitt ger ofta ett sätt att slutföra namnen på långa filer eller kommandon automatiskt, påskynda kommando posten och tillhandahålla tips.</span><span class="sxs-lookup"><span data-stu-id="9389a-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="9389a-105">Med PowerShell kan du fylla i fil namn och cmdlet-namn genom att trycka på <kbd>TABB</kbd> -tangenten.</span><span class="sxs-lookup"><span data-stu-id="9389a-105">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="9389a-106">Fliken utökas av den interna funktionen TabExpansion eller TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="9389a-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="9389a-107">Eftersom den här funktionen kan ändras eller åsidosättas, är den här diskussionen en guide till beteendet för standard-PowerShell-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="9389a-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="9389a-108">Om du vill fylla i ett fil namn eller en sökväg från tillgängliga alternativ automatiskt, anger du en del av namnet och trycker på <kbd>TABB</kbd> -tangenten.</span><span class="sxs-lookup"><span data-stu-id="9389a-108">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="9389a-109">PowerShell expanderar automatiskt namnet till den första matchning som hittas.</span><span class="sxs-lookup"><span data-stu-id="9389a-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="9389a-110">Om du trycker på <kbd>tabbtangenten</kbd> flera gånger kommer de tillgängliga alternativen att gå igenom.</span><span class="sxs-lookup"><span data-stu-id="9389a-110">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="9389a-111">Flikens expansion av cmdlet-namn skiljer sig något åt.</span><span class="sxs-lookup"><span data-stu-id="9389a-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="9389a-112">Om du vill använda TABB-expansion på ett cmdlet-namn skriver du hela den första delen av namnet (verbet) och bindestrecket som följer.</span><span class="sxs-lookup"><span data-stu-id="9389a-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="9389a-113">Du kan fylla i mer av namnet för en partiell matchning.</span><span class="sxs-lookup"><span data-stu-id="9389a-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="9389a-114">Om du till exempel skriver `get-co` och trycker på <kbd>tabbtangenten</kbd> , expanderar PowerShell automatiskt detta till `Get-Command` cmdleten (Observera att det även ändrar Skift läge för bokstäver till deras standard formulär).</span><span class="sxs-lookup"><span data-stu-id="9389a-114">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="9389a-115">Om du trycker på <kbd>tabbtangenten</kbd> igen ersätter PowerShell detta med det enda andra matchande cmdlet-namnet `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="9389a-115">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="9389a-116">Du kan använda utöka flera gånger på samma rad.</span><span class="sxs-lookup"><span data-stu-id="9389a-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="9389a-117">Du kan till exempel använda TABB-expansion på namnet på `Get-Content` cmdleten genom att ange:</span><span class="sxs-lookup"><span data-stu-id="9389a-117">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="9389a-118">När du trycker på <kbd>TABB</kbd> -tangenten expanderas kommandot till:</span><span class="sxs-lookup"><span data-stu-id="9389a-118">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="9389a-119">Du kan sedan delvis ange sökvägen till logg filen för Active Setup och använda TABB-expansion igen:</span><span class="sxs-lookup"><span data-stu-id="9389a-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="9389a-120">När du trycker på <kbd>TABB</kbd> -tangenten expanderas kommandot till:</span><span class="sxs-lookup"><span data-stu-id="9389a-120">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="9389a-121">En begränsning av processen för att utöka en flik är att flikarna alltid tolkas som försök att slutföra ett ord.</span><span class="sxs-lookup"><span data-stu-id="9389a-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="9389a-122">Om du kopierar och klistrar in kommando exempel i en PowerShell-konsol ser du till att exemplet inte innehåller flikar. om det gör det blir resultatet oförutsägbart och det är nästan verkligen inte det du avsåg.</span><span class="sxs-lookup"><span data-stu-id="9389a-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>
