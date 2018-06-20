---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: e4588e8c69efb965cd33c273ad09a8bef8e9bf16
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189575"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="34d05-102">Extrahera och parsa strukturerade objekt från sträng</span><span class="sxs-lookup"><span data-stu-id="34d05-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="34d05-103">Det skapar också några ytterligare funktioner för ConvertFrom-String-cmdlet:</span><span class="sxs-lookup"><span data-stu-id="34d05-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="34d05-104">Tar bort egenskapen text omfattning som standard.</span><span class="sxs-lookup"><span data-stu-id="34d05-104">Removes the extent text property by default.</span></span> <span data-ttu-id="34d05-105">Du kan inkludera den med parametern - IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="34d05-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="34d05-106">Många learning algoritmen felkorrigeringar från MVP och community-feedback.</span><span class="sxs-lookup"><span data-stu-id="34d05-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="34d05-107">En ny parameter - UpdateTemplate spara resultaten av Inlärningsalgoritmen till en kommentar i mallfilen.</span><span class="sxs-lookup"><span data-stu-id="34d05-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="34d05-108">Detta gör learning bearbeta (den långsammaste delen) en enstaka kostnad.</span><span class="sxs-lookup"><span data-stu-id="34d05-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="34d05-109">Kör konvertera strängen med en mall som innehåller kodade Inlärningsalgoritmen är nu nästan omedelbar.</span><span class="sxs-lookup"><span data-stu-id="34d05-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="34d05-110">Extrahera och parsa strukturerade objekt från strängen innehåll</span><span class="sxs-lookup"><span data-stu-id="34d05-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="34d05-111">I samarbete med [Microsoft Research](http://research.microsoft.com/), en ny **ConvertFrom sträng** cmdlet har lagts till.</span><span class="sxs-lookup"><span data-stu-id="34d05-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="34d05-112">Denna cmdlet har stöd för två lägen: basic avgränsade parsning och exempel-driven parsning av genereras automatiskt.</span><span class="sxs-lookup"><span data-stu-id="34d05-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="34d05-113">Avgränsad parsning som standard delar inmatningen vid blanksteg och tilldelar grupperna egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="34d05-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="34d05-114">Du kan anpassa avgränsaren:</span><span class="sxs-lookup"><span data-stu-id="34d05-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="34d05-115">1 \[C:\\temp\] &gt; &gt; ”Hello World” | ConvertFrom sträng | Format-Table-automatiskt</span><span class="sxs-lookup"><span data-stu-id="34d05-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="34d05-116">P1 P2</span><span class="sxs-lookup"><span data-stu-id="34d05-116">P1    P2</span></span>
--    --

<span data-ttu-id="34d05-117">Cmdleten stöder också automatiskt genererade exempel datadrivna parsning baserat på de [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) forskning arbete i [Microsoft Research](http://research.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="34d05-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="34d05-118">Överväg att en textbaserad adressbok för att komma igång:</span><span class="sxs-lookup"><span data-stu-id="34d05-118">To get started, consider a text-based address book:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

<span data-ttu-id="34d05-119">Kopiera några exempel till en fil som du vill använda som mallen:</span><span class="sxs-lookup"><span data-stu-id="34d05-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



<span data-ttu-id="34d05-120">Placera klammerparenteser runt data som du vill extrahera, ger den ett namn som du gör.</span><span class="sxs-lookup"><span data-stu-id="34d05-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="34d05-121">Eftersom den **namn** egenskapen (och dess associerade andra egenskaper) kan visas flera gånger, Använd en asterisk (\*) att indikera att detta resulterar i flera poster (i stället för att extrahera en massa egenskaper till en post):</span><span class="sxs-lookup"><span data-stu-id="34d05-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="34d05-122">Från den här uppsättningen exempel **ConvertFrom sträng** kan nu automatiskt extrahera objektbaserad utdata från indatafiler med liknande struktur.</span><span class="sxs-lookup"><span data-stu-id="34d05-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="34d05-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="34d05-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="34d05-124">&gt;&gt; Get-innehåll. \\addresses.output.txt | ConvertFrom-String - TemplateFile. \\addresses.template.txt | &gt; &gt; &gt; Format-Table-automatiskt</span><span class="sxs-lookup"><span data-stu-id="34d05-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="34d05-125">ExtentText namn stad tillstånd</span><span class="sxs-lookup"><span data-stu-id="34d05-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="34d05-126">ANA Trujillo...                ANA Trujillo Redmond, WA Antonio Moreno...              Antonio Moreno Renton WA Thomas Hardy...                Thomas Hardy Seattle WA Christina Berglund...          Christina Berglund Redmond WA Hanna Moos...                  Hanna Moos Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="34d05-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="34d05-127">Att göra ytterligare datamanipulering på extraherade text i **ExtentText** egenskapen fångar oformaterade texten som posten extraherades.</span><span class="sxs-lookup"><span data-stu-id="34d05-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="34d05-128">Ge feedback om den här funktionen eller dela innehåll som du har problem med skrivning till exempel e-postmeddelande till <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="34d05-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>
