---
description: Beskriver enklare, mer naturligt språk sätt för skript filter för objekt samlingar.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: d2e603b4d2092d4ba4ed9c1d7253991cc34ddca8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270387"
---
# <a name="about_simplified_syntax"></a><span data-ttu-id="1d082-104">about_Simplified_Syntax</span><span class="sxs-lookup"><span data-stu-id="1d082-104">about_Simplified_Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="1d082-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1d082-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="1d082-106">Beskriver enklare, mer naturligt språk sätt för skript filter för objekt samlingar.</span><span class="sxs-lookup"><span data-stu-id="1d082-106">Describes easier, more natural-language ways of scripting filters for collections of objects.</span></span>

## <a name="long-description"></a><span data-ttu-id="1d082-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1d082-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="1d082-108">Förenklad syntax, som introducerades i Windows PowerShell 3,0, gör att du kan bygga vissa filter kommandon utan att använda skript block.</span><span class="sxs-lookup"><span data-stu-id="1d082-108">Simplified syntax, introduced in Windows PowerShell 3.0, lets you build some filter commands without using script blocks.</span></span> <span data-ttu-id="1d082-109">Den förenklade syntaxen påminner mer om naturligt språk och är i första hand användbart med samlingar av objekt som får skickas i kommandon `Where-Object` och `ForEach-Object` deras motsvarande alias `where` och `foreach` .</span><span class="sxs-lookup"><span data-stu-id="1d082-109">The simplified syntax more closely resembles natural language, and is primarily useful with collections of objects that get piped into commands `Where-Object` and `ForEach-Object` and their corresponding aliases `where` and `foreach`.</span></span>

<span data-ttu-id="1d082-110">Du kan använda en metod för medlemmarna i en samling (oftast en matris) utan att referera till den automatiska variabeln `$_` i ett-skript block.</span><span class="sxs-lookup"><span data-stu-id="1d082-110">You can use a method on the members of a collection (most commonly, an array) without referring to the automatic variable `$_` inside a script block.</span></span>

<span data-ttu-id="1d082-111">Tänk på följande två anrop:</span><span class="sxs-lookup"><span data-stu-id="1d082-111">Consider the following two invocations:</span></span>

### <a name="standard-syntax"></a><span data-ttu-id="1d082-112">Standardsyntax</span><span class="sxs-lookup"><span data-stu-id="1d082-112">Standard Syntax</span></span>

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a><span data-ttu-id="1d082-113">Förenklad syntax</span><span class="sxs-lookup"><span data-stu-id="1d082-113">Simplified syntax</span></span>

<span data-ttu-id="1d082-114">Under den förenklade syntaxen behandlas jämförelse operatorer som fungerar på medlemmar av objekt i en samling som parametrar.</span><span class="sxs-lookup"><span data-stu-id="1d082-114">Under the simplified syntax, comparison operators that work on members of objects in a collection are treated as parameters.</span></span> <span data-ttu-id="1d082-115">Du kan anropa en metod för objekt i en samling utan att referera till den automatiska variabeln i `$_` ett-skript block.</span><span class="sxs-lookup"><span data-stu-id="1d082-115">You can invoke a method on objects in a collection without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="1d082-116">Jämför följande två anrop till dem i föregående exempel:</span><span class="sxs-lookup"><span data-stu-id="1d082-116">Compare the following two invocations to those of the previous example:</span></span>
```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

<span data-ttu-id="1d082-117">När båda syntaxerna fungerar returnerar den förenklade syntaxen resultat utan att referera till den automatiska variabeln `$_` i ett-skript block.</span><span class="sxs-lookup"><span data-stu-id="1d082-117">While both syntaxes work, the simplified syntax returns results without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="1d082-118">Metod namnet `GetKeyAlgorithm` behandlas som en parameter för `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="1d082-118">The method name `GetKeyAlgorithm` is treated as a parameter of `ForEach-Object`.</span></span>
<span data-ttu-id="1d082-119">Det andra kommandot returnerar samma resultat, men utan fel, eftersom den förenklade syntaxen inte försöker returnera resultat för objekt för vilka det angivna argumentet inte tillämpades.</span><span class="sxs-lookup"><span data-stu-id="1d082-119">The second command returns the same results, but without errors, because the simplified syntax does not attempt to return results for items for which the specified argument did not apply.</span></span>

<span data-ttu-id="1d082-120">I det här exemplet `Process` skickas egenskapen `Description` som medlems namn parameter till `ForEach-Object` kommandot.</span><span class="sxs-lookup"><span data-stu-id="1d082-120">In this example, the `Process` property `Description` is passed as the member name parameter to the `ForEach-Object` command.</span></span> <span data-ttu-id="1d082-121">Resultaten är beskrivningar av aktiva processer.</span><span class="sxs-lookup"><span data-stu-id="1d082-121">The results are descriptions of active processes.</span></span>

```powershell
Get-Process | foreach Description
```

<span data-ttu-id="1d082-122">I det här exemplet `DirectoryInfo` skickas metoden `GetFiles` som kommandots medlems namn parameter `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="1d082-122">In this example, the `DirectoryInfo` method `GetFiles` is passed as the member name parameter of the `ForEach-Object` command.</span></span>  
<span data-ttu-id="1d082-123">Metoden anropas med Sök mönster parametern `.*` .</span><span class="sxs-lookup"><span data-stu-id="1d082-123">The method is called with the search pattern parameter `.*`.</span></span>  
<span data-ttu-id="1d082-124">Resultaten är `FileInfo` poster för alla dolda filer i UNIX-format i användar arbets kataloger.</span><span class="sxs-lookup"><span data-stu-id="1d082-124">The results are `FileInfo` records for all Unix-style hidden files in user home directories.</span></span> 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a><span data-ttu-id="1d082-125">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="1d082-125">SEE ALSO</span></span>

- [<span data-ttu-id="1d082-126">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="1d082-126">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="1d082-127">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="1d082-127">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="1d082-128">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="1d082-128">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
- [<span data-ttu-id="1d082-129">-Objekt</span><span class="sxs-lookup"><span data-stu-id="1d082-129">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
