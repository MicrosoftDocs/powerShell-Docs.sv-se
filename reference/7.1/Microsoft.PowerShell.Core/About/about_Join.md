---
description: Beskriver hur kopplings operatorn (-JOIN) kombinerar flera strängar till en enda sträng.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: 578d12461a1e915e699970ca17c6f8220eb7fef1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272235"
---
# <a name="about-join"></a><span data-ttu-id="b0c5c-104">Om koppling</span><span class="sxs-lookup"><span data-stu-id="b0c5c-104">About join</span></span>

## <a name="short-description"></a><span data-ttu-id="b0c5c-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b0c5c-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b0c5c-106">Beskriver hur kopplings operatorn (-JOIN) kombinerar flera strängar till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-106">Describes how the join operator (-join) combines multiple strings into a single string.</span></span>

## <a name="long-description"></a><span data-ttu-id="b0c5c-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b0c5c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b0c5c-108">Operatorn Join sammanfogar en uppsättning strängar till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-108">The join operator concatenates a set of strings into a single string.</span></span> <span data-ttu-id="b0c5c-109">Strängarna läggs till i den resulterande strängen i den ordning som de visas i kommandot.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-109">The strings are appended to the resulting string in the order that they appear in the command.</span></span>

### <a name="syntax"></a><span data-ttu-id="b0c5c-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0c5c-110">Syntax</span></span>

<span data-ttu-id="b0c5c-111">Följande diagram visar syntaxen för operatorn Join.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-111">The following diagram shows the syntax for the join operator.</span></span>

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a><span data-ttu-id="b0c5c-112">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b0c5c-112">Parameters</span></span>

<span data-ttu-id="b0c5c-113">String []-anger en eller flera strängar som ska anslutas.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-113">String[] - Specifies one or more strings to be joined.</span></span>

<span data-ttu-id="b0c5c-114">Avgränsare – anger ett eller flera tecken som placeras mellan de sammanfogade strängarna.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-114">Delimiter - Specifies one or more characters placed between the concatenated strings.</span></span> <span data-ttu-id="b0c5c-115">Standardvärdet är ingen avgränsare ("").</span><span class="sxs-lookup"><span data-stu-id="b0c5c-115">The default is no delimiter ("").</span></span>

<span data-ttu-id="b0c5c-116">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b0c5c-116">Remarks</span></span>

<span data-ttu-id="b0c5c-117">Den unära kopplings operatorn (-JOIN <string [] >) har högre prioritet än ett kommatecken.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-117">The unary join operator (-join <string[]>) has higher precedence than a comma.</span></span> <span data-ttu-id="b0c5c-118">Om du skickar en kommaavgränsad lista med strängar till den unära kopplings operatorn skickas bara den första strängen (före det första kommatecknet) till kopplings operatorn.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-118">As a result, if you submit a comma-separated list of strings to the unary join operator, only the first string (before the first comma) is submitted to the join operator.</span></span>

<span data-ttu-id="b0c5c-119">Om du vill använda operatorn enställig koppling, omger du strängarna inom parentes eller lagrar strängarna i en variabel och skickar sedan variabeln till koppling.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-119">To use the unary join operator, enclose the strings in parentheses, or store the strings in a variable, and then submit the variable to join.</span></span>

<span data-ttu-id="b0c5c-120">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="b0c5c-120">For example:</span></span>

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a><span data-ttu-id="b0c5c-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="b0c5c-121">Examples</span></span>

<span data-ttu-id="b0c5c-122">Följande instruktion ansluter tre strängar:</span><span class="sxs-lookup"><span data-stu-id="b0c5c-122">The following statement joins three strings:</span></span>

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

<span data-ttu-id="b0c5c-123">Följande instruktion ansluter tre strängar avgränsade med blank steg:</span><span class="sxs-lookup"><span data-stu-id="b0c5c-123">The following statement joins three strings delimited by a space:</span></span>

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

<span data-ttu-id="b0c5c-124">Följande instruktioner använder en avgränsare med flera tecken för att ansluta till tre strängar:</span><span class="sxs-lookup"><span data-stu-id="b0c5c-124">The following statements use a multiple-character delimiter to join three strings:</span></span>

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

<span data-ttu-id="b0c5c-125">Följande instruktion kopplar ihop raderna i en här-sträng till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-125">The following statement joins the lines in a here-string into a single string.</span></span> <span data-ttu-id="b0c5c-126">Eftersom en här-sträng är en sträng måste raderna i den här-strängen delas innan de kan anslutas.</span><span class="sxs-lookup"><span data-stu-id="b0c5c-126">Because a here-string is one string, the lines in the here-string must be split before they can be joined.</span></span> <span data-ttu-id="b0c5c-127">Du kan använda den här metoden för att återansluta till strängarna i en XML-fil som har sparats i en här-sträng:</span><span class="sxs-lookup"><span data-stu-id="b0c5c-127">You can use this method to rejoin the strings in an XML file that has been saved in a here-string:</span></span>

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a><span data-ttu-id="b0c5c-128">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="b0c5c-128">SEE ALSO</span></span>

[<span data-ttu-id="b0c5c-129">about_Operators</span><span class="sxs-lookup"><span data-stu-id="b0c5c-129">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="b0c5c-130">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="b0c5c-130">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="b0c5c-131">about_Split</span><span class="sxs-lookup"><span data-stu-id="b0c5c-131">about_Split</span></span>](about_Split.md)

