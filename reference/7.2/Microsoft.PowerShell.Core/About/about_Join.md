---
description: Beskriver hur kopplings operatorn (-JOIN) kombinerar flera strängar till en enda sträng.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: d76e95aaeca1b5b94bb1a2216576a985ffb209c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708507"
---
# <a name="about-join"></a><span data-ttu-id="13fa8-103">Om koppling</span><span class="sxs-lookup"><span data-stu-id="13fa8-103">About join</span></span>

## <a name="short-description"></a><span data-ttu-id="13fa8-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="13fa8-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="13fa8-105">Beskriver hur kopplings operatorn (-JOIN) kombinerar flera strängar till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="13fa8-105">Describes how the join operator (-join) combines multiple strings into a single string.</span></span>

## <a name="long-description"></a><span data-ttu-id="13fa8-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="13fa8-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="13fa8-107">Operatorn Join sammanfogar en uppsättning strängar till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="13fa8-107">The join operator concatenates a set of strings into a single string.</span></span> <span data-ttu-id="13fa8-108">Strängarna läggs till i den resulterande strängen i den ordning som de visas i kommandot.</span><span class="sxs-lookup"><span data-stu-id="13fa8-108">The strings are appended to the resulting string in the order that they appear in the command.</span></span>

### <a name="syntax"></a><span data-ttu-id="13fa8-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="13fa8-109">Syntax</span></span>

<span data-ttu-id="13fa8-110">Följande diagram visar syntaxen för operatorn Join.</span><span class="sxs-lookup"><span data-stu-id="13fa8-110">The following diagram shows the syntax for the join operator.</span></span>

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a><span data-ttu-id="13fa8-111">Parameters (Parametrar)</span><span class="sxs-lookup"><span data-stu-id="13fa8-111">Parameters</span></span>

<span data-ttu-id="13fa8-112">String []-anger en eller flera strängar som ska anslutas.</span><span class="sxs-lookup"><span data-stu-id="13fa8-112">String[] - Specifies one or more strings to be joined.</span></span>

<span data-ttu-id="13fa8-113">Avgränsare – anger ett eller flera tecken som placeras mellan de sammanfogade strängarna.</span><span class="sxs-lookup"><span data-stu-id="13fa8-113">Delimiter - Specifies one or more characters placed between the concatenated strings.</span></span> <span data-ttu-id="13fa8-114">Standardvärdet är ingen avgränsare ("").</span><span class="sxs-lookup"><span data-stu-id="13fa8-114">The default is no delimiter ("").</span></span>

<span data-ttu-id="13fa8-115">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="13fa8-115">Remarks</span></span>

<span data-ttu-id="13fa8-116">Den unära kopplings operatorn (-JOIN <string [] >) har högre prioritet än ett kommatecken.</span><span class="sxs-lookup"><span data-stu-id="13fa8-116">The unary join operator (-join <string[]>) has higher precedence than a comma.</span></span> <span data-ttu-id="13fa8-117">Om du skickar en kommaavgränsad lista med strängar till den unära kopplings operatorn skickas bara den första strängen (före det första kommatecknet) till kopplings operatorn.</span><span class="sxs-lookup"><span data-stu-id="13fa8-117">As a result, if you submit a comma-separated list of strings to the unary join operator, only the first string (before the first comma) is submitted to the join operator.</span></span>

<span data-ttu-id="13fa8-118">Om du vill använda operatorn enställig koppling, omger du strängarna inom parentes eller lagrar strängarna i en variabel och skickar sedan variabeln till koppling.</span><span class="sxs-lookup"><span data-stu-id="13fa8-118">To use the unary join operator, enclose the strings in parentheses, or store the strings in a variable, and then submit the variable to join.</span></span>

<span data-ttu-id="13fa8-119">Exempel:</span><span class="sxs-lookup"><span data-stu-id="13fa8-119">For example:</span></span>

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

### <a name="examples"></a><span data-ttu-id="13fa8-120">Exempel</span><span class="sxs-lookup"><span data-stu-id="13fa8-120">Examples</span></span>

<span data-ttu-id="13fa8-121">Följande instruktion ansluter tre strängar:</span><span class="sxs-lookup"><span data-stu-id="13fa8-121">The following statement joins three strings:</span></span>

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

<span data-ttu-id="13fa8-122">Följande instruktion ansluter tre strängar avgränsade med blank steg:</span><span class="sxs-lookup"><span data-stu-id="13fa8-122">The following statement joins three strings delimited by a space:</span></span>

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

<span data-ttu-id="13fa8-123">Följande instruktioner använder en avgränsare med flera tecken för att ansluta till tre strängar:</span><span class="sxs-lookup"><span data-stu-id="13fa8-123">The following statements use a multiple-character delimiter to join three strings:</span></span>

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

<span data-ttu-id="13fa8-124">Följande instruktion kopplar ihop raderna i en här-sträng till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="13fa8-124">The following statement joins the lines in a here-string into a single string.</span></span> <span data-ttu-id="13fa8-125">Eftersom en här-sträng är en sträng måste raderna i den här-strängen delas innan de kan anslutas.</span><span class="sxs-lookup"><span data-stu-id="13fa8-125">Because a here-string is one string, the lines in the here-string must be split before they can be joined.</span></span> <span data-ttu-id="13fa8-126">Du kan använda den här metoden för att återansluta till strängarna i en XML-fil som har sparats i en här-sträng:</span><span class="sxs-lookup"><span data-stu-id="13fa8-126">You can use this method to rejoin the strings in an XML file that has been saved in a here-string:</span></span>

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a><span data-ttu-id="13fa8-127">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="13fa8-127">SEE ALSO</span></span>

[<span data-ttu-id="13fa8-128">about_Operators</span><span class="sxs-lookup"><span data-stu-id="13fa8-128">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="13fa8-129">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="13fa8-129">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="13fa8-130">about_Split</span><span class="sxs-lookup"><span data-stu-id="13fa8-130">about_Split</span></span>](about_Split.md)

