---
title: Bilaga A – syntax för hjälp
description: Den här artikeln förklarar hur du läser och förstår syntaxen för en cmdlet som presenteras av Get-Help.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8e28f66c02370b098f63a0396ef8a724cf3a1bd
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436304"
---
# <a name="appendix-a---help-syntax"></a><span data-ttu-id="8fcf2-103">Bilaga A – syntax för hjälp</span><span class="sxs-lookup"><span data-stu-id="8fcf2-103">Appendix A - Help Syntax</span></span>

<span data-ttu-id="8fcf2-104">I följande exempel visas avsnittet **syntax** i hjälpen för `Get-EventLog` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-104">The following example shows the **SYNTAX** section of the help for the `Get-EventLog` cmdlet.</span></span>

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

<span data-ttu-id="8fcf2-105">Endast den relevanta delen av hjälpen visas i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-105">Only the relevant portion of the help is shown in this example.</span></span>

<span data-ttu-id="8fcf2-106">Syntaxen består i första hand av flera uppsättningar inledande och avslutande hakparenteser ( `[]` ).</span><span class="sxs-lookup"><span data-stu-id="8fcf2-106">The syntax is primarily made up of several sets of opening and closing brackets (`[]`).</span></span> <span data-ttu-id="8fcf2-107">Dessa har två olika betydelser beroende på hur de används.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-107">These have two different meanings depending on how they're used.</span></span> <span data-ttu-id="8fcf2-108">Allt som ingår i hakparenteser är valfritt, om de inte är en uppsättning tomma hakparenteser `[]` .</span><span class="sxs-lookup"><span data-stu-id="8fcf2-108">Anything contained within square brackets is optional unless they're a set of empty square brackets `[]`.</span></span> <span data-ttu-id="8fcf2-109">Tomma hakparenteser visas bara efter en datatyp som `<string[]>` .</span><span class="sxs-lookup"><span data-stu-id="8fcf2-109">Empty square brackets only appear after a datatype such as `<string[]>`.</span></span> <span data-ttu-id="8fcf2-110">Det innebär att en viss parameter kan acceptera fler än ett värde av den typen.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-110">This means that particular parameter can accept more than one value of that type.</span></span>

<span data-ttu-id="8fcf2-111">Den första parametern i den första parameter uppsättningen i `Get-EventLog` är **LogName**.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-111">The first parameter in the first parameter set of `Get-EventLog` is **LogName**.</span></span> <span data-ttu-id="8fcf2-112">LogName omges av hakparenteser, vilket innebär att det är en positions parameter.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-112">LogName is surrounded by square brackets which means that it's a positional parameter.</span></span> <span data-ttu-id="8fcf2-113">Med andra ord är det valfritt att ange namnet på själva parametern så länge det anges på rätt plats.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-113">In other words, specifying the name of the parameter itself is optional as long as it's specified in the correct position.</span></span> <span data-ttu-id="8fcf2-114">Informationen inom vinkelparenteser ( `<>` ) efter parameter namnet anger att det behöver ett enskilt **sträng** värde.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-114">The information in the angle brackets (`<>`) after the parameter name indicates that it needs a single **string** value.</span></span> <span data-ttu-id="8fcf2-115">Hela parameter namnet och data typen omges inte av hakparenteser, så **LogName** -parametern krävs när du använder den här parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-115">The entire parameter name and datatype are not surrounded by square brackets so the **LogName** parameter is required when using this parameter set.</span></span>

```powershell
Get-EventLog [-LogName] <String>
```

<span data-ttu-id="8fcf2-116">Den andra parametern är **InstanceID**.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-116">The second parameter is **InstanceId**.</span></span> <span data-ttu-id="8fcf2-117">Observera att parameter namnet och data typen är båda helt omgiven av hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-117">Notice that the parameter name and the datatype are both completely surrounded by square brackets.</span></span> <span data-ttu-id="8fcf2-118">Det innebär att **InstanceID** -parametern är valfri, inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-118">This means that the **InstanceId** parameter is optional, not mandatory.</span></span> <span data-ttu-id="8fcf2-119">Observera också att **InstanceID** omges av en egen uppsättning hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-119">Also notice that **InstanceId** is surrounded by its own set of square brackets.</span></span> <span data-ttu-id="8fcf2-120">Precis som med parametern **LogName** innebär det att parametern är i position.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-120">As with the **LogName** parameter, this means the parameter is positional.</span></span> <span data-ttu-id="8fcf2-121">Det finns en sista uppsättning hakparenteser efter data typen.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-121">There's one last set of square brackets after the datatype.</span></span> <span data-ttu-id="8fcf2-122">Det innebär att den kan acceptera mer än ett värde i form av en matris eller en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-122">This means that it can accept more than one value in the form of an array or a comma-separated list.</span></span>

```
[[-InstanceId] <Int64[]>]
```

<span data-ttu-id="8fcf2-123">Den andra parameter uppsättningen har en **list** parameter.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-123">The second parameter set has a **List** parameter.</span></span> <span data-ttu-id="8fcf2-124">Det är en växel parameter eftersom det inte finns någon datatype efter parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-124">It's a switch parameter because there's no datatype following the parameter name.</span></span> <span data-ttu-id="8fcf2-125">När **list** parametern anges är värdet **True**.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-125">When the **List** parameter is specified, the value is **True**.</span></span> <span data-ttu-id="8fcf2-126">Värdet är **false**när det inte anges.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-126">When it's not specified, the value is **False**.</span></span>

```
[-List]
```

<span data-ttu-id="8fcf2-127">Information om syntaxen för ett kommando kan också hämtas med `Get-Command` hjälp av parametern **syntax** .</span><span class="sxs-lookup"><span data-stu-id="8fcf2-127">The syntax information for a command can also be retrieved using `Get-Command` using the **Syntax** parameter.</span></span> <span data-ttu-id="8fcf2-128">Det här är en praktisk genväg som jag använder hela tiden.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-128">This is a handy shortcut that I use all the time.</span></span> <span data-ttu-id="8fcf2-129">Det gör att du snabbt kan lära dig hur du använder ett kommando utan att behöva gå igenom flera sidor med hjälp information.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-129">It allows me to quickly learn how to use a command without having to sift through multiple pages of help information.</span></span> <span data-ttu-id="8fcf2-130">Om jag behöver mer information återgår jag till att använda det faktiska hjälp innehållet.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-130">If I end up needing more information, then I'll revert to using the actual help content.</span></span>

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

<span data-ttu-id="8fcf2-131">Mer information om hur du använder hjälp systemet i PowerShell blir den enklare att komma ihåg alla de olika olika delarna.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-131">The more you use the help system in PowerShell, the easier remembering all of the different nuances becomes.</span></span> <span data-ttu-id="8fcf2-132">Innan du vet det blir det andra natur.</span><span class="sxs-lookup"><span data-stu-id="8fcf2-132">Before you know it, using it becomes second nature.</span></span>
